---
title: "can't get broadcom wireless to work with 8.10"
date: 2009-04-17
forum: New to Ubuntu
---

### Post by smitty65 on 2009-04-17
I can't get my wireless to work-i've tried to snoop around the forums but haven't come up with it yet. Please Help--List

:00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 03)
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 82)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 02)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 02)
02:01.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)
02:04.0 CardBus bridge: Texas Instruments PCI1510 PC card Cardbus Controller
 *-network               
       description: Ethernet interface
       product: BCM4401 100Base-T
       vendor: Broadcom Corporation
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: wlan0
       version: 01
       serial: 00:0d:56:b4:60:c6
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=ndiswrapper+b44win driverversion=1.53+Broadcom,11/21/2006, 4.60.0 ip=192.168.1.114 latency=32 module=ndiswrapper multicast=yes
~$ lshw -c network

 *-network               
       description: Ethernet interface
       product: BCM4401 100Base-T
       vendor: Broadcom Corporation
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: wlan0
       version: 01
       serial: 00:0d:56:b4:60:c6
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=ndiswrapper+b44win driverversion=1.53+Broadcom,11/21/2006, 4.60.0 ip=192.168.1.114 latency=32 module=ndiswrapper multicast=yes

 *-network               
       description: Ethernet interface
       product: BCM4401 100Base-T
       vendor: Broadcom Corporation
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: wlan0
       version: 01
       serial: 00:0d:56:b4:60:c6
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=ndiswrapper+b44win driverversion=1.53+Broadcom,11/21/2006, 4.60.0 ip=192.168.1.114 latency=32 module=ndiswrapper multicast=yes

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:476 (476.0 B)  TX bytes:476 (476.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:0d:56:b4:60:c6  
          inet addr:192.168.1.114  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20d:56ff:feb4:60c6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2104 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1674 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2367119 (2.3 MB)  TX bytes:320267 (320.2 KB)
          Interrupt:7 Memory:fcffe000-fd000000

---

### Post by 73ckn797 on 2009-04-17
Go to System/Administration/Synaptic Package Manager.

In Synaptic Package Manager look for "ndisgtk". selecting that will also load the other necessary ndiswrapper files. Once installed you will find it under System/Administration as wireless drivers. Insert the CD that came with the card and copy the WINXP directory from the drivers directory to your download or document directory.

Open the new program and from there select the *.inf file from the directory you copied off of the disk. Once that is completed reboot your system. You may have to re-enter any password(s) for the wireless access.

This solution was for a different wireless card but ought to work since "ndiswrapper" is what is used to install Windows drivers for hardware in Ubuntu/Linux.

---

### Post by ptn107 on 2009-04-17
I have the same card.  System -> Administration -> Hardware Drivers worked for me.

---

### Post by fly-by-night on 2009-04-17
In your post I only see BCM4401.  

But in this post -
[http://ubuntuforums.org/showthread.php?p=7059121](http://ubuntuforums.org/showthread.php?p=7059121)

the poster had BCM4401 for Ethernet and BCM4318 [AirForce One 54g] for Wireless chipset.  Read the last post there.  It might be that your wired but not wireless is installed correctly.

Run those commands mentioned and see if you can find your chipset.
Then you can search for the "correct" chipset (assuming it's the same). 

Just a suggestion.  Good luck.

---

