MonkeyConfig
============

MonkeyConfig is a simple configuration library for user scripts. It allows for
easy creation of configuration dialog windows and takes care of storing and
retrieving the configuration parameters for the script.

Usage Example
-------------

Tell your user script to use MonkeyConfig by placing a `@require` directive in
the metadata section alongside the `@grant` permissions it requires:

```javascript
// ==UserScript==
// @name           AwesomeScript
// @description    My awesome userscript
// @require        https://cdn.rawgit.com/odyniec/MonkeyConfig/51456c3a36b9b6febe61d1351de16466c90695d2/monkeyconfig.js
// @grant          GM_getValue
// @grant          GM_setValue
// @grant          GM_addStyle
// @grant          GM_registerMenuCommand
// ==/UserScript==
```

Then, call `MonkeyConfig()` to construct your configuration object:

```javascript
var cfg = new MonkeyConfig({
    title: 'AwesomeScript Configuration',
    menuCommand: true,
    params: {
        font_size: {
            type: 'select',
            choices: [ 'Small', 'Medium', 'Large' ],
            default: 'Medium'
        },
        auto_adjust: {
            type: 'checkbox',
            default: true
        }
    }
});
```

And that's pretty much it. MonkeyConfig builds a configuration dialog based on
the passed data:

<!--
![Example configuration dialog](http://wwwtest.odyniec.net/projects/monkeyconfig/dialog.png)
-->
![Example configuration dialog](http://img691.imageshack.us/img691/6382/dialogs.png)

It also adds a menu item in the User Script Commands menu to open the
configuration dialog:

<!--
![Menu item to open the configuration dialog](http://wwwtest.odyniec.net/projects/monkeyconfig/menu_item.png)
-->
![Menu item to open the configuration dialog](http://img651.imageshack.us/img651/325/menuitemopc.png)

At any time in your script, you can retrieve the value of a configuration
parameter with the `get()` method:

```javascript
var auto_adjust = cfg.get('auto_adjust');
```

and set a new value using the `set()` method:

```javascript
cfg.set('font_size', 'Small');
```
