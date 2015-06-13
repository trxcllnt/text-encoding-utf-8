TextEncoderLite
==============

This is a lightweight fork of [text-encoding](https://github.com/inexorabletash/text-encoding).
It's pretty much the same thing, but a bunch of code deleted.

This is a polyfill for the [Encoding Living Standard](http://encoding.spec.whatwg.org/)
API for the Web, allowing encoding and decoding of textual data to and from Typed Array
buffers for binary data in JavaScript.

By default it adheres to the spec and does not support *encoding* to non-UTF encodings,
only *decoding*. It is also implemented to match the specification's algorithms, rather
than for performance. The intended use is within Web pages, so it has no dependency
on server frameworks or particular module schemes.

Basic examples and tests are included.

### Install ###

There are a few ways you can get the `text-encoder-lite` library.

#### Node ####

`text-encoder-lite` is on `npm`. Simply run:

```js
npm install text-encoder-lite
```

Or add it to your `package.json` dependencies.

#### Bower ####

`text-encoder-lite` is on `bower` as well. Install with bower like so:

```js
bower install text-encoder-lite
```

Or add it to your `bower.json` dependencies.

### HTML Page Usage ###

```html
  <!-- Required for non-UTF encodings -->
  <script src="encoding.js"></script>
```

### API Overview ###

Basic Usage

```js
  var uint8array = TextEncoder('utf-8').encode(string);
  var string = TextDecoder('utf-8').decode(uint8array);
```

Streaming Decode

```js
  var string = "", decoder = TextDecoder(encoding), buffer;
  while (buffer = next_chunk()) { 
    string += decoder.decode(buffer, {stream:true});
  }
  string += decoder.decode(); // finish the stream
```

### Encodings ###

Only UTF-8 encoding is supported.
See [text-encoding](https://github.com/inexorabletash/text-encoding) for full support,
including multi-lingual non-standard encodings that aren't supported by TextEncoder proper.

If it seems beneficial I could bring in support for utf-16be, utf-16le, and x-user-defined.
