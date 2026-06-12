---
title: "cannot create a wireless network..."
date: 2008-10-15
forum: Networking &amp; Wireless
---

### Post by mattlloyd on 2008-10-15
so in installed my linksys WMP54GS desktop wireless card in my desktop in the hopes of creating a wireless network from it and share its internet connection... the card appears to be working, but when i click on 'Create Wireless Network' it fails... a new network does appear containing at least 20 mismatched letters but it is not accessible and not controllable via the host. What am I missing?

---

### Post by Ayuthia on 2008-10-15
Can you post the results of (from the Terminal):
```
lspci -nn
lshw -C network
```

Also, please let us know which version of Ubuntu you are using.  If you are not for sure, please post the results of:
```
uname -a
```

Linksys uses various chipsets so I just want to see which one yours has.

---

### Post by mattlloyd on 2008-10-15
lspci -nn outputs:
```
00:00.0 Host bridge [0600]: Intel Corporation 82845 845 [Brookdale] Chipset Host Bridge [8086:1a30] (rev 03)
00:01.0 PCI bridge [0604]: Intel Corporation 82845 845 [Brookdale] Chipset AGP Bridge [8086:1a31] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev 12)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801BA ISA Bridge (LPC) [8086:2440] (rev 12)
00:1f.1 IDE interface [0101]: Intel Corporation 82801BA IDE U100 Controller [8086:244b] (rev 12)
00:1f.2 USB Controller [0c03]: Intel Corporation 82801BA/BAM USB Controller #1 [8086:2442] (rev 12)
00:1f.3 SMBus [0c05]: Intel Corporation 82801BA/BAM SMBus Controller [8086:2443] (rev 12)
00:1f.4 USB Controller [0c03]: Intel Corporation 82801BA/BAM USB Controller #1 [8086:2444] (rev 12)
01:00.0 VGA compatible controller [0300]: nVidia Corporation NV11 [GeForce2 MX/MX 400] [10de:0110] (rev b2)
02:08.0 Ethernet controller [0200]: Intel Corporation 82801BA/BAM/CA/CAM Ethernet Controller [8086:2449] (rev 03)
02:0a.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 03)
02:0b.0 Multimedia audio controller [0401]: Creative Labs SB Live! EMU10k1 [1102:0002] (rev 08)
02:0b.1 Input device controller [0980]: Creative Labs SB Live! Game Port [1102:7002] (rev 08)

```
lshw -C network outputs:
```
WARNING: you should run this program as super-user.
  *-network:0             
       description: Ethernet interface
       product: 82801BA/BAM/CA/CAM Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: eth0
       version: 03
       serial: 00:03:47:c9:5c:68
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI firmware=N/A ip=192.168.1.100 latency=32 maxlatency=56 mingnt=8 module=e100 multicast=yes
  *-network:1
       description: Wireless interface
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: a
       bus info: pci@0000:02:0a.0
       logical name: wlan0
       version: 03
       serial: 00:0f:66:f4:76:a0
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.52+ASUS,03/22/2004, 3.60.7.0 latency=32 module=ndiswrapper multicast=yes wireless=IEEE 802.11g

```

---

### Post by Ayuthia on 2008-10-15
does the following produce any error messages:
```
dmesg|grep ndiswrapper
```
Are you able to see wireless networks, but cannot connect?  Is your router encrypted?  If so, you might try to remove the encryption and see if you can connect.  It will let us know if the issue is with the ndiswrapper module or if it is an encryption issue.

Are you using Hardy?  If so, have you ever tried the b43 driver?

---

### Post by mattlloyd on 2008-10-16
dmesg|grep ndiswrapper outputs:
```
[   48.442610] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[   48.547324] usbcore: registered new interface driver ndiswrapper
[   57.056234] usbcore: deregistering interface driver ndiswrapper
[   57.085281] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[   57.136408] ndiswrapper: driver bcmwl5 (ASUS,03/22/2004, 3.60.7.0) loaded
[   57.145390] ndiswrapper: using IRQ 17
[   57.503064] usbcore: registered new interface driver ndiswrapper

```

so far i cannot connect, and no encryption on the router.  I am using Hardy, but I've not heard of that driver... this is my second failed attempt with this driver though :P

---

### Post by Ayuthia on 2008-10-16
The b43 driver is the one that can be found in System->Administration->Hardware Drivers.  It will require a working internet connection to make it work.  If you can install it that way, once it is complete, you will need to do the following:
```
sudo modprobe -r b43 ssb ndiswrapper bcm43xx
sudo modprobe b43
sudo iwlist scan
```
This will reset the wireless modules, load the b43 module, and then scan for wireless sites.  If it works, you will need to blacklist the ndiswrapper module.

---

