# eslint-config-zeal

[![npm version](https://badge.fury.io/js/eslint-config-zeal.svg)](https://www.npmjs.com/package/eslint-config-zeal)
[![CircleCI](https://circleci.com/gh/CodingZeal/eslint-config-zeal.svg?style=shield)](https://circleci.com/gh/CodingZeal/eslint-config-zeal)
[![License](https://img.shields.io/badge/license-MIT-blue.svg)](https://opensource.org/licenses/MIT)
[![Greenkeeper badge](https://badges.greenkeeper.io/CodingZeal/eslint-config-zeal.svg)](https://greenkeeper.io/)

A [shareable ESLint config](http://eslint.org/docs/developer-guide/shareable-configs) for Zeal's coding style.

Zeal's JavaScript coding style is still evolving as we do more projects, but this represents our current thinking.

## Install

To make use of this configuration, install eslint, babel-eslint,
eslint-plugin-import, eslint-plugin-import-order-alphabetical and this package
as development dependencies of your project:

```
npm install eslint babel-eslint eslint-plugin-import eslint-plugin-import-order-alphabetical eslint-config-zeal --save-dev
```

These packages are marked as peer dependencies, so you will get a warning if they're not installed.

## Usage

Add this to your `.eslintrc` file:

```
{
  "extends": "zeal"
}
```

_Note: ESLint assumes the `eslint-config-` prefix, so we can omit it._

You can override settings from the configuration(s) by adding them directly to your `.eslintrc` file.

We have added some additional optional configurations that you can add on top of the base `zeal` config:

- `zeal/ramda`: Adds rules for [Ramda.js](https://ramdajs.com/) development. You'll need to install [eslint-plugin-ramda](https://github.com/ramda/eslint-plugin-ramda) to use this configuration.
- `zeal/react`: Adds rules for [React](https://github.com/reactjs) development.
  You'll need to install
  [eslint-plugin-react](https://github.com/yannickcr/eslint-plugin-react), [eslint-plugin-react-hooks](https://www.npmjs.com/package/eslint-plugin-react-hooks), and
  [eslint-plugin-jsx-a11y](https://github.com/evcohen/eslint-plugin-jsx-a11y) to
  use this configuration.
- `zeal/react-native`: Adds rules for [React Native](https://facebook.github.io/react-native/) development. You'll need to install [eslint-plugin-react-native](https://github.com/intellicode/eslint-plugin-react-native) to use this configuration.
- `zeal/mocha`: Overrides rules for use with [Mocha](https://mochajs.org/). We recommend creating a separate `.eslintrc` file in the directory containing your tests and `extend`ing this config there.
- `zeal/chai`: Overrides rules for use with [Chai](http://chaijs.com/). We recommend creating a separate `.eslintrc` file in the directory containing your tests and `extend`ing this config there.
- `zeal/jest`: Adds and overrides rules for use with [Jest](http://facebook.github.io/jest/). You'll have to install [eslint-plugin-jest](https://www.npmjs.com/package/eslint-plugin-jest) to use this configuration. We recommend creating a separate `.estlintrc` file in the directory containing your tests and `extend`ing this config there.

You can extend multiple configurations using an array:

```
{
  "extends": ["zeal", "zeal/react"]
}
```

See the [ESLint configuration documentation](http://eslint.org/docs/user-guide/configuring) for more information on configuring ESLint.

## Usage with Ramda

If you're using [Ramda.js](https://ramdajs.com/) in your project, make sure you have [eslint-plugin-ramda](https://github.com/ramda/eslint-plugin-ramda) installed as well:

```
npm install eslint-plugin-ramda --save-dev
```

Then, in your `.eslintrc` file, extend both the `zeal` and `zeal/ramda` configurations:

```
{
  "extends": ["zeal", "zeal/ramda"]
}
```

## Usage With React

If you're using this package in a React project, make sure you have
[eslint-plugin-react](https://github.com/yannickcr/eslint-plugin-react),
[eslint-plugin-react-hooks](https://www.npmjs.com/package/eslint-plugin-react-hooks)
and [eslint-plugin-jsx-a11y](https://github.com/evcohen/eslint-plugin-jsx-a11y)
installed as well:

```
npm install eslint-plugin-react eslint-plugin-react-hooks eslint-plugin-jsx-a11y --save-dev
```

Then, in your `.eslintrc` file, extend both the `zeal` and `zeal/react` configurations:

```
{
  "extends": ["zeal", "zeal/react"]
}
```

## Usage with React Native

If you're using this package in a React Native project, make sure you have both [eslint-plugin-react](https://github.com/yannickcr/eslint-plugin-react) and [eslint-plugin-react-native](https://github.com/intellicode/eslint-plugin-react-native) installed as well:

```
npm install eslint-plugin-react eslint-plugin-react-native --save-dev
```

Then, in your `.eslintrc` file, extend the `zeal`, `zeal/react`, and `zeal/react-native` configurations:

```
{
  "extends": ["zeal", "zeal/react", "zeal/react-native"]
}
```

## Usage With Webpack

This configuration uses [eslint-plugin-import](https://github.com/benmosher/eslint-plugin-import). If your project uses Webpack, you'll need to add [eslint-import-resolver-webpack](https://www.npmjs.com/package/eslint-import-resolver-webpack):

```
npm install eslint-import-resolver-webpack
```

You'll also need to add the following to your `.eslintrc`:

```
"settings": {
  "import/resolver": "webpack"
}
```

or, if your webpack config file is not in the default location:

```
"settings": {
  "import/resolver": {
    "webpack": { "config": "path/to/webpack.config.js" }
  }
}
```

## Usage With Prettier

To use this configuration with [prettier](https://github.com/prettier/prettier), use [eslint-config-prettier](https://github.com/prettier/eslint-config-prettier) to override any conflicting rules:

```
npm install eslint-config-prettier --save-dev
```

Then, in your `.eslintrc` file, extend the `prettier` (and `prettier/react`) configurations after any `zeal` configurations. For example:

```
{
  "extends": ["zeal", "zeal/react", "prettier", "prettier/react"]
}
```

That way, the `prettier` configurations will override any `zeal` configurations that would otherwise conflict with prettier's formatting.

## Supported Versions

This plugin contains all of the rules available in:

- [ESLint](http://eslint.org/): 6.5.1
- [eslint-plugin-ramda](https://github.com/ramda/eslint-plugin-ramda): 2.5.1
- [eslint-plugin-import](https://github.com/benmosher/eslint-plugin-import): 2.18.2
- [eslint-plugin-import-order-alphabetical](https://www.npmjs.com/package/eslint-plugin-import-order-alphabetical): 1.0.0
- [eslint-plugin-jest](https://www.npmjs.com/package/eslint-plugin-jest): 22.19.0
- [eslint-plugin-jsx-a11y](https://github.com/evcohen/eslint-plugin-jsx-a11y): 6.2.3
- [eslint-plugin-react](https://github.com/yannickcr/eslint-plugin-react): 7.16.0
- [eslint-plugin-react-hooks](https://www.npmjs.com/package/eslint-plugin-react-hooks): 2.1.2
- [eslint-plugin-react-native](https://github.com/intellicode/eslint-plugin-react-native): 3.7.0

## License

Authored by the Engineering Team of [Coding ZEAL](https://codingzeal.com?utm_source=github)

Copyright (c) 2016 - 2019 Zeal, LLC. Licensed under the [MIT license](https://opensource.org/licenses/MIT).
