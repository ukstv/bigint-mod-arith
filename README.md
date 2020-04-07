[![JavaScript Style Guide](https://img.shields.io/badge/code_style-standard-brightgreen.svg)](https://standardjs.com)

# bigint-mod-arith

Some extra functions to work with modular arithmetic using native JS ([ES-2020](https://tc39.es/ecma262/#sec-bigint-objects)) implementation of BigInt. It can be used by any [Web Browser or webview supporting BigInt](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/BigInt#Browser_compatibility) and with Node.js (>=10.4.0).

> The operations supported on BigInts are not constant time. BigInt can be therefore **[unsuitable for use in cryptography](https://www.chosenplaintext.ca/articles/beginners-guide-constant-time-cryptography.html).** Many platforms provide native support for cryptography, such as [Web Cryptography API](https://w3c.github.io/webcrypto/) or [Node.js Crypto](https://nodejs.org/dist/latest/docs/api/crypto.html).

## Installation

bigint-mod-arith is distributed for [web browsers and/or webviews supporting BigInt](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/BigInt#Browser_compatibility) as an ES6 module or an IIFE file; and for Node.js (>=10.4.0), as a CJS module.

bigint-mod-arith can be imported to your project with `npm`:

```bash
npm install bigint-mod-arith
```
NPM installation defaults to the ES6 module for browsers and the CJS one for Node.js.

For web browsers, you can also directly download the [IIFE bundle](https://raw.githubusercontent.com/juanelas/bigint-mod-arith/master/lib/index.browser.bundle.js) or the [ES6 bundle module](https://raw.githubusercontent.com/juanelas/bigint-mod-arith/master/lib/index.browser.bundle.mod.js) from GitHub.

## Usage example

Import your module as :

 - Node.js
   ```javascript
   const bigintModArith = require('bigint-mod-arith')
   ... // your code here
   ```
 - JavaScript native project
   ```javascript
   import * as bigintModArith from 'bigint-mod-arith'
   ... // your code here
   ```
 - JavaScript native browser ES6 mod
   ```html
   <script type="module">
     import * as bigintModArith from 'lib/index.browser.bundle.mod.js'  // Use you actual path to the browser mod bundle
     ... // your code here
   </script>
   ```
 - JavaScript native browser IIFE
   ```html
   <script src="../../lib/index.browser.bundle.js"></script> <!-- Use you actual path to the browser bundle -->
   <script>
     ... // your code here
   </script>
 - TypeScript
   ```typescript
   import * as bigintModArith from 'bigint-mod-arith'
   ... // your code here
   ```
   > BigInt is [ES-2020](https://tc39.es/ecma262/#sec-bigint-objects). In order to use it with TypeScript you should set `lib` (and probably also `target` and `module`) to `esnext` in `tsconfig.json`.

```javascript
/* Stage 3 BigInts with value 666 can be declared as BigInt('666')
or the shorter syntax 666n.
Notice that you can also pass a number, e.g. BigInt(666), but it is not
recommended since values over 2**53 - 1 won't be safe but no warning will
be raised.
*/
const a = BigInt('5')
const b = BigInt('2')
const n = 19n

console.log(bigintModArith.modPow(a, b, n)) // prints 6

console.log(bigintModArith.modInv(2n, 5n)) // prints 3

console.log(bigintModArith.modInv(BigInt('3'), BigInt('5'))) // prints 2

```

## API reference documentation

<a name="abs"></a>

### abs(a) ⇒ <code>bigint</code>
Absolute value. abs(a)==a if a>=0. abs(a)==-a if a<0

**Kind**: global function  
**Returns**: <code>bigint</code> - the absolute value of a  

| Param | Type |
| --- | --- |
| a | <code>number</code> \| <code>bigint</code> | 

<a name="bitLength"></a>

### bitLength(a) ⇒ <code>number</code>
Returns the bitlength of a number

**Kind**: global function  
**Returns**: <code>number</code> - - the bit length  

| Param | Type |
| --- | --- |
| a | <code>number</code> \| <code>bigint</code> | 

<a name="eGcd"></a>

### eGcd(a, b) ⇒ [<code>egcdReturn</code>](#egcdReturn)
An iterative implementation of the extended euclidean algorithm or extended greatest common divisor algorithm.
Take positive integers a, b as input, and return a triple (g, x, y), such that ax + by = g = gcd(a, b).

**Kind**: global function  
**Returns**: [<code>egcdReturn</code>](#egcdReturn) - A triple (g, x, y), such that ax + by = g = gcd(a, b).  

| Param | Type |
| --- | --- |
| a | <code>number</code> \| <code>bigint</code> | 
| b | <code>number</code> \| <code>bigint</code> | 

<a name="gcd"></a>

### gcd(a, b) ⇒ <code>bigint</code>
Greatest-common divisor of two integers based on the iterative binary algorithm.

**Kind**: global function  
**Returns**: <code>bigint</code> - The greatest common divisor of a and b  

| Param | Type |
| --- | --- |
| a | <code>number</code> \| <code>bigint</code> | 
| b | <code>number</code> \| <code>bigint</code> | 

<a name="lcm"></a>

### lcm(a, b) ⇒ <code>bigint</code>
The least common multiple computed as abs(a*b)/gcd(a,b)

**Kind**: global function  
**Returns**: <code>bigint</code> - The least common multiple of a and b  

| Param | Type |
| --- | --- |
| a | <code>number</code> \| <code>bigint</code> | 
| b | <code>number</code> \| <code>bigint</code> | 

<a name="max"></a>

### max(a, b) ⇒ <code>bigint</code>
Maximum. max(a,b)==a if a>=b. max(a,b)==b if a<=b

**Kind**: global function  
**Returns**: <code>bigint</code> - maximum of numbers a and b  

| Param | Type |
| --- | --- |
| a | <code>number</code> \| <code>bigint</code> | 
| b | <code>number</code> \| <code>bigint</code> | 

<a name="min"></a>

### min(a, b) ⇒ <code>bigint</code>
Minimum. min(a,b)==b if a>=b. min(a,b)==a if a<=b

**Kind**: global function  
**Returns**: <code>bigint</code> - minimum of numbers a and b  

| Param | Type |
| --- | --- |
| a | <code>number</code> \| <code>bigint</code> | 
| b | <code>number</code> \| <code>bigint</code> | 

<a name="modInv"></a>

### modInv(a, n) ⇒ <code>bigint</code>
Modular inverse.

**Kind**: global function  
**Returns**: <code>bigint</code> - the inverse modulo n or NaN if it does not exist  

| Param | Type | Description |
| --- | --- | --- |
| a | <code>number</code> \| <code>bigint</code> | The number to find an inverse for |
| n | <code>number</code> \| <code>bigint</code> | The modulo |

<a name="modPow"></a>

### modPow(b, e, n) ⇒ <code>bigint</code>
Modular exponentiation b**e mod n. Currently using the right-to-left binary method

**Kind**: global function  
**Returns**: <code>bigint</code> - b**e mod n  

| Param | Type | Description |
| --- | --- | --- |
| b | <code>number</code> \| <code>bigint</code> | base |
| e | <code>number</code> \| <code>bigint</code> | exponent |
| n | <code>number</code> \| <code>bigint</code> | modulo |

<a name="toZn"></a>

### toZn(a, n) ⇒ <code>bigint</code>
Finds the smallest positive element that is congruent to a in modulo n

**Kind**: global function  
**Returns**: <code>bigint</code> - The smallest positive representation of a in modulo n  

| Param | Type | Description |
| --- | --- | --- |
| a | <code>number</code> \| <code>bigint</code> | An integer |
| n | <code>number</code> \| <code>bigint</code> | The modulo |

<a name="egcdReturn"></a>

### egcdReturn : <code>Object</code>
A triple (g, x, y), such that ax + by = g = gcd(a, b).

**Kind**: global typedef  
**Properties**

| Name | Type |
| --- | --- |
| g | <code>bigint</code> | 
| x | <code>bigint</code> | 
| y | <code>bigint</code> | 

