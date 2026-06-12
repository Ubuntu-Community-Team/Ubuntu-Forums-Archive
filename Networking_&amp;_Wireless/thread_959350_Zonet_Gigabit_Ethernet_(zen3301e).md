---
title: "Zonet Gigabit Ethernet (zen3301e)"
date: 2008-10-26
forum: Networking &amp; Wireless
---

### Post by techknow on 2008-10-26
I have a Zonet Gigabit Ethernet card (model number zen3301e) which I am trying to use with Ubuntu. I posted back in March this year asking for help but unfortunately I couldn't get any. I havn't been able to resolve this issue myself in the last few months so I was wondering if you guys have any ideas on how I can fix this. 

The card shows up in the network list although it is greyed out as Realtek RT-8169 Gigabit Ethernet. When I try and plug my ethernet cable into it nothing happens and I can't get network access. I know its not the cable as the on-board network card works.

The following is my lspci output if that helps. 
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
02:02.0 Communication controller: Conexant Systems, Inc. HSF 56k Data/Fax/Voice/Spkp Modem (rev 01)
02:08.0 Ethernet controller: Intel Corporation 82801DB PRO/100 VE (LOM) Ethernet Controller (rev 81)

```

I'd _really_ appreciate any help you guys can give me as this has been driving me crazy for the last few months.

EDIT: I tried switching the PCI slot that the card uses but that unfortunately hasn't fixed the problem. When I start the computer with the ethernet cable plugged into the card the green light stays on for about 10 seconds. It remains greyed out in the networking options.  

Thanks in advance

Tech

---

