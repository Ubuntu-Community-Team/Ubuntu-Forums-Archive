---
title: "Wireless not recognized"
date: 2008-09-15
forum: Networking &amp; Wireless
---

### Post by burgechris on 2008-09-15
Ok...this is my first step into Ubuntu on laptops.  I have just bought a cheapie new laptop, Toshiba Satellite L355D-S7815.  It is an AMD64 ship so I used hardy 64 for my install.  Everything went beautifully (yeah...you guys rock) but it does not appear to give me any information on the wireless and thus I can't seem to edit my wireless settings.  I'm totally dependent on the GUI as I'm a noob to many things in Linux.  Basicly I have a few issues:

1)  I don't know what kind of card I have but Hardware Testing option under Administration appears to say that I have an Atheros card (?)  Unfortunately, Toshiba just says I have a wireless card and not a specific of what type.  :P

2)  Under network configuration I can click on "Edit Wireless" but not I can't seem to add a SSID.  I'm assuming this is related to the problem above.

As a sanity check, I do have the wireless in the on position and I get a little blinky light that indicates that it is on. 

TIA!

---

### Post by knattlhuber on 2008-09-15
Here's your first contact with the Ubuntu command line :)
Open a terminal (Applications > Accessories > Terminal) and type

```
lspci | grep Network
iwconfig
```

Post the output of both commands here and we will take it from there.

---

### Post by burgechris on 2008-09-15
Ok...cool thanks!

lspci | grep Network gets me nothing

iwconfig gets me:

lo        no wireless extensions.

eth0        no wireless extensions.


LOL...so nothing from nothing is...

Thanks for any help!

:)

---

### Post by knattlhuber on 2008-09-15
Try just

```
lspci
```

---

### Post by burgechris on 2008-09-15
Cool!  Got something that I hope is helpful!  :P


00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:01.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (int gfx)
00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0)
00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1)
00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)
00:07.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 3)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 11h HyperTransport Configuration (rev 40)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 11h Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 11h DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 11h Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 11h Link Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS780MC [Radeon HD 3100 Graphics]
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 02)
05:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)


Thanks!

---

### Post by knattlhuber on 2008-09-15
Yes, that helped. My bad with the '*| grep network*'

Do you see any drivers listed under System > Administration > Hardware Drivers?

If not, then using 'ndiswrapper' is probably the way to go:
[http://www.ubuntugeek.com/atheros-ar5007-wireless-with-madwifi-on-ubuntu-804-hardy-heron.html]("http://www.ubuntugeek.com/atheros-ar5007-wireless-with-madwifi-on-ubuntu-804-hardy-heron.html")

Please note that you need to follow the 64-bit instructions. The instructions involve a fair amount of terminal commands. If you have any questions about that, don't hesitate to ask.

Welcome to Ubuntu!

---

