---
title: "complation problem"
date: 2010-08-18
forum: New to Ubuntu
---

### Post by gaurish108 on 2010-08-18
Hi I am trying to run this pices of code on my laptop and I am failing to compile the code. This is what I get after compilation (using the given makefile)

Please tell me what I should do to remedy the situation.

```

gaurish108@gaurish108-laptop:~/Desktop/play/ls$ make
Makefile:22: cutcell.dep: No such file or directory
Makefile:22: FDTD.dep: No such file or directory
Makefile:22: routine.dep: No such file or directory
Generating/Updating dependency for routine.cpp
Generating/Updating dependency for FDTD.cpp
Generating/Updating dependency for cutcell.cpp
g++ -g   -c -o FDTD.o FDTD.cpp
g++ -g   -c -o routine.o routine.cpp
g++ -g   -c -o cutcell.o cutcell.cpp
gfortran -g FDTD.o routine.o cutcell.o -lm -L/usr/lib -L. -llinpak -lblas -lstdc++ -o FDTD
/usr/bin/ld: skipping incompatible ./liblinpak.a when searching for -llinpak
/usr/bin/ld: skipping incompatible /usr/local/lib/liblinpak.a when searching for -llinpak
/usr/bin/ld: cannot find -llinpak
collect2: ld returned 1 exit status
make: *** [FDTD] Error 1
gaurish108@gaurish108-laptop:~/Desktop/EM/ls$ 

```




Also I cannot seem to find this -llinpak file in the repository......
Note that I installed almost every package with the word LINPACK as shown in synaptic before I compiled it.....


Is there something obvious that I am not doing?

I am new to programing and Ubuntu so some detail will be appreciated:lolflag:

---

### Post by gaurish108 on 2010-08-18
uppppp

---

