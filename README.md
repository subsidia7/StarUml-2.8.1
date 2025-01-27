# StarUml-2.8.1
> Source [git repo](https://gist.github.com/trandaison/40b1d83618ae8e3d2da59df8c395093a)
>
> Note: This is the guide for v 2.x.
>
> For the v3, please follow this url: https://blog.csdn.net/sam_shan/article/details/80585240 Thanks @liy-cn for contributing.


# StarUML
Download: [StarUML.io](http://staruml.io/)

# Crack
Source: [jorgeancal](http://jorgeancal.com/en/crack/crack-startuml/)


After installing StartUML successfully, modify `LicenseManagerDomain.js` as follow:
```js
/**
 * File name: LicenseManagerDomain.js
 * Mac OS: /Applications/StarUML.app/Contents/www/license/node/
 * Linux: /opt/staruml/www/license/node/
 */

(function () {
    "use strict";
 
    var NodeRSA = require('node-rsa');
 
    function validate(PK, name, product, licenseKey) {
        return{
           name: "sontd",
           product: "StarUML",
           licenseType: "vip",
           quantity: "unlimited",
           licenseKey: "no, thanks!"
        };
    }
 
    function init(domainManager) {
        if (!domainManager.hasDomain("LicenseManager")) {
            domainManager.registerDomain("LicenseManager", {major: 0, minor: 1});
        }
        domainManager.registerCommand(
            "LicenseManager", // domain name
            "validate",       // command name
            validate,         // command handler function
            false,            // this command is synchronous in Node ("false" means synchronous")
            "Validate License",
            [
                {
                    name: "PK",
                    type: "string",
                    description: "PK"
                },
                {
                    name: "name",
                    type: "string",
                    description: "name of license owner"
                },
                {
                    name: "product",
                    type: "string",
                    description: "product name"
                },
                {
                    name: "licenseKey",
                    type: "string",
                    description: "license key"
                }
            ],
            [
                {
                    name: "result", // return values
                    type: "object",
                    description: "result"
                }
            ]
        );
    }
 
    exports.init = init;
 
}());
```
Now, open it and go to `Help > Enter License` and you have to write the name and the licence key which you have written on `LicenseManagerDomain.js`. In this example would be the next:
```yml
name: "sontd"
License Key: "no, thanks!"
```
Enjoy it!
