---
title: "displaylink ethernet not working ubuntu 14.04.1"
date: 2016-02-09
forum: Networking &amp; Wireless
---

### Post by vickers-mathew on 2016-02-09
My HP EliteDisplay S231d connects via displaylink, and I can't get internet through it!

Oh pitiful me.

In the "live CD" version, pass-through ethernet worked. Now I have Ubuntu installed, it doesn't work.

apt-get update & upgrade tells me I am up to date...

(I have installed the displaylink drivers, but as the link below says: the drivers are for video. Audio and Ethernet are supported natively - the sound works.)
[http://support.displaylink.com/knowledgebase/articles/684649-how-to-install-displaylink-software-on-ubuntu](http://support.displaylink.com/knowledgebase/articles/684649-how-to-install-displaylink-software-on-ubuntu)



Perhaps you know a way to help me get the ol' internet working? 




does lspci give useful information?

:~$ lspci
00:00.0 Host bridge: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor DRAM Controller (rev 06)
00:02.0 VGA compatible controller: Intel Corporation 4th Gen Core Processor Integrated Graphics Controller (rev 06)
00:03.0 Audio device: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor HD Audio Controller (rev 06)
00:14.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB xHCI (rev 04)
00:16.0 Communication controller: Intel Corporation 8 Series/C220 Series Chipset Family MEI Controller #1 (rev 04)
00:19.0 Ethernet controller: Intel Corporation Ethernet Connection I217-V (rev 04)
00:1a.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 8 Series/C220 Series Chipset High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #1 (rev d4)
00:1c.6 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #7 (rev d4)
00:1c.7 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #8 (rev d4)
00:1d.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation HM87 Express LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 8 Series/C220 Series Chipset Family 6-port SATA Controller 1 [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation 8 Series/C220 Series Chipset Family SMBus Controller (rev 04)
02:00.0 Network controller: Broadcom Corporation BCM43228 802.11a/b/g/n
03:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5227 PCI Express Card Reader (rev 01)

---

### Post by howefield on 2016-02-09
Thread moved, you'll probably fare better here in the "*Networking & Wireless*" forum.

---

