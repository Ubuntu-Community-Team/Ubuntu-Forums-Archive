---
title: "Feisty wireless issues"
date: 2007-08-07
forum: Networking &amp; Wireless
---

### Post by kaufman on 2007-08-07
This is my 2nd try...no response to the first post.
I have an IBM z60t with atheros wireless running Ubuntu 7.04 (dual boot). 
It seems to recognize the wireless card, because it has no trouble detecting 
networks and showing signal levels, and it even detects the security type 
and asks for the appropriate password, but it has never been able to connect 
to any of them…even unsecured networks. 
I tried using my spare usb Linksys adaptor and it did the same thing. 
It shows both adaptors (atheros and “unknown usb vendor specific”) and the 
neworks listed under them, if I try to connect, I get the little orbiting comet icon, 
and then nothing. I’m relatively new at Linux, but trying…just need a little help with this. 
Thanks in advance.

---

### Post by dmizer on 2007-08-07
need your chipset first.

for a pcmcia/pci card post the output of 
```
lspci
```
for a usb adapter, post the output of
```
lsusb
```

---

### Post by kaufman on 2007-08-08
Here 's the output from "lspci":

kaufman@kaufman-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 4 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5751M Gigabit Ethernet PCI Express (rev 11)
13:00.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)
14:00.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev b3)
14:00.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394 Controller (rev 08)
14:00.2 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 17)
and thank you for responding...

---

### Post by dmizer on 2007-08-08
this is your chipset:
AR5212

try this:
[http://ubuntuforums.org/showthread.php?t=213355](http://ubuntuforums.org/showthread.php?t=213355)

i found this by using the forum search function with the following as my search parameters:
atheros AR5212

---

### Post by kaufman on 2007-08-11
Doesn't sound like the same problem...mine recognizes the card...sees the networks....just won't connect to any of them. I tried it anyway, though...didn't make a difference.

---

### Post by DrScum on 2007-08-11
had a similar problem with a dell latitude and Netgear wireless card, followed the link and was able to solve the problem. Thanks for the help!

The link says to edit /etc/network/interfaces in a way that everything is commented out exept the lo interface.

Can anyone explain to me what I have done to solve the problem? I hate to follow instructions but having absolutely no clue what I am doing.

---

