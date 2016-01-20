# Data-binding

## Overview

In this lesson we're going to go a bit deeper into the `{{ }}` curly brace syntax you've seen. What does it actually do?

## Objectives

- Describe one/two-way data-binding in `$scope`

## Data-binding

We've talked about data-binding before, but if it's not on the top of your memory you don't need to worry. Data-binding is the term for keeping our model values in sync with our view. Whenever the model changes, our view needs to change too to reflect the change. Whenever our view changes (such as a user typing into an input), we need to update our model with the latest value. This is done via data-binding.

### One-way

The curly braces syntax (`{{ }}`) binds our model value into our view in the form of text. This is one-way bound - the model can update the view, but our view cannot update the model (you can't type into text - only an input!).

We can also bind text into the DOM using a `ng-bind` attribute on the HTML element instead.

```js
{{ name }}
<span ng-bind="name"></span>
```

These will both display the same thing!

### Two-way

We can two-way bind our data into certain HTML elements - ones that accept input. For example, you guessed it - an `<input />`. This is done with the `ng-model` attribute (more on `ng-model` and `ng-bind` later on).

```js
<input type="text" ng-model="name" />
```

Whenever we type in our `<input />`, or `$scope.name` gets updated, they will both reflect the changes to the value. 

## Watching for updates

We can also watch for updates - how neat! The `$scope` object exposes a few APIs, one of them is `$watch`. `$watch` allows us to pass one of our `$scope` object's keys through, and fires off a callback whenever it updates.

For example:

```js
$scope.$watch('name', function (newValue, oldValue) {
  console.log('name changed from %s to %s', newValue, oldValue);
});
```

We could use this with the two-way data-binding example above. This would fire a `console.log` statement every time the user types in the input!
