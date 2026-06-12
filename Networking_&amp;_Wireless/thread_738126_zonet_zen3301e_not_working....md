---
title: "zonet zen3301e not working..."
date: 2008-03-28
forum: Networking &amp; Wireless
---

### Post by techknow on 2008-03-28
I just installed a new zonet gigabit ethernet card in my ubuntu box but I am unable to use it. I see it listed in the network interface list as RTL-8169 Gigabit Ethernet by Realtek Semiconductor Co.
When I plug my ethernet cable into the card the light indicating 100/1000 connection is lit up for a second or two, then it goes away. On plugging the cable into the card when the system is fully booted, I get nothing.

I have an intel ethernet adaptor already in the machine, its an integrated one but I'd doubt that its whats causing the problem.

I have my lspci output here  
```
00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 01)
00:01.0 PCI bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE Host-to-AGP Bridge (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation NV44A [GeForce 6200] (rev a1)
02:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet (rev 10)
02:02.0 Communication controller: Conexant HSF 56k Data/Fax/Voice/Spkp Modem (rev 01)
02:08.0 Ethernet controller: Intel Corporation 82801DB PRO/100 VE (LOM) Ethernet Controller (rev 81)
```


any help you guys can give me I would really appreciate. I hope that I can get this card working, else all my cabling and other work to get a gigabit network going is for nothing. :/

Cheerss

TechKnow

---

