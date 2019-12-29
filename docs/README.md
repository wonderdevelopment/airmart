# Airmart – React Native e-commerce app template

Inside you will found more than 30 screens for creating full-functionality e-commerce application.

## Getting Started

These instructions will get you a copy of the project up and running on your local machine for development and testing purposes. See deployment for notes on how to deploy the project on a live system.
Dowload package unzip go to dir

### Prerequisites

For running and installation Airmart you need 

Install [Node.js](https://nodejs.org/en/download/) on your local machine.

[NPM](https://www.npmjs.com/get-npm) or [Yarn](https://yarnpkg.com/lang/en/docs/install/) manager 

```
$ brew install node

$ brew install yarn
```

### Installing


1. Go to Airmart directory ```cd airmart_package```
2. Install packages ```yarn install```                   
3. Run Expo Airmart ```yarn start``` 


## Coding style tests

For test run ```yarn test``` 

## Built With npm packages:

* [@expo/vector-icons](https://github.com/expo/vector-icons) - Vector icons library for expo
* [axios](https://github.com/axios/axios) - Promise based HTTP client for the browser and node.js
* [expo](https://expo.io/) - Build, deploy, and iterate on native Android, iOS from the same JavaScript codebase.
* [expo-asset](https://docs.expo.io/versions/latest/sdk/asset/) - Provides an interface to Expo's asset system. 
* [expo-font](https://docs.expo.io/versions/latest/guides/using-custom-fonts/) - Adding a custom font to your Expo app
* [react](https://reactjs.org/) - A JavaScript library for building user interfaces
* [react-native](https://facebook.github.io/react-native/) - A framework for building native apps with React.
* [react-native-elements](https://react-native-elements.github.io/react-native-elements/) - Cross Platform React Native UI Toolkit.
* [react-native-keyboard-aware-scrollview](https://www.npmjs.com/package/react-native-keyboard-aware-scrollview) - A helper component meant to be used as a drop-in replacement for RN ScrollView
* [react-native-swipeout](https://github.com/dancormier/react-native-swipeout) - iOS-style swipeout buttons that appear from behind a component
* [react-native-swiper-flatlist](https://www.npmjs.com/package/react-native-swiper-flatlist) - Swiper FlatList component
* [react-navigation](https://reactnavigation.org/) - Routing and navigation for your React Native apps
* [react-native-gesture-handler](https://www.npmjs.com/package/react-native-gesture-handler) - Declarative API exposing platform native touch and gesture system to React Native.

## File structure

- __airmart__
   - [App.js](App.js)
   - [README.md](README.md)
   - __\_\_tests\_\___
     - [App\-test.js](__tests__/App-test.js)
   - [app.json](app.json)
   - __assets__
     - __fonts__
       - [SpaceMono\-Regular.ttf](assets/fonts/SpaceMono-Regular.ttf)
       - [WorkSans\-Bold.ttf](assets/fonts/WorkSans-Bold.ttf)
       - [WorkSans\-Regular.ttf](assets/fonts/WorkSans-Regular.ttf)
       - [WorkSans\-SemiBold.ttf](assets/fonts/WorkSans-SemiBold.ttf)
     - __images__
       - [icon.png](assets/images/icon.png)
       - [robot\-dev.png](assets/images/robot-dev.png)
       - [robot\-prod.png](assets/images/robot-prod.png)
       - [splash.png](assets/images/splash.png)
   - [babel.config.js](babel.config.js)
   - __components__
     - [ColorRadioButtons.js](components/ColorRadioButtons.js)
     - [IconWithBadge.js](components/IconWithBadge.js)
     - [SizeRadioButtons.js](components/SizeRadioButtons.js)
     - [StyledText.js](components/StyledText.js)
     - [TabBarIcon.js](components/TabBarIcon.js)
     - __\_\_tests\_\___
       - [StyledText\-test.js](components/__tests__/StyledText-test.js)
   - __constants__
     - [Api.js](constants/Api.js)
     - [Colors.js](constants/Colors.js)
     - [Layout.js](constants/Layout.js)
   - __navigation__
     - [AppNavigator.js](navigation/AppNavigator.js)
     - [AuthNavigator.js](navigation/AuthNavigator.js)
     - [MainTabNavigator.js](navigation/MainTabNavigator.js)
   - [package\-lock.json](package-lock.json)
   - [package.json](package.json)
   - __screens__
     - [AccountCreatedSuccessScreen.js](screens/AccountCreatedSuccessScreen.js)
     - [AuthScreen.js](screens/AuthScreen.js)
     - [CartScreen.js](screens/CartScreen.js)
     - [CheckoutScreen.js](screens/CheckoutScreen.js)
     - [ChildCategoriesScreen.js](screens/ChildCategoriesScreen.js)
     - [DeliveryAddressScreen.js](screens/DeliveryAddressScreen.js)
     - [DeliveryScreen.js](screens/DeliveryScreen.js)
     - [DiscountProductsScreen.js](screens/DiscountProductsScreen.js)
     - [HomeScreen.js](screens/HomeScreen.js)
     - [LostPasswordScreen.js](screens/LostPasswordScreen.js)
     - [OrderScreen.js](screens/OrderScreen.js)
     - [OrdersScreen.js](screens/OrdersScreen.js)
     - [ParentCategoriesScreen.js](screens/ParentCategoriesScreen.js)
     - [ProductInformationScreen.js](screens/ProductInformationScreen.js)
     - [ProductScreen.js](screens/ProductScreen.js)
     - [ProfileScreen.js](screens/ProfileScreen.js)
     - [RegistrationScreen.js](screens/RegistrationScreen.js)
     - [ReviewsScreen.js](screens/ReviewsScreen.js)
     - [SavedSuccessfulScreen.js](screens/SavedSuccessfulScreen.js)
     - [SuccessReviewScreen.js](screens/SuccessReviewScreen.js)
     - [ThankForOrderScreen.js](screens/ThankForOrderScreen.js)
     - [WriteReviewScreen.js](screens/WriteReviewScreen.js)

### - App.js

Main initialisation app file

1) App loader, while app loading  

```
if (!this.state.isLoadingComplete && !this.props.skipLoadingScreen) {
  return (
      <AppLoading
        startAsync={this._loadResourcesAsync}
        onError={this._handleLoadingError}
        onFinish={this._handleFinishLoading}
      />
  );
}
``` 

2) Async Font loading function. Here you can change path to your fonts 
```
_loadResourcesAsync = async () => {
    return Promise.all([
      Asset.loadAsync([
        require("./assets/images/robot-dev.png"),
        require("./assets/images/robot-prod.png")
      ]),
      Font.loadAsync({
        // This is the font that we are using for our tab bar
        ...Icon.Ionicons.font,
        // We include SpaceMono because we use it in DeliveryAddressScreen.js. Feel free
        // to remove this if you are not using it in your app
        "space-mono": require("./assets/fonts/SpaceMono-Regular.ttf"),
        "work-sans": require("./assets/fonts/WorkSans-Regular.ttf"),
        "work-sans-bold": require("./assets/fonts/WorkSans-Bold.ttf"),
        "work-sans-semibold": require("./assets/fonts/WorkSans-SemiBold.ttf")
      })
    ]);
};
``` 

3) Initial screen with calling Navigator component from /navigation/AppNavigator
```
<View style={styles.container}>
    {Platform.OS === "ios" && <StatusBar barStyle="default" />}
    <AppNavigator />
</View>
```

    


### - app.json

Expo configuration file. Here you can set path to app icon, change name and description for expo repo.


### - package.json

Configuration file with js packages

### - assets 
All assets: fonts, images etc.

#### -- fonts

Custom local fonts location

#### -- images

Images location

### - components

Custom components for screens, like buttons and badges

### - constants

Colors, Sizes, Layouts Constants for template customizing  

### - navigation

Navigation files: for bottom tab navigator, Auth navigation and Main navigation

### - screens

All screens witch uses in app

## Contributing

For Contributing please email: yes@wonder.network
 
## Authors

* [**Wonder Network**](https://wonder.network)


## License

This project is licensed under commercial license 

## Acknowledgments

* Happy coding !
