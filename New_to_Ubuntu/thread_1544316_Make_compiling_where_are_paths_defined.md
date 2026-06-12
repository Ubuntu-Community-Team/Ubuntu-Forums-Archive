---
title: "Make: compiling: where are paths defined?"
date: 2010-08-02
forum: New to Ubuntu
---

### Post by Hipfner on 2010-08-02
I am trying to compile a driver. See below

The instructions are simple, just type "make all", etc.
But the compile fails when it comes across an undefined identifier. 

But the identifier is defined in a sub-sub directory of the directory that "make[2]"  searched.

1. Does the compiler's search stop at the first directory that it entered? Can I force it go deeper?
2. Where is the definition of the directory that the compiler is searching? I've tried /etc/environment (no effect)

I did two days of google searches, got 3 books from the library. I really stuck!
Thanks for your help


terry@terry-desktop:~$ make all

make -C kmodule/ modules
make[1]: Entering directory `/home/terry/kmodule'
make -C /lib/modules/2.6.32-21-generic/build M="/home/terry/kmodule"  modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.32-21-generic'
  CC [M]  /home/terry/kmodule/martian.o
/home/terry/kmodule/martian.c: In function â€˜martian_isrâ€™:
/home/terry/kmodule/martian.c:131: warning: value computed is not used
/home/terry/kmodule/martian.c:148: error: â€˜TASK_INTERRUPTIBLEâ€™ undeclared (first use in this function)
/home/terry/kmodule/martian.c:148: error: (Each undeclared identifier is reported only once
/home/terry/kmodule/martian.c:148: error: for each function it appears in.)
/home/terry/kmodule/martian.c: In function â€˜martian_readâ€™:
/home/terry/kmodule/martian.c:554: error: â€˜TASK_INTERRUPTIBLEâ€™ undeclared (first use in this function)
/home/terry/kmodule/martian.c:554: error: implicit declaration of function â€˜signal_pendingâ€™
/home/terry/kmodule/martian.c:554: error: implicit declaration of function â€˜scheduleâ€™
make[3]: *** [/home/terry/kmodule/martian.o] Error 1
make[2]: *** [_module_/home/terry/kmodule] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.32-21-generic'
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/home/terry/kmodule'
make: *** [all] Error 2
terry@terry-desktop:~$

---

### Post by Bachstelze on 2010-08-02
Chances are that the driver you are trying to compile is not compatible with your kernel version.  Whar driver is it?

---

### Post by Hipfner on 2010-08-02
I downloaded the driver code from this site. For my internal dial-up modem.

[http://martian.barrelsoutofbond.org/](http://martian.barrelsoutofbond.org/)


The definition of TASK_INTERRUPTIBLE does exist in a header file. But it's two levels deeper than the compile step make[2] announced.

---

### Post by Bachstelze on 2010-08-02
You are probably trying to compile the one from 2008, it gives the same errors here.  The 2010 one [here]("http://linmodems.technion.ac.il/packages/ltmodem/kernel-2.6/martian/martian-full-20100123.tar.gz") works for me (or at least it builds fine, I don't have a martian modem to test it anymore).

---

### Post by Hipfner on 2010-08-02
Yes. That one compiled. Thanks very much.
:D

---

