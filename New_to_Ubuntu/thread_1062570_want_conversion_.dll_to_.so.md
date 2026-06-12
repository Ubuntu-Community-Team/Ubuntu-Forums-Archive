---
title: "want conversion .dll to .so"
date: 2009-02-07
forum: New to Ubuntu
---

### Post by void_void on 2009-02-07
Hello all,

i have dll and i want to use it on linux env from java.
so i need conversion from .dll to .so

or any other way to use existing 'dll ?

---

### Post by resander on 2009-02-07
A dll is executable program code that generally depends on functions of the Windows operating system. Windows understands the dll representation and calls the functions as required. Linux does not understand the dll representation at all and does not have exactly the same functions. Converting the dll would be difficult.
You may be able to run a program containing dlls using Wine on Linux. Wine does understand the dll representation and provides most standard functions of the Windows operating system. You can install Wine via synaptic manager.

---

### Post by ibuclaw on 2009-02-07
No ... Linux and Windows are binary incompatible, and the same goes for libraries too.

What type of library are you trying to use?

It may be a better idea to look for a version compiled for Linux, or a substitute that will do the exact same job.

Regards
Iain

---

### Post by void_void on 2009-02-09
i've made "dll " from C,
i do't have c code now and now i want to access that functions from "dll"
under linux(UBUNTU) using JAVA(JNI) 
thats it. .

is there any way to get passed. . .?

---

### Post by donkyhotay on 2009-02-09
If you had the source code I would recommend recompiling. Without the source code you're looking at either rewriting it or using wine.

---

### Post by void_void on 2009-02-10
will you please tell me how to use wine to use dll

---

### Post by jrusso2 on 2009-02-10
> **void_void said:**
> will you please tell me how to use wine to use dll

If your a programmer you can make a wrapper like they did for codecs and such maybe.

---

### Post by void_void on 2009-02-10
i am ia programmer but i haventt written any codec yet. ..
will you please give me some ideas or link or any more useful thing. . .

---

### Post by freak42 on 2009-02-10
what does your 'C' code do anyhow?

---

### Post by void_void on 2009-02-10
actually. . .
i have dlls made from c code..
 


now, any how i want to load dll in c code and want to access function resides in dlls
under linux,

i tried

#include <windows.h>

int main(int argc, char **argv) {

     HANDLE h;
    int (/*WINAPI?*/ *sort)(int int,int);
    unsigned int *nums =  malloc(sizeof(unsigned int) * 4);
    nums[0] = 3;
    nums[1] = 2;
    nums[2] = 1;
    nums[3] = 0;
    printf("loading . . . ");
    h = LoadLibrary("/home/jjoshi/Desktop/libcreateNEwDLL.dll");
    sort = GetProcAddress(h, "myPuts");
    printf("%d",sort(nums[1],4));

} 

but dlls in not getting loaded . .

so any how i want to load dll in c under linux.

---

### Post by void_void on 2009-02-10
i am loading ".so" files using following code

     void    *handle=dlopen("/home/jjoshi/NetBeansProjects/level0/dist/Debug/GNU-Linux-x86/liblevel0.so", RTLD_LOCAL | RTLD_LAZY);;

it works fine for '.so" 

how can i load ".dll" now?????

---

### Post by igknighted on 2009-02-10
Windows binaries are fundamentally different from linux ones, so you can't use them as is.  It is conceivable that you could convert them (with something like cabextract perhaps?  I'm grasping at straws here...), but I'm not sure.

You have to have the headers for them somewhere to build against, right?  If you don't have those you are sunk anyways.  And if you have the headers, you could always reimplement the functions.

---

### Post by void_void on 2009-02-10
as per wine
using following command

winedump spec Arithmetic.dll 

i can get 3 files

1.Arithmetic_main.c 
2.Arithmetic.spec
3.Arithmetic_dll.h 

but using this i m getting only first two  . 

after this how to use these files that i don't know

how can i use these to get the work done?

---

