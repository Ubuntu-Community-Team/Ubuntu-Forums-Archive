---
title: "Ansi C"
date: 2010-08-21
forum: New to Ubuntu
---

### Post by 1991sudarshan on 2010-08-21
i want ansi c for my system! could any pls tell from where can i download it??

how to compile c++ programs in linux?? If i compile with GCC it is  showing an error that iostream.h and conio.h files doesn't exist!!:frown:

---

### Post by orethrius on 2010-08-21
> **1991sudarshan said:**
> i want ansi c for my system! could any pls tell from where can i download it??

how to compile c++ programs in linux?? If i compile with GCC it is  showing an error that iostream.h and conio.h files doesn't exist!!:frown:

Start with **sudo apt-get install build-essential** and we'll go from there; swap **gksudo 'apt-get install build-essential'** for a GUI version.

---

### Post by Bachstelze on 2010-08-21
iostream.h and conio.h are not ANSI C.

And obviously C++ is not C either.  You seem very confused.

---

### Post by orethrius on 2010-08-21
> **Bachstelze said:**
> iostream.h and conio.h are not ANSI C.

And obviously C++ is not C either.  You seem very confused.

You noticed that, too? ;)

---

### Post by 1991sudarshan on 2010-08-21
i need the ansi c for installing the Kdrill and I need the normal C++ compiler for compiling the programs!!

---

### Post by 1991sudarshan on 2010-08-21
i am accessing the internet through internet cafe  and i cant do it through the terminal! could u pls send me the link of the  ansi and c++ compiler for linux

---

### Post by anewguy on 2010-08-21
If you followed the suggestion mentioned way above and installed build-essential (this can be done via Synaptic Package Manager or a command line, which ever you have access to) then you already installed g++ which is the C++ compiler.  If you have not installed the build-essential package, do so as you'll get a lot of things you are going to need all in 1 package.

As far as ANSI C goes, try your program with g++.  I think you may not understand what ANSI is and therefore what ANSI C is, and at this point in time you shouldn't need to worry about that.  Just go with g++ for the C++ compiler.

Dave ;)

---

### Post by 1991sudarshan on 2010-08-24
> **anewguy said:**
> If you followed the suggestion mentioned way above and installed build-essential (this can be done via Synaptic Package Manager or a command line, which ever you have access to) then you already installed g++ which is the C++ compiler.  If you have not installed the build-essential package, do so as you'll get a lot of things you are going to need all in 1 package.

As far as ANSI C goes, try your program with g++.  I think you may not understand what ANSI is and therefore what ANSI C is, and at this point in time you shouldn't need to worry about that.  Just go with g++ for the C++ compiler.

Dave ;)

But how to add the iostream.h  and conio.h files  to the library
every time when i put the cin and cout statements in my programs it is showing error

---

### Post by Paul820 on 2010-08-24
Kdrill is in the repositories, you can get it from there. conio.h is a windows header file, it won't work on linux. If you post the errors and a link to the software you are trying to build, then we might have a better idea of what you are trying to achieve.

---

### Post by Paul820 on 2010-08-24
Is this it? [http://www.bolthole.com/kdrill/]("http://www.bolthole.com/kdrill/")

If it is, then it is in the repositories, you need to install kdrill and kanjidic. Here it is on my desktop:

---

### Post by Vaphell on 2010-08-24
#include <stdio.h> is C
#include <iostream> is C++, this is what you want to use if you go with std::cin and std::cout
if you want to avoid std:: prefix, you need 'using namespace std;' line

---

### Post by d3v1150m471c on 2010-08-24
because gcc compiles C. you want:
```

g++ -o output input.cpp

```

---

### Post by anewguy on 2010-08-24
And hence why orethrius and myself said to install build-essential.  It includes g++ plus some more important things you'll end up needing anyway.

---

