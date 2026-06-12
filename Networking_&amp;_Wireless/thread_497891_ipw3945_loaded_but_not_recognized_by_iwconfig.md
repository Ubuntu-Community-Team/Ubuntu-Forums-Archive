---
title: "ipw3945 loaded but not recognized by iwconfig"
date: 2007-07-10
forum: Networking &amp; Wireless
---

### Post by msayag on 2007-07-10
Hi,
I am trying to get the wireless connection work on my new Lenovo 3000 N100 Laptop.
It works perfectly on the dual-boot Widows Vista but fails to work on Linux.
I am using Kubuntu 7.04 - Feisty Fawn.

I tried to follow the howto's and everything seems to be loaded ok but the interface is still disabled (not show by KNotworkManager nor by Network Settings panel)

```

$ lspci
.....
03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
.....

```

```

$lsmod | grep "ipw3945"
ipw3945               118816  0
ieee80211              34760  1 ipw3945

```

```

$ dmesg | grep Wireless
[   17.924000] ipw3945: Intel(R) PRO/Wireless 3945 Network Connection driver for Linux, 1.2.0mp
[   17.924000] ipw3945: Detected Intel PRO/Wireless 3945BG Network Connection

```

```

$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

$ iwconfig eth1
eth1      No such device

```

```

$ sudo ifup eth1
Password:
eth1: ERROR while getting interface flags: No such device
There is already a pid file /var/run/dhclient.eth1.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: No such device
eth1: ERROR while getting interface flags: No such device
eth1: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth1.

```

Thanks for your help

---

### Post by msayag on 2007-07-10
also

```

$ sudo lshw | grep 3945
Password:
                product: PRO/Wireless 3945ABG Network Connection
                configuration: driver=ipw3945 latency=0

```

---

### Post by msayag on 2007-07-12
Solved!
After struggling some more hours I found this post

[https://launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/62452]("https://launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/62452")
[https://launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/62452/comments/8]("https://launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/62452/comments/8")
> 
Roland Dreier  said on 2006-09-29:

I believe I had a similar problem with the default Edgy install on my ThinkPad X60s, which has ipw3945 wireless. After the install, there was no wireless network interface, even though the ipw3945 kernel module was loaded.

I noticed that there was no ipw3945d binary blob running in userspace. This was because ipw3945d is in the restricted modules package, which is not installed by default. After installing linux-restricted-modules-generic and reloading ipw3945, eth1 magically appeared and worked fine.

So I guess the resolution to this issue is to make sure that ipw3945d is installed on systems that use ipw3945.


I figured out that when I upgraded the kernel from 2.6.20-15 to 2.6.20-16 this module was not upgraded as it should.

Solution:
Uninstalled linux-restricted-module-2.6.20-15-generic 
Installed linux-restricted-module-2.6.20-16-generic 
reboot

Look Ma, No wires :)

---

### Post by dracomordag on 2007-07-27
david@bluenote:~$ sudo apt-get install linux-restricted-module-2.6.20-16-genericReading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package linux-restricted-module-2.6.20-16-generic

?

---

