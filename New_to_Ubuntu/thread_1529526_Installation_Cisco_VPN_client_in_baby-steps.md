---
title: "Installation Cisco VPN client in baby-steps"
date: 2010-07-12
forum: New to Ubuntu
---

### Post by Benfatto on 2010-07-12
Hi there,

A company I work for has requested me to install cisco vpn on my laptop to be able to log on to their system. I am running Ubuntu 9.04 with a 2.6.28-19-generic kernal and consider myself an absolute beginner on linux/ubuntu. When I try to follow the steps:

**1. Untar the VPN Client**
# tar xzf vpnclient-linux-x86_64-4.8.02.0030-k9.tar.gz

**2. Change to the vpnclient directory**
# cd vpnclient

**3. Install the client**
#./vpn_install

after downloading the client as provided [here]("http://projects.tuxx-home.at/?id=cisco_vpn_client") i get the following message: 

god@Prometheus:~$ tar xzf vpnclient-linux-4.8.01.0640-k9.tar.gz
tar: vpnclient-linux-4.8.01.0640-k9.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
god@Prometheus:~$ tar xzf vpnclient-linux-4.8.01.0640-k9.tar.gz
tar: vpnclient-linux-4.8.01.0640-k9.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
god@Prometheus:~$ wget -q [http://projects.tuxx-home.at/ciscovpn/p ... final.diff]("http://projects.tuxx-home.at/ciscovpn/patches/vpnclient-linux-2.6.24-final.diff")
god@Prometheus:~$ cd vpnclient
bash: cd: vpnclient: No such file or directory

Can someone with patience please explain me what I am doing wrong and how I can install the client?

---

### Post by mikewhatever on 2010-07-12
Make sure you run the first command from the location where you saved the vpnclient-linux-x86_64-4.8.02.0030-k9.tar.gz file. For example, if the file is on the desktop, you have to move there first with the following command:
```
cd Desktop
```

Edit: Any idea why install from tar.gz? It looks like there is a Cisco vpn client in the repositories.
```
vpnc is a VPN client compatible with cisco3000 VPN Concentrator (also
known as Cisco's EasyVPN equipment). vpnc runs entirely in userspace
and does not require kernel modules except of the tun driver to
communicate with the network layer.
```

I'd strongly suggest trying that first. Just open Synaptic and search for 'vpnc'.

---

### Post by Benfatto on 2010-07-12
Thanks for the input Mike, I installed VPNC through Synaptic, but how do I run it? No icon to be found.

---

### Post by mikewhatever on 2010-07-12
Hm, to be honest, I've never used Cisco VPN, but there are howtos.
[http://ubuntuforums.org/showthread.php?p=7705157](http://ubuntuforums.org/showthread.php?p=7705157)
Not exactly point and click, to be sure.;)

---

### Post by Benfatto on 2010-07-13
The link in the HowTo is dead, unfortunately. So I tried doing it the first way, but get stuck at this:

god@Prometheus:~/vpnclient$ ./vpn_install
Sorry, you need super user access to run this script.

---

### Post by mikewhatever on 2010-07-13
The superuser message means you need to run the command with 'sudo', like this:
```
sudo ./vpn_install
```

On the second thought, vpnc is already installed and all you need is a configuration file. Here is some info on creating one.
[http://www.debuntu.org/how-to-connect-to-a-cisco-vpn-using-vpnc](http://www.debuntu.org/how-to-connect-to-a-cisco-vpn-using-vpnc)

---

### Post by Benfatto on 2010-07-14
:ah that's silly, I should have thought of that. But then:

Directory where binaries will be installed [/usr/local/bin]

Automatically start the VPN service at boot time [yes]n

In order to build the VPN kernel module, you must have the
kernel headers for the version of the kernel you are running.


Directory containing linux kernel source code [/lib/modules/2.6.28-19-generic/build]

* Binaries will be installed in "/usr/local/bin".
* Modules will be installed in "/lib/modules/2.6.28-19-generic/CiscoVPN".
* The VPN service will *NOT* be started automatically at boot time.
* Kernel source from "/lib/modules/2.6.28-19-generic/build" will be used to build the module.

Is the above correct [y]

Making module
make -C /lib/modules/2.6.28-19-generic/build SUBDIRS=/home/god/vpnclient modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.28-19-generic'
  CC [M]  /home/god/vpnclient/linuxcniapi.o
In file included from /home/god/vpnclient/Cniapi.h:15,
                 from /home/god/vpnclient/linuxcniapi.c:31:
/home/god/vpnclient/GenDefs.h:113: error: conflicting types for ‘uintptr_t’
include/linux/types.h:40: error: previous declaration of ‘uintptr_t’ was here
make[2]: *** [/home/god/vpnclient/linuxcniapi.o] Error 1
make[1]: *** [_module_/home/god/vpnclient] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-19-generic'
make: *** [default] Error 2
Failed to make module "cisco_ipsec.ko".
god@Prometheus:~/vpnclient$

---

### Post by mikewhatever on 2010-07-14
No, it failed to build the module. Make sure you have the following installed:
```
build-essential
linux-headers
```

It's also a good idea to uninstall vpnc you'd installed from the repositores, since you are trying to build from source.

---

### Post by Benfatto on 2010-07-15
Ok, so I try to install build-essential and find this command in another thread. This is the result:

god@Prometheus:~$ gksudo aptitude install build-essential
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initialising package states... Done
Writing extended state information... Done
The following packages will be REMOVED:
  libbtctl4{u} libgnomebt0{u} libgnomescan-common{u} 
  libgnomescanui-common{u} linux-headers-2.6.28-15{u} 
  linux-headers-2.6.28-15-generic{u} resolvconf{u} 
0 packages upgraded, 0 newly installed, 7 to remove and 1 not upgraded.
Need to get 0B of archives. After unpacking 75.7MB will be freed.
Do you want to continue? [Y/n/?] 


I am a little worried that I&#314;l be messing up my system without knowing it.

---

### Post by Benfatto on 2010-07-25
Anyone else out there that can help me?

---

### Post by Benfatto on 2010-08-30
I have not found a solution yet nor have I given up

---

### Post by eljonny on 2011-01-26
I am running xubuntu 10.10 with kernel headers 2.6.35-24-generic, and trying to compile this fails; I am completely lost. The patches from other how-to's and forums get me 1 little step closer it seems, but it still won't compile. If anyone has any advice it would be greatly appreciated. Here is my current output when I attempt to compile with ./vpn_install:

```

root@jon-laptop:/home/jon/Downloads/vpnclient# ./vpn_install
Cisco Systems VPN Client Version 4.8.01 (0640) Linux Installer
Copyright (C) 1998-2006 Cisco Systems, Inc. All Rights Reserved.

By installing this product you agree that you have read the
license.txt file (The VPN Client license) and will comply with
its terms. 


Directory where binaries will be installed [/usr/local/bin]/usr/bin

Automatically start the VPN service at boot time [yes]

In order to build the VPN kernel module, you must have the
kernel headers for the version of the kernel you are running.


Directory containing linux kernel source code [/lib/modules/2.6.35-24-generic/build]/usr/src/linux-headers-2.6.35-24-generic

* Binaries will be installed in "/usr/bin".
* Modules will be installed in "/lib/modules/2.6.35-24-generic/CiscoVPN".
* The VPN service will be started AUTOMATICALLY at boot time.
* Kernel source from "/usr/src/linux-headers-2.6.35-24-generic" will be used to build the module.

Is the above correct [y]

Making module
make -C /usr/src/linux-headers-2.6.35-24-generic SUBDIRS=/home/jon/Downloads/vpnclient modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.35-24-generic'
  CC [M]  /home/jon/Downloads/vpnclient/linuxcniapi.o
  CC [M]  /home/jon/Downloads/vpnclient/frag.o
  CC [M]  /home/jon/Downloads/vpnclient/IPSecDrvOS_linux.o
  CC [M]  /home/jon/Downloads/vpnclient/interceptor.o
/home/jon/Downloads/vpnclient/interceptor.c:112: error: unknown field &#8216;init&#8217; specified in initializer
/home/jon/Downloads/vpnclient/interceptor.c:113: warning: initialization from incompatible pointer type
/home/jon/Downloads/vpnclient/interceptor.c: In function &#8216;interceptor_init&#8217;:
/home/jon/Downloads/vpnclient/interceptor.c:127: error: &#8216;struct net_device&#8217; has no member named &#8216;hard_start_xmit&#8217;
/home/jon/Downloads/vpnclient/interceptor.c:128: error: &#8216;struct net_device&#8217; has no member named &#8216;get_stats&#8217;
/home/jon/Downloads/vpnclient/interceptor.c:129: error: &#8216;struct net_device&#8217; has no member named &#8216;do_ioctl&#8217;
/home/jon/Downloads/vpnclient/interceptor.c: In function &#8216;add_netdev&#8217;:
/home/jon/Downloads/vpnclient/interceptor.c:266: error: &#8216;struct net_device&#8217; has no member named &#8216;hard_start_xmit&#8217;
/home/jon/Downloads/vpnclient/interceptor.c:267: error: &#8216;struct net_device&#8217; has no member named &#8216;hard_start_xmit&#8217;
/home/jon/Downloads/vpnclient/interceptor.c: In function &#8216;remove_netdev&#8217;:
/home/jon/Downloads/vpnclient/interceptor.c:289: error: &#8216;struct net_device&#8217; has no member named &#8216;hard_start_xmit&#8217;
/home/jon/Downloads/vpnclient/interceptor.c: In function &#8216;handle_vpnup&#8217;:
/home/jon/Downloads/vpnclient/interceptor.c:366: error: macro "for_each_netdev" requires 2 arguments, but only 1 given
/home/jon/Downloads/vpnclient/interceptor.c:366: error: &#8216;for_each_netdev&#8217; undeclared (first use in this function)
/home/jon/Downloads/vpnclient/interceptor.c:366: error: (Each undeclared identifier is reported only once
/home/jon/Downloads/vpnclient/interceptor.c:366: error: for each function it appears in.)
/home/jon/Downloads/vpnclient/interceptor.c:370: error: expected &#8216;;&#8217; before &#8216;{&#8217; token
make[2]: *** [/home/jon/Downloads/vpnclient/interceptor.o] Error 1
make[1]: *** [_module_/home/jon/Downloads/vpnclient] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-24-generic'
make: *** [default] Error 2
Failed to make module "cisco_ipsec.ko".

```

---

