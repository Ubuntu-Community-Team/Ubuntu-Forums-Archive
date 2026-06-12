---
title: "How to enable kernel modules"
date: 2011-09-04
forum: New to Ubuntu
---

### Post by Lasitha1991 on 2011-09-04
hi, I'm using ubuntu 11.04.
While I was trying to compile my module I got the following message.

lasitha@ubuntu:~$ make -C /usr/src/linux-headers-2.6.38-8 SUBDIRS=$pwd modules 
make: Entering directory `/usr/src/linux-headers-2.6.38-8' 
  HOSTCC  scripts/basic/fixdep 
scripts/basic/fixdep.c:432:1: fatal error: opening dependency file scripts/basic/.fixdep.d: Permission denied 
compilation terminated. 
make[2]: *** [scripts/basic/fixdep] Error 1 
make[1]: *** [scripts_basic] Error 2 

The present kernel configuration has modules disabled. 
Type 'make config' and enable loadable module support. 
Then build a kernel with module support enabled. 

make: *** [modules] Error 1 
make: Leaving directory `/usr/src/linux-headers-2.6.38-8' 


I want to know how to enable module support.

---

### Post by Leshrac on 2011-09-04
If what you want is to build a custom kernel with different options than the ones that come with the stock one you should read this:
[https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile)

---

### Post by Lasitha1991 on 2011-09-04
Thanks I'll try it...! :P:P:P

---

### Post by Frogs Hair on 2011-09-04
This might be of interest .[http://kcheck.sourceforge.net/](http://kcheck.sourceforge.net/)

---

