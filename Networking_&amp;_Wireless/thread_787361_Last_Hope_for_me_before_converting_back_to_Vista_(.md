---
title: "Last Hope for me before converting back to Vista :( (Please Help)"
date: 2008-05-08
forum: Networking &amp; Wireless
---

### Post by coldopm on 2008-05-08
I cannot figure out how to pickup the wireless signal in Hardy. Can anyone help me get it running please???

---

### Post by tamoneya on 2008-05-08
```
lshw -C network
```

---

### Post by MaindotC on 2008-05-08
Is your wireless card even working?

---

### Post by coldopm on 2008-05-08
Yes wireless works. In vista anyways.

---

### Post by coldopm on 2008-05-08
Everything else in Hardy is great, but I really need to get my wireless running. Anyone out there that can offer any assistance?

---

### Post by MaindotC on 2008-05-08
I don't mean in Vista, I mean is it detected in Hardy.  Can you post the output of tamoneya's command?  Is there a light indicator showing when the wireless card is working in Vista and if so, does it light up in Hardy?

---

### Post by coldopm on 2008-05-09
Yes sorry I got a bunch of threads going with the same issue, desperate for a solution.

coldopm@coldopm-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 12
       serial: 00:1d:09:41:ce:4b
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.20 firmware=N/A ip=24.67.91.177 latency=0 module=sky2 multicast=yes
  *-network UNCLAIMED
       description: Network controller
       product: BCM4310 USB Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
coldopm@coldopm-laptop:~$

---

### Post by moopere on 2008-05-09
I can't see a wireless card in that listing...might be wrong though.  How about the output of:

lspci

This might show something up.  Is your wireless 'card' a usb dongle by any chance?  If so, try 

lsusb

Regards,
Craig

---

### Post by coldopm on 2008-05-09
> **moopere said:**
> I can't see a wireless card in that listing...might be wrong though.  How about the output of:

lspci

This might show something up.  Is your wireless 'card' a usb dongle by any chance?  If so, try 

lsusb

Regards,
Craig

*-network UNCLAIMED
description: Network controller
product: BCM4310 USB Controller
vendor: Broadcom Corporation

I believe?

Here is lspci

-----

coldopm@coldopm-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
02:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
02:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
02:09.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
02:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
02:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
09:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller (rev 12)
0b:00.0 Network controller: Broadcom Corporation BCM4310 USB Controller (rev 01)
coldopm@coldopm-laptop:~$ 

----

and lsusb

----

coldopm@coldopm-laptop:~$ lsusb
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
coldopm@coldopm-laptop:~$

---

### Post by coldopm on 2008-05-09
Do any of these outputs help anyone?

---

### Post by trdc on 2008-05-09
Have a read of [this]("http://www.colinblog.com/2008/04/how-to-install-broadcom-bcm4310-usb.html") and let us know how you go.

---

### Post by MaindotC on 2008-05-09
the output from lsusb is all 0's so that tells me you don't have any USB devices plugged in - I think he wanted to know that in the event your card was USB-connected.  The lspci shoes:

```

0b:00.0 Network controller: Broadcom Corporation BCM4310 USB Controller (rev 01)

```

Which tells me it detects your WLAN card so it doesn't seem to be a hardware issue.  However, please check the manufacturer website for the latest version of your BIOS to eliminate that as a possibility.  The thread trdc provided seems helpful - not a big fan of ndiswrapper but I hope it helps you.

If that doesn't work, there are some drivers you can download through the repositories and we'll advise you if the trdc thread doesn't work for you.  I'm going to bed, ttyl.

---

### Post by SurferGTO on 2008-05-16
just got mine working. follow this thread hopefully it works.

[http://ubuntuforums.org/showthread.php?t=794816&page=2]("http://ubuntuforums.org/showthread.php?t=794816&page=2")

specifically there is a link for a "hack" that you should check out. thats what got it for me. otherwise i was having the identical problem of the driver and ndiswrapper installing fine, but not having it actually recognize the hardware. 

go to system>admin>windows wireless drivers.

does it list the driver but hardware present: NO?

do that hack and it should make the hardware recognized. thats all it took for me.

also, i had to use WICD rather than network manager or wifi-radar. point and click connection.

---

