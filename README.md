# nod

[![NPM version](https://img.shields.io/npm/v/generator-nod.svg?style=flat-square)](https://npmjs.org/package/generator-nod)
[![Build Status](https://img.shields.io/travis/diegohaz/nod/master.svg?style=flat-square)](https://travis-ci.org/diegohaz/nod) [![Coverage Status](https://img.shields.io/codecov/c/github/diegohaz/nod/master.svg?style=flat-square)](https://codecov.io/gh/diegohaz/nod/branch/master)

NodeJS module generator/boilerplate.

<p align="center"><img src="https://cloud.githubusercontent.com/assets/3068563/21958520/77e4f45e-da97-11e6-9685-fe380a9cce3d.gif"></p>

## Features

-   [**Babel**](https://babeljs.io/) - Write next generation JavaScript today.
-   [**Jest**](https://facebook.github.io/jest) - JavaScript testing framework used by Facebook.
-   [**ESLint**](http://eslint.org/) - Make sure you are writing a quality code.
-   [**Prettier**](https://prettier.io/) - Enforces a consistent style by parsing your code and re-printing it.
-   [**Flow**](https://flowtype.org/) - A static type checker for JavaScript used heavily within Facebook.
-   [**Travis CI**](https://travis-ci.org) - Automate tests and linting for every push or pull request.
-   [**Documentation**](http://documentation.js.org/) - A documentation system so good, you'll actually write documentation.
-   [**Conventional Changelog**](https://github.com/conventional-changelog/conventional-changelog) - Generate a changelog from git metadata.

## Install

The easiest way to use **nod** is through the Yeoman Generator.

```sh
$ npm install -g yo generator-nod
$ yo nod
```

If you don't want to use the generator, you can also download or `git clone` this repo

```sh
$ git clone https://github.com/diegohaz/nod my-module
$ cd my-module
$ rm -rf .git
$ npm install # or yarn
```

Just make sure to edit `package.json`, `README.md` and `LICENSE` files accordingly with your module's info.

## Commands

```sh
$ npm test # run tests with Jest
$ npm run coverage # run tests with coverage and open it on browser
$ npm run lint # lint code
$ npm run docs # generate docs
$ npm run build # generate docs and transpile code
```

### Publish

```sh
$ npm version patch|minor|major
$ npm publish
```

It'll automatically run `test`, `lint`, `docs`, `build` and generate CHANGELOG.md file.

## Removing stuff

<details><summary><strong>Flow</strong></summary>

1. Delete `.flowconfig` file.

2. Remove `flow` from `package.json`:

    ```diff
    "scripts": {
      "test": "jest",
    - "flow": "flow check",
      "clean": "rimraf dist",
    - "flowbuild": "flow-copy-source src dist",
    - "prebuild": "npm run docs && npm run clean && npm run flowbuild",
    + "prebuild": "npm run docs && npm run clean",
      "build": "babel src -d dist",
    },
    "devDependencies": {
      "@babel/preset-env": "^7.1.0",
    - "@babel/preset-flow": "^7.0.0",
      "eslint-config-prettier": "^3.0.1",
    - "eslint-plugin-flowtype": "^2.50.0",
    - "eslint-plugin-flowtype-errors": "^3.5.1",
      "eslint-plugin-prettier": "^2.6.2",
    - "flow-bin": "^0.81.0",
    - "flow-copy-source": "^2.0.2",
      "husky": "^1.0.0-rc.14"
    }
    ```

3. Remove `flow` from `.babelrc`:

    ```diff
    {
      "presets": [
        "@babel/preset-env",
    -   "@babel/preset-flow"
      ],
      "plugins": [
        "@babel/plugin-proposal-class-properties"
      ]
    }
    ```
    
4. Remove `flow` from `.eslintrc`:

    ```diff
    {
      "parser": "babel-eslint",
      "extends": [
        "airbnb-base",
    -   "plugin:flowtype/recommended",
        "plugin:prettier/recommended",
    -   "prettier/flowtype"
      ],
      "plugins": [
    -   "flowtype",
    -   "flowtype-errors"
      ],
      "env": {
        "jest": true
      },
      "rules": {
    -   "flowtype-errors/show-errors": "error"
      }
    }
    ```

5. Run `yarn`.

</details>

<details><summary><strong>Documentation</strong></summary>

1. Remove `documentation` from `package.json`:

```diff
"scripts": {
  "test": "jest",
- "docs": "documentation readme src --section=API",
- "postdocs": "git add README.md",
  "clean": "rimraf dist",
- "prebuild": "npm run docs && npm run clean",
+ "prebuild": "npm run clean",
  "build": "babel src -d dist",
},
"devDependencies": {
  "@babel/cli": "^7.1.0",
- "documentation": "^8.0.0",
  "eslint": "^5.6.0",
}
```

2. Run `yarn`.

</details>

## Built with Nod

_You can use those modules as a reference when creating yours. If you have built something with Nod, send a PR (try to write a helpful description for Nod users)._

-   [**styled-tools**](https://github.com/diegohaz/styled-tools) - Module using `flow-typed`, targeted to browser.
-   [**styled-theme**](https://github.com/diegohaz/styled-theme) - Module with `gh-pages`, targeted to browser.
-   [**webpack-blocks-happypack**](https://github.com/diegohaz/webpack-blocks-happypack) - Uses Jest snapshots.
-   [**webpack-blocks-split-vendor**](https://github.com/diegohaz/webpack-blocks-split-vendor) - Has peer dependencies.

[More examples](https://github.com/search?l=Markdown&q=generator-nod-2196F3&type=Code)

## API

<!-- Generated by documentation.js. Update this documentation by updating the source code. -->

#### Table of Contents

-   [sayHello](#sayhello)
    -   [Parameters](#parameters)

### sayHello

This function says hello.

#### Parameters

-   `name` **[string](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/String)** Some name to say hello for.

Returns **[string](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/String)** The hello.

## License

MIT © [Diego Haz](https://github.com/diegohaz)
