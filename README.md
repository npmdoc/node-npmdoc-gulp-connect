# api documentation for  [gulp-connect (v5.0.0)](https://github.com/avevlad/gulp-connect#readme)  [![npm package](https://img.shields.io/npm/v/npmdoc-gulp-connect.svg?style=flat-square)](https://www.npmjs.org/package/npmdoc-gulp-connect) [![travis-ci.org build-status](https://api.travis-ci.org/npmdoc/node-npmdoc-gulp-connect.svg)](https://travis-ci.org/npmdoc/node-npmdoc-gulp-connect)
#### Gulp plugin to run a webserver (with LiveReload)

[![NPM](https://nodei.co/npm/gulp-connect.png?downloads=true)](https://www.npmjs.com/package/gulp-connect)

[![apidoc](https://npmdoc.github.io/node-npmdoc-gulp-connect/build/screenCapture.buildNpmdoc.browser.%252Fhome%252Ftravis%252Fbuild%252Fnpmdoc%252Fnode-npmdoc-gulp-connect%252Ftmp%252Fbuild%252Fapidoc.html.png)](https://npmdoc.github.io/node-npmdoc-gulp-connect/build/apidoc.html)

![npmPackageListing](https://npmdoc.github.io/node-npmdoc-gulp-connect/build/screenCapture.npmPackageListing.svg)

![npmPackageDependencyTree](https://npmdoc.github.io/node-npmdoc-gulp-connect/build/screenCapture.npmPackageDependencyTree.svg)



# package.json

```json

{
    "authors": [
        {
            "name": "Vladislav Derjavin",
            "email": "dev@vld.me",
            "url": "http://vld.me/"
        },
        {
            "name": "Johannes Schickling",
            "email": "schickling.j@gmail.com",
            "url": "http://schickling.me/"
        },
        {
            "name": "Justin Chase",
            "email": "justin.m.chase@gmail.com",
            "url": "http://justinmchase.com"
        },
        {
            "name": "Contributors",
            "homepage": "https://github.com/AveVlad/gulp-connect/graphs/contributors"
        }
    ],
    "bugs": {
        "url": "https://github.com/avevlad/gulp-connect/issues"
    },
    "dependencies": {
        "connect": "^2.30.0",
        "connect-livereload": "^0.5.4",
        "event-stream": "^3.3.2",
        "gulp-util": "^3.0.6",
        "tiny-lr": "^0.2.1"
    },
    "description": "Gulp plugin to run a webserver (with LiveReload)",
    "devDependencies": {
        "coffee-script": "^1.10.0",
        "gulp": "^3.9.0",
        "gulp-stylus": "^2.1.1",
        "mocha": "^2.3.4",
        "supertest": "^1.1.0"
    },
    "directories": {},
    "dist": {
        "shasum": "f2fdf306ae911468368c2285f2d782f13eddaf4e",
        "tarball": "https://registry.npmjs.org/gulp-connect/-/gulp-connect-5.0.0.tgz"
    },
    "engines": {
        "node": ">=0.10.0"
    },
    "gitHead": "93980927255b564e6230f75b25ae115337a6454b",
    "homepage": "https://github.com/avevlad/gulp-connect#readme",
    "keywords": [
        "gulpfriendly",
        "connect",
        "livereload",
        "webserver",
        "server"
    ],
    "license": "MIT",
    "maintainers": [
        {
            "name": "avevlad",
            "email": "dev@vld.me"
        },
        {
            "name": "justinmchase",
            "email": "justin.m.chase@outlook.com"
        }
    ],
    "name": "gulp-connect",
    "optionalDependencies": {},
    "readme": "ERROR: No README data found!",
    "repository": {
        "type": "git",
        "url": "git://github.com/avevlad/gulp-connect.git"
    },
    "scripts": {
        "pretest": "coffee -o . -bc src/",
        "test": "mocha"
    },
    "version": "5.0.0"
}
```



# <a name="apidoc.tableOfContents"></a>[table of contents](#apidoc.tableOfContents)

#### [module gulp-connect](#apidoc.module.gulp-connect)
1.  [function <span class="apidocSignatureSpan">gulp-connect.</span>reload ()](#apidoc.element.gulp-connect.reload)
1.  [function <span class="apidocSignatureSpan">gulp-connect.</span>server (options)](#apidoc.element.gulp-connect.server)
1.  [function <span class="apidocSignatureSpan">gulp-connect.</span>serverClose ()](#apidoc.element.gulp-connect.serverClose)



# <a name="apidoc.module.gulp-connect"></a>[module gulp-connect](#apidoc.module.gulp-connect)

#### <a name="apidoc.element.gulp-connect.reload"></a>[function <span class="apidocSignatureSpan">gulp-connect.</span>reload ()](#apidoc.element.gulp-connect.reload)
- description and source-code
```javascript
reload = function () {
  return es.map(function(file, callback) {
    apps.forEach((function(_this) {
      return function(app) {
        if (app.livereload && typeof app.lr === "object") {
          return app.lr.changed({
            body: {
              files: file.path
            }
          });
        }
      };
    })(this));
    return callback(null, file);
  });
}
```
- example usage
```shell
...
    root: 'app',
    livereload: true
  });
});

gulp.task('html', function () {
  gulp.src('./app/*.html')
    .pipe(connect.reload());
});

gulp.task('watch', function () {
  gulp.watch(['./app/*.html'], ['html']);
});

gulp.task('default', ['connect', 'watch']);
...
```

#### <a name="apidoc.element.gulp-connect.server"></a>[function <span class="apidocSignatureSpan">gulp-connect.</span>server (options)](#apidoc.element.gulp-connect.server)
- description and source-code
```javascript
server = function (options) {
  var app;
  if (options == null) {
    options = {};
  }
  app = new ConnectApp(options);
  apps.push(app);
  return app;
}
```
- example usage
```shell
...
## Usage

'''js
var gulp = require('gulp'),
  connect = require('gulp-connect');

gulp.task('connect', function() {
  connect.server();
});

gulp.task('default', ['connect']);
'''

#### LiveReload
'''js
...
```

#### <a name="apidoc.element.gulp-connect.serverClose"></a>[function <span class="apidocSignatureSpan">gulp-connect.</span>serverClose ()](#apidoc.element.gulp-connect.serverClose)
- description and source-code
```javascript
serverClose = function () {
  apps.forEach(function(app) {
    return app.server.close();
  });
  return apps = [];
}
```
- example usage
```shell
...
'''js
gulp.task('jenkins-tests', function() {
  connect.server({
    port: 8888
  });
  // run some headless tests with phantomjs
  // when process exits:
  connect.serverClose();
});
'''


#### Multiple server

'''js
...
```



# misc
- this document was created with [utility2](https://github.com/kaizhu256/node-utility2)
