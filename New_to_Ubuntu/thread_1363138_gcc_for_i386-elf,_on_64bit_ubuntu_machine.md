---
title: "gcc for i386-elf, on 64bit ubuntu machine?"
date: 2009-12-24
forum: New to Ubuntu
---

### Post by minsf on 2009-12-24
hi there,
could someone tell me how to get gcc/g++ for i386-elf target?
i am running ubuntu 9.10 64bit. 
i installed g++ via the build-essentials package (apt-get install build-essentials).
this means that when i compile
```
g++ -o hello hello.cpp
```
then with
```
file hello
```
i see that i got ELF binaries for x86_64-linux-gnu, which work great on my machine.
but i am taking a class in which we need to build binaries for i386-elf, so i wonder how to do it.
is there some package that i should install?
thanks

---

### Post by gsmanners on 2009-12-24
You could set up a cross-compile environment, although that's probably more work than you want. Personally, I would set up Bloodshed in Wine.

[http://www.bloodshed.net/](http://www.bloodshed.net/)

---

### Post by minsf on 2009-12-31
i'd actually like to install it from source.
after a frustrating week, i've finally been able to compile binutils, gcc and libgcc from source with target i386-elf. 
anyone knows of a good reference about cross-compiling glibc from source?

---

