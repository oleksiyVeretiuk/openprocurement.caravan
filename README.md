# Caravan

[![CodeFactor](https://www.codefactor.io/repository/github/openprocurement/openprocurement.caravan/badge)](https://www.codefactor.io/repository/github/openprocurement/openprocurement.caravan)

The purpose of caravan is to interconnect web resources in "if this than that" manner. Also the project was built with extensibility and simplicity in mind, so you're welcome to contribute.

## Documentation

There are some diagrams, describing workflow and code structure of the project. You can find them in `docs/caravan.xml` and open them with [draw.io](https://draw.io)

## Summary

- Testing
- How it works

## Testing

Almost all of the present tests are environment-dependent.
It means, that they require working webapps and db to success.

So, environment-independent tests could be run separately.

Run all tests:
`$ ./bin/nosetests`

Run only environment-independent tests:
`$ ./bin/nosetests -a '!internal'`


## How it works

### Abstract

The main reason of caravan's existance is to interconnect web-resources in "if this than that" manner.

### Conceptions

To do its work, caravan uses a set of atomic actions called `observers`, organized into a network called `runner`.
This network is in charge of data processing. Such approach allows to reuse code and adapt to wide range of
interconnected resources with minimal changes to the present code.

Observers are classes that implement [`Observer`](https://en.wikipedia.org/wiki/Observer_pattern) pattern.
Thank to it, it's becomes possible to organize atomic actions, incapsulated in observers, into the runner.
Runner, in turn, is able to setup itself by interconnecting observers into desirable network, and therefore
control it.
