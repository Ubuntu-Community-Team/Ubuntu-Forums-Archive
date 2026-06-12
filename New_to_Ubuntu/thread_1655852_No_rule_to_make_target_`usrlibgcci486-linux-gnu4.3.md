---
title: "*** No rule to make target `/usr/lib/gcc/i486-linux-gnu/4.3.3/include/stddef.h', need"
date: 2010-12-30
forum: New to Ubuntu
---

### Post by signalp on 2010-12-30
Hi Guys,
Could anyone help me here to resolve this error:

user@ubuntu910desktop:~/coder/mpeg4_enc$ make VARIANT=i386 main
mkdir -p ./lib/i386
mkdir -p ./deps/codeclib/i386
mkdir -p ./objs/codeclib/mpeg4enc/i386
[COLOR=DarkRed]make: *** No rule to make target `/usr/lib/gcc/i486-linux-gnu/4.3.3/include/stddef.h', needed by `Algorithmic_data_encode.o'.  Stop.[/COLOR]

Thx in anctipation!

---

### Post by cipherboy_loc on 2010-12-30
What program are you trying to build? Any particular reason why you cannot install it from the repositories? I cannot tell you if it is in there without knowing the name of it, but it might be.


Cipherboy

---

### Post by signalp on 2010-12-30
> **cipherboy_loc said:**
> What program are you trying to build? Any particular reason why you cannot install it from the repositories? I cannot tell you if it is in there without knowing the name of it, but it might be.


Cipherboy
its a C programme.

---

### Post by signalp on 2010-12-30
tried updating build essentials etc..but the problem persists:


"
sudo apt-get install apt-file
sudo apt-file update
apt-file search stddef.h

" DONE


user@ubuntu910desktop:~/encoder/mpeg4_enc$ gcc -v
Using built-in specs.
Target: i486-linux-gnu
Configured with: ../src/configure -v --with-pkgversion='Ubuntu 4.4.1-4ubuntu9' --with-bugurl=file:///usr/share/doc/gcc-4.4/README.Bugs --enable-languages=c,c++,fortran,objc,obj-c++ --prefix=/usr --enable-shared --enable-multiarch --enable-linker-build-id --with-system-zlib --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --with-gxx-include-dir=/usr/include/c++/4.4 --program-suffix=-4.4 --enable-nls --enable-clocale=gnu --enable-libstdcxx-debug --enable-objc-gc --enable-targets=all --disable-werror --with-arch-32=i486 --with-tune=generic --enable-checking=release --build=i486-linux-gnu --host=i486-linux-gnu --target=i486-linux-gnu
Thread model: posix
gcc version 4.4.1 (Ubuntu 4.4.1-4ubuntu9) 
user@ubuntu910desktop:~/encoder/mpeg4_enc$ make VARIANT=i386_gcc main
mkdir -p ./lib/i386
mkdir -p ./deps/codeclib/i386
mkdir -p ./objs/codeclib/mpeg4enc/i386
[COLOR=DarkRed]make: *** No rule to make target `/usr/lib/gcc/i486-linux-gnu/4.3.3/include/stddef.h', needed by `Algorithmic_data_encode.o'.  Stop.[/COLOR]

---

### Post by Perfect Storm on 2010-12-30
May be it is pointing to the wrong gcc. When you're running the first command it's pointing to gcc4.4


But here at the second command;
```
make: *** No rule to make target `/usr/lib/gcc/i486-linux-gnu/4.3.3/include/stddef.h', needed by `Algorithmic_data_encode.o'. Stop.
```
It's looking in gcc4.3

---

### Post by signalp on 2010-12-30
> **Artificial Intelligence said:**
> May be it is pointing to the wrong gcc. When you're running the first command it's pointing to gcc4.4


But here at the second command;
```
make: *** No rule to make target `/usr/lib/gcc/i486-linux-gnu/4.3.3/include/stddef.h', needed by `Algorithmic_data_encode.o'. Stop.
```It's looking in gcc4.3
yeah, so how can I get over it?...

---

### Post by wep940 on 2010-12-30
You might also try posting this in the programming forum - someone there may be more apt to help you.

---

### Post by Elfy on 2010-12-31
Please do not post duplicate threads - and really don't post 3 of the same. Your issue is not anymore important than anyone elses.

If you want to move a thread - report it and staff will do so for you.

---

