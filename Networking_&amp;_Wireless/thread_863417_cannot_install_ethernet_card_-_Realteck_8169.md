---
title: "cannot install ethernet card - Realteck 8169"
date: 2008-07-18
forum: Networking &amp; Wireless
---

### Post by darbid on 2008-07-18
please help I am realtive new to ubuntu and this is my first install of a driver.

I have to do this

> Unpack the tarball :
		# tar vjxf r8169-6.aaa.bb.tar.bz2

	Change to the directory:
		# cd r8169-6.aaa.bb

	If you are running the target kernel, then you should be able to do :

		# make clean modules	(as root or with sudo)
		# make install
		# depmod -a
		# insmod ./src/r8169.ko	(or r8169.o for linux kernel 2.4.x)

This is what i get?????

```
wg@wg-server:~/driver/r8169-6.006.00$ sudo make clean modules
[sudo] password for wg: 
make -C src/ clean
make[1]: Entering directory `/home/wg/driver/r8169-6.006.00/src'
rm -rf *.o *.ko *~ core* .dep* .*.d .*.cmd *.mod.c *.a *.s .*.flags .tmp_versions Module.symvers Modules.symvers rset
make[1]: Leaving directory `/home/wg/driver/r8169-6.006.00/src'
make -C src/ modules
make[1]: Entering directory `/home/wg/driver/r8169-6.006.00/src'
make -C /lib/modules/2.6.24-19-generic/build SUBDIRS=/src modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.24-19-generic'
scripts/Makefile.build:41: /src/Makefile: No such file or directory
make[3]: *** No rule to make target `/src/Makefile'.  Stop.
make[2]: *** [_module_/src] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/home/wg/driver/r8169-6.006.00/src'
make: *** [modules] Error 2
wg@wg-server:~/driver/r8169-6.006.00$ 

```

why is this?  Could you please help.  i have a fully updated Ubuntu 8.04

---

### Post by darbid on 2008-07-18
oh oh stop typing, stop researching - it just turned up in my choices so somehow it is fixed

---

