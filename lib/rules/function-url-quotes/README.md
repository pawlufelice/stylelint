# function-url-quotes

Require or disallow quotes for urls.

```css
a { background: url("x.jpg") }
/**                 ↑     ↑
 *             These quotes */
```

## Options

`string`: `"always"|"never"`

### `"always"`

Urls *must always* be quoted.

The following patterns are considered warnings:

```css
@import url(foo.css);
```

```css
@document domain(http://www.w3.org/);
```

```css
@font-face { font-family: 'foo'; src: url(foo.ttf); }
```

```css
@-moz-document url-prefix() {}
```

The following patterns are *not* considered warnings:

```css
a { background: url('x.jpg'); }
```

```css
@import url("foo.css");
```

```css
@document domain('http://www.w3.org/');
```

```css
@font-face { font-family: "foo"; src: url("foo.ttf"); }
```

```css
@-moz-document url-prefix('') {}
```

### `"never"`

Urls *must never* be quoted.

The following patterns are considered warnings:

```css
a { background: url('x.jpg'); }
```

```css
@import url("foo.css");
```

```css
@font-face { font-family: "foo"; src: url('foo.ttf'); }
```

The following patterns are *not* considered warnings:

```css
a { background: url(x.jpg); }
```

```css
@import url(foo.css);
```

```css
@font-face { font-family: 'foo'; src: url(foo.ttf); }
```

## Optional secondary options

### `except: ["empty"]`

Reverse the primary option if the function has no arguments.

For example, with `"always"`.

The following pattern is *not* considered warnings:

```css
@-moz-document url-prefix() {}
```
