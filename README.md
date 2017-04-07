# api documentation for  [walk (v2.3.9)](https://github.com/coolaj86/node-walk)  [![npm package](https://img.shields.io/npm/v/npmdoc-walk.svg?style=flat-square)](https://www.npmjs.org/package/npmdoc-walk) [![travis-ci.org build-status](https://api.travis-ci.org/npmdoc/node-npmdoc-walk.svg)](https://travis-ci.org/npmdoc/node-npmdoc-walk)
#### A node port of python's os.walk

[![NPM](https://nodei.co/npm/walk.png?downloads=true)](https://www.npmjs.com/package/walk)

[![apidoc](https://npmdoc.github.io/node-npmdoc-walk/build/screenCapture.buildNpmdoc.browser._2Fhome_2Ftravis_2Fbuild_2Fnpmdoc_2Fnode-npmdoc-walk_2Ftmp_2Fbuild_2Fapidoc.html.png)](https://npmdoc.github.io/node-npmdoc-walk/build/apidoc.html)

![npmPackageListing](https://npmdoc.github.io/node-npmdoc-walk/build/screenCapture.npmPackageListing.svg)

![npmPackageDependencyTree](https://npmdoc.github.io/node-npmdoc-walk/build/screenCapture.npmPackageDependencyTree.svg)



# package.json

```json

{
    "author": {
        "name": "AJ ONeal",
        "email": "coolaj86@gmail.com"
    },
    "bugs": {
        "url": "https://github.com/coolaj86/node-walk/issues"
    },
    "contributors": [],
    "dependencies": {
        "foreachasync": "^3.0.0"
    },
    "description": "A node port of python's os.walk",
    "devDependencies": {},
    "directories": {
        "example": "examples",
        "test": "test"
    },
    "dist": {
        "shasum": "31b4db6678f2ae01c39ea9fb8725a9031e558a7b",
        "tarball": "https://registry.npmjs.org/walk/-/walk-2.3.9.tgz"
    },
    "files": [
        "lib"
    ],
    "gitHead": "cccd13e0fc6847443e9dd8cab468a27213b068cf",
    "homepage": "https://github.com/coolaj86/node-walk",
    "keywords": [
        "util",
        "os",
        "sys",
        "fs",
        "walk",
        "walkSync"
    ],
    "lib": ".",
    "licenses": [
        {
            "type": "MIT",
            "url": "http://www.opensource.org/licenses/mit-license.php"
        },
        {
            "type": "Apache2",
            "url": "http://opensource.org/licenses/apache2.0.php"
        }
    ],
    "main": "./lib/walk.js",
    "maintainers": [
        {
            "name": "coolaj86",
            "email": "coolaj86@gmail.com"
        }
    ],
    "name": "walk",
    "optionalDependencies": {},
    "readme": "ERROR: No README data found!",
    "repository": {
        "url": "git://github.com/coolaj86/node-walk.git"
    },
    "scripts": {
        "test": "./test/walk-test.sh"
    },
    "url": "http://github.com/coolaj86/node-walk",
    "version": "2.3.9"
}
```



# <a name="apidoc.tableOfContents"></a>[table of contents](#apidoc.tableOfContents)

#### [module walk](#apidoc.module.walk)
1.  [function <span class="apidocSignatureSpan"></span>walk (path, opts)](#apidoc.element.walk.walk)
1.  [function <span class="apidocSignatureSpan">walk.</span>walkSync (path, opts)](#apidoc.element.walk.walkSync)
1.  object <span class="apidocSignatureSpan">walk.</span>node_type_emitter

#### [module walk.node_type_emitter](#apidoc.module.walk.node_type_emitter)
1.  [function <span class="apidocSignatureSpan">walk.node_type_emitter.</span>createNodeGroups ()](#apidoc.element.walk.node_type_emitter.createNodeGroups)
1.  [function <span class="apidocSignatureSpan">walk.node_type_emitter.</span>emitNodeType (emitter, path, stats, next, self)](#apidoc.element.walk.node_type_emitter.emitNodeType)
1.  [function <span class="apidocSignatureSpan">walk.node_type_emitter.</span>emitNodeTypeGroups (emitter, path, nodes, next, self)](#apidoc.element.walk.node_type_emitter.emitNodeTypeGroups)
1.  [function <span class="apidocSignatureSpan">walk.node_type_emitter.</span>sortFnodesByType (stat, fnodes)](#apidoc.element.walk.node_type_emitter.sortFnodesByType)
1.  object <span class="apidocSignatureSpan">walk.node_type_emitter.</span>fnodeTypes
1.  object <span class="apidocSignatureSpan">walk.node_type_emitter.</span>fnodeTypesPlural
1.  object <span class="apidocSignatureSpan">walk.node_type_emitter.</span>isFnodeTypes



# <a name="apidoc.module.walk"></a>[module walk](#apidoc.module.walk)

#### <a name="apidoc.element.walk.walk"></a>[function <span class="apidocSignatureSpan"></span>walk (path, opts)](#apidoc.element.walk.walk)
- description and source-code
```javascript
walk = function (path, opts) {
  return new Walker(path, opts, false);
}
```
- example usage
```shell
...
"use strict";

var walk = require('walk')
  , fs = require('fs')
  , walker
  ;

walker = walk.walk("/tmp", options);

walker.on("file", function (root, fileStats, next) {
  fs.readFile(fileStats.name, function () {
    // doStuff
    next();
  });
});
...
```

#### <a name="apidoc.element.walk.walkSync"></a>[function <span class="apidocSignatureSpan">walk.</span>walkSync (path, opts)](#apidoc.element.walk.walkSync)
- description and source-code
```javascript
walkSync = function (path, opts) {
  return new Walker(path, opts, true);
}
```
- example usage
```shell
...
  // directories with these keys will be skipped
, filters: ["Temp", "_Temp"]
};

walker = walk.walk("/tmp", options);

// OR
// walker = walk.walkSync("/tmp", options);

walker.on("names", function (root, nodeNamesArray) {
  nodeNamesArray.sort(function (a, b) {
    if (a > b) return 1;
    if (a < b) return -1;
    return 0;
  });
...
```



# <a name="apidoc.module.walk.node_type_emitter"></a>[module walk.node_type_emitter](#apidoc.module.walk.node_type_emitter)

#### <a name="apidoc.element.walk.node_type_emitter.createNodeGroups"></a>[function <span class="apidocSignatureSpan">walk.node_type_emitter.</span>createNodeGroups ()](#apidoc.element.walk.node_type_emitter.createNodeGroups)
- description and source-code
```javascript
function createNodeGroups() {
  var nodeGroups = {};
  fnodeTypesPlural.concat("nodes", "errors").forEach(function (fnodeTypePlural) {
    nodeGroups[fnodeTypePlural] = [];
  });
  return nodeGroups;
}
```
- example usage
```shell
n/a
```

#### <a name="apidoc.element.walk.node_type_emitter.emitNodeType"></a>[function <span class="apidocSignatureSpan">walk.node_type_emitter.</span>emitNodeType (emitter, path, stats, next, self)](#apidoc.element.walk.node_type_emitter.emitNodeType)
- description and source-code
```javascript
function emitSingleEvents(emitter, path, stats, next, self) {
  var num = 1 + emitter.listeners(stats.type).length + emitter.listeners("node").length;

  function nextWhenReady() {
    num -= 1;
    if (0 === num) { next.call(self); }
  }

  emitter.emit(stats.type, path, stats, nextWhenReady);
  emitter.emit("node", path, stats, nextWhenReady);
  nextWhenReady();
}
```
- example usage
```shell
n/a
```

#### <a name="apidoc.element.walk.node_type_emitter.emitNodeTypeGroups"></a>[function <span class="apidocSignatureSpan">walk.node_type_emitter.</span>emitNodeTypeGroups (emitter, path, nodes, next, self)](#apidoc.element.walk.node_type_emitter.emitNodeTypeGroups)
- description and source-code
```javascript
function emitPluralEvents(emitter, path, nodes, next, self) {
  var num = 1;

  function nextWhenReady() {
    num -= 1;
    if (0 === num) { next.call(self); }
  }

  fnodeTypesPlural.concat(["nodes", "errors"]).forEach(function (fnodeType) {
    if (0 === nodes[fnodeType].length) { return; }
    num += emitter.listeners(fnodeType).length;
    emitter.emit(fnodeType, path, nodes[fnodeType], nextWhenReady);
  });
  nextWhenReady();
}
```
- example usage
```shell
n/a
```

#### <a name="apidoc.element.walk.node_type_emitter.sortFnodesByType"></a>[function <span class="apidocSignatureSpan">walk.node_type_emitter.</span>sortFnodesByType (stat, fnodes)](#apidoc.element.walk.node_type_emitter.sortFnodesByType)
- description and source-code
```javascript
function sortFnodesByType(stat, fnodes) {
  var i, isType;

  for (i = 0; i < isFnodeTypes.length; i += 1) {
    isType = isFnodeTypes[i];
    if (stat[isType]()) {
      stat.type = fnodeTypes[i];
      fnodes[fnodeTypesPlural[i]].push(stat);
      return;
    }
  }
}
```
- example usage
```shell
n/a
```



# misc
- this document was created with [utility2](https://github.com/kaizhu256/node-utility2)
