---
title: "FATAL: Module wl not found in directory /lib/modules/4.15.0-33-generic"
date: 2018-08-30
forum: Networking &amp; Wireless
---

### Post by saurabhgangurde on 2018-08-30
I'm getting following error while installing bcmwl-kernel-source from apt-get on ubuntu 18.04 LTS

ERROR: Cannot create report: [Errno 17] File exists: '/var/crash/bcmwl-kernel-source.0.crash'
Error! Bad return status for module build on kernel: 4.15.0-33-generic (x86_64)
Consult /var/lib/dkms/bcmwl/6.30.223.271+bdcom/build/make.log for more information.
modprobe: FATAL: Module wl not found in directory /lib/modules/4.15.0-33-generic



Please help.

---

### Post by praseodym on 2018-08-30
/var/lib/dkms/bcmwl/6.30.223.271+bdcom/build/make.log

Please show this file

---

### Post by saurabhgangurde on 2018-08-31
Content of file:

################################################################
DKMS make.log for bcmwl-6.30.223.271+bdcom for kernel 4.15.0-33-generic (x86_64)
Thu Aug 30 22:39:27 IST 2018
make: Entering directory '/usr/src/linux-headers-4.15.0-33-generic'
CFG80211 API is prefered for this kernel version
Using CFG80211 API
  CC [M]  /var/lib/dkms/bcmwl/6.30.223.271+bdcom/build/src/shared/linux_osl.o
gcc: error: unrecognized command line option ‘-fstack-protector-strong’
  CC [M]  /var/lib/dkms/bcmwl/6.30.223.271+bdcom/build/src/wl/sys/wl_linux.o
scripts/Makefile.build:332: recipe for target '/var/lib/dkms/bcmwl/6.30.223.271+bdcom/build/src/shared/linux_osl.o' failed
make[1]: *** [/var/lib/dkms/bcmwl/6.30.223.271+bdcom/build/src/shared/linux_osl.o] Error 1
make[1]: *** Waiting for unfinished jobs....
gcc: error: unrecognized command line option ‘-fstack-protector-strong’
scripts/Makefile.build:332: recipe for target '/var/lib/dkms/bcmwl/6.30.223.271+bdcom/build/src/wl/sys/wl_linux.o' failed
make[1]: *** [/var/lib/dkms/bcmwl/6.30.223.271+bdcom/build/src/wl/sys/wl_linux.o] Error 1
make[1]: *** wait: No child processes.  Stop.
Makefile:1552: recipe for target '_module_/var/lib/dkms/bcmwl/6.30.223.271+bdcom/build' failed
make: *** [_module_/var/lib/dkms/bcmwl/6.30.223.271+bdcom/build] Error 2
make: Leaving directory '/usr/src/linux-headers-4.15.0-33-generic'

---

### Post by saurabhgangurde on 2018-08-31
Solved.
 I was using older version of g++ for other purpose that caused problem.

---

### Post by praseodym on 2018-09-02
Great! Please use Thread tool to mark it [SOLVED]

---

