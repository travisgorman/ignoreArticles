#Sort Without Articles
Sort an array of band names alphabetically, ignoring articles ('a', 'an', 'the') and render into a list on the page.

#Features
Doesn't do anything other than display the resulting list. As you see 'The Bled' is second from the top, while 'A Skylit Drive' is second to the bottom because, while my sorting function is disregarding 'the' and 'a', we still want to display the band names correctly in the list.

![screenshot](http://i.imgur.com/Z6QkxPJ.jpg)

## `String.replace()` and Regular Expressions
`replace( x, y )` takes two arguements. `x` is the string pattern you want to replace, and `y` is what you want to replace instances of `x` with.  If you want to delete or ignore something, replace it with an empty string. 

Make a strip function that takes a string, and if it finds an instance of 'a', 'the' or 'an', replaces it with an empty string (`''`), returning the string without the article.

```js
function strip(bandname){
	return bandname.replace(/^(a |the |an )/i, '').trim()
}
```
### `String.trim()`
Returns a string with no whitespace on either end. In this case, I didn't see `trim()` making a difference, but adding it is probably best practice when ignoring or deleting a piece of string completely.

## `Array.sort`
`sort( [compare function] )` sorts the elements in a typed array in place, and returns the array. The function that defines the sort order is just the same as if we were sorting alphabetically or numerically (ascending) 

```js
const sorted = bands.sort((a, b) => (a > b) ? 1: -1)
```
except we're putting `a` and `b` through our `strip()` function so it can compare the two, ignoring articles.

```js
const sorted = bands.sort((a, b) => (strip(a) > strip(b)) ? 1 : -1)
```



