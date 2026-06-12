---
title: "Errors when compiling driver from Realtek site"
date: 2008-09-16
forum: Networking &amp; Wireless
---

### Post by panfist on 2008-09-16
I am trying to compile a driver from Realtek's site for my onboard 8111c.

The driver version is r8168-8.008.00.

The error I get is as follows:

lorsadmin@lorsbackupserver1:/usr/src/r8168-8.008.00$ sudo make clean modules
make -C src/ clean
make[1]: Entering directory `/usr/src/r8168-8.008.00/src'
rm -rf *.o *.ko *~ core* .dep* .*.d .*.cmd *.mod.c *.a *.s .*.flags .tmp_versions Module.symvers Modules.symvers *.order
make[1]: Leaving directory `/usr/src/r8168-8.008.00/src'
make -C src/ modules
make[1]: Entering directory `/usr/src/r8168-8.008.00/src'
make -C /lib/modules/2.6.24-19-server/build SUBDIRS=/src modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.24-19-server'
scripts/Makefile.build:41: /src/Makefile: No such file or directory
make[3]: *** No rule to make target `/src/Makefile'.  Stop.
make[2]: *** [_module_/src] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.24-19-server'
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/usr/src/r8168-8.008.00/src'
make: *** [modules] Error 2


Thank you.

---

### Post by panfist on 2008-09-17
I still have this problem and I hope someone can help.

Thanks.

---

### Post by scottlindner on 2008-11-08
I had the same issue and resolved it with the following two commands.  I don't know if the first was necessary, but it worked after the second command:
> sudo apt-get install linux-source
> sudo m-a update,prepare

This URL is my reference, [http://forum.tuxx-home.at/viewtopic.php?f=2&t=622]("http://forum.tuxx-home.at/viewtopic.php?f=2&t=622")

---

