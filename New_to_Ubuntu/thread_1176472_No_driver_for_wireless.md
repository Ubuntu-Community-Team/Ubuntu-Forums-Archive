---
title: "No driver for wireless"
date: 2009-06-02
forum: New to Ubuntu
---

### Post by AutumnPhoenix on 2009-06-02
I posted this in the upgrade forum but I'm thinking now that it's not a real upgrade problem but a driver one.

It occured during my upgrade to Jaunty

I get a no wireless extentions when I run > iwconfig

I have no ability to connect through a land-line, I only have wireless acess.

HELP

I'm still quite a n00b and I need to get some work stuff done.

---

### Post by 3rdalbum on 2009-06-02
Can you please run lspci and lsusb in a terminal for us so we know what wireless card you're using?

---

### Post by AutumnPhoenix on 2009-06-02
lspci 
> 00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03) 
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
14:00.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev b3) 
14:00.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394 Controller (rev 08) 
14:00.2 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 17) 
14:00.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 08) 
14:02.0 Ethernet controller: Atheros Communications Inc. AR5212 802.11abg NIC (rev 01) 

 lsusb 
> Bus 001 Device 003: ID 12f7:1e23 Memorex Products, Inc. TravelDrive 2007 Flash Drive 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 004 Device 002: ID 0483:2016 SGS Thomson Microelectronics Fingerprint Reader 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

---

### Post by bumanie on 2009-06-02
[This]("http://www.ubuntugeek.com/atheros-5007eg-with-madwifi-on-i386-platform.html/comment-page-2") may help as long as you are running the 32 bit version.

---

### Post by AutumnPhoenix on 2009-06-02
I don't know what version I'm running but I can't use those commands becuase they require an internet connection on that computer.  I don't have an internet connect, so I'd have to download it to a USB then copy the file somehow.

I do believe I tried to use madwifi in the past but it didn't really work.  Isn't it just a program to find wireless?

I have Wicd Network Manager (when my wireless is working) and has by far been the best program I've ever used.

But my little antenna light isn't even sparking on when I hit "refresh"....so I'm inclined to believe it is a driver problem.

---

### Post by bumanie on 2009-06-02
Someone else may know more, but that is the only driver I could find for that card. Re no internet, is it possible to go to a friend's or something and 'borrow' their wired connection for a short time while you find a driver? Sorry I could not be more helpful.

---

### Post by AutumnPhoenix on 2009-06-02
thanks.

I have also tried adding iwlagn to sudo nano /etc/modules but it was worthless.  

Unfortunatly, I'm a vicitm of the digitial age and I don't have acess to a wired connection.

---

### Post by AutumnPhoenix on 2009-06-02
also when I ran

sudo /etc/init.d/networking restart
 it told me that I alredy had a pid file

however
> set failed on device ath0 ; no such device

---

