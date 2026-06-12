---
title: "How to connect to wireless"
date: 2010-05-06
forum: New to Ubuntu
---

### Post by Nuu on 2010-05-06
Alright I'm running a Dell Vostro 1000 with 8.04. I'm not entirely sure how to get wireless and I'm not even sure if the laptop has a wireless card and if it has driver support. **What is the command to find out if I have a wireless card?**

---

### Post by yorkie on 2010-05-06
Open terminal and type iwconfig 
this should show wireless infomation

---

### Post by bredman on 2010-05-06
To check if you have wireless working, select menu item System/Preferences/Network Connections and select the Wireless tab.

To see what kind of wireless hardware you have, open a terminal (Applications/Accessories/Terminal) and enter the commands lspci and lsusb to list all of your PCI-connected and USB-connected hardware. Look for anything that mentions WiFi or wireless or 802.11.

To check if your hardware has known problems in Ubuntu, search the internet for the word Ubuntu followed by any identifying information from lspci/lsusb
For example Search for Ubuntu BCM4318

Note that a lot of wireless cards (especially the BCM series) need freeware which is freely available on the internet, but cannot legally be included in the Ubuntu distribution. So it could be an easy problem to fix if you know the identity of your WiFi hardware.

---

### Post by 3rdalbum on 2010-05-06
> **bredman said:**
> To check if you have wireless working, select menu item System/Preferences/Network Connections and select the Wireless tab.

Probably the easier method is to left-click on the Network Manager applet on your panel. It will say if there are any wireless networks detected; and in cities and even smaller towns you can usually pick up somebody's wireless network.

---

### Post by Nuu on 2010-05-08
```
~$ lspci
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:05.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:06.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS482 [Radeon Xpress 200]
05:00.0 Network controller: Broadcom Corporation BCM4312 802.11a/b/g (rev 01)
08:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
08:01.0 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
08:01.1 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
```

So presumably this means that I have a Broadcom BCM4312 wireless card. However, I know that it is not registering the wireless network which I have. Where do I get the appropriate software?

---

