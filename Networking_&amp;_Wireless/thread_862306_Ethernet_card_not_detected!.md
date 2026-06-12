---
title: "Ethernet card not detected!"
date: 2008-07-17
forum: Networking &amp; Wireless
---

### Post by Velvet Ghost on 2008-07-17
I've just installed an ethernet card on an old P4 desktop, which did not have one previously. Then, I formatted the hard disk and installed Ubuntu 8.04. However, it seems that the ethernet card was not detected. When I try pppoeconf (I have an ADSL connection), it says eth0 was not found and ifconfig shows only the loopback adapter and no eth0. Same problem with Fedora 9, haven't tried Windows yet. The card is seated perfectly in the PCI slot. I checked that multiple times, and also tried another PCI slot. The DSL modem is working perfectly, since I use the internet with that same modem on my laptop. Any ideas as to what could be wrong? Thanks.

---

### Post by chili555 on 2008-07-17
Perhaps it has not yet associated a correct driver. Maybe we can help. Please post:```
sudo lshw -C network
```Thanks.

---

### Post by Velvet Ghost on 2008-07-21
I ran the command. Here's the output:

atriya@atriya-desktop:~$ sudo lshw -C network
  *-network UNCLAIMED     
       description: Ethernet controller
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 10
       width: 32 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0 maxlatency=64 mingnt=32

Thanks for offering to help.

---

### Post by dntuan on 2008-07-21
command, wifi not correct driver, Lan link OK. Please help me!
 *-network               
       description: Cisco Systems
       physical id: 0
       version: 340 Series Wireless LAN Adapter
       slot: Socket 0
       resources: irq:3
  *-network
       description: Ethernet interface
       product: 82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: eth0
       version: 42
       serial: 00:d0:59:b6:92:ef
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation

---

### Post by Velvet Ghost on 2008-07-21
dntuan, I can see that you are new to the forums. Posting your own question is somebody else's thread is called thread 'hijacking' and is considered to be very rude. Kindly start your own thread. Welcome to the forums!

---

### Post by falcon61102 on 2008-07-21
Based on you post it looks like you don't have any drivers installed for the card which is why it's not being recognized.  

I'm not sure if Realtek supports linux with drivers, but I'd check that first and foremost but being that Ubuntu hasn't recognized it to this point, I'm guessing that's going to be a no.

In that case you should be able to use ndiswrapper to install WinXP drivers for your network card.

---

### Post by chili555 on 2008-07-22
A driver is included in the kernel. Please do:```
sudo modprobe 8139too
sudo lshw -C network
```Does your network card now have a driver and logical name such as eth0? If so, be sure the ethernet cable is attached and try:```
sudo dhclient eth0
```Thanks.

---

### Post by Velvet Ghost on 2008-07-22
chili555, I followed your instructions but they didn't work. See for yourself:

atriya@atriya-desktop:~$ sudo modprobe 8139too
[sudo] password for atriya: 
atriya@atriya-desktop:~$ sudo lshw -C network
atriya@atriya-desktop:~$ sudo dhclient eth0
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFADDR: No such device
eth0: ERROR while getting interface flags: No such device
eth0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device

Any more ideas? Could it be a hardware problem after all, even though linux is apparently 'detecting' the card?

Thanks.

---

### Post by chili555 on 2008-07-22
> atriya@atriya-desktop:~$ sudo lshw -C networkWhat did this tell us after you modprobed 8139too?> Could it be a hardware problem after allIt certainly could. The hardware could be defective.

---

### Post by Velvet Ghost on 2008-07-22
Well, after the 'lshw -C network' it said:

pci (sysfs) - for 2 seconds.

Then that vanished, and 'SCSI' and 'framebuffer devices' was flashed rapidly in it's place, almost too rapidly to be read. Then I got the $ again, no resultant output.

---

### Post by falcon61102 on 2008-07-22
Yeah, it's not recognizing your card at all.  Those were just the places it was looking for that you saw flashing up there.  It didn't find any hardware that it recognizes to be network related.

If you run:
```
lshw
```
and give it a minute, you will have a list of the hardware that is PCI/SCSI related.  If it's not listed in there somewhere, possibly as something else, then I'm going to have to agree that it may be the hardware.

---

