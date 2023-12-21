# What is the prototype?

In JavaScript, every object has a property called prototype. This is a reference to another object that contains shared properties and methods.

When you try to access a property or method on an object, JavaScript first looks at the object itself. If it doesn't find it there, it looks at the object's prototype, then the prototype's prototype, and so on up the chain until it either finds the property/method or reaches the end of the chain.

```
Object ----> Prototype ----> Prototype's Prototype ----> ... ----> null
```

# Are functions included?

Yes, functions are objects in JavaScript. They have a prototype property just like any other object. The only difference is that functions also have a special property called `prototype` that is used when the function is used as a constructor.

# Is direct property access not enough?

Direct properties are unique to each object. Prototype properties are shared across all instances of an object. This is useful when you want to share properties and methods across all instances of an object.

# What is the chain?

The chain simply refers to the process of looking up a property or method on an object and its prototype(s). And doing so recursively until the property/method is found or the end of the chain is reached.

# **proto** vs prototype? Any difference?

`__proto__` is a property on an object that points to its prototype.

`prototype` is a property on a function that is used when the function is used as a constructor.

`prototype` only exists on functions. `__proto__` exists on all objects.

# What is a constructor function?

In JavaScript, a constructor function is a special type of function used to create and initialize objects.

```ts
function Person(name, age) {
  this.name = name;
  this.age = age;
}

const wrongPerson = Person("Alice", 30); // Wrong! This doesn't create a new instance
const rightPerson = new Person("Alice", 30); // Right! This creates a new instance

console.log(rightPerson.constructor === Person); // true
```

Using the new Keyword: When you use the new keyword to call a constructor function, JavaScript does several things:

- It creates a new, empty object.
- It sets the prototype of the new object to the constructor function's prototype property.
- It sets `this` within the constructor function to refer to the new object.
- It executes the constructor function, initializing the new object.
- It returns the new object (unless the constructor explicitly returns a different object).

Every instance created using a constructor has a constructor property that points back to the constructor function that created it.

# End of the prototype chain

The prototype chain ends when an object's `__proto__` property is null. When JavaScript attempts to access a property on an object and doesn't find it, it follows the `__proto__` chain until it either finds the property or reaches an object whose `__proto__` is null. At that point, it returns undefined for the property lookup.
