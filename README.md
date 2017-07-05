# JavaScript async-defer

### Where should I put ```<script>``` tags in HTML markup?

Here's what happens when a browser loads a website with a ```<script>``` tag on it:

 * Fetch the HTML page (e.g index.html)
 * Begin parsing the HTML
 * The parser encounters a ```<script>``` tag referencing an external script file.
 * The browser request the script file. Meanwhile parser blocks and stop parsing the other HTML content on your page.
 * Once the script is downloaded and subsequently executes the other contents.

If parser blocks the content while loading the page it is a bad user experience. Your website basically stops loading until you've downloaded all scripts.

### <b>The modern approach</b>

Today, browsers support the ```async``` and ```defer``` attributes on scripts. These attributes tell the browser it's safe to continue parsing while the scripts are being downloaded.

### async

```javascript
<script type="text/javascript" src="path/to/script1.js" async></script>
<script type="text/javascript" src="path/to/script2.js" async></script>
```

Scripts with the async attribute are executed asynchronously. This means the script is executed as soon as it's downloaded, without blocking the browser in the meantime.
This implies that it's possible to script 2 is downloaded and executed before script 1.

According to http://caniuse.com/#feat=script-async, 90% of all browsers support this.


### defer

```javascript
<script type="text/javascript" src="path/to/script1.js" defer></script>
<script type="text/javascript" src="path/to/script2.js" defer></script>
```

Scripts with the defer attribute are executed in order (i.e. first script 1, then script 2). This also does not block the browser.

Unlike async scripts, defer scripts are only executed after the entire document has been loaded.

According to http://caniuse.com/#feat=script-defer, 90% of all browsers support this. 92% support it at least partially.
