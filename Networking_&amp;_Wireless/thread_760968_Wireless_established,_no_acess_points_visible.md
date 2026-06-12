---
title: "Wireless established, no acess points visible"
date: 2008-04-20
forum: Networking &amp; Wireless
---

### Post by MistaMatt90 on 2008-04-20
About a week ago, I decided to install Gutsy on an old laptop that my family has.  Upon the fresh install, Ubuntu detected and set up my wireless automatically.  It saw my home network (and networks of the neighbors) and I was able to connect to my network without any issues.  

Due to various reasons (unrelated to the Ubuntu install) I ended up formatting and installing again.  This time, the network manager sees that I have a wireless card, but doesn't list any available wireless networks--thus I cannot connect to any.

I've tried various things with ndiswrapper, but have had no luck.  Here some information:
```
matt@laptop:~$ lspci
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
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon RV250 [Mobility FireGL 9000] (rev 01)
02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5702X Gigabit Ethernet (rev 02)
02:01.0 CardBus bridge: O2 Micro, Inc. OZ711EC1 SmartCardBus Controller (rev 20)
02:01.1 CardBus bridge: O2 Micro, Inc. OZ711EC1 SmartCardBus Controller (rev 20)
02:03.0 Network controller: Intel Corporation PRO/Wireless LAN 2100 3B Mini PCI Adapter (rev 04)
``````
matt@laptop:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback
```

I think it very odd that an identical install on the same machine would yield a different result.  :confused:

Thanks for any help you can offer,
Matt

---

### Post by AndrewTheArt on 2008-04-20
I would wait a few days or Hardy Heron to come out, and install that. You can also try it now buy downloading the release candidate. It has vastly improved hardware compatibility, so it might just work with your card.

---

