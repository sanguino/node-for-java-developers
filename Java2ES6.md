From Java to JavaScript ES6
====================================

### Declaración de datos

En JS, las variables pueden ser declaradas de forma global y los valores son siempre mutables. Se puede usar `var` o `let` para declarar variables.

##### Java
```java
    String myData = "java";
```    

##### JS
```javascript
    let myData = "js";
```

### var vs let

`let` permite declarar variables limitando su alcance (scope) al bloque donde se ha declarado. En cambio `var` define una variable global o local en una función sin importar el ámbito del bloque. 

##### JS
```javascript
var a = 5;
var b = 10;

if (a === 5) {
  let a = 4; // El alcance es dentro del bloque if
  var b = 1; // El alcance es global o en la funcion
  
  console.log(a);  // 4
  console.log(b);  // 1
} 

console.log(a); // 5
console.log(b); // 1
```

### Constantes

En JS se utiliza `const` para declarar constantes

##### Java
```java
    final String MY_DATA = "java";
```

##### JS
```javascript
    const MY_DATA = "js";
```

### Tipos de datos simples

En JS los tipos de datos son dinamicos (una variable puede cambiar de tipo simplemente asignadole un valor de otro tipo), y no pudes definir el tipo de dato al declararlas. En JS solo se existe el tipo de dato `Number` y se usa para todos los tipos numericos.

##### Java
```java
    boolean userMan = true;
    int userAge = 81;
    float userAverage = 10.5;
    String userName = "Henri Bergson";
```
##### JS
```javascript
    let userMan = true;
    let userAge = 81;
    let userAverage = 10.5;
    let userName = 'Henri Bergson';
```

Ademas de `null` en JS existe los tipos de datos `undefined`,
y `NaN` (Not a Number). `undefined` es el valor que tiene algo que no esta definido, como una variable declarada sin valor. `NaN` es un valor de error que devuelven algunas operaciones matematicas, por ejemplo al dividir un numero por un string `console.log (3 / "a")`

### String details

Se pueden usar comillas simples y dobles para declarar variables. Por convenio se suelen usar comillas dobles en html y comillas simples en JS.

Tambien existen los template literals, que permiten strings con saltos de linea e interpolacion de variables dentro de un string. Los templates literals se declaran con comillas invertidas `. Son muy utiles para evitar errore en la concatenacion clasica de cadenas y valores. 

##### Java
```java
    String userFullName  = 
      userFirstName + " " + userLastName;
```
##### JS
```javascript
    let userFullName = `${userFirstName} ${userLastName}`;
    
    let address = `C/ Severo Ochoa 2,
    				 28232, Las Rozas
    				 Madrid`
```
          

Tambien son utiles para evitar escapar comillas simples o dobles en una misma cadena.

##### JS
```javascript
    let oldWay = '<p class="content">I\'m Henri !</p>';
    let newWay = `<p class="content">I'm Henri !</p>`;
```
          

### Listados de datos

El tamaño de un array es siempre dinamico en JS. Se usa length en vez de size, y no se usa get.

##### Java
```java
    List<String> userBooks = 
      new ArrayList<>();
    userBooks.add("Book 1");
    userBooks.get(0);
    userBooks.size();
```
##### JS
```javascript
    let userBooks = ['Book 1', 'Book 2'];
    userBooks.push('Book 3');
    userBooks[0];
    userBooks.length;
```

Un array puede tener multiples tipos de datos.

##### JS
```javascript
    let array = ['Some text', 23, true];
```

En vez de Hash maps se usan objetos planos en JS, cuyos keys son strings. JSON es un acrónimo de JavaScript Object Notation, por tanto un objeto en JS se escribe de forma similar a un JSON. A diferencia que en los JSON, en JS no es necesario que las keys lleven comillas si solo usan caracteres alfanumericos, y se pueden usar comillas simples y dobles.

##### Java
```java
    Map<String, String> user = 
      new HashMap<>();
    user.put("firstName", "Henri");
    user.put("lastName", "Bergson");
    user.get("firstName");
```
##### JS
```javascript
    let user = {
      firstName: 'Henri', 
      'last-Name': 'Bergson'
    };
    user.firstName;
```       

Existen 2 collecciones de datos más, `Map` y `Set`

El objeto Map almacena pares clave/valor.

##### JS
```javascript
var myMap = new Map();
myMap.set('name', 'Jonh');
myMap.set('age', 22);
```

Cualquier valor (tanto objetos como valores primitivos) pueden ser usados como clave o valor. `size` devuelve el tamaño. Con `get` obtenemos los valores.

##### JS
```javascript
var myMap = new Map();
myMap.set('name', {name:'jonh'});
myMap.set({id:1}, true);
myMap.set(function () {}, 'claveFunc');

myMap.size; // 3

myMap.get('name'); // {name:'jonh'}
myMap.get({id:1}); // undefined, ya que el objeto se ha declarado de nuevo, y aunque sea igual, no es la misma referencia.
```

El objeto Set te permite almacenar valores únicos de cualquier tipo. Las funciones principales son add, has, size y delete

##### JS
```javascript
const mySet = new Set();

mySet.add(1);
mySet.add('some text');

const o = {a: 1, b: 2};
mySet.add(o);

mySet.add({a: 1, b: 2}); // La variable "o" referencia a otro objeto, por lo que agrega otro valor.

mySet.has(1); // true
mySet.has(3); // false, 3 no ha sido añadido al Set
mySet.has(2-1);  // true
mySet.has('Some Text'.toLowerCase()); // true
mySet.has(o); // true

mySet.size; // 5

mySet.delete(1); // Elimina 1 del Set
mySet.has(1);    // false, 1 fue eliminado

mySet.size; // 4
```

Tambien existen `WeakMap` y `WeakSet`. Son parecidos que los anteriores salvo que las referencias a los objetos clave son mantenidas "débilmente", lo que quiere decir que no impiden la recolección de basura en caso de que no haya otras referencias al objeto.

### Blocks

Los bloques de código son iguales para los condiciones. Como veiamos antes, usaremos `let` siempre en bucles


##### Java
```java
    for (int i = 0; i < 10; i++) {
    	...
    }
```
##### JS
```javascript
    for (var i = 0; i < 10; i++) {
    	...
    }
    i; // 10, error prone

    for (let i = 0; i < 10; i++) {
    	...
    }
    i; // undefined
```

Los iteradores se usan con `for of`

##### Java
```java
    for (String value: userBooks) {
    	...
    }
```
##### JS
```javascript
    for (let value of userBooks) {
    	...
    }
```

O se puede usar foreach y una funcion que se ejecutara por cada valor


##### Java
```java
    for (int i = 0; i < books.size(); i++) {
        books.get(i);
    }
```
##### JS
```javascript
    books.foreach(function (value, index) {
    	...
    });
```

### Funciones

En JS, se puede acceder al scope padre directamente

##### Java
```java
    String myData = "java";
    void myMethod() {
      myData; // error
    }
```
##### JS
```javascript
    let myData = 'js';
    function myMethod() {
      console.log(myData); // "js"
    }
```
          

No existe el overload en JS (una funcion solo puede tener una definición) y sus parametros son siempre opcionales. Los valores por defecto son similares a Java.

##### Java
```java
    void myMethod(String required) {
      myMethod(required, "default");
    }
    void myMethod (String required, String optional) {
    	...
    }
```
##### JS
```javascript
    function myMethod ( notReallyRequired, optional = "default") {
        ...
    }
```

Existen funciones anonimas llamadas arrow functions, similares a las lambdas de java.

##### Java
```java
    numbersList.stream().filter(value -> value > 2);
```
##### JS
```javascript
    numbersList.filter(value => value > 2);
```

### this

En Java this referencia a la instancia actual a la que pertenece el metodo que se esta ejecutando. En JS this referencia al contexto que ha invocado la funcion, no a quien lo tiene declarado o referenciada. 

##### JS
```javascript
var person = {
  name: 'Jonh',
  sayHi: function() {
    console.log('Hi ' + name + "!");
  }
};

person. sayHi(); // Hi Jonh!
 
var otherPerson = {
  name: "Peter",
  sayHi: sayHi // referencia al método de persona
};
 
otherPerson.sayHi(); // Hi Peter!
```

Esto ocurre mucho cuando pasamos una function como parametro, por ejemplo en un forEach, la funccion se declara pero quien ejecuta la funcion no va a ser obj:

##### JS
```javascript

let obj = {
    array: [1, 2],
    log: function () {
       console.log(this.array) // [1, 2]
       this.array.forEach(function () { 
        	console.log(this.array) // undefined
       });
    }
};

obj.log();
	
```

Para evitar esto se puede usar la funcion bind que 'bindea' una funcion a un contexto lo ejecute quien lo ejecute:

##### JS
```javascript

let obj = {
    array: [1, 2],
    log: function () {
       console.log(this.array) // [1, 2]
       this.array.forEach(function () { 
        	console.log(this.array) // [1, 2]
       }.bind(this));
    }
};

obj.log();
	
```

Aunque lo más comodo es usar arrow functions:

##### JS
```javascript

let obj = {
    array: [1,2],
    log: function () {
       console.log(this.array) // [1, 2]
       this.array.forEach( () => { 
        	console.log(this.array) // [1, 2]
       });
    }
};

obj.log();
	
```




### Built-in methods

Algunos metosdos básicos en JS(`length` es una propiedad no un metodo)

##### Java
```java
    myEmail.indexOf("@");
    myEmail.replaceAll("(.*)@(.*)", " at ");
    myEmail.substring(0, 5);
    myEmail.length();
    Integer.parseInt("10");
```
##### JS
```javascript
    myEmail.strpos('@');
    myEmail.replace('@', ' at ');
    myEmail.substring(0, 5);
    myEmail.length;
    parseInt('10');
```

Cuando un funcion parece que se la llama directamente, como `parseInt()`,
es porque el objeto global se puede ignorar. Por tanto seria equivalente en un browser a `window.parseInt()` o en node a `global.parseInt()`. 

Recordamos que en JS se puede acceder al scope del padre directamente, y ese a su vez al suyo, etc, por tanto todo scope puede acceder siempre a global. Esto es lo que se conoce como scope chaining.

### Classes

En JS ES6 existen clases, pero todavia son muy simples. Las propiedades se declaran directamente en el constructor. En futuras versiones se añadiran propiedades predeclaradas como en Java

##### Java
```java
    public class User {
      public String firstName;
      public User(String firstName) {
        this.firstName = firstName;
      }
      public void sayHello() {}
    }

    User myUser = new User("Henri");
    myUser.firstName;
    myUser.sayHello();
```

##### JS
```javascript
    class User {
      public constructor(firstName) {
        this.firstName = firstName;
      }
      public sayHello() {}
    }

    let myUser = new User('Henri');
    myUser.firstName;
    myUser.sayHello();
```
          

La herencia en JS es bastante parecida

##### Java
```java
    public class Editor extends User {
      public Editor(String firstName) {
        super(firstName);
      }
      public void sayHello() {
        super.sayHello();
      }
    }
```
##### JS
```javascript
    class Editor extends User {
      constructor(firstName) {
        super(firstName);
      }
      sayHello() {
        super.sayHello();
      }
    }
```     

Los getters y setters tienen una sintaxis especial:

##### Java
```java
    public class User {
      protected String name;
      public String getName() {
        return this.name;
      }
      public void setName(String newName) {
        this.name = newName;
      }
    }
    
    User myUser = new User('Henri');
    myUser.getName();
    myUser.setName('New name');
```
##### JS
```javascript
    class User {
      constructor (name) {
	      this._name = name;
      }
      
      public get name() {
        return this._name;
      }
      public set name(newName) {
        this._name = newName;
      }
    }

    let myUser = new User('Henri');
    myUser.name;
    myUser.name = 'New name';
```

Los metodos y propiedades privadas serán publicados en futuras versiones de JS. Mientras tanto por convenio se usa guion bajo delante del nombre de variable para comunicar que el desarrollador pretende que la variable no se acceda desde fuera aunque puedas. En clases por convenio se usan 2 guiones bajos para privados `__private` y uno para portejidas `_protected`. 


Para metodos estaticos se usa una sintaxis similar a los getters y setters

##### JS
```javascript
    class Utilities {
      static filter() {}
    }

    Utilities.filter();
```

No existen de momento interfaces en JS ni herencia multiple.
          

### modulos

El sistema de namespacing de js o modulos es manejado directamente por es6 y se usan las palabras reservadas `export` e `ìmport`. Cuando estos metodos se usan automaticamente ya no se esta en el scope global. 

##### Java
```java
    // User.java
    package accounts;

    public class User {}

    // main.java
    import accounts.User;

    User myUser = new User();
```

##### JS
```javascript
    // User.JS
    export class User {}

    // script.JS
    import { User } from "./User";

    let myUser = new User();
```

Se pueden exportar multiples elementos

##### JS
```javascript
    // User.JS
    export class User {}
   
    export const USER_DEFAULT = 'Admin';

    // script.JS
    import { User, USER_DEFAULT } from "./User";

    let myUser = new User();
```

Se pueden exportar varios elementos declarados en el fichero al final del mismo

##### JS
```javascript
    // User.JS
    class User {}
   
    const USER_DEFAULT = 'Admin';
    
    export { User, USER_DEFAULT }

    // script.JS
    import { User, USER_DEFAULT } from "./User";

    let myUser = new User();
```



Se pueden exportar un elemento, y solo uno, por defecto. Esto permite a quien lo importa nombrarlo como desee

##### JS
```javascript
    // User.JS
    export default class User {}

    // script.JS
    import Usuario from "./User";

    let myUser = new Usuario();
```



En node se sigue usando `require` en vez de los modulos de ES6. Require es anterior a ES6 y tiene una interfaz parecida pero diferente. En node ya esta implementado el sistema de modulos de ES6 aunque hace falta un flag en la ejecucion ya que esta en beta. Por tanto si no se va a usar node en produccion, mejor aprende a usar modulos de ES6.

### promises

TBD

### async await

TBD

### iteradores

TBD

### generadores

TBD
