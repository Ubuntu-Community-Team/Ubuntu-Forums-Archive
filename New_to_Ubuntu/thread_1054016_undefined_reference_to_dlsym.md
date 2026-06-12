---
title: "undefined reference to dlsym"
date: 2009-01-29
forum: New to Ubuntu
---

### Post by void_void on 2009-01-29
Running "/usr/bin/make  -f Makefile CONF=Debug" in /home/jjoshi/NetBeansProjects/function2

/usr/bin/make -f nbproject/Makefile-Debug.mk SUBPROJECTS= .build-conf
make[1]: Entering directory `/home/jjoshi/NetBeansProjects/function2'
/usr/bin/make  -f nbproject/Makefile-Debug.mk dist/Debug/GNU-Linux-x86/function2
make[2]: Entering directory `/home/jjoshi/NetBeansProjects/function2'
mkdir -p build/Debug/GNU-Linux-x86/_ext/home/jjoshi/NetBeansProjects/function2
rm -f build/Debug/GNU-Linux-x86/_ext/home/jjoshi/NetBeansProjects/function2/function2.o.d
gcc    -c -g -I/home/jjoshi/Desktop/c\ lib -I/home/jjoshi/Desktop/lib -MMD -MP -MF build/Debug/GNU-Linux-x86/_ext/home/jjoshi/NetBeansProjects/function2/function2.o.d -o build/Debug/GNU-Linux-x86/_ext/home/jjoshi/NetBeansProjects/function2/function2.o /home/jjoshi/NetBeansProjects/function2/function2.c
/home/jjoshi/NetBeansProjects/function2/function2.c: In function ‘main’:
/home/jjoshi/NetBeansProjects/function2/function2.c:57: warning: passing argument 1 of ‘printf’ from incompatible pointer type
/home/jjoshi/NetBeansProjects/function2/function2.c:61:2: warning: no newline at end of file
mkdir -p dist/Debug/GNU-Linux-x86
gcc     -o dist/Debug/GNU-Linux-x86/function2 build/Debug/GNU-Linux-x86/_ext/home/jjoshi/NetBeansProjects/function2/function2.o  
build/Debug/GNU-Linux-x86/_ext/home/jjoshi/NetBeansProjects/function2/function2.o: In function `main':
/home/jjoshi/NetBeansProjects/function2/function2.c:48: undefined reference to `dlopen'
/home/jjoshi/NetBeansProjects/function2/function2.c:52: undefined reference to `dlsym'
collect2: ld returned 1 exit status
make[2]: *** [dist/Debug/GNU-Linux-x86/function2] Error 1
make[2]: Leaving directory `/home/jjoshi/NetBeansProjects/function2'
make[1]: *** [.build-conf] Error 2
make[1]: Leaving directory `/home/jjoshi/NetBeansProjects/function2'
make: *** [.build-impl] Error 2

Build failed. Exit value 2.



how to over come this error ?? ? ? ? ? ?

---

