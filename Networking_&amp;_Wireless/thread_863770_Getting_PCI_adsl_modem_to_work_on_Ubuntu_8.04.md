---
title: "Getting PCI adsl modem to work on Ubuntu 8.04"
date: 2008-07-18
forum: Networking &amp; Wireless
---

### Post by rossco on 2008-07-18
Hi all,

I am trying to get my PCI ADSL card to work on my Ubuntu Server 8.04 system.  The closest post I can find is the following [link]("http://ubuntuforums.org/archive/index.php/t-1906.html").  This is quite an old post so that may be the reason why it isn't working.  I have gotten this far:

> I use only this package from that guide.
[http://patrick.spacesurfer.com/adsl/CnxADSL-6.1.2.007-PIM-2.6-1.1.tar.bz2](http://patrick.spacesurfer.com/adsl/CnxADSL-6.1.2.007-PIM-2.6-1.1.tar.bz2)
I suppose to unpack in /root

To compile it you need the kernel headers. Chose it from Synaptic. Pay attention to choose the header of your kernel.
I use the linux-headers-2.6.8.1-3-k7

Download and unpack this source:

Now you need a link to your source because the driver look for /usr/src/linux and ubuntu uses /usr/src/linux-headers-2.6.8.1-3-k7. or
Example:
$ ln -s /usr/src/linux-headers-2.6.8.1-3-k7 /usr/src/linux

Now return to the source dir.

$ cd /root/CnxADSL-6.1.2.007-PIM-2.6-1.1

Build the Makefile running configure.
$ ./configure

**** This didn't work, but further down someone had posted this same error and the recommendation was to ignore this command

Build the driver with make.
$ make

When I run (sudo) make I get the following output:

> sudo make
for n in KernelModule/DpController; \
                do if [ -d $n ]; then make -C $n all || exit; fi; done
for n in KernelModule DownLoadApp; do make -C $n all || exit; done
make[1]: Entering directory `/home/ross/CnxADSL-6.1.2.007-PIM-2.6-1.7/KernelModule'
make CnxADSL.ko
make[2]: Entering directory `/home/ross/CnxADSL-6.1.2.007-PIM-2.6-1.7/KernelModule'
make -C /usr/src/linux SUBDIRS=`pwd` modules
make[3]: Entering directory `/usr/src/linux-headers-2.6.24-16-server'
  CC [M]  /home/ross/CnxADSL-6.1.2.007-PIM-2.6-1.7/KernelModule/ARMAbstract.o
In file included from /home/ross/CnxADSL-6.1.2.007-PIM-2.6-1.7/KernelModule/LnxTools.h:44,
                 from /home/ross/CnxADSL-6.1.2.007-PIM-2.6-1.7/KernelModule/ARMAbstract.c:34:
/home/ross/CnxADSL-6.1.2.007-PIM-2.6-1.7/KernelModule/Version.h:87:2: error: invalid preprocessing directive #warn
make[4]: *** [/home/ross/CnxADSL-6.1.2.007-PIM-2.6-1.7/KernelModule/ARMAbstract.o] Error 1
make[3]: *** [_module_/home/ross/CnxADSL-6.1.2.007-PIM-2.6-1.7/KernelModule] Error 2
make[3]: Leaving directory `/usr/src/linux-headers-2.6.24-16-server'
make[2]: *** [CnxADSL.ko] Error 2
make[2]: Leaving directory `/home/ross/CnxADSL-6.1.2.007-PIM-2.6-1.7/KernelModule'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/home/ross/CnxADSL-6.1.2.007-PIM-2.6-1.7/KernelModule'
make: *** [all] Error 2


Does anyone know what the problem is or if there is a more up to date place for configuring my modem?

---

