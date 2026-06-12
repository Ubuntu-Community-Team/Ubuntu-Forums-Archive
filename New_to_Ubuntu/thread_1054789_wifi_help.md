---
title: "wifi help"
date: 2009-01-30
forum: New to Ubuntu
---

### Post by acespade on 2009-01-30
hi ubuntu i just installed kubuntu 7.10 to my comp. and fully took windows off. (oops) probably not so smart huh?? well im trying to get my wifi to work but im having trouble. i went to dells web site and downloaded the driver for my wireless card and its in my kubuntu documents. how do i install it?? any help? thanx

---

### Post by Crafty Kisses on 2009-01-30
First off, what kind of wireless card is it? Once we have that bit of information I or someone else can help your further.

---

### Post by acespade on 2009-01-30
i'm thinking its a broadcam wireless card

---

### Post by acespade on 2009-01-30
broadcom

---

### Post by Crafty Kisses on 2009-01-30
I'm going to need more then that, so here's what I want you to do: Open up the Terminal by going to KMenu->System->Konsole, then when you see the prompt, enter this command:
```
lspci
```
Once it has gave you an output of that, please post it back here at the forums so I or someone can help you a bit further.

---

### Post by acespade on 2009-01-30
brett@brett-laptop:~$ lspci   
00:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge
00:01.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx)
00:05.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 1)
00:07.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 3)
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] AddressMap
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS690M [Radeon X1200 Series]
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
03:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
03:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
03:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
0b:00.0 Network controller: Broadcom Corporation BCM4306 802.11a Wireless LAN Controller (rev 03)
brett@brett-laptop:~$

---

### Post by Crafty Kisses on 2009-01-30
OK good deal, so this is the wireless card you have:
```
Broadcom Corporation BCM4306 802.11a Wireless LAN Controller (rev 03)
```Since I have that piece of information, I'm going to ask you to read this link: [http://ubuntuforums.org/showthread.php?t=340689](http://ubuntuforums.org/showthread.php?t=340689). Follow that persons instructions, and if that doesn't work, I will assist you further.

---

### Post by acespade on 2009-01-30
ok thanks watch for me ill let you kno wut happens

---

### Post by acespade on 2009-01-30
not much help he used xubuntu things wernt happing the way he described

---

