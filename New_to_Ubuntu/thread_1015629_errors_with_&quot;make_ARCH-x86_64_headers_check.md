---
title: "errors with &quot;make ARCH-x86_64 headers check"
date: 2008-12-19
forum: New to Ubuntu
---

### Post by mrbiggbrain on 2008-12-19
im trying to do linux from scratch to learn more about linux.

i un-tar the linux source 

 >> tar jxf linux-2.6.24.7.tar.bz2 

 >> cd linux-2.6.24.7

 >> make mrpropper 

everything is ok so far, nothing appears for the previous command so i assume all went well

 >> make ARCH=x86_64 headers_check

this one goes CRAZY! so i took a look, it seems that linux-2.6.24.7/arch/x86_64 dosnt exist!

so im a little confused as to where this folder is? do i have to download a special source to get the folder i need and thus the makefile i need?

---

### Post by mrbiggbrain on 2008-12-19
i got the sources right from the [www.kernel.org](www.kernel.org)

if anyone can help it would be appreciated

---

### Post by igknighted on 2008-12-19
EDIT:

LFS is _not_ a beginners topic... try in the other OS talk, or I'm sure there is an LFS forum somewhere?  Tools for compiling a kernel from source are very distro specific, so the ubuntu method is very different than the LFS method which is different from the gentoo method, etc.

---

