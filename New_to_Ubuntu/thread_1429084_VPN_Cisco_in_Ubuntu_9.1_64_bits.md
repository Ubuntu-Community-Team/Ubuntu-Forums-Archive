---
title: "VPN Cisco in Ubuntu 9.1 64 bits"
date: 2010-03-13
forum: New to Ubuntu
---

### Post by ElTron on 2010-03-13
Hi:

I'm trying to install Cisco VPN in an AMD64 with Ubuntu 9.1 2.6.31-20.

I have followed exactly the steps given by peteguhl

[http://ubuntuforums.org/showthread.php?t=592475](http://ubuntuforums.org/showthread.php?t=592475)

When I arrive at  Install the client   [ ./vpn_install ]
 that's what I obtain:

raym@raym-desktop:~/vpnclient$ ./vpn_install
Sorry, you need super user access to run this script.
raym@raym-desktop:~/vpnclient$ su
Contraseña: 
root@raym-desktop:/home/raym/vpnclient# ./vpn_install
Cisco Systems VPN Client Version 4.8.00 (0490) Linux Installer
Copyright (C) 1998-2005 Cisco Systems, Inc. All Rights Reserved.

By installing this product you agree that you have read the
license.txt file (The VPN Client license) and will comply with
its terms. 


Directory where binaries will be installed [/usr/local/bin]

Automatically start the VPN service at boot time [yes]

In order to build the VPN kernel module, you must have the
kernel headers for the version of the kernel you are running.


Directory containing linux kernel source code [/lib/modules/2.6.31-20-generic/build]

* Binaries will be installed in "/usr/local/bin".
* Modules will be installed in "/lib/modules/2.6.31-20-generic/CiscoVPN".
* The VPN service will be started AUTOMATICALLY at boot time.
* Kernel source from "/lib/modules/2.6.31-20-generic/build" will be used to build the module.

Is the above correct [y]y

Making module
make -C /lib/modules/2.6.31-20-generic/build SUBDIRS=/home/raym/vpnclient modules
make[1]: se ingresa al directorio `/usr/src/linux-headers-2.6.31-20-generic'
scripts/Makefile.build:49: *** CFLAGS was changed in "/home/raym/vpnclient/Makefile". Fix it to use EXTRA_CFLAGS.  Alto.
make[1]: *** [_module_/home/raym/vpnclient] Error 2
make[1]: se sale del directorio `/usr/src/linux-headers-2.6.31-20-generic'
make: *** [default] Error 2
Failed to make module "cisco_ipsec.ko".
root@raym-desktop:/home/raym/vpnclient# 



Any ideas.

Would the reason be that the patch is made for distro 2.6.22 and I'm using 2.6.31?

---

### Post by Rocket2DMn on 2010-03-13
Sounds like it may be a kernel compatibility issue.  Are you not able to use the NetworkManager Cisco VPN plugin, network-manager-vpnc ?  Is that not supported for 64 bit?

---

### Post by ElTron on 2010-03-13
OK. It is solved.

I have installed 32 bits libs and it worked.

thanks

---

### Post by bongdong on 2010-04-19
What 32 bits libs? I'm having the same problem.

---

### Post by sandyd on 2010-04-19
> **bongdong said:**
> What 32 bits libs? I'm having the same problem.

gcc-multilib & ia32libs (i *think* thats what its called, i just remember it starting w/ ia32...

---

### Post by bongdong on 2010-04-19
I finally got it working.

After following the instructions from [here.]("http://www.lamnk.com/blog/vpn/how-to-install-cisco-vpn-client-on-ubuntu-jaunty-jackalope-and-karmic-koala-64-bit/") I successfully installed vpnclient. But the VPN connection always hangs within minutes after the connection is established. 

After hours of searching, I finally found the fix from one of the comments to [this post]("http://ilapstech.blogspot.com/2009/09/cisco-vpn-client-on-karmic-koala.html").

"Cruz said...  For those experiencing the problem of loosing the VPN connection after some time when using kernel 2.6.31, you'll have to manually add a route to your local IP subnet after connecting to the VPN, e.g., if your local ip subnet is 192.168.1.0/24 and you are connecting to it using your eth0 interface, use the command "/sbin/route add -net 192.168.1.0/24 dev eth0".
You can obtain the information you need to use the "/sbin/route" command in the abovementioned way, by using it first in its simplest form, "/sbin/route"(choose from the list the network interface that is used to reach your default-gateway). This operation will overcome the ARP issue, which some people experience and some don't because some routers (the default-gateway of the PC) store in their ARP table the MAC addresses of devices connected to the local network for a longer time than others (some do this indefinitely): when the ARP entry corresponding to the PC using the Cisco VPN client expires in the ARP table of the local router, the local router will be unable to reach the PC, as it no longer knows its MAC address, and the VPN connection will first appear to have stop working and than disconnect after the Dead Peer Detection times out."

  This did the trick. Now I can access my company's network from my freshly built 64 bit Ubuntu 9.10 without any issue! Hope this can help those facing the same problem.

---

