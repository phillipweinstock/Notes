# C# Notes
These are self notes. <br>
I've made references to other languages that I know for better understanding.*
<br>
<br>

## Installation
On Arch Linux [Mono package](https://wiki.archlinux.org/index.php/Mono) is required to compile and execute C# scripts.

scripts are compiled using the `mcs` command and executed with `mono`
```sh
$ mcs file_name.cs
$ mono file_name.exe
```
This can be done in 1-line with the addition of a [shell script](https://github.com/LexxFade/Tools/blob/main/1-Line%20Run%20C%23/cs.sh) added as an alias in shellrc.

<br>

## Hello World 
Like C++, to add functionality to a C# script certain files must be imported. <br>
`Namespace` is more or less like a `module` in ruby- a collection of methods. Code would compile without error even without them.

```cs
learning.cs
--------------------------------------------------------
using System;                                       // using derective

namespace Learning                                  // namespace declaration
{                                                   // namespace block [start]
    class Program                                   // create class
    {                                               // class block [start]
        static void Main(string[] args)             // create method
        {                                           // method block [start]
            // Main code will come here
            Console.WriteLine("Hello World");       // expression statement
        }                                           // method block [end]
    }                                               // class block [end]
}                                                   // namespace block [end]
```
### Rules
- `using directives` and `expresion statement`ends with `;`
- `namespaces`, `classes` and `methods` use `{ }`

Only 1 function can be called `Main` and be `Static`.<br>
`using System;` allows the file to use `System` namespace <u>without having to **fully qualify**</u>.<br>
Without it, this same code would be-
```cs
learning.cs
--------------------------------------------------------
namespace Learning
{
    class Program
    {
        static void Main(string[] args)
        {
            System.Console.WriteLine("Hello World");
        }
    }
}

```
**Key Term:** `code block is code between {}`<br>
\* `Console` is a function in the`System` namespace.

<br>

## Data Types
| DataType  | Size                  | Description                                                                   |
|-----------|-----------------------|-------------------------------------------------------------------------------|
|int        | 4 bytes               | whole numbers from -2,147,483,648 to 2,147,483,647                            |
|long       | 8 bytes               | whole numbers from -9,223,372,036,854,775,808 to 9,223,372,036,854,775,807    |
|float      | 4 bytes               | fractional numbers. stores up to 6 to 7 decimal digits                        |
|double     | 8 bytes               | fractional numbers. stores up to 15 decimal digits                            |
|bool       | 1 bit                 | true or false values                                                          |
|char       | 2 bytes               | a single character/letter, surrounded by single quotes                        |
|string     | 2 bytes per character | a sequence of characters, surrounded by double quotes                         |
<br>

when a float is defined, `f` is added after the numbers; and `m` for decimals
```cs
float number = 23.213f;
decimal number = 12.32m
```
Data type conversion happens quite differently.
- Implicit Casting - converting a smaller type to a larger type size <br>
`char -> int -> long -> float -> double` <br>
conversion happens <u>automatically</u>
```cs
int trial_int = 23;
double trial_double = trial_int;

Console.WriteLine("Int: " + trial_int);
Console.WriteLine("Double: " + trial_double);
```

- Explicit Casting - converting a larger type to a smaller size type<br>
`double -> float -> long -> int -> char`<br>
conversion is done manually
```cs
double trial_double = 213;
int trial_int = (int) trial_double;

Console.WriteLine("Double: " + trial_double);
Console.WriteLine("Int: " + trial_int);
```

Alternate Method:
```cs
int trial_int = 213;
double trial_double = 43;

int new_int = Convert.ToInt32(trial_double);
double new_double = Convert.ToDouble(trial_int);
string numerical_string = Convert.ToString(trial_int);
```

<br>

## Basic Input Output
`Console.WriteLine` is same as ruby `puts`, while `Console.Write` is same as ruby `print`.<br>
Unlike ruby and python, `Console.WriteLine(var_a + var_b)` is possible when `type(var_a) != type(var_b)`.

vars can be print in middle of strings like-
```cs
Console.WriteLine($"some string data {variable}")
```

User input is read by `Console.ReadLine()`. It only returns string.
```cs
WRONG WAY
int userInput = Console.ReadLine();

RIGHT WAY
int userInput = Convert.ToInt32(Console.ReadLine());
```


## Operators
Arithmetic
| Operator  | Name          | Description                       | Example   |
|-----------|---------------|-----------------------------------|-----------|
|     +     | Addition      | Adds together two values          | x + y     |
|     -     | Subtraction   | Subtracts one value from another  | x - y     |
|     *     | Multiplication| Multiplies two values             | x * y     |
|     /     | Division      | Divides one value by another      | x / y     |
|     %     | Modulus       | Returns the division remainder    | x % y     |
|     ++    | Increment     | Increment of 1                    | x++       |
|     --    | Decrement     | Decrement of 1                    | x--       |

