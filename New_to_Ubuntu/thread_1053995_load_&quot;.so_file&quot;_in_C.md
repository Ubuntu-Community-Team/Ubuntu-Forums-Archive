---
title: "load &quot;.so file&quot; in C"
date: 2009-01-29
forum: New to Ubuntu
---

### Post by void_void on 2009-01-29
i want to use function from ".so file"  in c code in linux ?
how to load .so file in c?

---

### Post by niteshifter on 2009-01-29
Hi,

You don't load the *.so file into your C program. A .so (system object) file is an already compiled library file.

You call what functions you require from the library. Let's say we have a file libspecial_funcs.so - the special_functions library. Inside that library is a function we wish to use, a_useful_func(). 

Below illustrates the basic parts in your source:

```
/* testpgm.c */
#include <special_funcs.h>  /* the header file for the lib */

void main(void) {    /* our main program / function */

  a_useful_func();   /* call out to the function in the library */

  }

```

You then compile and tell gcc this:

```
gcc  -o testpgm testpgm.c **-llibspecial_funcs**
```
Note the -l option, followed by the library name.

For what it's worth you'll get more / better responses if you ask in the programming area of the forums  - just a hint ;)

---

