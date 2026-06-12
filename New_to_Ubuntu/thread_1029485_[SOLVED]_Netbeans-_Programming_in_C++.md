---
title: "[SOLVED] Netbeans- Programming in C++"
date: 2009-01-03
forum: New to Ubuntu
---

### Post by nayeret43 on 2009-01-03
Ok, so I have this problem with Netbeans IDE 6.1

Every time I try to run a C++ program it returns this error:
```
 C++ Compiler is missing or invalid 
```

I have no clue what to do, I tried downloading C++ compilers, and still, it returns the same error.

I am very new at Ubuntu, and Linux in general, so if you'd be able to help me step by step, I would really appreciate that.

Thank you.

---

### Post by anders_c_ on 2009-01-03
have you installed the package "g++" try searching for it in synaptic.

---

### Post by jpmelos on 2009-01-03
Type it in a terminal:

```
sudo apt-get install build-essentials
```

But check if your NetBeans is configured to look for "gcc" or "g++" when you try to compile C/C++ code. You can check it in Tools > Options... > C/C++. Fill the "C Compiler" and "C++ Compiler" fields as follows:

[INDENT]C Compiler: /usr/bin/gcc
C++ Compiler: /usr/bin/g++[/INDENT]

But it will work only after you install the build-essentials package.

---

### Post by ibuclaw on 2009-01-03
> **jpmelos said:**
> Type it in a terminal:

```
sudo apt-get install build-essentials
```

But check if your NetBeans is configured to look for "gcc" or "g++" when you try to compile C/C++ code. You can check it in Tools > Options... > C/C++. Fill the "C Compiler" and "C++ Compiler" fields as follows:

[INDENT]C Compiler: /usr/bin/gcc
C++ Compiler: /usr/bin/g++[/INDENT]

But it will work only after you install the build-essentials package.

Wrong
```
sudo apt-get install build-essential
```
There is no trailing 's' in the package name :)

Regards
Iain

---

### Post by nayeret43 on 2009-01-03
It worked!

Thanks!

---

### Post by utnubuuser on 2009-01-03
Solved?  Thread Tool>>Mark thread as solved.

---

