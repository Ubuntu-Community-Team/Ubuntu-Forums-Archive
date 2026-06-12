---
title: "Cisco VPN client error"
date: 2006-10-30
forum: Networking &amp; Wireless
---

### Post by lynxus on 2006-10-30
Hi guys, 
Im trying to install teh cisco vpn client without any luck!

Ive tried the walkthroughs and get no avail. Ive patched it, unpatched it etc etc etc

Still nothing.
Here is a copy of the error im getting.

Ive got the latest cgg and make installed.
Also the same error happens weather its sudo or non sudo.

ANY IDEAS PLEASE!
I have the correct headers installed aswell.
2.6.15-27-386

---

gsmart@gsmart-laptop:~/Desktop/cisco client/VPN/vpnclient$./vpn_install
Cisco Systems VPN Client Version 4.8.00 (0490) Linux Installer
Copyright (C) 1998-2005 Cisco Systems, Inc. All Rights Reserved.

By installing this product you agree that you have read the
license.txt file (The VPN Client license) and will comply with
its terms.


Directory where binaries will be installed [/usr/local/bin]

Automatically start the VPN service at boot time [yes]yes

In order to build the VPN kernel module, you must have the
kernel headers for the version of the kernel you are running.


Directory containing linux kernel source code [/lib/modules/2.6.15-27-386/build]
* Binaries will be installed in "/usr/local/bin".
* Modules will be installed in "/lib/modules/2.6.15-27-386/CiscoVPN".
* The VPN service will be started AUTOMATICALLY at boot time.
* Kernel source from "/lib/modules/2.6.15-27-386/build" will be used to build the module.

Is the above correct [y]y

Making module
make -C /lib/modules/2.6.15-27-386/build SUBDIRS=/home/gsmart/Desktop/cisco client/VPN/vpnclient modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.15-27-386'
make[1]: *** No rule to make target `client/VPN/vpnclient'. Stop.
make[1]: Leaving directory `/usr/src/linux-headers-2.6.15-27-386'
make: *** [default] Error 2
Failed to make module "cisco_ipsec.ko".

---

### Post by x64Jimbo on 2006-11-16
You need to use your kernel headers directory, which is something like /usr/src/linux-headers-2.6.15-27-386/ but you'll need to check what that last directory is called by running uname -r

---

