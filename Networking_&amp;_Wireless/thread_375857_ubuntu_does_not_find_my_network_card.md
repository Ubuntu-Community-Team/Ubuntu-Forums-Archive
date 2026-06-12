---
title: "ubuntu does not find my network card"
date: 2007-03-04
forum: Networking &amp; Wireless
---

### Post by unikum on 2007-03-04
Wireless D-link DWL-G650.
I have installed networkmanager and disabled everything in /etc/network/interaces except lo.
How do i get ubuntu to install the card?

---

### Post by JonnyTrombone on 2007-03-04
First, there are three versions of the DWL-G650 card. Go to [this page]("http://support.dlink.com/products/revision.asp?productId=DWL-G650") to see which version you have. 

Try this: go into console and type ```
lspcmcia
```Theoretically, it will show your card and list a driver.

---

### Post by unikum on 2007-03-04
rev c4

```
unikum@laptop:~$ lspcmcia
Socket 0 Bridge:        [yenta_cardbus]         (bus ID: 0000:01:09.0)
  CardBus card -- see "lspci" for more information
unikum@laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82830 830 Chipset Host Bridge (rev 04)
00:02.0 VGA compatible controller: Intel Corporation 82830 CGC [Chipset Graphics Controller] (rev 04)
00:02.1 Display controller: Intel Corporation 82830 CGC [Chipset Graphics Controller]
00:1d.0 USB Controller: Intel Corporation 82801CA/CAM USB (Hub #1) (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801CA/CAM USB (Hub #2) (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 42)
00:1f.0 ISA bridge: Intel Corporation 82801CAM ISA Bridge (LPC) (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801CAM IDE U100 (rev 02)
00:1f.3 SMBus: Intel Corporation 82801CA/CAM SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801CA/CAM AC'97 Audio Controller (rev 02)
00:1f.6 Modem: Intel Corporation 82801CA/CAM AC'97 Modem Controller (rev 02)
01:05.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
01:09.0 CardBus bridge: O2 Micro, Inc. OZ601/6912/711E0 CardBus/SmartCardBus Controller
02:00.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)

```

---

### Post by JonnyTrombone on 2007-03-05
Your wireless card *may* work with [Linux-wlan-ng]("http://www.linux-wlan.com/linux-wlan/") drivers. You can either check synaptic for them (I believe they're there) or take the above link.

---

### Post by cvmostert on 2007-03-08
I have a AR5212 and it works with edgy and breezy... just have to activate wireless in network settings...

---

