---
title: "Problem with installation of VPN-Client"
date: 2008-09-08
forum: Networking &amp; Wireless
---

### Post by JuppSupp on 2008-09-08
Hi,

I switched to Ubunto a couple of weeks ago and now I moved to an appartment in the town where I attend university. Here I've got two possibilities to go online. First via proxy, but I can use that only for programms that support proxy such as firefox or ICQ.
On the other hand I've got a VPN account for using all other programms (updates, package manager, games only work with VPN). My university offers a vpn client for download called "vpnclient-linux-x86_64-4.8.01.0640-k9.tar.gz". So I downloaded and unpacked it. Then using the terminal I switched to the vpnclient-folder and started the installation.
This is the result of my terminal:

--------------------------------------------------------------------

jan@jan-laptop:~$ cd vpnclient/
jan@jan-laptop:~/vpnclient$ sudo ./vpn_install
[sudo] password for jan: 
Cisco Systems VPN Client Version 4.8.01 (0640) Linux Installer
Copyright (C) 1998-2006 Cisco Systems, Inc. All Rights Reserved.

By installing this product you agree that you have read the
license.txt file (The VPN Client license) and will comply with
its terms. 


Directory where binaries will be installed [/usr/local/bin]

Automatically start the VPN service at boot time [yes]

In order to build the VPN kernel module, you must have the
kernel headers for the version of the kernel you are running.


Directory containing linux kernel source code [/lib/modules/2.6.24-19-generic/build]

* Binaries will be installed in "/usr/local/bin".
* Modules will be installed in "/lib/modules/2.6.24-19-generic/CiscoVPN".
* The VPN service will be started AUTOMATICALLY at boot time.
* Kernel source from "/lib/modules/2.6.24-19-generic/build" will be used to build the module.

Is the above correct [y]

Making module
make -C /lib/modules/2.6.24-19-generic/build SUBDIRS=/home/jan/vpnclient modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-19-generic'
  CC [M]  /home/jan/vpnclient/linuxcniapi.o
In file included from /home/jan/vpnclient/Cniapi.h:15,
                 from /home/jan/vpnclient/linuxcniapi.c:31:
/home/jan/vpnclient/GenDefs.h:113: error: conflicting types for &#8216;uintptr_t&#8217;
include/linux/types.h:40: error: previous declaration of &#8216;uintptr_t&#8217; was here
make[2]: *** [/home/jan/vpnclient/linuxcniapi.o] Error 1
make[1]: *** [_module_/home/jan/vpnclient] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'
make: *** [default] Error 2
Failed to make module "cisco_ipsec.ko".
jan@jan-laptop:~/vpnclient$ 


-------------------------------------------------------------------

I don't have any idea why there are 2 errors.

The same error occurs if I download the client from other webpages.

I really hope that someone of you has expierience with this vpn client and knows what I've done wrong. Please help, I really need the client for using the internet apart from just browsing the web.
Let me know if you need further information of my system.

Thanks in advance!

---

### Post by JuppSupp on 2008-09-08
solved...got help in another forum :)

---

