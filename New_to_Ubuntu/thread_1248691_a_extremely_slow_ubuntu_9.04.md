---
title: "a extremely slow ubuntu 9.04"
date: 2009-08-24
forum: New to Ubuntu
---

### Post by shreyanshjain8 on 2009-08-24
:confused::confused:
i have just now made a fresh installation of ubuntu 9.04 and now my system is running very very slow.. even system monitor is also always showing more than 50% of system process in use.....

before i was having ubuntu 8.04 and that was stunning fast.... 
i feel like crying after installing 9.04...

plzz help me out ...!!

urgent...!!

thanx in advance

---

### Post by zkriesse on 2009-08-24
Hmm.....not sure what that is all about. Do you have an Intel Graphics driver card?

---

### Post by shreyanshjain8 on 2009-08-24
:confused::confused::confused::confused:

plzzzzzz anyone reply me.....

i just installed it freshely .. i havn't installed anything yet and still its crawling like a snail... its very slow... plzzz anybody tell me any solution .. else i need to install 8.10 again...

---

### Post by shreyanshjain8 on 2009-08-24
shreyansh@shreyansh-laptop:~$ lspci
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
02:09.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
02:09.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
09:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller (rev 12)
0b:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
shreyansh@shreyansh-laptop:~$

---

### Post by zkriesse on 2009-08-24
Ok my man, looks like you have nothing but Intel on your system. Intel is not exactly the best with Jaunty. But don't give up hope yet! Go back to the version that worked for you and when Karmic Koala releases it should work for the Intel pc's.

---

### Post by shreyanshjain8 on 2009-08-24
:confused:
hey jack i have posted my lspci output.. its a intel..  :-(

---

### Post by zkriesse on 2009-08-24
Yes. I saw...did you read my post?

---

### Post by shreyanshjain8 on 2009-08-24
which post... can u paste the link here ...which can help me... :-(

---

### Post by zkriesse on 2009-08-24
Look at my signature....

---

