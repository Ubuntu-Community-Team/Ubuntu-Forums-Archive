---
title: "Edgy eft and Ndiswrapper"
date: 2006-10-26
forum: Networking &amp; Wireless
---

### Post by ab4ever on 2006-10-26
Hi Guys,
 I've installed Edgy Eft RC and I'm pretty excited about and by ubuntu as a whole. One problem I have run into is when installing ndiswrapper , while trying "make" or "make install" , this is what happens.... 
*****************************************************************
root@ab-desktop:/home/ab/Desktop/ndiswrapper-1.8# make
make -C driver
make[1]: Entering directory `/home/ab/Desktop/ndiswrapper-1.27/driver'
Can't find kernel sources in /lib/modules/2.6.17-10-generic/build;
  give the path to kernel sources with KSRC=<path>             argument to make
make[1]: *** [prereq_check] Error 1
make[1]: Leaving directory `/home/ab/Desktop/ndiswrapper-1.27/driver'
make: *** [all] Error 2
*****************************************************************

I did look around a bit in the forums , tried reinstalling the kernel headers as it said in one of the forums but it did not work..
I have an AMD athlon 32 bit processor and one thing I did notice was that the /lib/modules contains two directories. 
1. 2.6.17-10-386
2. 2.6.17-10-generic

and only the first one has the build folder with the source code...

Any ideas?

p.s. - i need ndiswrapper for my Silan sc90231 ethernet card , any alternate method u can suggest to get the ethernet card to work would be fine too..

AB-

---

### Post by ab4ever on 2006-10-27
...anyone?

---

### Post by squibT on 2006-10-27
ndiswrapper is already in SP  Manager install it from there

---

