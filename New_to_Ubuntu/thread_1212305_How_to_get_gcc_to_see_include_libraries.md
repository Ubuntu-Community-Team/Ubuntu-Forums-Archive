---
title: "How to get gcc to see include libraries"
date: 2009-07-13
forum: New to Ubuntu
---

### Post by Java Geek on 2009-07-13
Hello everyone. Thank you for taking a look at my problem.
My gcc is malfunctioning and I don't know what's happening.
I have posted the simple hello world C++ program:

```

#include <iostream>
using namespace std;

int main(int argc, char *argv[]) {
	cout >> "Hello Wold";
	return 0;
}

```

and I get this result:

```

helloworld.c:1:20: error: iostream: No such file or directory
helloworld.c:2: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘namespace’
helloworld.c: In function ‘main’:
helloworld.c:5: error: ‘cout’ undeclared (first use in this function)
helloworld.c:5: error: (Each undeclared identifier is reported only once
helloworld.c:5: error: for each function it appears in.)

```

Everytime I try to compile a program I get an error on the first line saying that the include file cannot be found. If anyone can give me assistance, I would appreciate it.

---

### Post by test_test_testing on 2009-07-13
Hi,

You use g++ to compile C++ programs and gcc to compile C programs. gcc doesn't recognise the C++ include file <iostream>.

Use g++ exactly like gcc, but replacing gcc with g++, eg:
```
$ g++ -o ./hello ./hello.cpp
```

BTW: the stream operator << is used with cout. >> is for cin (input).

HTH

---

### Post by johnl on 2009-07-13
Hi,

make sure you have installed the 'build-essential' package. (sudo apt-get install build-essential).


Edit:

Actually,  test_test_testing nailed it.  You named your file 'helloworld.c'.  Thus GCC is expecting C code, which does not have <iostream>.

You should
1) give your file a c++ extension (.cc, .cxx, .cpp, .c++)
2) use g++ in place of gcc.

GCC will compile your C++ code correctly if you give it a correct extension, but it's a better practice to invoke g++ explicitly.

---

### Post by test_test_testing on 2009-07-13
> **johnl said:**
> Hi,

make sure you have installed the 'build-essential' package. (sudo apt-get install build-essential).

He has that package (hence the errors from gcc, not "bash: gcc not found") - he's just trying to build with the GNU C compiler gcc. See above post. ;)

---

### Post by Java Geek on 2009-07-13
> **test_test_testing said:**
> Hi,

You use g++ to compile C++ programs and gcc to compile C programs. gcc doesn't recognise the C++ include file <iostream>.

Use g++ exactly like gcc, but replacing gcc with g++, eg:
```
$ g++ -o ./hello ./hello.cpp
```

BTW: the stream operator << is used with cout. >> is for cin (input).

HTH

OMG, I have programmed forever and that was it?! I forgot g++, wow, thanks man. The stream operator was just bad luck, i havent done a console application in a long time. =D THANK YOU hehehe

---

### Post by test_test_testing on 2009-07-13
No problem! Glad to have helped ;)

---

