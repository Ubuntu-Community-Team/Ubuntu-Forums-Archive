---
title: "Cisco VPN Client on Ubuntu 7.10 x86 How to?"
date: 2007-12-31
forum: Networking &amp; Wireless
---

### Post by cometcomputing on 2007-12-31
I am currently running a x86 notebook not a x86-x64 64 notebook and am trying to install the Cisco VPN Client on Unbuntu 7.10

Does an x86_x64 driver mean 64bit only? The reason I am asking is because I have followed all the instructions and tried both versions and I am getting the following errors. The cisco files are named. In the documentation it does say it is for 32bit and 64bit any advice would be greatly appreciated.

vpnclient-linux-x86_64-4.8.01.0640-k9.tar.gz
vpnclient-linux-x86_64-4.8.00.0490-k9.tar.gz
:


Cisco Systems VPN Client Version 4.8.00 (0490) Linux Installer
Copyright (C) 1998-2005 Cisco Systems, Inc. All Rights Reserved.

By installing this product you agree that you have read the
license.txt file (The VPN Client license) and will comply with
its terms. 


Directory where binaries will be installed [/usr/local/bin]

Automatically start the VPN service at boot time [yes]

In order to build the VPN kernel module, you must have the
kernel headers for the version of the kernel you are running.


Directory containing linux kernel source code [/lib/modules/2.6.22-14-generic/build]

* Binaries will be installed in "/usr/local/bin".
* Modules will be installed in "/lib/modules/2.6.22-14-generic/CiscoVPN".
* The VPN service will be started AUTOMATICALLY at boot time.
* Kernel source from "/lib/modules/2.6.22-14-generic/build" will be used to build the module.

Is the above correct [y]

Making module
make -C /lib/modules/2.6.22-14-generic/build SUBDIRS=/home/harryyeh/Desktop/Downloads/network applications/vpnclient-4.8.00.0490 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
make[1]: *** No rule to make target `applications/vpnclient-4.8.00.0490'.  Stop.
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
make: *** [default] Error 2
Failed to make module "cisco_ipsec.ko".

Cisco Systems VPN Client Version 4.8.01 (0640) Linux Installer
Copyright (C) 1998-2006 Cisco Systems, Inc. All Rights Reserved.

By installing this product you agree that you have read the
license.txt file (The VPN Client license) and will comply with
its terms. 


Directory where binaries will be installed [/usr/local/bin]

Automatically start the VPN service at boot time [yes]

In order to build the VPN kernel module, you must have the
kernel headers for the version of the kernel you are running.


Directory containing linux kernel source code [/lib/modules/2.6.22-14-generic/build]

* Binaries will be installed in "/usr/local/bin".
* Modules will be installed in "/lib/modules/2.6.22-14-generic/CiscoVPN".
* The VPN service will be started AUTOMATICALLY at boot time.
* Kernel source from "/lib/modules/2.6.22-14-generic/build" will be used to build the module.

Is the above correct [y]

Making module
make -C /lib/modules/2.6.22-14-generic/build SUBDIRS=/home/harryyeh/Desktop/Downloads/network applications/vpnclient-4.8.01.0640 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
make[1]: *** No rule to make target `applications/vpnclient-4.8.01.0640'.  Stop.
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
make: *** [default] Error 2
Failed to make module "cisco_ipsec.ko".


Any suggestions?

Harry Yeh
Comet Computing
5375 Parkwood Place
Richmond, BC
Canada
[http://www.cometcomputing.com](http://www.cometcomputing.com)
:confused::confused::confused:

---

### Post by christianxxx on 2008-01-03
Hi,

Had the same problem, but found a solution on the net. There's a patch to apply, have a look at [http://www.longren.org/2007/05/17/how-to-cisco-vpn-client-on-ubuntu-704-feisty-fawn/]("http://www.longren.org/2007/05/17/how-to-cisco-vpn-client-on-ubuntu-704-feisty-fawn/")

I still can't connect to my VPN network, but I suspect that's an authentication issue. Let me know if if works, would be cool if the client worked ok.


Christian

---

### Post by cmoman on 2008-01-05
To get 64bit working with Gutsy Gibbon

Get the lastest Cisco client from (well the lastest I can find)

[http://longren.org/files/](http://longren.org/files/)

and patch it with the patch on this page

[http://aggregator.foolab.org/node/20364](http://aggregator.foolab.org/node/20364)

It is working well on my machine AMD Turion 64x2 running 64bit Gutsy Gibbon (Kubuntu)

I had wanted to use the vpnc included as part of Kvpnc as this had worked in the past (on 32bit using Dapper) but I keep getting the following error so I tried the above and it works nicely.  

vpnc-connect: binding to 0.0.0.0:500: Address already in use

In fact, I'd still prefer to use Kvpnc as the integration into the knetwork manager looks very tidy.

Hopes this helps

---

### Post by cometcomputing on 2008-02-17
I am actually using a 32bit Client that was my question that I couldn't get it to work.

Harry Yeh
[http://www.cometcomputing.com](http://www.cometcomputing.com)

---

### Post by cometcomputing on 2008-02-17
DOH! Where you have the VPN Client extracted, make sure there is no space in the directory name. After I did that, the install worked, go figure...

Harry Yeh
[http://www.cometcomputing.com](http://www.cometcomputing.com)

---

