# About this fork

This fork is used to compile the Scratch Blocks library for the [Scratch Blocks G Suite Add-on](https://github.com/zakkolar/scratch-blocks-gsuite). The purpose of a separate repo is to include new translations that have not yet been incorporated into the original. New translations include:
* Khmer (10/27/19)

# General Docs

Make pictures of Scratch blocks from text.

[![Screenshot](http://scratchblocks.github.io/screenshot.png)](https://scratchblocks.github.io/#when%20flag%20clicked%0Aclear%0Aforever%0Apen%20down%0Aif%20%3C%3Cmouse%20down%3F%3E%20and%20%3Ctouching%20%5Bmouse-pointer%20v%5D%3F%3E%3E%20then%0Aswitch%20costume%20to%20%5Bbutton%20v%5D%0Aelse%0Aadd%20(x%20position)%20to%20%5Blist%20v%5D%0Aend%0Amove%20(foo)%20steps%0Aturn%20ccw%20(9)%20degrees)

**[Try it out!](http://scratchblocks.github.io/)**

---

**scratchblocks** is used to write Scratch scripts:

- in [Scratch Forum](http://scratch.mit.edu/discuss/topic/14772/) posts
- in [Scratch Wiki](http://wiki.scratch.mit.edu/wiki/Block_Plugin) articles
- in the [Code Club](https://www.codeclub.org.uk) project guides

It's MIT licensed, so you can use it in your projects. (But do send me a link
[on Twitter](http://twitter.com/blob8108)!)

For the full guide to the syntax, see [the wiki](http://wiki.scratch.mit.edu/wiki/Block_Plugin/Syntax).

# Usage

## MediaWiki

Use [the MediaWiki plugin](https://github.com/tjvr/wiki-scratchblocks). (This is what the [Scratch Wiki](http://wiki.scratch.mit.edu/wiki/Block_Plugin) uses.)

## WordPress

I found [a WordPress plugin](https://github.com/tkc49/scratchblocks-for-wp). It might work for you; I haven't tried it.

## Pandoc

Code Club use their own [lesson_format](https://github.com/CodeClub/lesson_format) tool to generate the PDF versions of their project guides. It uses the [pandoc_scratchblocks](https://github.com/CodeClub/pandoc_scratchblocks) plugin they wrote to make pictures of Scratch scripts.

This would probably be a good way to write a Scratch book.

## HTML

Include the scratchblocks JS file on your webpage:

```html
<script src="https://scratchblocks.github.io/js/scratchblocks-v3.x-min.js"></script>
```

`x` must be replaced with a version number. You can see [the list of the available versions](https://github.com/scratchblocks/scratchblocks.github.io/tree/master/js).

Then call `scratchblocks.renderMatching` after the page has loaded, which
will render matching page elements to shiny scratch blocks. Its sole argument
is the CSS-style selector for the elements that contain the scratchblocks code.
It uses `pre.blocks` by default.

```js
scratchblocks.renderMatching('pre.blocks');
```

### Inline blocks

To use blocks inside a paragraph...

```html
I'm rather fond of the <code class="b">stamp</code> block in Scratch.
```

...make a separate call to `renderMatching` using the `inline` argument.

```js
scratchblocks.renderMatching("code.b", {inline: true});
```

## Browserify

You can even use `scratchblocks` with browserify, if you're into that sort of
thing.

Once you've got browserify set up to build a client-side bundle from your app
code, you can just add `scratchblocks` to your dependencies, and everything
should Just Work™.

```js
var scratchblocks = require('scratchblocks');
scratchblocks.renderMatching('pre.blocks');
```

# Languages

To update the translations:
```sh
npm upgrade scratchr2_translations
npm run locales
```

In the browser, include [`translations.js`](https://github.com/tjvr/scratchblocks/blob/master/build/translations.js), [`translations-all.js`](https://github.com/tjvr/scratchblocks/blob/master/build/translations-all.js) or build your own language pack.

`translations.js` contains all the languages needed [on the Scratch Forums](http://scratch.mit.edu/discuss/#category_head_6).

`translations-all.js` contains all the languages Scratch supports.

If you want to build your own language pack, use `scratchblocks.loadLanguage(lang)` where lang is the contents of `src/locales/lang.json`.

## Adding a language

Each language **requires** some [additional words](https://github.com/tjvr/scratchblocks/blob/master/locales-src/extra_aliases.js) which aren't in Scratch itself (mainly the words used for the flag and arrow images). I'd be happy to accept pull requests for those! You'll need to rebuild the translations with `npm run locales` after editing the aliases.

# Development

This should set you up and start a http-server for development:

```
npm install
npm start
```

Then open <http://localhost:8000/> :-)

For more details, see [`CONTRIBUTING.md`](https://github.com/tjvr/scratchblocks/blob/master/.github/CONTRIBUTING.md).


# Credits

Many, many thanks to the [contributors](https://github.com/tjvr/scratchblocks/graphs/contributors)!

* Authored by [tjvr](https://github.com/tjvr)
* Icons derived from [Scratch Blocks](https://github.com/LLK/scratch-blocks) (Apache License 2.0)
* Scratch 2 SVG proof-of-concept, shapes & filters by [as-com](https://github.com/as-com)
* Anna helped with a formula, and pointed out that I can't read graphs
* JSO designed the syntax and wrote the original [Block Plugin](http://wiki.scratch.mit.edu/wiki/Block_Plugin_\(1.4\))
* Help with translation code from [joooni](http://scratch.mit.edu/users/joooni/)
* Block translations from the [Scratch translation server](http://translate.scratch.mit.edu/)
* Ported to node by [arve0](https://github.com/arve0)
