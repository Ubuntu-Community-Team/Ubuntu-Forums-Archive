---
title: "cisco vpn client problems"
date: 2008-11-13
forum: Networking &amp; Wireless
---

### Post by dealton on 2008-11-13
Hi everyone,

I am still new to ubuntu but am loving the transition. 

I have to vpn into my work computer and have been getting an error while trying to install cisco vpn client can anyone help? It would be great!

rick@rick-laptop:~/vpnclient$ sudo ./vpn_install
sudo: unable to resolve host rick-laptop
[sudo] password for rick:
Cisco Systems VPN Client Version 4.8.00 (0490) Linux Installer
Copyright (C) 1998-2005 Cisco Systems, Inc. All Rights Reserved.

By installing this product you agree that you have read the
license.txt file (The VPN Client license) and will comply with
its terms.


Directory where binaries will be installed [/usr/local/bin]

Automatically start the VPN service at boot time [yes]

In order to build the VPN kernel module, you must have the
kernel headers for the version of the kernel you are running.


Directory containing linux kernel source code [/lib/modules/2.6.24-21-generic/build]

* Binaries will be installed in "/usr/local/bin".
* Modules will be installed in "/lib/modules/2.6.24-21-generic/CiscoVPN".
* The VPN service will be started AUTOMATICALLY at boot time.
* Kernel source from "/lib/modules/2.6.24-21-generic/build" will be used to build the module.

Is the above correct [y]

Making module
make -C /lib/modules/2.6.24-21-generic/build SUBDIRS=/home/rick/vpnclient modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-21-generic'
  CC [M]  /home/rick/vpnclient/linuxcniapi.o
/home/rick/vpnclient/linuxcniapi.c:12:26: error: linux/config.h: No such file or directory
In file included from /home/rick/vpnclient/Cniapi.h:15,
                 from /home/rick/vpnclient/linuxcniapi.c:27:
/home/rick/vpnclient/GenDefs.h:113: error: conflicting types for 'uintptr_t'
include/linux/types.h:40: error: previous declaration of 'uintptr_t' was here
/home/rick/vpnclient/linuxcniapi.c: In function 'CniInjectReceive':
/home/rick/vpnclient/linuxcniapi.c:297: error: implicit declaration of function 'skb_set_timestamp'
/home/rick/vpnclient/linuxcniapi.c:331: error: 'struct sk_buff' has no member named 'nh'
/home/rick/vpnclient/linuxcniapi.c:332: error: 'struct sk_buff' has no member named 'mac'
/home/rick/vpnclient/linuxcniapi.c: In function 'CniInjectSend':
/home/rick/vpnclient/linuxcniapi.c:454: error: 'struct sk_buff' has no member named 'mac'
/home/rick/vpnclient/linuxcniapi.c:455: error: 'struct sk_buff' has no member named 'nh'
/home/rick/vpnclient/linuxcniapi.c:458: error: 'struct sk_buff' has no member named 'h'
/home/rick/vpnclient/linuxcniapi.c:458: error: 'struct sk_buff' has no member named 'nh'
make[2]: *** [/home/rick/vpnclient/linuxcniapi.o] Error 1
make[1]: *** [_module_/home/rick/vpnclient] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-21-generic'
make: *** [default] Error 2
Failed to make module "cisco_ipsec.ko".
rick@rick-laptop:~/vpnclient$

---

### Post by jmslee_2000 on 2009-01-22
I got the same thing as you had, I have sufered on the google, all instructions did not make this successful.:(

---

### Post by dealton on 2009-01-22
i still was unable to get the vpninstall working. My company that i work for provided a vpnsetup.sh file that i was able to run from the terminal and that seemed to set everything up correctly. Sorry I couldn't be of more assistance

---

### Post by Kaomy on 2009-12-26
I have the same problem! with exactly the same output errors.  I have tried everything, i even tried to install vpnc instead vpn but still i  can't connect... please, help us! :(

---

