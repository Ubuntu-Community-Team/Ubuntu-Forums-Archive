---
title: "can't make ndiswrapper"
date: 2008-04-24
forum: Networking &amp; Wireless
---

### Post by adonikam on 2008-04-24
i'm trying to use this tutorial, which worked in gutsy:
[http://ubuntuforums.org/showthread.php?t=201902&highlight=broadcom+4306](http://ubuntuforums.org/showthread.php?t=201902&highlight=broadcom+4306)

but i'm stuck on step 11 which is in the ndiswrapper directory:
sudo make

when i do it i get these errors.
make[2]: Entering directory `/usr/src/linux-headers-2.6.24-16-generic'
scripts/Makefile.build:46: *** CFLAGS was changed in "/home/cs/ndiswrapper/ndiswrapper-1.48rc1/driver/Makefile". Fix it to use EXTRA_CFLAGS.  Stop.
make[2]: *** [_module_/home/cs/ndiswrapper/ndiswrapper-1.48rc1/driver] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.24-16-generic'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/cs/ndiswrapper/ndiswrapper-1.48rc1/driver'
make: *** [all] Error 2


when i type 
make (no sudo) 
i get this error:
make[2]: Entering directory `/usr/src/linux-headers-2.6.24-16-generic'
  CC [M]  /home/cs/ndiswrapper/ndiswrapper-1.48rc1/driver/proc.o
/home/cs/ndiswrapper/ndiswrapper-1.48rc1/driver/proc.c: In function ‘wrap_procfs_init’:
/home/cs/ndiswrapper/ndiswrapper-1.48rc1/driver/proc.c:507: error: ‘proc_net’ undeclared (first use in this function)
/home/cs/ndiswrapper/ndiswrapper-1.48rc1/driver/proc.c:507: error: (Each undeclared identifier is reported only once
/home/cs/ndiswrapper/ndiswrapper-1.48rc1/driver/proc.c:507: error: for each function it appears in.)
/home/cs/ndiswrapper/ndiswrapper-1.48rc1/driver/proc.c: In function ‘wrap_procfs_remove’:
/home/cs/ndiswrapper/ndiswrapper-1.48rc1/driver/proc.c:534: error: ‘proc_net’ undeclared (first use in this function)

help!!!

---

### Post by kevdog on 2008-04-24
You didn't install the linux headers appropriately I bet.

sudo aptitude install linux-headers-`uname -r`

---

### Post by adonikam on 2008-04-24
i got the newest version 1.52 and it worked, thanks

---

