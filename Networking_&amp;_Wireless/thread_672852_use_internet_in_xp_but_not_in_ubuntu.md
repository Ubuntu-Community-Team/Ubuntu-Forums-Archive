---
title: "use internet in xp but not in ubuntu"
date: 2008-01-20
forum: Networking &amp; Wireless
---

### Post by Arpan Chakrabarti on 2008-01-20
I have windows xp & ubuntu 7.04 .In xp i can use my internet service.But in linux i cannot use it.I think ubuntu 7.04 cannot detect my ethernet card,because when i working in linux the red light of the network card is off.Please help me for use the internet in ubuntu.

---

### Post by banewman on 2008-01-20
Please type in a terminal 
lspci 
and post the output of the command.
this will tell us if ubuntu has seen your card
:)

---

### Post by Didad on 2008-01-20
I have the same problem. So here is my result.
william@delta:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. VT8366/A/7 [Apollo KT266/A/333] (rev 80)
00:01.0 PCI bridge: VIA Technologies, Inc. VT8366/A/7 [Apollo KT266/A/333 AGP]
00:0a.0 Parallel controller: Timedia Technology Co Ltd Unknown device 7268 (rev 01)
00:0c.0 Communication controller: ESS Technology ES2838/2839 SuperLink Modem (rev 01)
00:0d.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon RV100 QY [Radeon 7000/VE]

---

### Post by yachp on 2008-01-21
I have the same problem as well

---

### Post by Arpan Chakrabarti on 2008-01-23
00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 01)

00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)

00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)

00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)

00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)

00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 81)

00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 01)

00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 01)

00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)

00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)

01:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

I think it detects my ethernet card.But that card's LED in still off.Plese help me.

---

### Post by banewman on 2008-01-25
Have you set the ethernet up in networking? From the menu applications - system - admin - network  your card should be shown because the system has seen it - then set it up - select dhcp to have default settings.
:)

---

