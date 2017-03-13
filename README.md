modlazy
====

Lightweight (3KB!) lazy loader for JS, CSS &amp; LESS assets.

On demand assets loader built with ease, nested dependencies support and cache care.

modlazy is a fork of Lazy Loader ( https://github.com/orenyakobi/lazy ) that fixes a bug in URL handling. 

Installation
----

* Install with bower: `bower install modlazy`

* Or clone it and add dist/modlazy.js to your DOM: `git clone https://github.com/robertdmunn/modlazy.git`

Usage
----
### Asynchronic assets load
```javascript
modlazy.load(['myScript.js','myStyle.css','myLessStyle.less']);`
```


### Dependencies
Use the '<' operator to define dependencies while x < y means: x depends on y, so modlazy will make sure y is being loaded before x. You can also use '<' to define nested dependencies:

```javascript
modlazy.load(['loadMeLast.js < loadMeSecond.js < loadMeFirst.less'], ['LoadMeWhenEver.js', 'LoadMeWhenEverAsWell.js']);
```

loadMeLast.js depends on loadMeSecond.js, which depends on loadMeFirst.less

### modlazy loading with callback
You can send a function variable or an anonymous function as the second variable to be call when all the files are loaded

```javascript
modlazy.load(['loadMeLast.js < loadMeFirst.less ', 'LoadMeWhenEver.js'], function(){
    console.log('All files have been loaded');
});
```

### Further reading
* Cache:
```javascript
modlazy.load(['myScript.js','myOtherScript.js','myScript.js']);
```
myScript.js will be loaded only once

* Note: For using modlazy with LESS files you have to (*modlazy*) load [less.js](https://github.com/less/less.js) first
