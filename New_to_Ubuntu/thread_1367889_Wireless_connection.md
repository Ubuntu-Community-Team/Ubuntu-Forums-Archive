---
title: "Wireless connection"
date: 2009-12-30
forum: New to Ubuntu
---

### Post by newbcake on 2009-12-30
i have using a dell inspiron 9200 >.>.i recently installed ubuntu on to it  and im facing problems with the wirless internet and graphic card.because iam a total noon and dont know crap about ubuntu i need help and fast.first of all i can connect to a wireless network but i cant surf the web .i am connected but there are no sites opening on firefox. also the graphic card problem i dont know if i have that yet but many people have it with ati cards im using ati mobility radeon 9700 and ive heard people talking about its driver problems is there a way to fix that ? i jsut installed ubuntu yesterday so i dont know if im having that problem. i need the graphic card working kos i play lots of games mainly WoW so please help me
:lolflag:

---

### Post by Paqman on 2009-12-30
If you plug directly into the router with an ethernet cable, can you browse the web? Have you installed any wifi drivers the system suggests? Do you know what kind of wifi chipset your machine has?

---

### Post by newbcake on 2009-12-30
i dont connect a cable to my laptop to connect to the inter i have a router.the internet does get conncted it detects the signal and connects but when i try to open a web site it doesnt load =s

---

### Post by Paqman on 2009-12-30
Can you copy this into a terminal and post the output:
```
lspci
```

---

### Post by 3rdalbum on 2009-12-30
> **newbcake said:**
> i dont connect a cable to my laptop to connect to the inter i have a router.the internet does get conncted it detects the signal and connects but when i try to open a web site it doesnt load =s

Go to the Network Manager applet (where you connect to your network) and right-click the icon. Go to Edit Connections and locate where your network's entry is in this window. Click it and click Edit, and go across to the IPv4 tab.

Change the method to "Automatic (DHCP) Addresses Only" and input the following as your DNS:

```
208.67.220.220
```

Try connecting now, and see if you can access websites. This DNS is free for community use (it's OpenDNS).

---

### Post by 3rdalbum on 2009-12-30
As for the graphics drivers: ATI doesn't make drivers for your 9700 anymore. Ubuntu contains open-source drivers for the cards that ATI has abandoned, and these drivers will be loaded automatically.

You might not have 3D acceleration with the open-source driver. You might, though - if your menus fade in and out and you see animations when you open and close a window, then you have 3D acceleration. You can try WoW.

If there's no 3D acceleration, then you can't play any 3D games.

The solution? Downgrade to Ubuntu 8.04 where ATI's old driver still works, or replace your graphics card with something a bit more modern, that ATI still supports. (or better yet, get an Nvidia card).

---

### Post by newbcake on 2009-12-30
i have tried the DNS u gave me. at first firefox wasnt loading any thing some tiems u wait and it keeps loading thengives the intenetprob message but after tryingthe new one i have to wait along time and still the site doesnt load -.-. alsohow do i check if i have 3d hardware acceleration. themens are fading and i can see animations when i openfire fox and other programs but i want to be sure.

---

### Post by newbcake on 2009-12-30
when i put the command in to the terminal this is what i got :

   00:00.0 Host bridge: Intel Corporation 82855PM Processor to I/O Controller (rev 03)
  00:01.0 PCI bridge: Intel Corporation 82855PM Processor to AGP Controller (rev 03)
  00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
  00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
  00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
  00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
  00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 81)
  00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 01)
  00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 01)
  00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
  00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 01)
  01:00.0 VGA compatible controller: ATI Technologies Inc RV350 [Mobility Radeon 9600 M10]
  02:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
  02:01.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev b3)
  02:01.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394 Controller (rev 08)
  02:01.2 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 17)
  02:03.0 Network controller: Intel Corporation PRO/Wireless LAN 2100 3B Mini PCI Adapter (rev 04)

---

### Post by newbcake on 2009-12-30
that smileyis actually 8 ) without the space

---

