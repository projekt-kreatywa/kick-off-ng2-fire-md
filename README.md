# kick-off-ng2-fire-md

this incarnation of kick-off template is a progressive web app built with [angular2](https://angular.io/) + [firebase](https://firebase.google.com/) + 
[google material design](https://www.google.com/design/spec/material-design/introduction.html)


[![](https://kick-off-ng2-fire-md-4cc50.firebaseapp.com/assets/pomegranate-logo-002-header.svg)](https://kick-off-ng2-fire-md-4cc50.firebaseapp.com/)

---


## table of contents

- [kick-off-ng2-fire-md](#kick-off-ng2-fire-md)
  * [table of contents](#table-of-contents)
  * [what is this](#what-is-this)
  * [the app](#the-app)
  * [used libraries, guides, etc.](#used-libraries--guides--etc)
    + [libraries](#libraries)
    + [guides](#guides)
    + [other resources](#other-resources)
  * [installation](#installation)
  * [firebase configuration](#firebase-configuration)
  * [development with angular-cli](#development-with-angular-cli)
    + [code scaffolding](#code-scaffolding)
    + [build](#build)
    + [tests](#tests)
      - [unit tests](#unit-tests)
      - [e2e tests](#e2e-tests)
    + [deploying to github pages](#deploying-to-github-pages)
    + [further help](#further-help)
  * [using @angular/flex-layout module](#using--angular-flex-layout-module)
    + [fast start](#fast-start)
    + [npm](#npm)
    + [application usages](#application-usages)
    + [further help](#further-help-1)
  * [credits](#credits)
  * [license](#license)

---

## what is this
kick-off-ng2-fire-md is an incarnation of kick-off-template-project. this time it is a template for a progressive web app built with [angular2](https://angular.io/) + [firebase](https://firebase.google.com/) + 
[google material design](https://www.google.com/design/spec/material-design/introduction.html)

currently it contains following features:
 * social media login (facebook, twitter, google+ and github)
 * personal 'todo' item list
 * chat with other users
 
the project was generated with [angular-cli](https://github.com/angular/angular-cli) version 1.0.0-beta.21 and is a clone of [angular2-firebase-material-demo](https://github.com/tarlepp/angular2-firebase-material-demo) by [tarleoo](https://github.com/tarlepp)

## the app

currently the application lives at [https://kick-off-ng2-fire-md-4cc50.firebaseapp.com/](https://kick-off-ng2-fire-md-4cc50.firebaseapp.com/)

[![qr code to the application](https://raw.githubusercontent.com/projekt-kreatywa/kick-off-ng2-fire-md/master/kick-off-ng2-fire-md-url-dynamic.png)](https://kick-off-ng2-fire-md-4cc50.firebaseapp.com/)

while the demo of the seed application can be found at [https://fir-todo-v3.firebaseapp.com/](https://fir-todo-v3.firebaseapp.com/)

## used libraries, guides, etc.

### libraries
 * [angular 2](https://github.com/angular/angular)
 * [material design for angular 2](https://github.com/angular/material2)
 * [angularfire2](https://github.com/angular/angularfire2)
 * [angular2-moment](https://github.com/urish/angular2-moment)
 * [angular-cli](https://github.com/angular/angular-cli)
 
### guides
 * [angular 2 style guide](https://angular.io/docs/ts/latest/guide/style-guide.html)
 
### other resources
 * [firebase](https://firebase.google.com/)
 * [material design](https://www.google.com/design/spec/material-design/)

---

## installation
first of all you have to install ```npm``` and ```node.js``` to your box. installation instructions can
be found [here](https://github.com/joyent/node/wiki/installing-node.js-via-package-manager). 

note that ```node.js 6.x``` is required.

```bash
$ git clone https://github.com/projekt-kreatywa/kick-off-ng2-fire-md.git
$ cd kick-off-ng2-fire-md

# install the project's dependencies with npm
$ npm install

# fast install (via yarn, https://yarnpkg.com)
$ yarn install  # or yarn
```
---

## firebase configuration
see `/src/app/config/config.ts_example` file and copy it to `/src/app/config/config.ts` file and make necessary changes to it. note that you need a [firebase account](https://firebase.google.com/) to get all necessary config values.

if you are not familiar with firebase and/or don't have a firebase developer account, sign up quickly with your google id here: [https://firebase.google.com/](https://firebase.google.com/).

after you have created new application you will need to make some [security rules](https://firebase.google.com/docs/database/security/quickstart) 
for the used data storage. below is configuration that this demo application uses, so you can use the same within your 
application.

```
{
    "rules": {
      "messages": {
          ".write": "auth !== null",
          ".read": "auth !== null"
      },
      "todos": {
        "$uid": {
          // grants write access to the owner of this user account whose uid must exactly match the key ($uid)
          ".write": "auth !== null && auth.uid === $uid",
          // grants read access to any user who is logged in with facebook
          ".read": "auth !== null && auth.uid === $uid"
        }
      }
    }
}
```

these rules ensure that 'todo' items are show only to user who made those. also chat messages requires that user is
logged in to read / write those.

---

## development with angular-cli
to start developing in the project run:

```bash
$ npm start
# or
$ ng serve
```

then head to `http://localhost:4200` in your browser.

### code scaffolding
run `ng generate component component-name` to generate a new component. you can also use `ng generate directive/pipe/service/class`.

### build
run `ng build` to build the project. the build artifacts will be stored in the `dist/` directory. use the `-prod` flag for a production build.

### tests

#### unit tests
to run tests run:

```bash
$ npm test
# or
$ ng test
```

#### e2e tests
to run tests run:

```bash
$ npm run e2e
# or
$ ng e2e
```

### deploying to github pages

run `ng github-pages:deploy` to deploy to github pages.

### further help

to get more help on the `angular-cli` use `ng --help` or check out the [angular-cli readme](https://github.com/angular/angular-cli/blob/master/readme.md).

---

## using @angular/flex-layout module

this will require a bit of footwork until npm install of [@angular/flex-layout](https://github.com/angular/flex-layout) is available via standard `npm i @angular/flex-layout` which will be after the the flex-layout v1.0.0-beta.1 release (week of december 20, 2016).

### fast start 

installing flex-layout with npm is **not yet** available. developers can easily install this `@angular/flex-layout` library using a **local build** and directory copy:

```console
gulp build:release
ditto ./dist/@angular/flex-layout <your project>/node_modules/@angular/flex-layout
```

### npm

the expected deployment process to **npm** (and the standardized use of `npm i @angular/flex-layout`) is **not** yet available. npm installs will be available after the the flex-layout v1.0.0-beta.1 release (week of december 20, 2016).

### application usages
in their application module, developers import the global layout api directives (as shown below): 

```ts
// demo-app-module.ts

import { flexlayoutmodule } from '@angular/flex-layout';

@ngmodule({
  imports: [
    browsermodule, commonmodule, formsmodule, httpmodule,  // import ng2 core modules
    flexlayoutmodule.forroot(),                            // import dependency on flex-layout
  ], 
)}
export class demoappmodule { }
```

in their component templates, developers easily use the layout api to build
complex, dynamic layouts:

```html
<div fx-layout="row">
  <div [fx-layout]="firstcol" [fx-flex]="firstcolwidth" >
    <div fx-flex="27%"> first item in row  </div>
    <div fx-flex      > second item in row </div>
  </div>
  <div [fx-layout]="secondcol" flex >
    <div fx-flex       > first item in column  </div>
    <div fx-flex="33px"> second item in column </div>
  </div>
</div>
``` 

### further help

to get more help on the installation and use of @angular/flex-layout check out [flex-layout readme](https://github.com/angular/flex-layout)

---

## credits


- [rafszul](https://github.com/rafszul) for [projekt:kreatywa](https://github.com/projekt-kreatywa)
- tarmo leppänen - author of the [seed repo](https://github.com/tarlepp/angular2-firebase-material-demo) 

---

## license
[the mit license (mit)](license)