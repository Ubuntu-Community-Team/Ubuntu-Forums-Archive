---
title: "Intel Modem PCI 56K CTR-21"
date: 2006-10-22
forum: Networking &amp; Wireless
---

### Post by SysFAILURE on 2006-10-22
Hi to all, i've a problem.

I've a "Intel Internal 56K PCI modem", "Intel Modem PCI 56K CTR-21 (537EP)".

When i try to compile drivers, i receive this error:

```

sysfailure@CDC:~/intel/intel-537EP_secure-2.60.80.1$ sudo make clean
cd coredrv; make clean
make[1]: Entering directory `/home/sysfailure/intel/intel-537EP_secure-2.60.80.1/coredrv'
rm -f *.ko *.o .*.o.cmd *.mod.c *~ core .*.ko.cmd Modules.symvers
rm -rf .tmp_versions
make[1]: Leaving directory `/home/sysfailure/intel/intel-537EP_secure-2.60.80.1/coredrv'
rm -f *.o *.ko
sysfailure@CDC:~/intel/intel-537EP_secure-2.60.80.1$ sudo make 537
   Module precompile check
   Current running kernel is: 2.6.15-23-386
   /lib/modules...   autoconf.h exists
   autoconf.h matches running kernel
   version.h matches running kernel
2.6.15-23-386
make[1]: Entering directory `/home/sysfailure/intel/intel-537EP_secure-2.60.80.1/coredrv'
make -C /lib/modules/2.6.15-23-386/build SUBDIRS=/home/sysfailure/intel/intel-537EP_secure-2.60.80.1/coredrv modules
make[2]: Entering directory `/lib/modules/2.6.15-23-386/build'
make[2]: *** No rule to make target `modules'.  Stop.
make[2]: Leaving directory `/lib/modules/2.6.15-23-386/build'
make[1]: *** [537core_26] Error 2
make[1]: Leaving directory `/home/sysfailure/intel/intel-537EP_secure-2.60.80.1/coredrv'
2.6.15-23-386
Failed to build driver
sysfailure@CDC:~/intel/intel-537EP_secure-2.60.80.1$

```

URGENT!!! How can i solve this problem? Thanks you very much.

---
SysFAILURE // Ubuntu Linux User #

---

### Post by SysFAILURE on 2006-10-22
nobody can help me? :( 


](*,)

---

### Post by Matchless on 2006-10-22
Hi,
   Do a search for 537ep in the Ubuntu forum and you will find a lot of threads on that modem as well as Chuckmans Howto. I am sure you will get it going.

---

