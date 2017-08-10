_This project is no longer maintained. If you are interested in taking over the project, email [contact@zapier.com](mailto:contact@zapier.com)._

# Zapier's very own CoffeeScript

## Does three things at the moment:

1. A ```/* */``` style comment for the version which CoffeeScript places on every file. This makes it play nicer with tools that concatentate files.
2. Supports a new ```from ... import ...``` syntax which playes nicely with RequireJS
3. Also support a plain ```import ...``` syntax for imports without return values

Example usage:

```coffeescript
#
# core utilities
import 'log'
from 'json' import JsonWrapper
#
# framework dependencies 
from 'jquery' import $
import 'mylib'
from 'use!underscore' import _  
from 'use!backbone' import Backbone
from 'use!backbonecache' BackboneCache

initialize = () ->
 go('now')
```

gets pre-compiled into

```javascript
/* Generated by CoffeeScript 1.4.0 */

define(['json', 'log', 'jquery', 'use!underscore', 'use!backbone', 'log', 'mylib'], function(JsonWrapper, LogWrapper, $, _, Backbone) {
  var initialize;
  return initialize = function() {
    return go('now');
  };
});

```

*NOTE*
We detect the end of the "importing" section of the header by a blank line so make sure not to put a blank line until after your last import.

##To deploy this to your server##
Pre-reqs:
* npm is installed
* `npm install -g jison`

1. `git clone git@github.com:zapier/coffee-script.git`
2. `cd coffee-script`
3. `bin/cake build:full` (note: might have to run`npm install jison` if error about jison)
4. `sudo bin/cake install`

## MISC
To rebuild the compiler if you messed something up: ```git checkout lib```
