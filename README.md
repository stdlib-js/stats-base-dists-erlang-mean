<!--

@license Apache-2.0

Copyright (c) 2018 The Stdlib Authors.

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

   http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.

-->


<details>
  <summary>
    About stdlib...
  </summary>
  <p>We believe in a future in which the web is a preferred environment for numerical computation. To help realize this future, we've built stdlib. stdlib is a standard library, with an emphasis on numerical and scientific computation, written in JavaScript (and C) for execution in browsers and in Node.js.</p>
  <p>The library is fully decomposable, being architected in such a way that you can swap out and mix and match APIs and functionality to cater to your exact preferences and use cases.</p>
  <p>When you use stdlib, you can be absolutely certain that you are using the most thorough, rigorous, well-written, studied, documented, tested, measured, and high-quality code out there.</p>
  <p>To join us in bringing numerical computing to the web, get started by checking us out on <a href="https://github.com/stdlib-js/stdlib">GitHub</a>, and please consider <a href="https://opencollective.com/stdlib">financially supporting stdlib</a>. We greatly appreciate your continued support!</p>
</details>

# Mean

[![NPM version][npm-image]][npm-url] [![Build Status][test-image]][test-url] [![Coverage Status][coverage-image]][coverage-url] <!-- [![dependencies][dependencies-image]][dependencies-url] -->

> [Erlang][erlang-distribution] distribution [expected value][expected-value].

<!-- Section to include introductory text. Make sure to keep an empty line after the intro `section` element and another before the `/section` close. -->

<section class="intro">

The [mean][expected-value] for an [Erlang][erlang-distribution] random variable is

<!-- <equation class="equation" label="eq:erlang_mean" align="center" raw="\mathbb{E} \left[ X \right] = \frac{k}{\lambda}" alt="Mean for an Erlang distribution."> -->

```math
\mathbb{E} \left[ X \right] = \frac{k}{\lambda}
```

<!-- <div class="equation" align="center" data-raw-text="\mathbb{E} \left[ X \right] = \frac{k}{\lambda}" data-equation="eq:erlang_mean">
    <img src="https://cdn.jsdelivr.net/gh/stdlib-js/stdlib@51534079fef45e990850102147e8945fb023d1d0/lib/node_modules/@stdlib/stats/base/dists/erlang/mean/docs/img/equation_erlang_mean.svg" alt="Mean for an Erlang distribution.">
    <br>
</div> -->

<!-- </equation> -->

where `k` is the shape parameter and `λ` is the rate parameter.

</section>

<!-- /.intro -->

<!-- Package usage documentation. -->

<section class="installation">

## Installation

```bash
npm install @stdlib/stats-base-dists-erlang-mean
```

Alternatively,

-   To load the package in a website via a `script` tag without installation and bundlers, use the [ES Module][es-module] available on the [`esm`][esm-url] branch (see [README][esm-readme]).
-   If you are using Deno, visit the [`deno`][deno-url] branch (see [README][deno-readme] for usage intructions).
-   For use in Observable, or in browser/node environments, use the [Universal Module Definition (UMD)][umd] build available on the [`umd`][umd-url] branch (see [README][umd-readme]).

The [branches.md][branches-url] file summarizes the available branches and displays a diagram illustrating their relationships.

To view installation and usage instructions specific to each branch build, be sure to explicitly navigate to the respective README files on each branch, as linked to above.

</section>

<section class="usage">

## Usage

```javascript
var mean = require( '@stdlib/stats-base-dists-erlang-mean' );
```

#### mean( k, lambda )

Returns the [expected value][expected-value] of an [Erlang][erlang-distribution] distribution with parameters `k` (shape parameter) and `lambda` (rate parameter).

```javascript
var v = mean( 1, 1.0 );
// returns 1.0

v = mean( 4, 12.0 );
// returns ~0.333

v = mean( 8, 2.0 );
// returns 4.0
```

If provided `NaN` as any argument, the function returns `NaN`.

```javascript
var v = mean( NaN, 2.0 );
// returns NaN

v = mean( 2.0, NaN );
// returns NaN
```

If not provided a positive integer for `k`, the function returns `NaN`.

```javascript
var v = mean( 1.8, 1.0 );
// returns NaN

v = mean( -1.0, 1.0 );
// returns NaN
```

If provided `lambda <= 0`, the function returns `NaN`.

```javascript
var v = mean( 2, 0.0 );
// returns NaN

v = mean( 2, -1.0 );
// returns NaN
```

</section>

<!-- /.usage -->

<!-- Package usage notes. Make sure to keep an empty line after the `section` element and another before the `/section` close. -->

<section class="notes">

</section>

<!-- /.notes -->

<!-- Package usage examples. -->

<section class="examples">

## Examples

<!-- eslint no-undef: "error" -->

```javascript
var uniform = require( '@stdlib/random-array-uniform' );
var discreteUniform = require( '@stdlib/random-array-discrete-uniform' );
var logEachMap = require( '@stdlib/console-log-each-map' );
var EPS = require( '@stdlib/constants-float64-eps' );
var mean = require( '@stdlib/stats-base-dists-erlang-mean' );

var opts = {
    'dtype': 'float64'
};
var k = discreteUniform( 10, 0, 10, opts );
var lambda = uniform( 10, EPS, 10.0, opts );

logEachMap( 'k: %d, λ: %0.4f, E(X;k,λ): %0.4f', k, lambda, mean );
```

</section>

<!-- /.examples -->

<!-- C interface documentation. -->

* * *

<section class="c">

## C APIs

<!-- Section to include introductory text. Make sure to keep an empty line after the intro `section` element and another before the `/section` close. -->

<section class="intro">

</section>

<!-- /.intro -->

<!-- C usage documentation. -->

<section class="usage">

### Usage

```c
#include "stdlib/stats/base/dists/erlang/mean.h"
```

#### stdlib_base_dists_erlang_mean( k, lambda )

Evaluates the [expected value][expected-value] of an [Erlang][erlang-distribution] distribution with parameters `k` (shape parameter) and `lambda` (rate parameter).

```c
double out = stdlib_base_dists_erlang_mean( 1, 1.0 );
// returns 1.0
```

The function accepts the following arguments:

-   **k**: `[in] int32_t` shape parameter.
-   **lambda**: `[in] double` rate parameter.

```c
double stdlib_base_dists_erlang_mean( const int32_t k, const double lambda );
```

</section>

<!-- /.usage -->

<!-- C API usage notes. Make sure to keep an empty line after the `section` element and another before the `/section` close. -->

<section class="notes">

</section>

<!-- /.notes -->

<!-- C API usage examples. -->

<section class="examples">

### Examples

```c
#include "stdlib/stats/base/dists/erlang/mean.h"
#include "stdlib/constants/float64/eps.h"
#include "stdlib/math/base/special/round.h"
#include <stdlib.h>
#include <stdint.h>
#include <stdio.h>

static double random_uniform( const double min, const double max ) {
    double v = (double)rand() / ( (double)RAND_MAX + 1.0 );
    return min + ( v*(max-min) );
}

int main( void ) {
    double lambda;
    int32_t k;
    double y;
    int i;

    for ( i = 0; i < 25; i++ ) {
        k = stdlib_base_round( random_uniform( 0.0, 10.0 ) );
        lambda = random_uniform( STDLIB_CONSTANT_FLOAT64_EPS, 10.0 );
        y = stdlib_base_dists_erlang_mean( k, lambda );
        printf( "k: %d, λ: %lf, E(X;k,λ): %lf\n", k, lambda, y );
    }
}
```

</section>

<!-- /.examples -->

</section>

<!-- /.c -->

<!-- Section to include cited references. If references are included, add a horizontal rule *before* the section. Make sure to keep an empty line after the `section` element and another before the `/section` close. -->

<section class="references">

</section>

<!-- /.references -->

<!-- Section for related `stdlib` packages. Do not manually edit this section, as it is automatically populated. -->

<section class="related">

</section>

<!-- /.related -->

<!-- Section for all links. Make sure to keep an empty line after the `section` element and another before the `/section` close. -->


<section class="main-repo" >

* * *

## Notice

This package is part of [stdlib][stdlib], a standard library for JavaScript and Node.js, with an emphasis on numerical and scientific computing. The library provides a collection of robust, high performance libraries for mathematics, statistics, streams, utilities, and more.

For more information on the project, filing bug reports and feature requests, and guidance on how to develop [stdlib][stdlib], see the main project [repository][stdlib].

#### Community

[![Chat][chat-image]][chat-url]

---

## License

See [LICENSE][stdlib-license].


## Copyright

Copyright &copy; 2016-2025. The Stdlib [Authors][stdlib-authors].

</section>

<!-- /.stdlib -->

<!-- Section for all links. Make sure to keep an empty line after the `section` element and another before the `/section` close. -->

<section class="links">

[npm-image]: http://img.shields.io/npm/v/@stdlib/stats-base-dists-erlang-mean.svg
[npm-url]: https://npmjs.org/package/@stdlib/stats-base-dists-erlang-mean

[test-image]: https://github.com/stdlib-js/stats-base-dists-erlang-mean/actions/workflows/test.yml/badge.svg?branch=main
[test-url]: https://github.com/stdlib-js/stats-base-dists-erlang-mean/actions/workflows/test.yml?query=branch:main

[coverage-image]: https://img.shields.io/codecov/c/github/stdlib-js/stats-base-dists-erlang-mean/main.svg
[coverage-url]: https://codecov.io/github/stdlib-js/stats-base-dists-erlang-mean?branch=main

<!--

[dependencies-image]: https://img.shields.io/david/stdlib-js/stats-base-dists-erlang-mean.svg
[dependencies-url]: https://david-dm.org/stdlib-js/stats-base-dists-erlang-mean/main

-->

[chat-image]: https://img.shields.io/gitter/room/stdlib-js/stdlib.svg
[chat-url]: https://app.gitter.im/#/room/#stdlib-js_stdlib:gitter.im

[stdlib]: https://github.com/stdlib-js/stdlib

[stdlib-authors]: https://github.com/stdlib-js/stdlib/graphs/contributors

[umd]: https://github.com/umdjs/umd
[es-module]: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Modules

[deno-url]: https://github.com/stdlib-js/stats-base-dists-erlang-mean/tree/deno
[deno-readme]: https://github.com/stdlib-js/stats-base-dists-erlang-mean/blob/deno/README.md
[umd-url]: https://github.com/stdlib-js/stats-base-dists-erlang-mean/tree/umd
[umd-readme]: https://github.com/stdlib-js/stats-base-dists-erlang-mean/blob/umd/README.md
[esm-url]: https://github.com/stdlib-js/stats-base-dists-erlang-mean/tree/esm
[esm-readme]: https://github.com/stdlib-js/stats-base-dists-erlang-mean/blob/esm/README.md
[branches-url]: https://github.com/stdlib-js/stats-base-dists-erlang-mean/blob/main/branches.md

[stdlib-license]: https://raw.githubusercontent.com/stdlib-js/stats-base-dists-erlang-mean/main/LICENSE

[erlang-distribution]: https://en.wikipedia.org/wiki/Erlang_distribution

[expected-value]: https://en.wikipedia.org/wiki/Expected_value

</section>

<!-- /.links -->
