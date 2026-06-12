---
title: "Need to connect using wireless in Ubuntu 9.10"
date: 2009-12-09
forum: New to Ubuntu
---

### Post by tbullock17 on 2009-12-09
I installed ubuntu 9.10 on dell inspiron 2200.  all previous operating systems were erased before installing 9.10.

9.10 is working fine using a wired connection.  How do I activate the wireless?  How do I find out if I have a needed driver?

I am a beginner in both ubuntu and wireless.  Is there a web page with wireless installation instructions for 9.10?

thanks to all who help!!  ;)

---

### Post by nothingspecial on 2009-12-09
Open a terminal and post the output of ```
sudo lshw -C network
``` here.

---

### Post by chf on 2009-12-09
hello,

do you have activated the proprietary hardware drivers?

System--> Administration --> Hardware Drivers

There you need to activate the drivers. I had the same problem on a dell some days ago.


best regards

chf

---

### Post by lotharmat on 2009-12-09
also, can you post the output of 

```
lspci
```

and

```
lsusb
```

run both of these commands in the terminal

applications-->accessories-->terminal

---

### Post by tbullock17 on 2009-12-10
> **nothingspecial said:**
> Open a terminal and post the output of ```
sudo lshw -C network
``` here.


Here is the results of running the above command:
  *-network:0             
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@0000:02:03.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64
       resources: irq:19 memory:dfdfe000-dfdfffff
  *-network:1
       description: Ethernet interface
       product: 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller Mobile
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: eth0
       version: 03
       serial: 00:12:3f:f5:f8:bb
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=full firmware=N/A ip=129.74.212.218 latency=64 link=yes maxlatency=56 mingnt=8 multicast=yes port=MII speed=100MB/s
       resources: irq:20 memory:dfdfd000-dfdfdfff ioport:df40(size=64)
  *-network DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:14:a4:2f:3a:6d
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg

Thank you very much!  Now I know I have a driver and that it is disabled.  I will see if I can enable it.  Very kind of you to help me with this command.  I appreciate it very much.

Tom

---

### Post by tbullock17 on 2009-12-10
> **chf said:**
> hello,

do you have activated the proprietary hardware drivers?

System--> Administration --> Hardware Drivers

There you need to activate the drivers. I had the same problem on a dell some days ago.


best regards

chf
Your problem was mine too.  Thanks for pointing this out.  Using your instruction I have successfully activated my driver.
Thank you very much!  I do appreciate your sharing your experience.  It really helped me.

Tom

---

### Post by tbullock17 on 2009-12-10
> **lotharmat said:**
> also, can you post the output of 

```
lspci
```and

```
lsusb
```run both of these commands in the terminal

applications-->accessories-->terminal

Here is the output of lspci:
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
02:01.0 CardBus bridge: Texas Instruments PCI1510 PC card Cardbus Controller
02:03.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
02:08.0 Ethernet controller: Intel Corporation 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller Mobile (rev 03)

Here is the output of lsusb:

Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Thanks for asking for this information.  I see it tells me I have a Broadcom wireless controller.  Is there anything else I should be learning from this output?

I appreciate your taking the time to help me.

Considering the results from the prior to responders to this thread and my replies, do you think I need to do anything further before attempting to create a connection to a wireless network?

Thanks for your help, much appreciated.

Tom

---

### Post by lotharmat on 2009-12-10
> **tbullock17 said:**
> Here is the output of lspci:
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
02:01.0 CardBus bridge: Texas Instruments PCI1510 PC card Cardbus Controller
02:03.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
02:08.0 Ethernet controller: Intel Corporation 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller Mobile (rev 03)

Here is the output of lsusb:

Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Thanks for asking for this information.  I see it tells me I have a Broadcom wireless controller.  Is there anything else I should be learning from this output?

I appreciate your taking the time to help me.

Considering the results from the prior to responders to this thread and my replies, do you think I need to do anything further before attempting to create a connection to a wireless network?

Thanks for your help, much appreciated.

Tom

If enabling the hardware proprietary drivers worked and you can now see your wireless network then it sounds like you are good to go!

Have fun!

---

### Post by chf on 2009-12-10
@Tom

you are welcome!

best regards

chf

---

### Post by woodnymph on 2009-12-12
if the above did not work for you, check here:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

---

### Post by tbullock17 on 2009-12-13
To all who were kind enough to reply to my request for help:

This is just to  confirm that your suggests did in fact lead to solving my wireless driver concerns.  This final message (thread can now be closed) is being sent using the wireless network from within ubuntu 9.10.

Thanks again to all of you.  This forum, and people like you who make it a reality, is a wonderful  idea to offset the feelings of being alone and lost for those of us who are learning in isolation from a class or the support of an experienced teacher.  You guys are just great!

Tom

---

