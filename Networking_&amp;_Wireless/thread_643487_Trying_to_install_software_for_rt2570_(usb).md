---
title: "Trying to install software for rt2570 (usb)"
date: 2007-12-17
forum: Networking &amp; Wireless
---

### Post by toarlach on 2007-12-17
Okay, tell me what I'm doing wrong, I'm following the instructions in the README file...

root@csweely-desktop:/home/csweely/Drivers/rt2570-cvs-2007121615/Module# make # compile driver source code
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  Building modules, stage 2.
  MODPOST 1 modules
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
root@csweely-desktop:/home/csweely/Drivers/rt2570-cvs-2007121615/Module# make install # installs kernel module driver
2.6 module install
make -C /lib/modules/2.6.22-14-generic/build SUBDIRS=/home/csweely/Drivers/rt2570-cvs-2007121615/Module  modules_install
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  INSTALL /home/csweely/Drivers/rt2570-cvs-2007121615/Module/rt2570.ko
  DEPMOD  2.6.22-14-generic
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
/sbin/depmod -a
*** Update /etc/modprobe.d/ralink alias for rausb0
root@csweely-desktop:/home/csweely/Drivers/rt2570-cvs-2007121615/Module# modprobe rt2570
root@csweely-desktop:/home/csweely/Drivers/rt2570-cvs-2007121615/Module# ifup rausb0
Ignoring unknown interface rausb0=rausb0.
root@csweely-desktop:/home/csweely/Drivers/rt2570-cvs-2007121615/Module# 

I don't get why it's not recognizing rausb0

---

