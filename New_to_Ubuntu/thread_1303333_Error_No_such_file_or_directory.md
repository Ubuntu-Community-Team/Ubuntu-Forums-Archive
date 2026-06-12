---
title: "Error: No such file or directory"
date: 2009-10-28
forum: New to Ubuntu
---

### Post by LiaGalanodel on 2009-10-28
When I want to execute a program that I have compile with arm-linux-gcc :

```
./filename
```He tell me: 

```
-bash: ./filename: No such file or directory
```I don't understand why. I compile the program with arm-linux-gcc because I execute in arrm9.

But it doesn't work!

---

### Post by kellemes on 2009-10-28
You have made it executable?
```
chmod +x filename
```
And you're sure you're in the same position as the file?

---

### Post by LiaGalanodel on 2009-10-28
I write chmod
:
```
root@(none):~/program# ls -l
total 21
-rwxr-xr-x 1 root root 11859 Oct 28  2009 filename
```And I sure I'm in the right position.

It's maybe the fact that I don't compile the program in the arm machine. But if I compile with arm-linux-gcc It must work.

Thanks for you answer ;)

---

### Post by djurny on 2009-10-28
so you're running on an arm9 machine and compiling something for that machine? or are you cross-compiling?

---

### Post by LiaGalanodel on 2009-10-28
I compile with a cross compiler that I have install like this site say:

[http://platformx.sourceforge.net/Documents/nuts/ToolChain.html](http://platformx.sourceforge.net/Documents/nuts/ToolChain.html)

---

### Post by djurny on 2009-10-28
if you are cross compiling you cannot execute the binaries on your host (or buildhost) machine.. you have to execute it on the target system..
if you are trying to execute it on your target system, maybe you are using the incorrect crosscompiler options, wrong endianness can generate the strangest of errors on target systems :)

---

### Post by LiaGalanodel on 2009-10-28
Okay! Thanks!

Yes I try to execute in my target system who use arm9.
So it's the parameter, I try to understand all of the parameter of my arm-linux-gcc with man.

So I made this code:

```
arm-linux-gcc mcpu=arm9 -o filnamehello filename.c

```
It's still dosn't work but if it's the paremeter who made this error:```
 No such file or directory.
```

I think I can find the probleme even if I don't know how change must I do.

But thank you very much!

---

### Post by LiaGalanodel on 2009-10-28
I want to ask a question.
Do you think that we can verify that the execute file (after compilation) is a execute file for arm?

---

### Post by djurny on 2009-10-28
you can always do
```
file filnamehello
```
on your build host and check if all assumptions are correct..

---

### Post by LiaGalanodel on 2009-10-28
Ok thanks! You are my rescuer!

I write the code.
```

amelieathanassiadis@SorinLinux:~/workspace/HelloWorld2$ file filenamehello 
filenamehello: ELF 32-bit LSB executable, ARM, version 1, dynamically linked (uses shared libs), for GNU/Linux 2.0.0, not stripped
```So he should work in ARM traget.

**But why there are version 1?**

---

### Post by djurny on 2009-10-28
> **LiaGalanodel said:**
> Ok thanks! You are my rescuer!

I write the code.
```

amelieathanassiadis@SorinLinux:~/workspace/HelloWorld2$ file filenamehello 
filenamehello: ELF 32-bit LSB executable, ARM, version 1, dynamically linked (uses shared libs), for GNU/Linux 2.0.0, not stripped
```

So he should work in ARM traget.
it should work on an arm target with an arm v1 instruction set in little endian mode..

---

### Post by LiaGalanodel on 2009-10-28
Ok thank you.

I understand that I have a problem so i try to change parameter.

---

### Post by djurny on 2009-10-28
you could try to compile for the armv5te architecture, as after some googling, looks like the pxa(2)55 supports armv5te as well..

---

### Post by LiaGalanodel on 2009-10-28
> **djurny said:**
> you could try to compile for the armv5te architecture, as after some googling, looks like the pxa(2)55 supports armv5te as well..


I try and look it.

Thanks.

---

### Post by LiaGalanodel on 2009-10-28
What is the  the pxa(2)55 supports armv5te ?

---

### Post by LiaGalanodel on 2009-10-28
I put:

```
arm-linux-gcc -mcup=arm9 -o filenamehello filename.c
```

But it doesn't work:
```

ELF 32-bit LSB executable, ARM, version 1, dynamically linked (uses shared libs), for GNU/Linux 2.0.0, not stripped
```

Normaly, it's change version...but not.

---

### Post by djurny on 2009-10-28
for more info on arm archs;
[http://en.wikipedia.org/wiki/ARM_architecture](http://en.wikipedia.org/wiki/ARM_architecture)

i'm not an arm guru, but i think the correct arm-linux-gcc option would be -march=armv5

---

### Post by LiaGalanodel on 2009-10-28
I try but it doesn't change anything, maybe It's my installation of arm-linux-gcc that wrong.

And I am already in this site, but thank you.

For your patience.

---

### Post by carml on 2009-10-28
Maybe I'm wrong,but are you sure you gave to the compiler the right path? I mean if I want to compile from source a SW,placed e.g. on my desktop under a specific directory I have to give  ```
cd /home/carmelo/Desktop/SWDirectory/targetDirectory
```.
I hope this can help :)

---

### Post by LiaGalanodel on 2009-10-28
Thank you ;)

Yes I have a good position my compilation is in /home/workspace/HelloWorld2/filename.c
And when I compile I'm in the directory HelloWorld2

So I think it's good.

And even when I want execute:

The filenamehello is in /home/program (in my target arm)

And when I want to compile I do:
```

cd /home/program
./filnamehello
```

But it still doesn't work.

---

### Post by LiaGalanodel on 2009-10-29
I don't understand why when I put:

```
arm-linux-gcc -march=armv5 filename.c
```

He doesn't change the version of arm when I put:

```
file filename
```

It's still the **version 1.**

---

### Post by LiaGalanodel on 2009-10-29
I believe I find the matter, it's the configuration of my installation:

```

amelieathanassiadis@SorinLinux:~/workspace/HelloWorld2$ arm-linux-gcc -v -march=armv5 Hello.c 
Reading specs from /usr/local/arm/3.3.2/lib/gcc-lib/arm-linux/3.3.2/specs
[COLOR=Red]Configured with: ../gcc-3.3.2/configure --target=arm-linux -_**-with-cpu=strongarm1100**_ --prefix=/usr/local/arm/3.3.2 i686-pc-linux-gnu --with-headers=/work/kernel.h3900/include --enable-threads=pthreads --enable-shared --enable-static --enable-languages=c,c++[/COLOR]
Thread model: posix
gcc version 3.3.2
 /usr/local/arm/3.3.2/lib/gcc-lib/arm-linux/3.3.2/cc1 -quiet -v -D__GNUC__=3 -D__GNUC_MINOR__=3 -D__GNUC_PATCHLEVEL__=2 -D__ARM_ARCH_5__ Hello.c -quiet -dumpbase Hello.c -march=armv5 -auxbase Hello -version -o /tmp/ccCR39xS.s
GNU C version 3.3.2 (arm-linux)
    compiled by GNU C version 3.3.1 (Mandrake Linux 9.2 3.3.1-2mdk).
GGC heuristics: --param ggc-min-expand=98 --param ggc-min-heapsize=128269
ignoring nonexistent directory "/usr/local/arm/3.3.2/arm-linux/include"
#include "..." search starts here:
#include <...> search starts here:
 /usr/local/arm/3.3.2/include
 /usr/local/arm/3.3.2/lib/gcc-lib/arm-linux/3.3.2/include
 /usr/local/arm/3.3.2/arm-linux/sys-include
End of search list.
 /usr/local/arm/3.3.2/lib/gcc-lib/arm-linux/3.3.2/../../../../arm-linux/bin/as -march=armv5 -o /tmp/ccgXIdWE.o /tmp/ccCR39xS.s
 /usr/local/arm/3.3.2/lib/gcc-lib/arm-linux/3.3.2/collect2 -dynamic-linker /lib/ld-linux.so.2 -X -m armelf_linux -p /usr/local/arm/3.3.2/lib/gcc-lib/arm-linux/3.3.2/../../../../arm-linux/lib/crt1.o /usr/local/arm/3.3.2/lib/gcc-lib/arm-linux/3.3.2/../../../../arm-linux/lib/crti.o /usr/local/arm/3.3.2/lib/gcc-lib/arm-linux/3.3.2/crtbegin.o -L/usr/local/arm/3.3.2/lib/gcc-lib/arm-linux/3.3.2 -L/usr/local/arm/3.3.2/lib/gcc-lib/arm-linux/3.3.2/../../../../arm-linux/lib /tmp/ccgXIdWE.o -lgcc -lgcc_eh -lc -lgcc -lgcc_eh /usr/local/arm/3.3.2/lib/gcc-lib/arm-linux/3.3.2/crtend.o /usr/local/arm/3.3.2/lib/gcc-lib/arm-linux/3.3.2/../../../../arm-linux/lib/crtn.o
amelieathanassiadis@SorinLinux:~/workspace/HelloWorld2$ 

```

---

### Post by LiaGalanodel on 2009-10-29
In fact it's just a file text so it's not that I think. But it should be a bad parameter.

I search.

---

### Post by LiaGalanodel on 2009-10-30
I try to reinstall arm-linux-gcc but it still doesn't work.

I really don't understand why it put: No such file or directory.

Be cause I'm in the good position and it's a excutable even if it's note the good arm version he should tell me: cannot execute binary file.

---

