# PostCSS Short [![Build Status][ci-img]][ci]

<img align="right" width="135" height="95" src="http://postcss.github.io/postcss/logo-leftp.png" title="Philosopher’s stone, logo of PostCSS">

[PostCSS Short] is a [PostCSS] plugin that allows that extends shorthand properties in CSS.

Shorthand properties allow you write more concise and often more readable style sheets, saving time and energy.

```css
/* before */

.banner {
	position: fixed 0 0 *;
	size: 100% 48px;
}

.section {
	margin: 40px;
	text: bold center uppercase dimgrey 1.25em 1.5 .05em;
}

.section.inset {
	margin: * auto;
}

/* after */

.banner {
	position: fixed;
	top: 0;
	right: 0;
	left: 0;
	width: 100%;
	height: 48px;
}

.section {
	margin: 40px;
	color: dimgrey;
	font-weight: bold;
	text-align: center;
	text-transform: uppercase;
	font-size: 1.25em;
	line-height: 1.5;
	letter-spacing: .05em;
}

.section.inset {
	margin-right: 0;
	margin-left: 0;
}
```

- The asterisk (`*`) value prevents the overriding of a previous value.
- The `position` property uses the same [1-to-4-value syntax] as `margin` and `padding`.
- The `text` property shorthands text-related properties, including `color`, `font-style`, `font-variant`, `font-weight`, `font-stretch`, `text-decoration`, `text-align`, `text-rendering`, `text-transform`, `white-space`, `font-size`, `line-height`, `letter-spacing`, `word-spacing`, and `font-family`.
- Shorthands are processed for `margin`, `padding`, `position`, `size`, `min-size`, `max-size`, and `text`.

## Usage

You just need to follow these two steps to use [PostCSS Short]:

1. Add [PostCSS] to your build tool.
2. Add [PostCSS Short] as a PostCSS process.

```sh
npm install postcss-short --save-dev
```

### Node

```js
postcss([ require('postcss-short')(/* options */) ])
```

### Grunt

Install [Grunt PostCSS]:

```shell
npm install postcss-short --save-dev
```

Enable [PostCSS Short] within your Gruntfile:

```js
grunt.loadNpmTasks('grunt-postcss');

grunt.initConfig({
	postcss: {
		options: {
			processors: [
				require('postcss-short')(/* options */)
			]
		},
		dist: {
			src: 'css/*.css'
		}
	}
});
```

### Options

**allow** (`Array`): If specified, only properties explicitly allowed will be processed.

**deny** (`Array`): If specified, deny specific properties from being processed.

**prefix** (`String`, `Object`): prepends a prefix (surrounded by dashes) to the property. This may be useful for preventing clashes with any future syntax.


```js
{
	deny: ['text'], // do not process the text property
	prefix: 's' // process properties with the -s- prefix
}
```

```js
{
	allow: ['text'], // only process the text property
	prefix: {
		'text': 's' // process the prefixed '-s-text' property
	}
}
```

[1-to-4-value syntax]: https://developer.mozilla.org/en-US/docs/Web/CSS/Shorthand_properties#Tricky_edge_cases
[ci]: https://travis-ci.org/jonathantneal/postcss-short
[ci-img]: https://travis-ci.org/jonathantneal/postcss-short.svg
[Grunt PostCSS]: https://github.com/nDmitry/grunt-postcss
[PostCSS]: https://github.com/postcss/postcss
[PostCSS Short]: https://github.com/jonathantneal/postcss-short
