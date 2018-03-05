# d3-array

JavaScript 中的数据通常由一个数组来表示，所以当可视化或分析数据时往往也会操作数组。常见的数组操作包括切片，过滤，遍历等等。JavaScript 本身支持的数组操作可以参考 [这里](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/prototype).

JavaScript 中 **修改数组自身** 的方法:

* [*array*.pop](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/pop) - 移除最后一个元素.
* [*array*.push](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/push) - 追加一个或多个元素.
* [*array*.reverse](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/reverse) - 数组翻转.
* [*array*.shift](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/shift) - 移除第一个元素.
* [*array*.sort](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/sort) - 排序.
* [*array*.splice](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/splice) - 添加或者移除.
* [*array*.unshift](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/unshift) - 在数组前添加一个或多个元素.

JavaScript 中数组的 **存取方法** :

* [*array*.concat](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/concat) - 将数组与数组或值合并.
* [*array*.join](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/join) - 只用指定的字符串将数组转为一个字符串.
* [*array*.slice](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/slice) - 提取切片.
* [*array*.indexOf](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/indexOf) - 找出指定元素的索引.
* [*array*.lastIndexOf](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/lastIndexOf) - 找出指定元素的最后一个索引.

JavaScript 中数组的 **迭代方法** :

* [*array*.filter](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/filter) - 过滤.
* [*array*.forEach](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/forEach) - 对每个元素执行某个方法.
* [*array*.every](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/every) - 是否每个元素都符合给定的条件.
* [*array*.map](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/map) - 根据指定的操作对每个元素执行后返回一个新的数组.
* [*array*.some](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/some) - 是否存在符合某个条件的元素.
* [*array*.reduce](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/reduce) - 从左到右执行 reduce 操作并返回一个值.
* [*array*.reduceRight](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/reduceRight) - 从右到左执行 reduce 操作并返回一个值.

## Installing

NPM 安装: `npm install d3-array`. 或者下载 [latest release](https://github.com/d3/d3-array/releases/latest). 也可以直接从 [d3js.org](https://d3js.org) 以 [standalone library](https://d3js.org/d3-array.v1.min.js) 或作为 [D3 4.0](https://github.com/d3/d3) 的一部分载入. 支持 AMD, CommonJS 以及最基本的标签引入形式, 如果使用标签引入会暴露全局 `d3` 变量:

```html
<script src="https://d3js.org/d3-array.v1.min.js"></script>
<script>

var min = d3.min(array);

</script>
```

[在浏览器中测试 d3-array .](https://tonicdev.com/npm/d3-array)

## API Reference

* [Statistics](#statistics)
* [Search](#search)
* [Transformations](#transformations)
* [Histograms](#histograms)
* [Histogram Thresholds](#histogram-thresholds)

### Statistics

基本的统计类方法.

<a name="min" href="#min">#</a> d3.<b>min</b>(<i>array</i>[, <i>accessor</i>]) [<源码>](https://github.com/d3/d3-array/blob/master/src/min.js "Source")

对指定的 *array* 进行自然排序返回最小值。如果数组为空则返回 undefined。可选的参数 *accessor* 可以用来自定义如何访问数组中的元素。*accessor* 将会被传递给 *map* 以在数组的每个元素上进行调用，返回值将会被作为对比依据。

与内置的 [Math.min](https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Math/min) 不同，这个方法可以忽略 undefined, null 和 NaN 等特殊值。在可视化中用来忽略缺失数据是很有用的。需要注意的是，对比是以自然排序进行的，而非数值对比。比如对字符串 ['20', '3'] 进行 `min` 操作返回 `20`，而对数值 [20, 3] 进行 `min` 操作则返回 `3`。

See also [scan](#scan) and [extent](#extent).

<a name="max" href="#max">#</a> d3.<b>max</b>(<i>array</i>[, <i>accessor</i>]) [<源码>](https://github.com/d3/d3-array/blob/master/src/max.js "Source")

对指定的 *array* 进行自然排序返回最大值。如果数组为空则返回 undefined。可选的参数 *accessor* 可以用来自定义如何访问数组中的元素。*accessor* 将会被传递给 *map* 以在数组的每个元素上进行调用，返回值将会被作为对比依据。

与内置的 [Math.max](https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Math/max) 不同，这个方法可以忽略 undefined, null 和 NaN 等特殊值。在可视化中用来忽略缺失数据是很有用的。需要注意的是，对比是以自然排序进行的，而非数值对比。比如对字符串 ['20', '3'] 进行 `max` 操作返回 '3'，而对数值 [20, 3] 进行 `max` 操作则返回 20。

请参阅 [scan](#scan) 和 [extent](#extent).

<a name="extent" href="#extent">#</a> d3.<b>extent</b>(<i>array</i>[, <i>accessor</i>]) [<源码>](https://github.com/d3/d3-array/blob/master/src/extent.js "Source")

使用自然排序返回指定数组的 [最小值](#min) 和 [最大值](#max)。如果数组为空，则返回 [undefined, undefined]。可选的 *accessor* 可以用来指定数组元素的访问方式，如果指定了 *accessor* 则在获取最值前会通过 *array*.map(*accessor*) 进行计算。

<a name="sum" href="#sum">#</a> d3.<b>sum</b>(<i>array</i>[, <i>accessor</i>]) [<源码>](https://github.com/d3/d3-array/blob/master/src/sum.js "Source")

对指定的 *array* 计算和. 如果数组为空则返回 0，可选的 *accessor* 可以用来指定数组元素的访问方式，如果指定了 *accessor* 则在求和前会通过 *array*.map(*accessor*) 进行计算。在忽略 undefined 和 NaN 时 *accessor* 很有用.

<a name="mean" href="#mean">#</a> d3.<b>mean</b>(<i>array</i>[, <i>accessor</i>]) [<源码>](https://github.com/d3/d3-array/blob/master/src/mean.js "Source")

对指定的数组返回数组的均值。如果数组为空则返回 undefined. 如果指定了 *accessor* 则相当于在计算之前调用了 *array.map(accessor)*. 这个方法会忽略 undefined 和 NaN. 在忽略缺失值时指定 *accessor* 会很有用。

<a name="median" href="#median">#</a> d3.<b>median</b>(<i>array</i>[, <i>accessor</i>]) [<源码>](https://github.com/d3/d3-array/blob/master/src/median.js "Source")

对指定的数组使用 [R-7 方法](https://en.wikipedia.org/wiki/Quantile#Estimating_quantiles_from_a_sample)返回数组的中位数。如果数组为空则返回 undefined. 如果指定了 *accessor* 则相当于在计算之前调用了 *array.map(accessor)*. 这个方法会忽略 undefined 和 NaN.

<a name="quantile" href="#quantile">#</a> d3.<b>quantile</b>(<i>array</i>, <i>p</i>[, <i>accessor</i>]) [<源码>](https://github.com/d3/d3-array/blob/master/src/quantile.js "Source")

返回指定 **有序数组** 的 *p*-分位数, *p* 是 [0, 1] 之间的小数. 例如中位数相当于 *p* = 0.5, 使用 *p* = 0.25 计算第一个四分位数, *p* = 0.75 表示第三个四分位数. 这个方法也使用 [R-7 方法](http://en.wikipedia.org/wiki/Quantile#Quantiles_of_a_population). 例如:

```js
var a = [0, 10, 30];
d3.quantile(a, 0); // 0
d3.quantile(a, 0.5); // 10
d3.quantile(a, 1); // 30
d3.quantile(a, 0.25); // 5
d3.quantile(a, 0.75); // 20
d3.quantile(a, 0.1); // 2
```

如果指定了 *accessor* 则相当于在计算之前调用了 *array.map(accessor)*。

<a name="variance" href="#variance">#</a> d3.<b>variance</b>(<i>array</i>[, <i>accessor</i>]) [<源码>](https://github.com/d3/d3-array/blob/master/src/variance.js "Source")

根据指定的数组返回 [unbiased estimator of the population variance(无偏估计方差)](http://mathworld.wolfram.com/SampleVariance.html). 如果数组中包含的元素个数小于 2 则返回 undefined. 如果指定了 *accessor* 则相当于在计算之前调用了 *array.map(accessor)*. 这个方法忽略了 undefined 和 NaN. 在忽略缺失数据时会很有用.

<a name="deviation" href="#deviation">#</a> d3.<b>deviation</b>(<i>array</i>[, <i>accessor</i>]) [<源码>](https://github.com/d3/d3-array/blob/master/src/deviation.js "Source")

返回数组的标准差，标准差定义为 [bias-corrected variance(方差)](#variance) 的平方根。如果数组中包含的元素个数小于 2 则返回 undefined. 如果指定了 *accessor* 则相当于在计算之前调用了 *array.map(accessor)*. 这个方法忽略了 undefined 和 NaN. 在忽略缺失数据时会很有用.

### Search

查找类方法.

<a name="scan" href="#scan">#</a> d3.<b>scan</b>(<i>array</i>[, <i>comparator</i>]) [<源码>](https://github.com/d3/d3-array/blob/master/src/scan.js "Source")

对指定的数组执行线性扫描，根据指定的比较器返回最小元素的索引。如果给定的数组中没有可比较的元素 ( 比如比较时返回 NaN ) 则返回 undefined。如果没有指定 *comparator* 则默认为 [ascending(升序)](#ascending)，例如:

```js
var array = [{foo: 42}, {foo: 91}];
d3.scan(array, function(a, b) { return a.foo - b.foo; }); // 0
d3.scan(array, function(a, b) { return b.foo - a.foo; }); // 1
```

这个方法类似于 [min](#min)，但是使用的是比较器而不是访问器并且返回的是索引而不是元素值。参考 [bisect](#bisect).

<a name="bisectLeft" href="#bisectLeft">#</a> d3.<b>bisectLeft</b>(<i>array</i>, <i>x</i>[, <i>lo</i>[, <i>hi</i>]]) [<源码>](https://github.com/d3/d3-array/blob/master/src/bisect.js#L6 "Source")

返回指定的 *x* 在已有 *array* 中的插入位置并保证依然有序。*lo* 和 *hi* 参数用来在 *array* 中指定一个查找子集以在寻找插入点时只考虑子集。默认情况下考虑所有的元素。如果 *x* 已经存在原有的数组中，则插入点会在已有的元素前面(在已有元素的左侧)。返回值可以用来对数组进行 [splice](https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Array/splice) 操作。返回的值将原数组分为两部分，假设 *v* 为原数组中的值，则 *v* < *x* 的值包含在 *array*.slice(*lo*, *i*) 中(左半部分)，*v* >= *x* 的值包含在 *array*.slice(*i*, *hi*) 中(右半部分).

<a name="bisect" href="#bisect">#</a> d3.<b>bisect</b>(<i>array</i>, <i>x</i>[, <i>lo</i>[, <i>hi</i>]]) [<源码>](https://github.com/d3/d3-array/blob/master/src/bisect.js "Source")<br>
<a name="bisectRight" href="#bisectRight">#</a> d3.<b>bisectRight</b>(<i>array</i>, <i>x</i>[, <i>lo</i>[, <i>hi</i>]]) [<源码>](https://github.com/d3/d3-array/blob/master/src/bisect.js#L6 "Source")

与 [bisectLeft](#bisectLeft) 操作类似，但是遍历方向是自右向左，如果 *x* 和 *array* 中的值一样则插入点会定位在已有元素的右侧。返回的插入点会将原数组分为两部分: *v* <= *x* 的值会包含在 *array*.slice(*lo*, *i*) 中(左侧半部分)，*v* > *x* 包含在 *array*.slice(*i*, *hi*) 中(右半部分)。

<a name="bisector" href="#bisector">#</a> d3.<b>bisector</b>(<i>accessor</i>) [<源码>](https://github.com/d3/d3-array/blob/master/src/bisector.js "Source")
<br><a name="bisector" href="#bisector">#</a> d3.<b>bisector</b>(<i>comparator</i>) [<源码>](https://github.com/d3/d3-array/blob/master/src/bisector.js "Source")

根据指定的 *accessor* 或 *comparator* 返回一个新的二分查找对象。这个方法可以被用来二等分对象数组，而不会仅仅局限于基本的数组(基础数据类型组成的数组)。可以看做是 [bisect](#bisect) 的补充。例如给定一下对象数组:

```js
var data = [
  {date: new Date(2011, 1, 1), value: 0.5},
  {date: new Date(2011, 2, 1), value: 0.6},
  {date: new Date(2011, 3, 1), value: 0.7},
  {date: new Date(2011, 4, 1), value: 0.8}
];
```

可以指定一个适当的划分函数:

```js
var bisectDate = d3.bisector(function(d) { return d.date; }).right;
```

等价于指定一个比较器:

```js
var bisectDate = d3.bisector(function(d, x) { return d.date - x; }).right;
```

然后以 *bisectDate*(*array*, *date*) 的形式调用，返回一个索引值。请注意，比较器总是传递需要检索的值 `x` 作为第二个参数。使用比较器而不是访问器则可以将自定义排序规则，比如使用降序而不是升序来查找索引位置。

<a name="bisector_left" href="#bisector_left">#</a> <i>bisector</i>.<b>left</b>(<i>array</i>, <i>x</i>[, <i>lo</i>[, <i>hi</i>]]) [<源码>](https://github.com/d3/d3-array/blob/master/src/bisector.js#L6 "Source")

等价于 [bisectLeft](#bisectLeft), 但是使用的是 bisector 的访问比较器.

<a name="bisector_right" href="#bisector_right">#</a> <i>bisector</i>.<b>right</b>(<i>array</i>, <i>x</i>[, <i>lo</i>[, <i>hi</i>]]) [<源码>](https://github.com/d3/d3-array/blob/master/src/bisector.js#L16 "Source")

等价于 [bisectRight](#bisectRight), 但是使用的是 bisector 的访问比较器.

<a name="ascending" href="#ascending">#</a> d3.<b>ascending</b>(<i>a</i>, <i>b</i>) [<源码>](https://github.com/d3/d3-array/blob/master/src/ascending.js "Source")

如果 *a* 小于 *b* 则返回 -1, 如果 *a* 大于 *b* 返回 1 否则返回 0. 这是自然排序的比较器，可以与内置的 [*array*.sort](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/sort) 一起使用使用以安装升序排列元素。内部实现为:

```js
function ascending(a, b) {
  return a < b ? -1 : a > b ? 1 : a >= b ? 0 : NaN;
}
```

请注意，如果没有为内置的排序函数指定比较器则会默认安装字典顺序排序，会导致想不到的排序结果。

<a name="descending" href="#descending">#</a> d3.<b>descending</b>(<i>a</i>, <i>b</i>) [<源码>](https://github.com/d3/d3-array/blob/master/src/descending.js "Source")

如果 *a* 大于 *b* 则返回 -1, 如果 *a* 小于 *b* 返回 1 否则返回 0. 这是自然排序的比较器，可以与内置的 [*array*.sort](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/sort) 一起使用使用以安装降序排列元素。内部实现为:

```js
function descending(a, b) {
  return b < a ? -1 : b > a ? 1 : b >= a ? 0 : NaN;
}
```

请注意，如果没有为内置的排序函数指定比较器则会默认安装字典顺序排序，会导致想不到的排序结果。

### Transformations

数组变换类方法，生成新的数组

<a name="cross" href="#cross">#</a> d3.<b>cross</b>(<i>a</i>, <i>b</i>[, <i>reducer</i>]) [<源码>](https://github.com/d3/d3-array/blob/master/src/cross.js "Source")

返回两个数组 *a* 和 *b* 的 [Cartesian product(笛卡尔积)](https://en.wikipedia.org/wiki/Cartesian_product)，对于 *a* 中的每个元素 *i* 以及数组 *b* 中的每个元素 *j*，有序的调用指定的 *reducer* 函数，元素 *i* 和 *j* 作为 *reducer* 的两个参数。如果没有指定 *reducer* 则默认为每一个组创建一个包含两个元素的二元数组:

```js
function pair(a, b) {
  return [a, b];
}
```

例如:

```js
d3.cross([1, 2], ["x", "y"]); // returns [[1, "x"], [1, "y"], [2, "x"], [2, "y"]]
d3.cross([1, 2], ["x", "y"], (a, b) => a + b); // returns ["1x", "1y", "2x", "2y"]
```

<a name="merge" href="#merge">#</a> d3.<b>merge</b>(<i>arrays</i>) [<源码>](https://github.com/d3/d3-array/blob/master/src/merge.js "Source")

将指定的一系列 *arrays* 合并为一个单独的数组。这个方法与内置的 `concat` 方法类似，但是当你有一个数组的数组时会更方便:

```js
d3.merge([[1], [2, 3]]); // returns [1, 2, 3]
```

<a name="pairs" href="#pairs">#</a> d3.<b>pairs</b>(<i>array</i>[, <i>reducer</i>]) [<源码>](https://github.com/d3/d3-array/blob/master/src/pairs.js "Source")

对数组中的每两个相邻的元素，一次调用指定的 *reducer* 函数并传递当前的两个元素 *i* 和 *i* -1。如果没有指定 *reducer* 则默认为每一个组合创建一个二元数组:

```js
function pair(a, b) {
  return [a, b];
}
```

例如:

```js
d3.pairs([1, 2, 3, 4]); // returns [[1, 2], [2, 3], [3, 4]]
d3.pairs([1, 2, 3, 4], (a, b) => b - a); // returns [1, 1, 1];
```

如果指定的数组中元素小于两个则返回一个空数组.

<a name="permute" href="#permute">#</a> d3.<b>permute</b>(<i>array</i>, <i>indexes</i>) [<源码>](https://github.com/d3/d3-array/blob/master/src/permute.js "Source")

使用指定的 *indexes* 数组返回重新排列后的 *array*。返回的数组包含原数组对应索引的元素。比如 permute(["a", "b", "c"], [1, 2, 0]) 返回 ["b", "c", "a"]. *indexes* 的长度可以与 *array* 的长度可以不一致，并且可以接受重复索引值或忽略某些索引值。

这个方法可以将对象中的属性按照一定次序提取到数组中。按顺序提取值可以用于生成嵌套选择的数据数据。比如:

```js
var object = {yield: 27, variety: "Manchuria", year: 1931, site: "University Farm"},
    fields = ["site", "variety", "yield"];

d3.permute(object, fields); // returns ["University Farm", "Manchuria", 27]
```

<a name="shuffle" href="#shuffle">#</a> d3.<b>shuffle</b>(<i>array</i>[, <i>lo</i>[, <i>hi</i>]]) [<源码>](https://github.com/d3/d3-array/blob/master/src/shuffle.js "Source")

使用 [Fisher–Yates shuffle](http://bost.ocks.org/mike/shuffle/) 算法将数组的顺序随机打乱。

<a name="ticks" href="#ticks">#</a> d3.<b>ticks</b>(<i>start</i>, <i>stop</i>, <i>count</i>) [<源码>](https://github.com/d3/d3-array/blob/master/src/ticks.js "Source")

在 *start* 和 *stop* (包含)之间返回大约 *count* + 1 个等间隔的数组序列，每个值都是 10 的 1, 2 或 5 的次幂。参考  [d3.tickIncrement](#tickIncrement), [d3.tickStep](#tickStep) 和 [*linear*.ticks](https://github.com/d3/d3-scale/blob/master/README.md#linear_ticks).

当且仅当精确时可能包含指定的起始值。

Ticks are inclusive in the sense that they may include the specified *start* and *stop* values if (and only if) they are exact, nicely-rounded values consistent with the inferred [step](#tickStep). More formally, each returned tick *t* satisfies *start* ≤ *t* and *t* ≤ *stop*.

<a name="tickIncrement" href="#tickIncrement">#</a> d3.<b>tickIncrement</b>(<i>start</i>, <i>stop</i>, <i>count</i>) [<源码>](https://github.com/d3/d3-array/blob/master/src/ticks.js#L16 "Source")

Like [d3.tickStep](#tickStep), except requires that *start* is always less than or equal to *step*, and if the tick step for the given *start*, *stop* and *count* would be less than one, returns the negative inverse tick step instead. This method is always guaranteed to return an integer, and is used by [d3.ticks](#ticks) to avoid guarantee that the returned tick values are represented as precisely as possible in IEEE 754 floating point.

<a name="tickStep" href="#tickStep">#</a> d3.<b>tickStep</b>(<i>start</i>, <i>stop</i>, <i>count</i>) [<源码>](https://github.com/d3/d3-array/blob/master/src/ticks.js#L16 "Source")

Returns the difference between adjacent tick values if the same arguments were passed to [d3.ticks](#ticks): a nicely-rounded value that is a power of ten multiplied by 1, 2 or 5. Note that due to the limited precision of IEEE 754 floating point, the returned value may not be exact decimals; use [d3-format](https://github.com/d3/d3-format) to format numbers for human consumption.

<a name="range" href="#range">#</a> d3.<b>range</b>([<i>start</i>, ]<i>stop</i>[, <i>step</i>]) [<源码>](https://github.com/d3/d3-array/blob/master/src/range.js "Source")

Returns an array containing an arithmetic progression, similar to the Python built-in [range](http://docs.python.org/library/functions.html#range). This method is often used to iterate over a sequence of uniformly-spaced numeric values, such as the indexes of an array or the ticks of a linear scale. (See also [d3.ticks](#ticks) for nicely-rounded values.)

If *step* is omitted, it defaults to 1. If *start* is omitted, it defaults to 0. The *stop* value is exclusive; it is not included in the result. If *step* is positive, the last element is the largest *start* + *i* \* *step* less than *stop*; if *step* is negative, the last element is the smallest *start* + *i* \* *step* greater than *stop*. If the returned array would contain an infinite number of values, an empty range is returned.

The arguments are not required to be integers; however, the results are more predictable if they are. The values in the returned array are defined as *start* + *i* \* *step*, where *i* is an integer from zero to one minus the total number of elements in the returned array. For example:

```js
d3.range(0, 1, 0.2) // [0, 0.2, 0.4, 0.6000000000000001, 0.8]
```

This unexpected behavior is due to IEEE 754 double-precision floating point, which defines 0.2 * 3 = 0.6000000000000001. Use [d3-format](https://github.com/d3/d3-format) to format numbers for human consumption with appropriate rounding; see also [linear.tickFormat](https://github.com/d3/d3-scale/blob/master/README.md#linear_tickFormat) in [d3-scale](https://github.com/d3/d3-scale).

Likewise, if the returned array should have a specific length, consider using [array.map](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/map) on an integer range. For example:

```js
d3.range(0, 1, 1 / 49); // BAD: returns 50 elements!
d3.range(49).map(function(d) { return d / 49; }); // GOOD: returns 49 elements.
```

<a name="transpose" href="#transpose">#</a> d3.<b>transpose</b>(<i>matrix</i>) [<源码>](https://github.com/d3/d3-array/blob/master/src/transpose.js "Source")

Uses the [zip](#zip) operator as a two-dimensional [matrix transpose](http://en.wikipedia.org/wiki/Transpose).

<a name="zip" href="#zip">#</a> d3.<b>zip</b>(<i>arrays…</i>) [<源码>](https://github.com/d3/d3-array/blob/master/src/zip.js "Source")

Returns an array of arrays, where the *i*th array contains the *i*th element from each of the argument *arrays*. The returned array is truncated in length to the shortest array in *arrays*. If *arrays* contains only a single array, the returned array contains one-element arrays. With no arguments, the returned array is empty.

```js
d3.zip([1, 2], [3, 4]); // returns [[1, 3], [2, 4]]
```

### Histograms

[<img src="https://raw.githubusercontent.com/d3/d3-array/master/img/histogram.png" width="480" height="250" alt="Histogram">](http://bl.ocks.org/mbostock/3048450)

Histograms bin many discrete samples into a smaller number of consecutive, non-overlapping intervals. They are often used to visualize the distribution of numerical data.

<a name="histogram" href="#histogram">#</a> d3.<b>histogram</b>() [<源码>](https://github.com/d3/d3-array/blob/master/src/histogram.js "Source")

Constructs a new histogram generator with the default settings.

<a name="_histogram" href="#_histogram">#</a> <i>histogram</i>(<i>data</i>) [<源码>](https://github.com/d3/d3-array/blob/master/src/histogram.js#L14 "Source")

Computes the histogram for the given array of *data* samples. Returns an array of bins, where each bin is an array containing the associated elements from the input *data*. Thus, the `length` of the bin is the number of elements in that bin. Each bin has two additional attributes:

* `x0` - the lower bound of the bin (inclusive).
* `x1` - the upper bound of the bin (exclusive, except for the last bin).

<a name="histogram_value" href="#histogram_value">#</a> <i>histogram</i>.<b>value</b>([<i>value</i>]) [<源码>](https://github.com/d3/d3-array/blob/master/src/histogram.js#L58 "Source")

If *value* is specified, sets the value accessor to the specified function or constant and returns this histogram generator. If *value* is not specified, returns the current value accessor, which defaults to the identity function.

When a histogram is [generated](#_histogram), the value accessor will be invoked for each element in the input data array, being passed the element `d`, the index `i`, and the array `data` as three arguments. The default value accessor assumes that the input data are orderable (comparable), such as numbers or dates. If your data are not, then you should specify an accessor that returns the corresponding orderable value for a given datum.

This is similar to mapping your data to values before invoking the histogram generator, but has the benefit that the input data remains associated with the returned bins, thereby making it easier to access other fields of the data.

<a name="histogram_domain" href="#histogram_domain">#</a> <i>histogram</i>.<b>domain</b>([<i>domain</i>]) [<源码>](https://github.com/d3/d3-array/blob/master/src/histogram.js#L62 "Source")

If *domain* is specified, sets the domain accessor to the specified function or array and returns this histogram generator. If *domain* is not specified, returns the current domain accessor, which defaults to [extent](#extent). The histogram domain is defined as an array [*min*, *max*], where *min* is the minimum observable value and *max* is the maximum observable value; both values are inclusive. Any value outside of this domain will be ignored when the histogram is [generated](#_histogram).

For example, if you are using the the histogram in conjunction with a [linear scale](https://github.com/d3/d3-scale/blob/master/README.md#linear-scales) `x`, you might say:

```js
var histogram = d3.histogram()
    .domain(x.domain())
    .thresholds(x.ticks(20));
```

You can then compute the bins from an array of numbers like so:

```js
var bins = histogram(numbers);
```

Note that the domain accessor is invoked on the materialized array of [values](#histogram_value), not on the input data array.

<a name="histogram_thresholds" href="#histogram_thresholds">#</a> <i>histogram</i>.<b>thresholds</b>([<i>count</i>]) [<源码>](https://github.com/d3/d3-array/blob/master/src/histogram.js#L66 "Source")
<br><a name="histogram_thresholds" href="#histogram_thresholds">#</a> <i>histogram</i>.<b>thresholds</b>([<i>thresholds</i>])  [<源码>](https://github.com/d3/d3-array/blob/master/src/histogram.js#L66 "Source")

If *thresholds* is specified, sets the [threshold generator](#histogram-thresholds) to the specified function or array and returns this histogram generator. If *thresholds* is not specified, returns the current threshold generator, which by default implements [Sturges’ formula](#thresholdSturges). (Thus by default, the histogram values must be numbers!) Thresholds are defined as an array of values [*x0*, *x1*, …]. Any value less than *x0* will be placed in the first bin; any value greater than or equal to *x0* but less than *x1* will be placed in the second bin; and so on. Thus, the [generated histogram](#_histogram) will have *thresholds*.length + 1 bins. See [histogram thresholds](#histogram-thresholds) for more information.

Any threshold values outside the [domain](#histogram_domain) are ignored. The first *bin*.x0 is always equal to the minimum domain value, and the last *bin*.x1 is always equal to the maximum domain value.

If a *count* is specified instead of an array of *thresholds*, then the [domain](#histogram_domain) will be uniformly divided into approximately *count* bins; see [ticks](#ticks).

### Histogram Thresholds

These functions are typically not used directly; instead, pass them to [*histogram*.thresholds](#histogram_thresholds). You may also implement your own threshold generator taking three arguments: the array of input [*values*](#histogram_value) derived from the data, and the [observable domain](#histogram_domain) represented as *min* and *max*. The generator may then return either the array of numeric thresholds or the *count* of bins; in the latter case the domain is divided uniformly into approximately *count* bins; see [ticks](#ticks).

<a name="thresholdFreedmanDiaconis" href="#thresholdFreedmanDiaconis">#</a> d3.<b>thresholdFreedmanDiaconis</b>(<i>values</i>, <i>min</i>, <i>max</i>) [<源码>](https://github.com/d3/d3-array/blob/master/src/threshold/freedmanDiaconis.js "Source")

Returns the number of bins according to the [Freedman–Diaconis rule](https://en.wikipedia.org/wiki/Histogram#Mathematical_definition); the input *values* must be numbers.

<a name="thresholdScott" href="#thresholdScott">#</a> d3.<b>thresholdScott</b>(<i>values</i>, <i>min</i>, <i>max</i>) [<源码>](https://github.com/d3/d3-array/blob/master/src/threshold/scott.js "Source")

Returns the number of bins according to [Scott’s normal reference rule](https://en.wikipedia.org/wiki/Histogram#Mathematical_definition); the input *values* must be numbers.

<a name="thresholdSturges" href="#thresholdSturges">#</a> d3.<b>thresholdSturges</b>(<i>values</i>) [<源码>](https://github.com/d3/d3-array/blob/master/src/threshold/sturges.js "Source")

Returns the number of bins according to [Sturges’ formula](https://en.wikipedia.org/wiki/Histogram#Mathematical_definition); the input *values* must be numbers.