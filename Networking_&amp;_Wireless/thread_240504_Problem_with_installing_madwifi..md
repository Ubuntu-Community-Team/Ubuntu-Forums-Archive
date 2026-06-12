---
title: "Problem with installing madwifi."
date: 2006-08-20
forum: Networking &amp; Wireless
---

### Post by wickedcultgod on 2006-08-20
I've got a Toshiba Satellite notebook with an Atheros card in it. I've already downloaded madwifi 0.92 but I'm a newb at linux and have no idea how to install it. I know how to boot up as the root user and how to open up a terminal but I'm lost from there. Please someone give me some help. I would appreciate it a lot. Thanks.

---

### Post by tombs on 2006-08-21
Hi
You didn't give enough information about your devices.
First of all, whats your pcmcia card? And whats the kernel? Whats your satellite model?
To find out about the card, with the card plugged, on a terminal type: lspci
and search the lines with Network controller.
To find oute about your kernel, on a terminal type: uname -r
Paste your outputs here please.

---

### Post by tturrisi on 2006-08-21
[http://madwifi.org/wiki/UserDocs/Distro/Debian/MadWifi](http://madwifi.org/wiki/UserDocs/Distro/Debian/MadWifi)

---

### Post by wickedcultgod on 2006-08-21
Here's the card info.

0000:00:00.0 Host bridge: ATI Technologies Inc: Unknown device 5a31 (rev 01)
0000:00:01.0 PCI bridge: ATI Technologies Inc: Unknown device 5a3f
0000:00:04.0 PCI bridge: ATI Technologies Inc: Unknown device 5a36
0000:00:06.0 PCI bridge: ATI Technologies Inc: Unknown device 5a38
0000:00:07.0 PCI bridge: ATI Technologies Inc: Unknown device 5a39
0000:00:12.0 IDE interface: ATI Technologies Inc ATI 4379 Serial ATA Controller (rev 80)
0000:00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
0000:00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
0000:00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
0000:00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 82)
0000:00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller ATI (rev 80)
0000:00:14.2 0403: ATI Technologies Inc: Unknown device 437b (rev 01)
0000:00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
0000:00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
0000:01:05.0 VGA compatible controller: ATI Technologies Inc: Unknown device 5a62
0000:02:00.0 Ethernet controller: Atheros Communications, Inc.: Unknown device 001c (rev 01)
0000:0b:06.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)
0000:0b:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
0000:0b:0a.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev c0)

Here's the kernel info. 2.6.15-26-386

My Satellite is a A105-S2101.
I'm a complete newb so step by step instructions would help. Thanks. You've already been a big help.

---

### Post by tturrisi on 2006-08-21
1. boot comp.
2. system > administration > synaptic
3. enter password
4. synaptic/settings menu/repositories
5. put a check next to all of them
6. ok out of the window
7. toolbar menu/reload
8. locate restricted in left frame
9. locate the linux-restricted-modules for your kernel
10. install linux-restricted-modules

madwifi is the driver for atheros chipsets and it is contained in the linux-restricted-modules packages.

if need to find out what kernel you have (to match with the linux-restricted-modeles) open a terminal and type: uname -r

reboot comp

---

### Post by wickedcultgod on 2006-08-23
Which restricted linux module do I install? There are a couple of different categories and none of them mention madwifi, only nvidia cards.

---

### Post by wickedcultgod on 2006-08-23
I found which module to install and have. How do I install madwifi? I know it says type the command "make" into the madwifi source terminal or something but I don't know how to do that.

---

### Post by hajk on 2006-08-23
Just install the restricted modules package that matches your installed kernel. This package contains the madwifi drivers, and they should load automatically once the kernel recognizes the wireless card with the Atheros chip, e.g. when inserting a PC-Card (PCMCIA) or USB device, or when booting. No need to "make" -- that's only when you want to compile the latest version of the drivers yourself (not something that I recommend for a newcomer to Linux).

Of course, with the drivers loaded you must also configure the ath0 interface in the Systems - Administration - Networking menu.

---

