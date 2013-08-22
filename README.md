js-binaryheap-decreasekey
=========================

**JS Min Binary Heap implementation w/ decrease-key support.**

I wrote this because I needed a Dijkstra's algorithm with priority queue in my [Paris Public Transports route planning webapp](http://rombdn.github.com/fx-metrobusparis)

The original binary heap implementation is from the book *Eloquent Javascript* by Marijn Haverbeke : [source](http://eloquentjavascript.net/appendix2.html)


Usage
---------

**Prototype**

*function BinaryHeap( scoreFunction, idFunction, valueProperty )*
`scoreFunction` must return the property used for ordering
`idFunction` must return the property used as key
`valueProperty` is the name of the property to be modified in decreaseKey


**Example**

```javascript
var heap = new BinaryHeap(
  function(element) { return element.age; },
  function(element) { return element.name; },
  'age'
);

heap.push({ age: 20, name: 'foo' });
//heap.content => {name: 'foo',...}
//heap.map => {foo: 0}
heap.push({ age: 45, name: 'bar' });
//heap.content => {name: 'foo',...}, {name: 'bar', ...}
//heap.map => {foo: 0, bar: 1}
heap.push({ age: 7, name: 'joe' });
//heap.content => {name: 'joe', ...}, {name: 'foo',...}, {name: 'bar', ...}
//heap.map =>foo: 2, bar: 1, joe: 0 (children not always in order)
heap.decreaseKey( 'bar', 5 );
//heap.content => {name: 'bar', ...}, {name: 'joe',...}, {name: 'foo', ...}
//heap.map =>foo: 2, bar: 0, joe: 1
heap.pop()
//=> {name: 'bar', ...}
```

Real world usage : [Fx OS Paris Transport webapp](https://github.com/rombdn/fxos-metrobusparis/blob/master/js/app.js#L380)


Licence
---------
(c) 2013 Romain BEAUDON This code may be freely distributed under the terms of the MIT Licence
