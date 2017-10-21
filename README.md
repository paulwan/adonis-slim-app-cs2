# Adonis Slim App (using CoffeeScript *.coffee files)

The Adonis slim app is the tinest boilerplate to create Adonisjs applications with minimal footprint and you get all the goodies of Adonis IoC container, autoloading, ace commands etc.

## What's next?

This project structure can scale as you go, simply execute the `ace` commands to create **Controllers**, **Models**, etc for you.

Also make sure to read the [guides](http://dev.adonisjs.com/docs/4.0/installation)

## Steps for CoffeeScript support in Adonis

* NOTE: nodemon is CoffeeScript aware, so just pass it server.coffee!
* See: https://github.com/remy/nodemon

1) Changes to /usr/local/lib/node_modules/@adonisjs/cli/src/Commands/Serve/index.js

* Change 'server.js' to 'server.coffee'
* Change 'js json' to 'js json coffee'

2) Changes to {PROJECT_ROOT}/node_modules/@adonisjs/framework/src/Config/index.js

```
   syncWithFileSystem () {
     try {
       this._config = requireAll({
         dirname: this._configPath,
-        filters: /(.*)\.js$/
+        filter: /(.*)\.(?:js|coffee)$/
       })
```

3) Override default appFile in {PROJECT_ROOT}/server.coffee as follows:

```
 new Ignitor(require('@adonisjs/fold'))
   .appRoot(__dirname)
+  .appFile('start/app') # internal default is 'app.js'
```

## Testing CoffeeScript 2

```
npm install
cp .env.example .env
coffee server.coffee
```
