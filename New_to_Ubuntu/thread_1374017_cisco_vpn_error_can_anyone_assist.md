---
title: "cisco vpn error can anyone assist"
date: 2010-01-06
forum: New to Ubuntu
---

### Post by crazysexycool on 2010-01-06
hi hopefully i can get some help in this area i am trying to install my works cisco vpn client reason i am not using open vpn or any of the other is because i am not to familiar on how to set it up any assistance will be greatly appreciated i am using ubuntu 9.10 

here is my error during installation 

Cisco Systems VPN Client Version 4.8.01 (0640) Linux Installer
Copyright (C) 1998-2006 Cisco Systems, Inc. All Rights Reserved.

By installing this product you agree that you have read the
license.txt file (The VPN Client license) and will comply with
its terms. 


Directory where binaries will be installed [/usr/local/bin]

Automatically start the VPN service at boot time [yes]

In order to build the VPN kernel module, you must have the
kernel headers for the version of the kernel you are running.


Directory containing linux kernel source code [/lib/modules/2.6.31-16-generic/build]

* Binaries will be installed in "/usr/local/bin".
* Modules will be installed in "/lib/modules/2.6.31-16-generic/CiscoVPN".
* The VPN service will be started AUTOMATICALLY at boot time.
* Kernel source from "/lib/modules/2.6.31-16-generic/build" will be used to build the module.

Is the above correct [y]

Making module
make -C /lib/modules/2.6.31-16-generic/build SUBDIRS=/home/f3091236/Desktop/vpnclient modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-16-generic'
  CC [M]  /home/f3091236/Desktop/vpnclient/linuxcniapi.o
In file included from /home/f3091236/Desktop/vpnclient/Cniapi.h:15,
                 from /home/f3091236/Desktop/vpnclient/linuxcniapi.c:31:
/home/f3091236/Desktop/vpnclient/GenDefs.h:113: error: conflicting types for ‘uintptr_t’
include/linux/types.h:41: note: previous declaration of ‘uintptr_t’ was here
make[2]: *** [/home/f3091236/Desktop/vpnclient/linuxcniapi.o] Error 1
make[1]: *** [_module_/home/f3091236/Desktop/vpnclient] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-16-generic'
make: *** [default] Error 2
Failed to make module "cisco_ipsec.ko".
f3091236@f3091236-laptop:~/Desktop/vpnclient$

---

### Post by crazysexycool on 2010-01-07
Hi ok i have successfully installed Cisco VPN client 

however i am now a bit clueless as to how i go about installing the certificate as well as starting the client....

---

