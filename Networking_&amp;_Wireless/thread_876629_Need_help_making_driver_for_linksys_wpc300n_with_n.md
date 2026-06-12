---
title: "Need help making driver for linksys wpc300n with ndiswrapper in 8.04"
date: 2008-07-31
forum: Networking &amp; Wireless
---

### Post by mnemonik on 2008-07-31
Hello, I've been having some issues trying to get my linksys wpc300n working with 8.04. I'm doing all this on a dual booting xp/ubuntu 8.04 dell inspiron 6000 and my only connection to the internet is through my wireless card so ubuntu is completely cut off. I managed to install ndiswrapper, all its utilities, and ndisgtk by following various guides; I copy pasted the blacklisting command; and I made a driver for my wireless card from the *.inf file in the windows driver, then tried to delete the extra *.sys files from the ndiswrapper folder but I get an "Error removing file: Permission denied" message. I googled the error and it seems most people had it with their trash, and what the needed to do was log in as a different user. Well, when I was installing Ubuntu I only made one account so I don't know what user I could login as to gain permission. Also, do I delete ALL the *.sys files, or do I keep the wpc300n.sys file (the other *.sys files are different wireless card models)? On top of all this when I run lspci all i get is broadcom stuff, nothing to do with linksys so I suspect that Ubuntu can't even recognize that the card is plugged in (the LED lights are off, but I had read that they don't work in linux).

thanks in advance. :)

---

### Post by cariboo on 2008-08-01
If you run:

```
lspci
```

You will probably see Broadcom in the output for your wireless card. Just because it says Linksys on your wireless doesn't mean it was manufactured by linksys. You may find a better solution if you specify the Broadcom chip number. 

Jim

---

### Post by mnemonik on 2008-08-01
```
mnemonik@mnemonik-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 915GM/PM Express PCI Express Root Port (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc M22 [Mobility Radeon X300]
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
03:01.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev b3)
03:01.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394 Controller (rev 08)
03:01.2 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 17)
03:03.0 Network controller: Intel Corporation PRO/Wireless 2915ABG Network Connection (rev 05)
04:00.0 Network controller: Broadcom Corporation BCM43XG (rev 01)


```

Edit: Does this help? It doesn't mean too much to me, but I do see broadcom. I just don't know if it is my ethernet, built in (and broken) wireless adapter, or the linksys card.

---

