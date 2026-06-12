---
title: "standard place for libraries in ubuntu"
date: 2010-10-25
forum: New to Ubuntu
---

### Post by gaurish108 on 2010-10-25
Hi I want to download the LAPACK library and make it work with C programs. 
That is why I wanted to ask the following questions.

1. What is the standard place/folder to store libraries for C/C++ downloaded from the internet for a standard UBUNTU system?

2. When we compile a C program with the command  [I][B]gcc hello.c -lm
 [/B][/I]the -lm option is for linking the math library right? What is the _standard_ place for libraries which are linked with the option -l(*whatever*)

I am relatively new to LINUX so a detailed answer will be really helpful

Thank you!

---

### Post by Paul820 on 2010-10-25
Libraries go in /usr/lib
You can get the libraries for LAPACK through synaptic. Just search for **liblapack-dev** and it will install the **.so** which is the library.

---

### Post by TeoBigusGeekus on 2010-10-25
Don't know about ubuntu, but in Arch they're in /usr/include. 
Have a look in that directory.

---

### Post by Simian Man on 2010-10-25
If you install it with the package manager, they will be placed into /usr/lib.  If you install them manually, you can put them wherever you want, but /usr/local/lib is the standard place to put them which is where most install scripts will use as a default location.

---

### Post by Simian Man on 2010-10-25
> **TeoBigusGeekus said:**
> Don't know about ubuntu, but in Arch they're in /usr/include. 
Have a look in that directory.

Header files go in /usr/[local/]include, library files go in /usr/[local/]lib.

---

### Post by gaurish108 on 2010-10-25
Why do we have two include and lib directories that is why do we have

/usr/include
/usr/lib

and /usr/local/include
      /usr/local/lib

Does this serve any purpose? 

Is it that one of them contains standard libraries and should not be tampered with whereas the other one can contain the the .h files and libraries which the user defines/ downloads from the net?

---

