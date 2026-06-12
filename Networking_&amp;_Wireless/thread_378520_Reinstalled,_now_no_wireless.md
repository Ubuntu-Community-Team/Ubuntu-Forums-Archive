---
title: "Reinstalled, now no wireless"
date: 2007-03-07
forum: Networking &amp; Wireless
---

### Post by lsutiger on 2007-03-07
OK. I reinstalled Ubuntu in order to do a dual boot. Boots fine, I had a wreless network card in the Network settings. It was not functional. I got it to work on the last install. I tried the ndiswrapper listed in this article:
Go Back  	   	Ubuntu Forums > Ubuntu Release Assistance  > Other Support Categories  > Tutorials & Tips
Reload this Page HOWTO: Broadcom 4318 Wireless Cards 
Now my wireless card doesn't even show up!
Here is the setup log:
```
Log of echo Script version: 0.1.2 
Wed Mar  7 02:05:50 2007

Script version: 0.1.2

Wed Mar  7 02:05:50 2007
----------------
Log of lspci 
Wed Mar  7 02:05:50 2007

0000:00:00.0 Host bridge: Silicon Integrated Systems [SiS] 760/M760 Host (rev 03)
0000:00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SG86C202
0000:00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS963 [MuTIOL Media IO] (rev 25)
0000:00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
0000:00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE]
0000:00:02.6 Modem: Silicon Integrated Systems [SiS] AC'97 Modem Controller (rev a0)
0000:00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] Sound Controller (rev a0)
0000:00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
0000:00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
0000:00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
0000:00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 91)
0000:00:06.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 02)
0000:00:0b.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
0000:00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
0000:00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
0000:00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
0000:00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
0000:01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760/761 PCI/AGP VGA Display Adapter

Wed Mar  7 02:05:50 2007
----------------
Log of echo /etc/issue MD5 sum: 3cb50a593ad7f171a5aa9f5803354aa2 
Wed Mar  7 02:05:50 2007

/etc/issue MD5 sum: 3cb50a593ad7f171a5aa9f5803354aa2

Wed Mar  7 02:05:50 2007
----------------
Log of echo Dapper final release detected. 
Wed Mar  7 02:05:50 2007

Dapper final release detected.

Wed Mar  7 02:05:50 2007
----------------
Log of rmmod ndiswrapper 
Wed Mar  7 02:05:50 2007

ERROR: Module ndiswrapper does not exist in /proc/modules
rmmod died with exit status 1

Wed Mar  7 02:05:50 2007
----------------
Log of rmmod bcm43xx 
Wed Mar  7 02:05:50 2007


Wed Mar  7 02:05:50 2007
----------------
Log of echo Dapper 
Wed Mar  7 02:05:50 2007

Dapper

Wed Mar  7 02:05:50 2007
----------------
Log of apt-get --assume-yes install ndiswrapper-utils 
Wed Mar  7 02:05:50 2007

Reading package lists...
Building dependency tree...
E: Couldn't find package ndiswrapper-utils
apt-get died with exit status 100

Wed Mar  7 02:05:50 2007
----------------
Log of ndiswrapper -e bcmwl5 
Wed Mar  7 02:05:50 2007

ndiswrapper: No such file or directory
ndiswrapper died with exit status 1

Wed Mar  7 02:05:50 2007
----------------
Log of ndiswrapper -e bcmwl5a 
Wed Mar  7 02:05:50 2007

ndiswrapper: No such file or directory
ndiswrapper died with exit status 1

Wed Mar  7 02:05:50 2007
----------------
Log of ndiswrapper -l 
Wed Mar  7 02:05:50 2007

ndiswrapper: No such file or directory
ndiswrapper died with exit status 1

Wed Mar  7 02:05:50 2007
----------------
Log of echo You appear to have an i386 system...installing the i386 drivers... 
Wed Mar  7 02:05:50 2007

You appear to have an i386 system...installing the i386 drivers...

Wed Mar  7 02:05:50 2007
----------------
Log of tar -xf drivers-32.tar.gz 
Wed Mar  7 02:05:50 2007


Wed Mar  7 02:05:50 2007
----------------
Log of ndiswrapper -i bcmwl5.inf 
Wed Mar  7 02:05:50 2007

ndiswrapper: No such file or directory
ndiswrapper died with exit status 1

Wed Mar  7 02:05:50 2007
----------------
Log of modprobe ndiswrapper 
Wed Mar  7 02:05:50 2007


Wed Mar  7 02:05:50 2007
----------------
Log of iwconfig 
Wed Mar  7 02:05:50 2007

lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.


Wed Mar  7 02:05:50 2007
----------------
Log of ifconfig 
Wed Mar  7 02:05:50 2007

eth0      Link encap:Ethernet  HWaddr 00:C0:9F:C0:23:F8  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:169 Base address:0x1800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:117 errors:0 dropped:0 overruns:0 frame:0
          TX packets:117 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:8960 (8.7 KiB)  TX bytes:8960 (8.7 KiB)


Wed Mar  7 02:05:50 2007
----------------
Log of iwlist scan 
Wed Mar  7 02:05:50 2007

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

sit0      Interface doesn't support scanning.


Wed Mar  7 02:05:50 2007
----------------
Log of echo Script version: 0.1.2 
Wed Mar  7 02:22:16 2007

Script version: 0.1.2

Wed Mar  7 02:22:16 2007
----------------
Log of lspci 
Wed Mar  7 02:22:16 2007

0000:00:00.0 Host bridge: Silicon Integrated Systems [SiS] 760/M760 Host (rev 03)
0000:00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SG86C202
0000:00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS963 [MuTIOL Media IO] (rev 25)
0000:00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
0000:00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE]
0000:00:02.6 Modem: Silicon Integrated Systems [SiS] AC'97 Modem Controller (rev a0)
0000:00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] Sound Controller (rev a0)
0000:00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
0000:00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
0000:00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
0000:00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 91)
0000:00:06.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 02)
0000:00:0b.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
0000:00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
0000:00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
0000:00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
0000:00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
0000:01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760/761 PCI/AGP VGA Display Adapter

Wed Mar  7 02:22:16 2007
----------------
Log of echo /etc/issue MD5 sum: 3cb50a593ad7f171a5aa9f5803354aa2 
Wed Mar  7 02:22:16 2007

/etc/issue MD5 sum: 3cb50a593ad7f171a5aa9f5803354aa2

Wed Mar  7 02:22:16 2007
----------------
Log of echo Dapper final release detected. 
Wed Mar  7 02:22:16 2007

Dapper final release detected.

Wed Mar  7 02:22:16 2007
----------------
Log of rmmod ndiswrapper 
Wed Mar  7 02:22:16 2007


Wed Mar  7 02:22:16 2007
----------------
Log of rmmod bcm43xx 
Wed Mar  7 02:22:16 2007

ERROR: Module bcm43xx does not exist in /proc/modules
rmmod died with exit status 1

Wed Mar  7 02:22:16 2007
----------------
Log of echo Dapper 
Wed Mar  7 02:22:16 2007

Dapper

Wed Mar  7 02:22:16 2007
----------------
Log of apt-get --assume-yes install ndiswrapper-utils 
Wed Mar  7 02:22:16 2007

Reading package lists...
Building dependency tree...
E: Couldn't find package ndiswrapper-utils
apt-get died with exit status 100

Wed Mar  7 02:22:16 2007
----------------
Log of ndiswrapper -e bcmwl5 
Wed Mar  7 02:22:16 2007

ndiswrapper: No such file or directory
ndiswrapper died with exit status 1

Wed Mar  7 02:22:16 2007
----------------
Log of ndiswrapper -e bcmwl5a 
Wed Mar  7 02:22:16 2007

ndiswrapper: No such file or directory
ndiswrapper died with exit status 1

Wed Mar  7 02:22:16 2007
----------------
Log of ndiswrapper -l 
Wed Mar  7 02:22:16 2007

ndiswrapper: No such file or directory
ndiswrapper died with exit status 1

Wed Mar  7 02:22:16 2007
----------------
Log of echo You appear to have an i386 system...installing the i386 drivers... 
Wed Mar  7 02:22:16 2007

You appear to have an i386 system...installing the i386 drivers...

Wed Mar  7 02:22:16 2007
----------------
Log of tar -xf drivers-32.tar.gz 
Wed Mar  7 02:22:16 2007

tar: drivers-32.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar died with exit status 2

Wed Mar  7 02:22:16 2007
----------------
Log of ndiswrapper -i bcmwl5.inf 
Wed Mar  7 02:22:16 2007

ndiswrapper: No such file or directory
ndiswrapper died with exit status 1

Wed Mar  7 02:22:16 2007
----------------
Log of modprobe ndiswrapper 
Wed Mar  7 02:22:16 2007


Wed Mar  7 02:22:16 2007
----------------
Log of iwconfig 
Wed Mar  7 02:22:16 2007

lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.


Wed Mar  7 02:22:16 2007
----------------
Log of ifconfig 
Wed Mar  7 02:22:16 2007

eth0      Link encap:Ethernet  HWaddr 00:C0:9F:C0:23:F8  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:169 Base address:0x1800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:183 errors:0 dropped:0 overruns:0 frame:0
          TX packets:183 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:14356 (14.0 KiB)  TX bytes:14356 (14.0 KiB)


Wed Mar  7 02:22:16 2007
----------------
Log of iwlist scan 
Wed Mar  7 02:22:16 2007

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

sit0      Interface doesn't support scanning.


Wed Mar  7 02:22:16 2007
----------------

```
I also blacklisted the 43xx driver that comes with Ubuntu, because it coes not work.
Could someone read that log and tell me what the problem is and how to resolve it?
Thanx in advance!
Jude

---

### Post by solar george on 2007-03-07
Have you tried [this]("http://www.ubuntuforums.org/showthread.php?t=197102")

---

### Post by lsutiger on 2007-03-07
Yep..thats where I started last time
Check this out:
```
complexity@complexity-laptop:~$ lspci | grep Broadcom\ Corporation
0000:00:0b.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

```

But it is not listed in network settings???!!!!?!?

```
 sudo ifdown eth1
ifdown: interface eth1 not configured
complexity@complexity-laptop:~$ sudo ifup eth1
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

SIOCSIFADDR: No such device
eth1: ERROR while getting interface flags: No such device
eth1: ERROR while getting interface flags: No such device
Bind socket to interface: No such device

```

Now it was in network settings before I ran the command at the page you sent me to ( which is where I was before you replied)
Appreciate any help you can give me!
jude

---

### Post by solar george on 2007-03-08
If the install has worked you should be seeing wlan0 not eth1

---

### Post by lsutiger on 2007-03-08
[Here are the steps I have taken]("http://ubuntuforums.org/showthread.php?t=378615") and now it works
Thanx for the reply!

---

