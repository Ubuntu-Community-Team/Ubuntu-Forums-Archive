---
title: "Wireless stopped working in ASUS desktop"
date: 2014-09-30
forum: Networking &amp; Wireless
---

### Post by chuckrp on 2014-09-30
I have been running Linux Mint 16 on a desktop machine for several months with an ASUS wireless card connected to my network. On Saturday, I left the computer running connected to the internet for the day. (mistake) When I got home that evening I found that the computer would no connect to the internet. For some reason my wireless connection was missing. My wireless router is working because my Windows Vista laptop, Ipad, Mythbuntu computer (with wireless card) are all still working and connecting to the router. I restarted the router just in case there was an issue. I have tried several of the various suggestions found in the forums with no luck. I also swapped out the wireless card in the desktop with one that is working. No luck. Currently the computer is connected to the internet with a wired connection. I am not showing my wireless connection or any of the wireless connections of my neighbors. So I decided to upgraded to Linux Mint 17. Still no wireless. When I originally install Linux Mint 16 the wireless came right up. I used the terminal window and did a full update. Still nothing. This is an ASUS motherboard, 8GB ram and a 1TB HD running only Linux. I am attaching the wireless-info. txt file in case someone can see something I am missing. If there is other info that might help let me know.

---

### Post by tgalati4 on 2014-09-30
I didn't see any output for *rfkill*.  Can you post:

```
rfkill list
```

It should look like:

> tgalati4@Mint14-Extensa ~ $ rfkill list
0: acer-wireless: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no


I would take the machine apart, clean it and reseat everything.  I would put the wireless card in a different slot.

Is there a reason why you are not using a wired connection on a desktop?

---

### Post by wildmanne39 on 2014-09-30
Your wireless card is not even being seen so you may also check in your bios and see if there is a setting to activate the card if not you can reset the bios if you are not using UEFI, also the recommendations in the other post should be tried as well.

---

### Post by chuckrp on 2014-10-01
I get nothing when I run rfkill list. I have cleaning the machine and moved the wifi card to a new slot. I have even tried a different card.
As for the wired connection, I don't have enough ports on the router for everything to be connected. Also this computer is in a bad location for a wired connection.

Here is a print out of the lspci file. Will that help?

chuck@chuck-System-Product-Name ~ $ lspci
00:00.0 Host bridge: Advanced Micro Devices, Inc. [AMD/ATI] RX780/RX790 Host Bridge
00:02.0 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] RX780/RD790 PCI to PCI bridge (external gfx0 port A)
00:04.0 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] RD790 PCI to PCI bridge (PCI express gpp port A)
00:09.0 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] RD790 PCI to PCI bridge (PCI express gpp port E)
00:0a.0 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] RD790 PCI to PCI bridge (PCI express gpp port F)
00:11.0 SATA controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 SATA Controller [IDE mode] (rev 40)
00:12.0 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:12.2 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:13.0 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:13.2 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:14.0 SMBus: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 SMBus Controller (rev 42)
00:14.1 IDE interface: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 IDE Controller (rev 40)
00:14.2 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 Azalia (Intel HDA) (rev 40)
00:14.3 ISA bridge: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 LPC host controller (rev 40)
00:14.4 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 PCI to PCI Bridge (rev 40)
00:14.5 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI2 Controller
00:15.0 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] SB700/SB800/SB900 PCI to PCI bridge (PCIE port 0)
00:16.0 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:16.2 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:18.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 10h Processor HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 10h Processor Address Map
00:18.2 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 10h Processor DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 10h Processor Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 10h Processor Link Control
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 06)
03:00.0 USB controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 03)
04:00.0 IDE interface: JMicron Technology Corp. JMB368 IDE controller
06:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Cedar [Radeon HD 5000/6000/7350/8350 Series]
06:00.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Cedar HDMI Audio [Radeon HD 5400/6300 Series]

---

### Post by chuckrp on 2014-10-02
I am thinking that whatever part of the motherboard that controls the PCI slots must have burnt out. I transferred the cards over to another computer and everything is showing up. So I know the cards are fine. It has to be the motherboard.
Thanks for the help and suggestions.

---

### Post by Vladlenin5000 on 2014-10-03
> **chuckrp said:**
> It has to be the motherboard.

Indeed. As I always say: Whenever something suddenly and unexpectedly stops working and there were no significant changes in the OS, ALWAYS troubleshoot the hardware first.

---

