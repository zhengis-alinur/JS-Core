# JS Code - Tech Check

## 1. Variables, Values, Types (number, string, boolean, object, null, undefined, Symbol), declaration (var, let, const, hoisting, temporary dead zone)

In JavaScript, variables are containers for storing data values. There are different types of values that variables can hold. These include:

1. **Number**: It represents both integer and floating point numbers.
2. **String**: It represents a sequence of characters and is used for storing text.
3. **Boolean**: This type has two values, `true` and `false`.
4. **Object**: It represents instances which can store collections of data and more complex entities. Objects can be created using `{}` notation.
5. **Null**: It represents a deliberate non-value.
6. **Undefined**: It indicates that a variable has not been assigned a value.
7. **Symbol**: Introduced in ES6, symbols are unique and immutable data type often used as an identifier for object properties.
8. **BigInt**: Numeric primitive in JavaScript that can represent integers with arbitrary magnitude.

For declaring these variables, JavaScript offers three keywords:

- **var**: This declaration is scoped to the nearest function block. `var` is hoisted, which means that it can be accessed in its enclosing scope even before it is declared, but only declared not initialized.
- **let**: Introduced in ES6, it is similar to `var`, but `let` has block-level scope. It's not hoisted in the same way as `var`, which helps in avoiding some common bugs caused by hoisting.
- **const**: Also block-scoped like `let`, but the difference is that a `const` variable cannot be reassigned after it is assigned once. `const` must be initialized during declaration.

**Hoisting**: In JavaScript, `var` and function declarations are moved to the top of their enclosing scope during the compilation phase, a behavior known as hoisting. This is why variables declared with `var` can be referenced before their declaration in the code.
Example:

- **var hoisting**:

```javascript
console.log(bar); // undefined
var bar = "foo";
```

- **Function declaration hoisting**:

```javascript
foo(); // 'something';
function foo() {
  console.log("something");
}
```

**Temporary Dead Zone**: It’s the term used to describe the state where variables exist in the block but are not accessible before their declaration with `let` or `const`. Accessing the block-scoped variable before the declaration will result in a `ReferenceError`.

Understanding these concepts is crucial for mastering variable declarations and scopes in JavaScript. If you have more specific questions or need examples, feel free to ask!

```
console.log(myVariable); // RefferenceError

let myVariable = 'magic';
```

&nbsp;

## 2. Expressions, Operators, Statements (literals, conditions, loops), destructuring, string templating

### 1. Expressions and Operators:

- **Expressions**: An expression is a piece of code that produces a value. For example, `5 * 10` is an expression that evaluates to 50.
- **Operators**: These are used to manipulate values in expressions. They include:
  - Arithmetic operators (`+`, `-`, `*`, `/`, `%`)
  - Comparison operators (`>`, `<`, `>=`, `<=`, `==`, `===`, `!=`, `!==`)
  - Logical operators (`&&`, `||`, `!`)
  - Assignment operators (`=`, `+=`, `-=`, `*=`, `/=`, `??=`, `&&=`, etc.)
  - Unary operators such as `typeof`, `delete`, `void`, etc.
  - Ternary operator (conditional operator) `? :`, which is used as a shorthand for an `if-else` statement.

### 2. Statements:

- **Literals**: They represent values in JavaScript. For example, `42`, `"Hello"`, `true`, are all literals.
- **Conditionals (If, Else, Switch)**: These statements control the flow of execution based on different conditions.
  - `if` condition evaluates an expression and runs a block of code if the expression is `true`.
  - `switch` statements compare a value with several case clauses and execute the corresponding block of code.
- **Loops (For, While, Do-While)**: They repeatedly execute a block of code as long as a given condition is true.
  - `for` loop is typically used when you know how many times you want to execute a statement.
  - `while` loop is used when you want the execution to continue until a specified condition evaluates to false.
  - `do-while` loop is similar to `while`, but it will always be executed at least once.

### 3. Destructuring:

It's a convenient way to extract values from arrays or properties from objects into distinct variables.

- **Array Destructuring**:
  ```javascript
  let [a, b] = [1, 2];
  console.log(a); // 1
  console.log(b); // 2
  ```
- **Object Destructuring**:
  ```javascript
  let { x, y } = { x: 1, y: 2 };
  console.log(x); // 1
  console.log(y); // 2
  ```

### 4. String Templating (Template Literals):

Template literals are string literals allowing embedded expressions, making it much easier to build strings. They are enclosed by backticks `` ` ``.

```javascript
let a = 5;
let b = 10;
console.log(`Fifteen is ${a + b} and not ${2 * a + b}.`);
// "Fifteen is 15 and not 20."
```

## &nbsp;

## 3. Objects (create, manage properties, built-in methods, hash data structure, property descriptors, static methods, calculated props, getter/setter)

### All ways to **Create** an object

- ### 1. Object Literal

  The simplest way to create an object in JavaScript is by using an object literal. It’s just a list of key-value pairs enclosed in curly braces {}.

  ```javascript
  const person = {
    name: "John",
    age: 30,
  };
  console.log(person); //{name: 'John', age: 30}
  ```

- ### 2. Object. create()

  `Object.create()` is a method available since ECMAScript 5 (ES5) that allows you to create an object with the specified prototype object and properties. It provides more control over the prototype chain.

  ```javascript
  const person = Object.create({
    firstName: "john",
    age: 30,
  });
  console.log(person.age); //30
  ```

- ### 3. ES6 Classes

  With the introduction of ES6 (ECMAScript 2015), JavaScript got native support for classes. Classes provide a more structured way to create objects and define their behavior.

  ```javascript
  class Person {
    constructor(name, age) {
      this.name = name;
      this.age = age;
    }
  }
  const user = new Person("John", 30);
  console.log(user); //Person {name: 'John', age: 30}
  ```

- ### 4. new Object()

  Create an empty JavaScript object using new Object()

  ```javascript
  // Create an Object
  const person = new Object();

  // Add Properties
  person.firstName = "John";
  person.lastName = "Doe";
  person.age = 50;
  person.eyeColor = "blue";
  ```

- ### 5. Constructor Functions

  Constructor functions are one of the oldest ways to create objects in JavaScript. They are essentially regular functions. However, there are two rules for using them:

  The name of the constructor function should start with a capital letter.
  The constructor function invoked with the new keyword to create new instances

  ```javascript
  function Person(name, age) {
    this.name = name;
    this.age = age;
  }
  let user = new Person("John", 30);
  console.log(user); //Person {name: 'John', age: 30}
  ```

### Manage properties

Key of Object is a string

Adding and deleting property:

```javascript
fruits.apple = 10;
delete fruits.apple;
```

Calculated properties:

```javascript
const name = 'Alex';
const id = `id`;

const product = {
    [id]: `12WAF312-${name}`;
}
```

### Buil-in methods

**<details><summary>Object.assign();</summary>**

The Object.assign() static method copies all enumerable own properties from one or more source objects to a target object. It returns the modified target object.

```javascript
const target = { a: 1, b: 2 };
const source = { b: 4, c: 5 };

const returnedTarget = Object.assign(target, source);

console.log(target);
// Expected output: Object { a: 1, b: 4, c: 5 }

console.log(returnedTarget === target);
// Expected output: true
```

</details>

**<details><summary>Object.create();</summary>**

The Object.create() static method creates a new object, using an existing object as the prototype of the newly created object.

```javascript
const person = {
  isHuman: false,
  printIntroduction: function () {
    console.log(`My name is ${this.name}. Am I human? ${this.isHuman}`);
  },
};

const me = Object.create(person);

me.name = "Matthew"; // "name" is a property set on "me", but not on "person"
me.isHuman = true; // Inherited properties can be overwritten

me.printIntroduction();
// Expected output: "My name is Matthew. Am I human? true"
```

</details>

**<details><summary>Object.defineProperties();</summary>**
The Object.defineProperties() static method defines new or modifies existing properties directly on an object, returning the object.

```javascript
const object1 = {};

Object.defineProperties(object1, {
  property1: {
    value: 42,
    writable: true,
  },
  property2: {},
});

console.log(object1.property1);
// Expected output: 42
```

</details>

**<details><summary>Object.defineProperty();</summary>**
The Object.defineProperty() static method defines a new property directly on an object, or modifies an existing property on an object, and returns the object.

```javascript
const object1 = {};

Object.defineProperty(object1, "property1", {
  value: 42,
  writable: false,
});

object1.property1 = 77;
// Throws an error in strict mode

console.log(object1.property1);
// Expected output: 42
```

</details>

**<details><summary>Object.entries();</summary>**
The Object.entries() static method returns an array of a given object's own enumerable string-keyed property key-value pairs.

```javascript
const object1 = {
  a: "somestring",
  b: 42,
};

for (const [key, value] of Object.entries(object1)) {
  console.log(`${key}: ${value}`);
}

// Expected output:
// "a: somestring"
// "b: 42"
```

</details>

**<details><summary>Object.freeze();</summary>**
The Object.freeze() static method freezes an object. Freezing an object prevents extensions and makes existing properties non-writable and non-configurable. A frozen object can no longer be changed: new properties cannot be added, existing properties cannot be removed, their enumerability, configurability, writability, or value cannot be changed, and the object's prototype cannot be re-assigned. freeze() returns the same object that was passed in.

Freezing an object is the highest integrity level that JavaScript provides.

```javascript
const obj = {
  prop: 42,
};

Object.freeze(obj);

obj.prop = 33;
// Throws an error in strict mode

console.log(obj.prop);
// Expected output: 42
```

</details>

**<details><summary>Object.fromEntries();</summary>**
The Object.fromEntries() static method transforms a list of key-value pairs into an object.

```javascript
const entries = new Map([
  ["foo", "bar"],
  ["baz", 42],
]);

const obj = Object.fromEntries(entries);

console.log(obj);
// Expected output: Object { foo: "bar", baz: 42 }
```

</details>

**<details><summary>Object.getOwnPropertyDescriptor();</summary>**
The `Object.getOwnPropertyDescriptor()` static method returns an object describing the configuration of a specific property on a given object (that is, one directly present on an object and not in the object's prototype chain). The object returned is mutable but mutating it has no effect on the original property's configuration.

```javascript
const object1 = {
  property1: 42,
};

const descriptor1 = Object.getOwnPropertyDescriptor(object1, "property1");

console.log(descriptor1.configurable);
// Expected output: true

console.log(descriptor1.value);
// Expected output: 42
```

</details>

**<details><summary>Object.getOwnPropertyDescriptors();</summary>**
The Object.getOwnPropertyDescriptors() static method returns all own property descriptors of a given object.

```javascript
const object1 = {
  property1: 42,
};

const descriptors1 = Object.getOwnPropertyDescriptors(object1);

console.log(descriptors1.property1.writable);
// Expected output: true

console.log(descriptors1.property1.value);
// Expected output: 42
```

</details>

**<details><summary>Object.getOwnPropertyNames();</summary>**
The `Object.getOwnPropertyNames()` static method returns an array of all properties (including non-enumerable properties except for those which use Symbol) found directly in a given object.

```javascript
const object1 = {
  a: 1,
  b: 2,
  c: 3,
};

console.log(Object.getOwnPropertyNames(object1));
// Expected output: Array ["a", "b", "c"]
```

</details>

**<details><summary>Object.getOwnPropertySymbols();</summary>**
The `Object.getOwnPropertySymbols()` static method returns an array of all symbol properties found directly upon a given object.

```javascript
const object1 = {};
const a = Symbol("a");
const b = Symbol.for("b");

object1[a] = "localSymbol";
object1[b] = "globalSymbol";

const objectSymbols = Object.getOwnPropertySymbols(object1);

console.log(objectSymbols.length);
// Expected output: 2
```

</details>

**<details><summary>Object.getPrototypeOf();</summary>**
The `Object.getPrototypeOf()` static method returns the prototype (i.e. the value of the internal [[Prototype]] property) of the specified object.

```javascript
const prototype1 = {};
const object1 = Object.create(prototype1);

console.log(Object.getPrototypeOf(object1) === prototype1);
// Expected output: true
```

</details>

**<details><summary>Object.groupBy();</summary>**
The Object.groupBy() static method groups the elements of a given iterable according to the string values returned by a provided callback function. The returned object has separate properties for each group, containing arrays with the elements in the group.

This method should be used when group names can be represented by strings. If you need to group elements using a key that is some arbitrary value, use Map.groupBy() instead.

```javascript
const inventory = [
  { name: "asparagus", type: "vegetables", quantity: 5 },
  { name: "bananas", type: "fruit", quantity: 0 },
  { name: "goat", type: "meat", quantity: 23 },
  { name: "cherries", type: "fruit", quantity: 5 },
  { name: "fish", type: "meat", quantity: 22 },
];

const result = Object.groupBy(inventory, ({ type }) => type);

/* Result is:
{
  vegetables: [
    { name: 'asparagus', type: 'vegetables', quantity: 5 },
  ],
  fruit: [
    { name: "bananas", type: "fruit", quantity: 0 },
    { name: "cherries", type: "fruit", quantity: 5 }
  ],
  meat: [
    { name: "goat", type: "meat", quantity: 23 },
    { name: "fish", type: "meat", quantity: 22 }
  ]
}
*/
```

</details>

**<details><summary>Object.hasOwn();</summary>**
The `Object.hasOwn()` static method returns true if the specified object has the indicated property as its own property. If the property is inherited, or does not exist, the method returns false.

```javascript
const object1 = {
  prop: "exists",
};

console.log(Object.hasOwn(object1, "prop"));
// Expected output: true

console.log(Object.hasOwn(object1, "toString"));
// Expected output: false

console.log(Object.hasOwn(object1, "undeclaredPropertyValue"));
// Expected output: false
```

</details>

**<details><summary>Object.is();</summary>**
The `Object.is()` static method determines whether two values are the same value.

```javascript
console.log(Object.is("1", 1));
// Expected output: false

console.log(Object.is(NaN, NaN));
// Expected output: true

console.log(Object.is(-0, 0));
// Expected output: false

const obj = {};
console.log(Object.is(obj, {}));
// Expected output: false
```

</details>

**<details><summary>Object.isExtensible();</summary>**
The `Object.isExtensible()` static method determines if an object is extensible (whether it can have new properties added to it).

```javascript
const object1 = {};

console.log(Object.isExtensible(object1));
// Expected output: true

Object.preventExtensions(object1);

console.log(Object.isExtensible(object1));
// Expected output: false
```

</details>

**<details><summary>Object.isFrozen();</summary>**
The `Object.isFrozen()` static method determines if an object is frozen.

```javascript
const object1 = {
  property1: 42,
};

console.log(Object.isFrozen(object1));
// Expected output: false

Object.freeze(object1);

console.log(Object.isFrozen(object1));
// Expected output: true
```

</details>

**<details><summary>Object.isSealed();</summary>**
The `Object.isSealed() `static method determines if an object is sealed.

```javascript
const object1 = {
  property1: 42,
};

console.log(Object.isSealed(object1));
// Expected output: false

Object.seal(object1);

console.log(Object.isSealed(object1));
// Expected output: true
```

</details>

**<details><summary>Object.keys();</summary>**
The `Object.keys()` static method returns an array of a given object's own enumerable string-keyed property names.

```javascript
const object1 = {
  a: "somestring",
  b: 42,
  c: false,
};

console.log(Object.keys(object1));
// Expected output: Array ["a", "b", "c"]
```

</details>

**<details><summary>Object.preventExtensions();</summary>**
The `Object.preventExtensions()` static method prevents new properties from ever being added to an object (i.e. prevents future extensions to the object). It also prevents the object's prototype from being re-assigned.

```javascript
const object1 = {};

Object.preventExtensions(object1);

try {
  Object.defineProperty(object1, "property1", {
    value: 42,
  });
} catch (e) {
  console.log(e);
  // Expected output: TypeError: Cannot define property property1, object is not extensible
}
```

</details>

**<details><summary>Object.seal();</summary>**
The `Object.seal()` static method seals an object. Sealing an object prevents extensions and makes existing properties non-configurable. A sealed object has a fixed set of properties: new properties cannot be added, existing properties cannot be removed, their enumerability and configurability cannot be changed, and its prototype cannot be re-assigned. Values of existing properties can still be changed as long as they are writable. seal() returns the same object that was passed in.

```javascript
const object1 = {
  property1: 42,
};

Object.seal(object1);
object1.property1 = 33;
console.log(object1.property1);
// Expected output: 33

delete object1.property1; // Cannot delete when sealed
console.log(object1.property1);
// Expected output: 33
```

</details>

**<details><summary>Object.setPrototypeOf();</summary>**
The `Object.setPrototypeOf()` static method sets the prototype (i.e., the internal [[Prototype]] property) of a specified object to another object or null.

```javascript
const obj = {};
const parent = { foo: "bar" };

console.log(obj.foo);
// Expected output: undefined

Object.setPrototypeOf(obj, parent);

console.log(obj.foo);
// Expected output: "bar"
```

</details>

**<details><summary>Object.values();</summary>**
The `Object.values()` static method returns an array of a given object's own enumerable string-keyed property values.

```javascript
const object1 = {
  a: "somestring",
  b: 42,
  c: false,
};

console.log(Object.values(object1));
// Expected output: Array ["somestring", 42, false]
```

</details>

### Property Descriptors

Both data and accessor descriptors are objects. They share the following optional keys (please note: the defaults mentioned here are in the case of defining properties using `Object.defineProperty()`):

- `configurable`
  when this is set to false, the type of this property cannot be changed between data property and accessor property, and
  the property may not be deleted, and other attributes of its descriptor cannot be changed.
  `Defaults to false`.

  > however, if it's a data descriptor with `writable: true`, the value can be changed, and writable can be changed to false - not to true.

- `enumerable`
  true if and only if this property shows up during enumeration of the properties on the corresponding object.
  `Defaults to false`.

- `value`
  The value associated with the property. Can be any valid JavaScript value (number, object, function, etc.).
  `Defaults to undefined`.

- `writable`
  true if the value associated with the property may be changed with an assignment operator.
  `Defaults to false`.

- `get`
  A function which serves as a getter for the property, or undefined if there is no getter. When the property is accessed, this function is called without arguments and with this set to the object through which the property is accessed (this may not be the object on which the property is defined due to inheritance). The return value will be used as the value of the property.
  `Defaults to undefined`.

- `set`
  A function which serves as a setter for the property, or undefined if there is no setter. When the property is assigned, this function is called with one argument (the value being assigned to the property) and with this set to the object through which the property is assigned.
  `Defaults to undefined`.

### Static Methods

Static methods are methods that belong to the class, not to any instance of the class.

```javascript
class Person {
  static species() {
    return "Homo Sapiens";
  }
}
console.log(Person.species()); // 'Homo Sapiens'
```

### Calculated Properties (Computed Properties)

Properties that are dynamically defined at object creation.

```javascript
let propName = "status";
const user = {
  name: "Alice",
  [propName]: "active", // Computed property
};
```

### Getters/Setters

These are functions that execute on getting and setting a value, respectively.

```javascript
const user = {
  firstName: "Bruce",
  lastName: "Wayne",
  get fullName() {
    return `${this.firstName} ${this.lastName}`;
  },
  set fullName(name) {
    [this.firstName, this.lastName] = name.split(" ");
  },
};

console.log(user.fullName); // Bruce Wayne

user.fullName = "Clark Kent";
console.log(user.fullName); // Clark Kent
```

## &nbsp;

## 4. Arrays (create, indexes, length, modification, built-in methods: sorting, filtering, search, iterating, static methods)

### Creating an Array

- **Array literal**:

```javascript
const cars = ["Saab", "Volvo", "BMW"];
```

- **new Keyword**:

```javascript
const cars = new Array("Saab", "Volvo", "BMW");
```

- **Array.of()**:

```javascript
let myFavoriteFoods = Array.of("pizza", "ice cream", "salad");
```

- **split()**:

```javascript
const str = "I love freeCodeCamp";
```

- **Array.from()**:

```javascript
console.log(Array.from("foo"));
// Expected output: Array ["f", "o", "o"]

---------------------------
const set = new Set(["foo", "bar", "baz", "foo"]);
Array.from(set);
// [ "foo", "bar", "baz" ]

--------------------------
const map = new Map([
  [1, 2],
  [2, 4],
  [4, 8],
]);
Array.from(map);
// [[1, 2], [2, 4], [4, 8]]

const mapper = new Map([
  ["1", "a"],
  ["2", "b"],
]);
Array.from(mapper.values());
// ['a', 'b'];

Array.from(mapper.keys());
// ['1', '2'];
```

### Build-in methods

**<details><summary>Array.prototype.at();</summary>**
The `at()` method takes an integer value and returns the item at that index, allowing for positive and negative integers. Negative integers count back from the last item in the array.

```javascript
const array1 = [5, 12, 8, 130, 44];
let index = 2;

console.log(array1.at(index));
// Expected output: 8

index = -2;
console.log(array1.at(index));
// Expected output: 130
```

</details>

**<details><summary>Array.prototype.concat();</summary>**
The `concat()` method is used to merge two or more arrays. This method does not change the existing arrays but instead returns a new array.

```javascript
const array1 = ["a", "b", "c"];
const array2 = ["d", "e", "f"];

const newArray = array1.concat(array2);

console.log(newArray);
// Expected output: ["a", "b", "c", "d", "e", "f"]
```

</details>

**<details><summary>Array.prototype.copyWithin();</summary>**
The `copyWithin()` method shallow copies part of an array to another location in the same array and returns it without modifying its length.

```javascript
const array1 = ["a", "b", "c", "d", "e"];

// copy to index 0 the element at index 3
console.log(array1.copyWithin(0, 3, 4));
// Expected output: ["d", "b", "c", "d", "e"]

// copy to index 1 all elements from index 3 to the end
console.log(array1.copyWithin(1, 3));
// Expected output: ["d", "d", "e", "d", "e"]
```

</details>

**<details><summary>Array.prototype.entries();</summary>**
The `entries()` method returns a new Array Iterator object that contains the key/value pairs for each index in the array.

```javascript
const array1 = ["a", "b", "c"];
const iterator = array1.entries();

console.log(iterator.next().value);
// Expected output: [0, 'a']

console.log(iterator.next().value);
// Expected output: [1, 'b']
```

</details>

**<details><summary>Array.prototype.every();</summary>**
The `every()` method tests whether all elements in the array pass the test implemented by the provided function. It returns a Boolean value.

```javascript
const isBelowThreshold = (currentValue) => currentValue < 40;
const array1 = [1, 30, 39, 29, 10, 13];

console.log(array1.every(isBelowThreshold));
// Expected output: true
```

</details>

**<details><summary>Array.prototype.fill();</summary>**
The `fill()` method changes all elements in an array to a static value, from a start index (default 0) to an end index (default array.length). It returns the modified array.

```javascript
const array1 = [1, 2, 3, 4];

// Fill with 0 from position 2 until position 4
console.log(array1.fill(0, 2, 4));
// Expected output: [1, 2, 0, 0]

// Fill with 5 from position 1
console.log(array1.fill(5, 1));
// Expected output: [1, 5, 5, 5]

console.log(array1.fill(6));
// Expected output: [6, 6, 6, 6]
```

</details>

**<details><summary>Array.prototype.filter();</summary>**
The `filter()` method creates a new array with all elements that pass the test implemented by the provided function.

```javascript
const words = [
  "spray",
  "limit",
  "elite",
  "exuberant",
  "destruction",
  "present",
];

const result = words.filter((word) => word.length > 6);

console.log(result);
// Expected output: ["exuberant", "destruction", "present"]
```

</details>

**<details><summary>Array.prototype.find();</summary>**
The `find()` method returns the value of the first element in the provided array that satisfies the provided testing function. If no values satisfy the testing function, undefined is returned.

```javascript
const array1 = [5, 12, 8, 130, 44];

const found = array1.find((element) => element > 10);

console.log(found);
// Expected output: 12
```

</details>

**<details><summary>Array.prototype.findIndex();</summary>**
The `findIndex()` method returns the index of the first element in the array that satisfies the provided testing function. Otherwise, it returns -1, indicating that no element passed the test.

```javascript
const array1 = [5, 12, 8, 130, 44];

const isLargeNumber = (element) => element > 13;

console.log(array1.findIndex(isLargeNumber));
// Expected output: 3
```

</details>

**<details><summary>Array.prototype.findLast();</summary>**
The `findLast()` method returns the value of the last element in the array that satisfies the provided testing function. If none of the elements satisfy the testing condition, undefined is returned.

```javascript
const array1 = [5, 12, 8, 130, 44, 10];

const found = array1.findLast((element) => element < 15);

console.log(found);
// Expected output: 10
```

</details>

**<details><summary>Array.prototype.findLastIndex();</summary>**
The `findLastIndex()` method returns the index of the last element in the array that satisfies the provided testing function. If no element qualifies, it returns -1.

```javascript
const array1 = [5, 12, 8, 130, 44, 10];

const isSmallNumber = (element) => element < 15;

console.log(array1.findLastIndex(isSmallNumber));
// Expected output: 5
```

</details>

**<details><summary>Array.prototype.flat();</summary>**
The `flat()` method creates a new array with all sub-array elements concatenated into it recursively up to the specified depth.

```javascript
const arr1 = [1, 2, [3, 4, [5, 6]]];

console.log(arr1.flat());
// Expected output: [1, 2, 3, 4, [5, 6]]

console.log(arr1.flat(2));
// Expected output: [1, 2, 3, 4, 5, 6]
```

</details>

**<details><summary>Array.prototype.flatMap();</summary>**
The `flatMap()` method first maps each element using a mapping function, then flattens the result into a new array. It is identical to a map followed by a flat of depth 1, but `flatMap` is often more efficient.

```javascript
const arr1 = [1, 2, 3, 4];

const mergeDoubled = arr1.flatMap((x) => [x, x * 2]);

console.log(mergeDoubled);
// Expected output: [1, 2, 2, 4, 3, 6, 4, 8]
```

</details>

**<details><summary>Array.prototype.forEach();</summary>**
The `forEach()` method executes a provided function once for each array element.

```javascript
const array1 = ["a", "b", "c"];

array1.forEach((element) => console.log(element));

// Expected output:
// "a"
// "b"
// "c"
```

</details>

**<details><summary>Array.prototype.includes();</summary>**
The `includes()` method determines whether an array includes a certain value among its entries, returning true or false as appropriate.

```javascript
const array1 = [1, 2, 3];

console.log(array1.includes(2));
// Expected output: true

console.log(array1.includes(4));
// Expected output: false
```

</details>

**<details><summary>Array.prototype.indexOf();</summary>**
The `indexOf()` method returns the first index at which a given element can be found in the array, or -1 if it is not present.

```javascript
const beasts = ["ant", "bison", "camel", "duck", "bison"];

console.log(beasts.indexOf("bison"));
// Expected output: 1

// start from index 2
console.log(beasts.indexOf("bison", 2));
// Expected output: 4

console.log(beasts.indexOf("giraffe"));
// Expected output: -1
```

</details>

**<details><summary>Array.prototype.join();</summary>**
The `join()` method creates and returns a new string by concatenating all of the elements in an array, separated by commas or a specified separator string.

```javascript
const elements = ["Fire", "Air", "Water"];

console.log(elements.join());
// Expected output: "Fire,Air,Water"

console.log(elements.join(""));
// Expected output: "FireAirWater"

console.log(elements.join("-"));
// Expected output: "Fire-Air-Water"
```

</details>

**<details><summary>Array.prototype.keys();</summary>**
The `keys()` method returns a new Array Iterator object that contains the keys for each index in the array.

```javascript
const array1 = ["a", "b", "c"];
const iterator = array1.keys();

for (let key of iterator) {
  console.log(key);
}

// Expected output:
// 0
// 1
// 2
```

</details>

**<details><summary>Array.prototype.lastIndexOf();</summary>**
The `lastIndexOf()` method returns the last index at which a given element can be found in the array, or -1 if it is not present. The array is searched backwards.

```javascript
const animals = ["Dodo", "Tiger", "Penguin", "Dodo"];

console.log(animals.lastIndexOf("Dodo"));
// Expected output: 3

console.log(animals.lastIndexOf("Tiger"));
// Expected output: 1
```

</details>

**<details><summary>Array.prototype.map();</summary>**
The `map()` method creates a new array populated with the results of calling a provided function on every element in the calling array.

```javascript
const array1 = [1, 4, 9, 16];

// pass a function to map
const map1 = array1.map((x) => x * 2);

console.log(map1);
// Expected output: [2, 8, 18, 32]
```

</details>

**<details><summary>Array.prototype.pop();</summary>**
The `pop()` method removes the last element from an array and returns that element. This method changes the length of the array.

```javascript
const plants = ["broccoli", "cauliflower", "cabbage", "kale", "tomato"];

console.log(plants.pop());
// Expected output: "tomato"

console.log(plants);
// Expected output: ["broccoli", "cauliflower", "cabbage", "kale"]
```

</details>

**<details><summary>Array.prototype.push();</summary>**
The `push()` method adds one or more elements to the end of an array and returns the new length of the array.

```javascript
const animals = ["pigs", "goats", "sheep"];

const count = animals.push("cows");

console.log(count);
// Expected output: 4

console.log(animals);
// Expected output: ["pigs", "goats", "sheep", "cows"]
```

</details>

**<details><summary>Array.prototype.reduce();</summary>**
The `reduce()` method executes a reducer function (that you provide) on each element of the array, resulting in a single output value.

```javascript
const array1 = [1, 2, 3, 4];
const reducer = (accumulator, currentValue) => accumulator + currentValue;

// 1 + 2 + 3 + 4
console.log(array1.reduce(reducer));
// Expected output: 10

// 5 + 1 + 2 + 3 + 4
console.log(array1.reduce(reducer, 5));
// Expected output: 15
```

</details>

**<details><summary>Array.prototype.reduceRight();</summary>**
The `reduceRight()` method applies a function against an accumulator and each value of the array (from right-to-left) to reduce it to a single value.

```javascript
const array1 = [
  [0, 1],
  [2, 3],
  [4, 5],
].reduceRight((accumulator, currentValue) => accumulator.concat(currentValue));

console.log(array1);
// Expected output: [4, 5, 2, 3, 0, 1]
```

</details>

**<details><summary>Array.prototype.reverse();</summary>**
The `reverse()` method reverses an array in place. The first array element becomes the last, and the last array element becomes the first.

```javascript
const array1 = ["one", "two", "three"];
const reversed = array1.reverse();

console.log("reversed:", reversed);
// Expected output: "reversed: ["three", "two", "one"]"

console.log("array1:", array1);
// Expected output: "array1: ["three", "two", "one"]"
```

</details>

**<details><summary>Array.prototype.shift();</summary>**
The `shift()` method removes the first element from an array and returns that removed element. This method changes the length of the array.

```javascript
const array1 = [1, 2, 3];

const firstElement = array1.shift();

console.log(firstElement);
// Expected output: 1

console.log(array1);
// Expected output: [2, 3]
```

</details>

**<details><summary>Array.prototype.slice();</summary>**
The `slice()` method returns a shallow copy of a portion of an array into a new array object selected from start to end (end not included) where start and end represent the index of items in that array. The original array will not be modified.

```javascript
const animals = ["ant", "bison", "camel", "duck", "elephant"];

console.log(animals.slice(2));
// Expected output: ["camel", "duck", "elephant"]

console.log(animals.slice(2, 4));
// Expected output: ["camel", "duck"]
```

</details>

**<details><summary>Array.prototype.some();</summary>**
The `some()` method tests whether at least one element in the array passes the test implemented by the provided function. It returns a Boolean value.

```javascript
const array = [1, 2, 3, 4, 5];

const even = (element) => element % 2 === 0;

console.log(array.some(even));
// Expected output: true
```

</details>

**<details><summary>Array.prototype.sort();</summary>**
The `sort()` method sorts the elements of an array in place and returns the sorted array. The default sort order is built upon converting the elements into strings, then comparing their sequences of UTF-16 code units values.

```javascript
const months = ["March", "Jan", "Feb", "Dec"];
months.sort();
console.log(months);
// Expected output: ["Dec", "Feb", "Jan", "March"]
```

</details>

**<details><summary>Array.prototype.splice();</summary>**
The `splice()` method changes the contents of an array by removing or replacing existing elements and/or adding new elements in place.

```javascript
const months = ["Jan", "March", "April", "June"];
months.splice(1, 0, "Feb");
// inserts at index 1
console.log(months);
// Expected output: ["Jan", "Feb", "March", "April", "June"]

months.splice(4, 1, "May");
// replaces 1 element at index 4
console.log(months);
// Expected output: ["Jan", "Feb", "March", "April", "May"]
```

</details>

### Array static methods

Below are the static methods available on the `Array` constructor in JavaScript. These methods are available directly on the Array object and not on the instances of arrays.

- The `Array.from()` static method creates a new, shallow-copied Array instance from an array-like or iterable object.

  ```javascript
  console.log(Array.from("foo"));
  // Expected output: ['f', 'o', 'o']

  const set = new Set(["foo", "bar", "baz", "foo"]);
  console.log(Array.from(set));
  // Expected output: ['foo', 'bar', 'baz']
  ```

- The `Array.isArray()` static method determines whether the passed value is an Array.

  ```javascript
  Array.isArray([1, 2, 3]); // true
  Array.isArray({ foo: 123 }); // false
  Array.isArray("foobar"); // false
  Array.isArray(undefined); // false
  ```

- The `Array.of()` static method creates a new Array instance from a variable number of arguments, regardless of number or type of the arguments.

  ```javascript
  Array.of(1); // [1]
  Array.of(1, 2, 3); // [1, 2, 3]
  Array.of(undefined); // [undefined]
  ```

  &nbsp;

## 5. Functions (create, invoke, arrow functions, rest operator, default parameters)

### All ways to create Functions:

- **Function Declaration**:
  A function statement or declaration defines a function with the specified parameters. You can then call it later in your code.

  ```javascript
  function sayHello(name) {
    console.log("Hello " + name);
  }

  sayHello("John"); // Output: "Hello John"
  ```

- **Function as an Expression**:
  A function expression defines a function as a part of a larger expression syntax (typically a variable assignment ). Functions defined this way can be anonymous; they do not have to have a name.

  ```javascript
  const greet = function (name) {
    console.log("Hello " + name);
  };

  greet("Jane"); // Output: "Hello Jane"
  ```

- **Function as an Arrow Function**:
  Arrow functions are a compact alternative to traditional function expressions, introduced in ES6. They omit the `function` keyword and incorporate the use of the `=>` syntax.

  ```javascript
  const add = (a, b) => {
    return a + b;
  };

  console.log(add(5, 3)); // Output: 8

  // For single-expression functions, the curly braces and 'return' statement can be omitted:
  const multiply = (a, b) => a * b;

  console.log(multiply(5, 3)); // Output: 15
  ```

- **Function Created Using the Function Constructor**:
  The `Function` constructor creates a new function object. In JavaScript, functions are first-class objects, meaning they can be constructed dynamically, passed around as any other value, or used as objects.

  ```javascript
  const sum = new Function("a", "b", "return a + b;");

  console.log(sum(2, 6)); // Output: 8
  ```

  > This constructor is less syntactically convenient and generally less preferable due to performance issues on modern JavaScript engines and difficulties with debugging and minification. Use of the `Function` constructor also carries similar risks to eval(), particularly in executing arbitrary code. It's usually better to use function declarations, expressions, or arrow functions.

In JavaScript, functions can be enhanced with additional features like the rest operator and default parameters, which provide more flexibility and functionality while invoking functions. Below, I uncover what these functionalities mean and how they can be implemented.

### Rest Operator

The rest operator (`...`) allows you to represent an indefinite number of arguments as an array. This is particularly useful when you want to handle function parameters dynamically.

#### Example:

```javascript
function sumNumbers(...numbers) {
  return numbers.reduce((total, num) => total + num, 0);
}

console.log(sumNumbers(1, 2, 3, 4)); // Output: 10
console.log(sumNumbers(10, 20)); // Output: 30
```

In this example, the function `sumNumbers` accepts any number of arguments, aggregates them into an array called `numbers`, and then sums them.

It is possible to get all arguments by `this.arguments` property of function, but rest operator is better, because of grouping arguments and less code.

### Default Parameters

Default parameters allow you to initialize named parameters with default values if no value or `undefined` is passed.

#### Example:

```javascript
function greet(name, greeting = "Hello") {
  console.log(`${greeting} ${name}!`);
}

greet("Alice"); // Output: "Hello Alice!"
greet("Bob", "Hi"); // Output: "Hi Bob!"
greet("Charlie", "Welcome"); // Output: "Welcome Charlie!"
```

In this example, `greet` takes two parameters: `name` and `greeting`. If the `greeting` is not provided when the function is called, it defaults to "Hello".
