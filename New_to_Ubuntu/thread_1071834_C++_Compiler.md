---
title: "C++ Compiler?"
date: 2009-02-16
forum: New to Ubuntu
---

### Post by Leo Dragonheart on 2009-02-16
Can someone recommend a good C,C++ compiler for beginers and some documentation on how to use it? Thanx.

---

### Post by Cl0ud9 on 2009-02-16
gcc for C, and g++ for C++. Both are available in the repositories. You should also the install build-essential package.

```

sudo apt-get install build-essesntial

```

A quick Google found this [tutorial]("http://pages.cs.wisc.edu/~beechung/ref/gcc-intro.html").

---

### Post by snova on 2009-02-16
Well, first of all there is a difference between compilers and IDE's.

As far as compilers go, there's really only one, and that's GCC.

Regarding IDE's, many many many. A few to look at:

[list]
[*] Geany - lightweight.
[*] Code::Blocks
[*] Anjuta
[*] Netbeans
[*] Eclipse
[*] Kdevelop
[/list]

And others, but those are the ones I can think of.

[Programming Talk]("http://ubuntuforums.org/forumdisplay.php?f=39")

---

### Post by Leo Dragonheart on 2009-02-16
What is an IDE?

---

### Post by Leo Dragonheart on 2009-02-16
> **Cl0ud9 said:**
> gcc for C, and g++ for C++. Both are available in the repositories. You should also the install build-essential package.

```

sudo apt-get install build-essesntial

```

A quick Google found this [tutorial]("http://pages.cs.wisc.edu/~beechung/ref/gcc-intro.html").

I ran that sudo in terminal and it says it can't find the package...What now?

---

### Post by Cl0ud9 on 2009-02-16
> **Leo Dragonheart said:**
> I ran that sudo in terminal and it says it can't find the package...What now?

Sorry, a typo on my part. It should be:

```

sudo apt-get install build-essential

```

---

### Post by snova on 2009-02-16
> **Leo Dragonheart said:**
> What is an IDE?

Integrated Development Environment. As in, a program that manages the build for you, integrates a debugger, manages your files... If you've ever used Visual Studio or Dev-C++, that's an IDE.

---

### Post by Leo Dragonheart on 2009-02-16
> **snova said:**
> Integrated Development Environment. As in, a program that manages the build for you, integrates a debugger, manages your files... If you've ever used Visual Studio or Dev-C++, that's an IDE.


Thanx for the info...

---

### Post by Leo Dragonheart on 2009-02-16
> **Cl0ud9 said:**
> Sorry, a typo on my part. It should be:

```

sudo apt-get install build-essential

```

I got it thanx. I should have caught if I would have just looked at it...;-)

---

### Post by Leo Dragonheart on 2009-02-16
I think maybe I am looking for an IDE. I downloaded gcc, g++, and build essentials but I can't find them anywhere what did I do?

---

### Post by snova on 2009-02-16
> **Leo Dragonheart said:**
> I think maybe I am looking for an IDE. I downloaded gcc, g++, and build essentials but I can't find them anywhere what did I do?

That would be the difference between compilers and IDE's...

Compilers are not large, graphical programs designed to assist you in writing your program. They deal in source code and command line options.

If you wanted to do it this way (various reasons to), the compilation command is:

```
g++ **source.cpp** -o **program**
```

Or, compile without linking:

```
g++ -c **source.cpp** -o **program**
```

C++ compiler is g++, C is gcc.

---

### Post by Leo Dragonheart on 2009-02-16
ok thanx

---

### Post by Ptero-4 on 2009-02-16
> **snova said:**
> That would be the difference between compilers and IDE's...

Compilers are not large, graphical programs designed to assist you in writing your program. They deal in source code and command line options.

If you wanted to do it this way (various reasons to), the compilation command is:

```
g++ **source.cpp** -o **program**
```

Or, compile without linking:

```
g++ -c **source.cpp** -o **program**
```

C++ compiler is g++, C is gcc.

BTW: If you decide to go that route. It would help a lot to install bluefish. It´s a text editor that can do syntax highlighting for a large amount of programming and scripting languages.

---

