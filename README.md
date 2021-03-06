# go2-itertools

A port of Python itertools, functools, built-ins, and more-itertools for Go 2 with type generics.


### Remarks

- Currently (2020/11/30), go2go does not recognize the suffix `*_test` in package name. This is why they belong to "main" package so far.


### itertools: infinite iterators

|Python|Slice I/O|Channel I/O|Channel I/O + context|
|:--|:--|:--|:--|
|itertools.count||Count|CountWithContext|
|itertools.cycle|Cycle<sup>[1](#infinite1)</sup>|CycleC|CycleCWithContext|
|itertools.repeat||Repeat|RepeatWithContext|

<a name="infinite1">1</a>: Input slice, output channel


### itertools: iterators terminating on the shortest input sequence

|Python|Slice I/O|Channel I/O|
|:--|:--|:--|
|itertools.accumulate|Accumulate|AccumulateC|
||AccumulateIface|AccumulateIfaceC|
|itertools.chain|Chain|ChainC|
|itertools.chain.from_iterable|ChainFromIterable|ChainFromIterableC|
|itertools.compress|Compress|CompressC|
|itertools.dropwhile|DropWhile|DropWhileC|
|itertools.takewhile|TakeWhile|TakeWhileC|
|itertools.filterfalse|FilterFalse|FilterFalseC|
|itertools.groupby|GroupBy|GroupByC|
||GroupByIface|GroupByIfaceC|
|itertools.islice|ISlice|ISliceC|
|itertools.tee|Tee|TeeC|
|itertools.zip_longest|ZipLongest2|ZipLongest2C|
||ZipLongest3|ZipLongest3C|
||ZipLongest4|ZipLongest4C|

(Note: StarMap is not ported as its original concept is not applicable to Go.)


### functools

#### LRU cache

|Python|Golang|Remarks|
|:--|:--|:--|
|functools.lru_cache|WrapLRUAny|Wraps `func(T any) U`|
|functools.lru_cache|WrapLRUComparable|Wraps `func(T itertools.Comparable) U`|
|functools.lru_cache|WrapLRUHashable|Wraps `func(T itertools.Hashable[T]) U`|


#### Reduce

|Python|Slice I/O|Channel I/O|
|:--|:--|:--|
|functools.reduce|Reduce|ReduceC|


### Python built-ins

|Python|Slice I/O|Channel I/O|
|:--|:--|:--|
|all|All|AllC|
|any|Any|AnyC|
|enumerate|<sup>[1](#builtins1)</sup>|EnumerateC|
|filter|Filter|FilterC|
|map|Map|MapC|
|min|Min|MinC|
|max|Max|MaxC|
|range|Range|RangeC|
|reversed|Reversed|ReversedC|
|sorted|Sorted|SortedC|
|sum|Sum|SumC|
||SumIface|SumIfaceC|
|zip|Zip2|Zip2C|
||Zip3|Zip3C|
||Zip4|Zip4C|

<a name="builtins1">1</a>: Enumeration of slice is useless as Go natively supports it
