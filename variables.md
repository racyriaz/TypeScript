# TypeScript Variables

A variable is a name given to a memory container, that holds our values

To have a variable in TypeScript it must follow the **JavaScript Naming Rules**:

- Must start with Alphabets, cannot start with digits
- Can have Alphabets and Numberic Digits
- Cannot have Spaces and Special Characters, _except UnderScore_ ( _ ) and \_except dollar sign_( $ )

## Variable declaration in TypeScript:

- A variable must be **declared before its used**
- The following are the four major ways a variable can be declared:

1. Delaring its type and value in one statement. (shorthand way)

   - `var [identifier_name] : [DataType / type-annotation] = value ;`
   - eg: `var my_cha: string = "hello world";`

2. Declare its type but no value. In this case, the variable will be set to **undefined**.

   - `var [identifier_name] : [DataType / type-annotation] ;`
   - eg: `var my_cha: "assalamu alaikum";`

3. Declare its value but no type. The variable type will be set to the data type of the assigned value.

   - `var [identifier_name] = value ;`
   - eg: `var my_num = 5;`

4. Declare neither value not type. In this case, the data type of the variable will be any and will be initialized to undefined.

   - `var [identifier_name] ;`
   - eg: `var my_num ;`

# Hoisting

Hoisting is a JavaScript mechanism where variables and function declarations are moved to the top of their scope before code execution. This means that if we do this

```Javascript
console.log (greeter);
var greeter = "say hello"
```

i.e. using the varible before declaring it and finally declaring it in the end of the program.

# Variable Scope:

## `var` vs `let` vs `const`

| Name  | declared outside function | declared inside function | declared inside a programming block | hoisting | update | re-declare |
| :---: | :-----------------------: | :----------------------: | :---------------------------------: | :------: | :----: | :--------: |
|  var  |          global           |          local           | global (passes to parent and child) |   yes    |  yes   |    yes     |
|  let  |          global           |          local           |    local (passes only to child)     |   yes    |  yes   |     no     |
| const |          global           |          local           |        local similar to let         |    -     |   no   |     no     |

### var

- A var variable declared inside a function will have local scope meaning, the variable cannot be accessed outside of the function.
- A var variable declared at top level/ outside of the function will have Global scope, meaning it can be accessed by all function
- A var variable can be re-declared

### let

- Let is now a preferred way for variable declaration. Its life span stays within the `{` `}` curly braces block.
- a let variable can be updated but cannot be re-declared like var variable

  ```Javascript
  let greeting = "say hi";
  greeting = "hello"; // will update

  let greeting = "bye"; // will give an error: Identifier has been already declared

  <!-- but in var -->
  var greet = "hi";
  var greet = "bye"; //can re declare
  ```

### const

- Variables declared with the const maintain constant values. const declarations share some similarities with let declarations.
- Like let declarations, const declarations can only be accessed within the block they were declared.
- This means that the value of a variable declared with const remains the same within its scope. It cannot be updated or re-declared
- If we update its value, it ll pop out `error : Assignment to constant variable`
- but there is a catch for this, say if you have objects in const, you can update the value of the object in const

  Example:-

```Javascript
 var tester = "hey hi";

 if(3>2){
    var builder = "bob"; //block scope
 }

 function newFunction() {
     var hello = "hello"; //functional scope
 }
 console.log(hello); // error: hello is not defined
 console.log(builder):
 //Ouput: bob
```

### Problem with VAR:

Consider these examples for better understanding:

1. Here the greet variable is defined in global scope in line 1, so any changes made to the name `greet` will alter the origin value.

```Javascript
// code 1
var numb = 5;

if (numb > 3){
   var greet = "hi";
   // this value will be passed both to parents and child components
   console.log(greet);
   // OUTPUT: hi

   numb = 1;
   console.log(numb);
   // Output: 1
}

console.log(greet);
// OUTPUT: hi
console.log(numb);
// OUTPUT: 1
```

2. Here the Variable `greet` is declared in global scope in line 1, but but look at line 4, it has got a `let` scope, which means that the changes made inside this block will not reflect back to global scope.

```Javascript

// code 2
var greet = "hello";
var numb = 5;

if (numb > 3){
   let greet = "hi";

   console.log(greet);
   // OUTPUT: hi
}

console.log(greet);
// OUTPUT: hello
```

3. Same applies to the `let` variable scope, when it is declared at top level, similar to example 1

```Javascript

// code 3
let greet = "hello"; // this variable can be inherited by childrens but not by parents
var numb = 5;

if (numb > 3){
   greet = "hi";

   console.log(greet);
   // OUTPUT: hi
}

console.log(greet);
// OUTPUT: hi
```

4. Now lets only use `let` scope variable

```Javascript

// code 4
let greet = "hello"; //will remain local to this scope of indentation
var numb = 5;

if (numb > 3){
   let greet = "hi"; // will remain local to this scope of indentation, outside this it ll vanish

   console.log(greet);
   // OUTPUT: hi
}

console.log(greet);
// OUTPUT: hello
```

[Back to Home](./index.html)
