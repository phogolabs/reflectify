# inflate
A Golang reflection package on steroids

[![Documentation][godoc-img]][godoc-url]
[![License][license-img]][license-url]
[![Build Status][action-img]][action-url]
[![Coverage][codecov-img]][codecov-url]
[![Go Report Card][report-img]][report-url]

## Motivation

There are a lot of package that supports data type conversions but neither of
them have good support for extensibility and handling different scenarios. The
purpose of this library is to cover cases in which we want to make
data manipulations based on specific needs. The library works in greedy manner
by trying to convert as much as it can values from one type to another.

## Installation

```console
$ go get -u github.com/phogolabs/inflate
```

## Usage

If you want to convert a value from one type to another, you can use the
following function:

```golang
type Order struct {
  ID string `field:"order_id"`
}

type OrderItem struct {
  OrderID string `field:"order_id"`
}
```

```golang
source := &Order{ID: "0000123"}
target := &OrderItem{}

if err := inflate.Set(source, target); err != nil {
  panic(err)
}
```

You can use the package to set the default values (if they are not set):

```golang
type Account struct {
  Category string `default:"unknown"`
}
```

```golang
account := &Account{}

if err := inflate.SetDefault(account); err != nil {
  panic(err)
}
```

The package supports serialization of parameters in [OpenAPI spec](https://swagger.io/docs/specification/serialization/) format.
For more advanced examples, please read the online documentation.

## Contributing

We are open for any contributions. Just fork the
[project](https://github.com/phogolabs/inflate).

[report-img]: https://goreportcard.com/badge/github.com/phogolabs/inflate
[report-url]: https://goreportcard.com/report/github.com/phogolabs/inflate
[logo-author-url]: https://www.freepik.com/free-vector/abstract-cross-logo-template_1185919.htm
[logo-license]: http://creativecommons.org/licenses/by/3.0/
[codecov-url]: https://codecov.io/gh/phogolabs/inflate
[codecov-img]: https://codecov.io/gh/phogolabs/inflate/branch/master/graph/badge.svg
[action-img]: https://github.com/phogolabs/inflate/workflows/pipeline/badge.svg
[action-url]: https://github.com/phogolabs/inflate/actions
[godoc-url]: https://godoc.org/github.com/phogolabs/inflate
[godoc-img]: https://godoc.org/github.com/phogolabs/inflate?status.svg
[license-img]: https://img.shields.io/badge/license-MIT-blue.svg
[license-url]: LICENSE
