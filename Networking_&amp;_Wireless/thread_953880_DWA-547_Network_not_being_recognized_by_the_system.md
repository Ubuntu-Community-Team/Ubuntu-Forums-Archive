---
title: "DWA-547 Network not being recognized by the system"
date: 2008-10-20
forum: Networking &amp; Wireless
---

### Post by zelekt on 2008-10-20
As the topic says, my shiny new network card isnt found by the system.

I'm using ndiswrapper and I've got the driver installed, but when I do a lspci the output I get is as following:


&#65533; lspci
00:00.0 Host bridge: Intel Corporation 82815 815 Chipset Host Bridge and Memory Controller Hub (rev 04)
00:02.0 VGA compatible controller: Intel Corporation 82815 CGC [Chipset Graphics Controller] (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 11)
00:1f.0 ISA bridge: Intel Corporation 82801BA ISA Bridge (LPC) (rev 11)
00:1f.1 IDE interface: Intel Corporation 82801BA IDE U100 (rev 11)
00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB (Hub #1) (rev 11)
00:1f.3 SMBus: Intel Corporation 82801BA/BAM SMBus (rev 11)
00:1f.4 USB Controller: Intel Corporation 82801BA/BAM USB (Hub #2) (rev 11)
00:1f.5 Multimedia audio controller: Intel Corporation 82801BA/BAM AC'97 Audio (rev 11)
01:09.0 Network controller: Atheros Communications, Inc. Unknown device 0003 (rev 01)
01:0c.0 Ethernet controller: 3Com Corporation 3c905C-TX/TX-M [Tornado] (rev 7

As you can see, the network card isnt recognized.

You guys have any ideas on what I should do?


EDIT: For the record, I have madwifi installed too, but the card is found as ioctl there. Any hints?

Thanks
Zelekt

---

