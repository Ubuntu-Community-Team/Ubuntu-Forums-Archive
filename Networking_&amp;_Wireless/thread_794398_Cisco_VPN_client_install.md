---
title: "Cisco VPN client install"
date: 2008-05-14
forum: Networking &amp; Wireless
---

### Post by navy pilot 26734 on 2008-05-14
Does anyone know how to get the Cisco VPN client to work in 8.04?  I downloaded and extracted the client (vpnclient-linux-x86_64-4.8.01.0640-k9.tar.gz) into a directory on my desktop, but when I try to compile and install it I get the following output:

[B]Cisco Systems VPN Client Version 4.8.01 (0640) Linux Installer
Copyright (C) 1998-2006 Cisco Systems, Inc. All Rights Reserved.

By installing this product you agree that you have read the
license.txt file (The VPN Client license) and will comply with
its terms. 


Directory where binaries will be installed [/usr/local/bin]

Automatically start the VPN service at boot time [yes]

In order to build the VPN kernel module, you must have the
kernel headers for the version of the kernel you are running.


Directory containing linux kernel source code [/lib/modules/2.6.24-16-generic/build]/usr/src/linux-headers-2.6.24-16-generic

* Binaries will be installed in "/usr/local/bin".
* Modules will be installed in "/lib/modules/2.6.24-16-generic/CiscoVPN".
* The VPN service will be started AUTOMATICALLY at boot time.
* Kernel source from "/usr/src/linux-headers-2.6.24-16-generic" will be used to build the module.

Is the above correct [y]

Making module
make -C /usr/src/linux-headers-2.6.24-16-generic SUBDIRS=/home/robert/Desktop/vpnclient modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-16-generic'
scripts/Makefile.build:46: *** CFLAGS was changed in "/home/navy pilot/Desktop/vpnclient/Makefile". Fix it to use EXTRA_CFLAGS.  Stop.
make[1]: *** [_module_/home/navy pilot/Desktop/vpnclient] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-16-generic'
make: *** [default] Error 2
Failed to make module "cisco_ipsec.ko".
[/B]

I'm not sure how to fix this so I can get it installed.  I am running the 64 bit version of Ubuntu 8.04.  Please help.  Thanks.

---

### Post by jkilgrow on 2008-05-22
This may help....I just found it and am trying it now...

[http://www.lamnk.com/blog/domain/how-to-install-cisco-vpn-client-on-ubuntu-hardy-heron-804/](http://www.lamnk.com/blog/domain/how-to-install-cisco-vpn-client-on-ubuntu-hardy-heron-804/)

---

### Post by Paris Heng on 2008-05-22
> **jkilgrow said:**
> This may help....I just found it and am trying it now...

[http://www.lamnk.com/blog/domain/how-to-install-cisco-vpn-client-on-ubuntu-hardy-heron-804/](http://www.lamnk.com/blog/domain/how-to-install-cisco-vpn-client-on-ubuntu-hardy-heron-804/)

Thanks, how to run it indeed? It is GUI based or CLI?

---

### Post by vanadium on 2008-05-22
The easiest way is to install the network manager plugin from the repositories: network-manager-vpnc

This way, you can easily setup your connection from the network manager icon, and, once setup, connect with a click.

---

### Post by azredwing on 2008-05-22
I had the same problem installing the Cisco VPN client.

There is a patch available at:

[http://projects.tuxx-home.at/?id=cisco_vpn_client](http://projects.tuxx-home.at/?id=cisco_vpn_client)

Just follow the directions. It's worked for me every time.

---

### Post by mnk0 on 2008-05-27
i get a crash, after about 10-15 min of cisco vpn + rdesktop .. anyone else getting this//?

---

