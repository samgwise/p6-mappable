Mappable
========

Mappable - a composable interface for serialising objects

SYNOPSIS
========

    use Mappable;
    use Test;

    class Foo does Mappable {
      has $.value;

      to-map( --> Map) {
        %(
          :$!value
        )
      }

      from-map(Map $map --> Foo) {
        self.new(|$map)
      }
    }

    my $obj = Foo.new( :value('Bar') );

    is-deeply $obj.to-map, $obj.from-map($obj.to-map), "";

DESCRIPTION
===========

Mappable is a simple interface that specifies a simple contract. I can give you a map, which represents my current state and consume a map to recreate my current state.

AUTHOR
======

Sam Gillespie <samgwise@gmail.com>

COPYRIGHT AND LICENSE
=====================

Copyright 2017 Sam Gillespie

This library is free software; you can redistribute it and/or modify it under the Artistic License 2.0.
