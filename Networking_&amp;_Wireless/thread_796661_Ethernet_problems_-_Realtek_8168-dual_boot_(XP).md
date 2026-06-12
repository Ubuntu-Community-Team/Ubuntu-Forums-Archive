---
title: "Ethernet problems - Realtek 8168-dual boot (XP)"
date: 2008-05-16
forum: Networking &amp; Wireless
---

### Post by AgDon92 on 2008-05-16
Hello,
I am brand new to Ubuntu. In fact, I just installed it yesterday. I have a Realtek 8168 card in an Acer laptop. I've tried all of the tricks posted (started with network cable plugged in, reset all power, etc). I think it's a driver problem. I downloaded the r8168-8.006.00.tar.bz2 file from Realtek and followed the instructions in the readme. They are the same as posted above. Here are my results:


sudo make clean modules
make -C src/ clean
make[1]: Entering directory `/tmp/r8168-8.006.00/src'
rm -rf *.o *.ko *~ core* .dep* .*.d .*.cmd *.mod.c *.a *.s .*.flags .tmp_versions Module.symvers Modules.symvers rset
make[1]: Leaving directory `/tmp/r8168-8.006.00/src'
make -C src/ modules
make[1]: Entering directory `/tmp/r8168-8.006.00/src'
make -C /lib/modules/2.6.24-16-generic/build SUBDIRS=/src modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.24-16-generic'
scripts/Makefile.build:41: /src/Makefile: No such file or directory
make[3]: *** No rule to make target `/src/Makefile'. Stop.
make[2]: *** [_module_/src] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.24-16-generic'
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/tmp/r8168-8.006.00/src'
make: *** [modules] Error 2

================================================== ==========
uname -r
2.6.24-16-generic


Any help or suggestions are appreciated.

Cheers!

Don

---

### Post by AgDon92 on 2008-05-19
I actually found a solution to this problem.  I still have a problem and will post a new thread.

Thanks.

Don

---

