# Holberton School - \_printf

## Quick description

The repository contains **my_print.c** and **all the files** used to compile our own `printf()`
\_printf() is a function that formats and prints data. This has the direction of use of the `printf()` of `<stdio.h>.


## Compilation command

Our program will be compiled enabling most of the commons and optional warning options and treating them all as errors, by following strict C language rules and using the older C89 santard with some extra features specific to GCC and ignoring warnings about mismatched printf style format strings

This will be compiled this way :
``gcc -Wall -Werror -Wextra -pedantic -std=gnu89 -Wno-format *.c``


### Requirements

#### Betty Style
All the files are written with the [Betty coiding style](https://www.holbertonschool.fr/post/quest-ce-que-la-regle-betty-dans-le-langage-de-programmation-c)

#### Macro and functions allowed
`write`
`malloc`, `free`
`va_start`, `va_end`, `va_copy`, `va_arg`

#### Repository files list

| File name          | Description                                                                  |
| ------------------ | ---------------------------------------------------------------------------- |
| my_printf.c        | Contains the main function `_printf()`                                       |
| get_function.c     | Contains `get_function()` that checks \*format and calls the function needed |
| print_char.c       | Contains `print_char()` that prints a character (***%c***)                   |
| print_string.c     | Contains `print_string()`that prints a string (***%s***)                     |
| print_37.c         | Contains `print_37()`that printf '%' (***%%***)                              |
| print_int_or_dec.c | Contains `print_int_or_dec()` that prints decimals (***%i***) or (***%d***)  |
| main.h             | Contains all the headers, prototypes and structure needed                    |

#### Flowchart
We've started the project to re-write the `\_printf` by writting a flowchart to organise our code.

```mermaid
flowchart TB
    A[_printf] --> B(while *format)
    B --> AA((Non)) --> Z[Stop program]
    B --> AB((yes)) --> C{*format == '%'}
    C --> X((Yes)) --> F[format  i + 1]
    F --> G{if '%' + 1 == *CHECK}
    G --> W((No)) --> K[print %  and<br>the next character]
    K --> V[increment<br>continue loop]
    G --> J[Identify CHECK]
    J --> L{CHECK = 'c'}
    J --> M{CHECK = 's'}
    J --> N{CHECK = '%'}
    J --> O{CHECK = 'i'}
    J --> P{CHECK = 'd'}
    L --> Q[call print_char]
    M --> R[call print_string]
    N --> S[call print_37]
    O --> T[call print_int_or_dec]
    P --> U[call print_int_or_dec]
    Q --> V
    R --> V
    S --> V
    T --> V
    U --> V
    V --> B
    C --> Y((No)) --> D[Print *format<br>continue loop]
```