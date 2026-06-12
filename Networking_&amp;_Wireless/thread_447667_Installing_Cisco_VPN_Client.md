---
title: "Installing Cisco VPN Client"
date: 2007-05-18
forum: Networking &amp; Wireless
---

### Post by lastoftheeld on 2007-05-18
Hey guys, I'm currently trying to install the Cisco VPN Client in order to connect to the wireless network on my campus. However, the install keeps crashing (output listed below). I'm running 7.04, and as far as I can tell all of the kernel headers are installed. Anyone have any suggestions? Thanks in advance. 



* Binaries will be installed in "/usr/local/bin".
* Modules will be installed in "/lib/modules/2.6.20-15-generic/CiscoVPN".
* The VPN service will be started AUTOMATICALLY at boot time.
* Kernel source from "/lib/modules/2.6.20-15-generic/build" will be used to build the module.

Is the above correct [y]

Making module
make -C /lib/modules/2.6.20-15-generic/build SUBDIRS=/home/ender/Desktop/vpnclient modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-15-generic'
  CC [M]  /home/ender/Desktop/vpnclient/linuxcniapi.o
/home/ender/Desktop/vpnclient/linuxcniapi.c:12:26: error: linux/config.h: No such file or directory
make[2]: *** [/home/ender/Desktop/vpnclient/linuxcniapi.o] Error 1
make[1]: *** [_module_/home/ender/Desktop/vpnclient] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-15-generic'
make: *** [default] Error 2
Failed to make module "cisco_ipsec.ko".

---

### Post by spin2cool on 2007-05-18
If you're having problems with the cisco client, you might try using vpnc instead.  There's more info on this forum or with a google search.

---

### Post by lastoftheeld on 2007-05-18
If anyone runs into the same problem, the patch and instructions at this site worked for me. Hope this helps someone else.

[http://tuxx-home.at/archives/2007/04/10/T15_55_43/](http://tuxx-home.at/archives/2007/04/10/T15_55_43/)

---

