---
title: "Please help me install netgear wpnt511 240 pci card"
date: 2008-10-15
forum: Networking &amp; Wireless
---

### Post by henry_d on 2008-10-15
I have a laptop with a netgear rangemax WPNT511 240 pci card and i cannot seem to get it working. I installed ubuntu 7.04 as i read it worked out the box but it didnt. Also the laptop has no way of connecting to the internet as the ethernet slot is broken so i dont know how to download updates and install ndiswrappers.

I have read about ndiswrappers but i am quite new to linux and i dont understand most of it and some of the guides had broken links.

If someone could tell me what i need to do or where there is a good guide i would really appreciate it.

---

### Post by overdrank on 2008-10-15
> **henry_d said:**
> I have a laptop with a netgear rangemax WN511T 240 pci card and i cannot seem to get it working. I installed ubuntu 7.04 as i read it worked out the box but it didnt. Also the laptop has no way of connecting to the internet as the ethernet slot is broken so i dont know how to download updates and install ndiswrappers.

I have read about ndiswrappers but i am quite new to linux and i dont understand most of it and some of the guides had broken links.

If someone could tell me what i need to do or where there is a good guide i would really appreciate it.

Hi and I can not find anything on that wireless card, could you post the output of the command lspci.
Edit also you may try a newer version of ubuntu are feisty support is ending soon. :)

---

### Post by henry_d on 2008-10-15
Hi i think i have an ubuntu 8.04 install disc so i will probably upgrade it. But the laptop doesnt have much ram or a big hard drive so if i decide to install xubuntu 8.04 will all the commands and procedures to get the wi-fi card working be the same?

The command lspci shows:

00:00.0 Host bridge: VIA Technologies, Inc. P/KN266 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8633 [Apollo Pro266 AGP]
00:09.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller
00:0b.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 46)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 80)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
01:00.0 VGA compatible controller: S3 Inc. VT8375 [ProSavage8 KM266/KL266]
02:00.0 Ethernet controller: Airgo Networks Inc AGN300 802.11 a/b/g True MIMO Wireless Card (rev 01)

Just to clarify the wi-fi card is a netgear wpnt511 and its a pci card (i think) its the one where it has a slot not a usb.

---

### Post by henry_d on 2008-10-15
Does anyone know?

Thanks

---

### Post by jualin on 2008-10-19
In that case the correct command is > lspcmcia

---

