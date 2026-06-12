---
title: "Max volume + sound through speakers &amp; headphones at same time"
date: 2010-09-13
forum: New to Ubuntu
---

### Post by adobrakic on 2010-09-13
I have two (hopefully) simple issues. I have a HP p6540y desktop, and I'm running Ubuntu 10.04. When I plug headphones into my front audio port, my speakers which are plugged into the rear audio port still play sound. Is there a way to disable this without having to unplug the rear speakers every time I want to listen on my headphones?

Also, I notice that under sound preferences, you can go passed 100% volume. However, if I turn down the volume and raise it back up, it doesn't go passed that 100%. Is there a way to default the extra volume to 100% so I don't have to go into the preferences to get to it? 

```
ado@ado-desktop ~ $ lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge Alternate
00:01.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (int gfx)
00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1)
00:0a.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 5)
00:11.0 RAID bus controller: ATI Technologies Inc SB700/SB800 SATA Controller [Non-RAID5 mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3c)
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:14.5 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Link Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS880 [Radeon HD 4200]
02:00.0 Network controller: RaLink RT3090 Wireless 802.11n 1T/1R PCIe
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
04:06.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller (rev c0)
ado@ado-desktop ~ $ 

```

---

### Post by adobrakic on 2010-09-14
bumplz

---

### Post by adobrakic on 2010-09-16
no one!? :|

---

### Post by drifter2502 on 2010-10-13
Try this fix...[http://www.howtogeek.com/howto/10964/how-to-fix-sound-issues-in-ubuntu-9.10/](http://www.howtogeek.com/howto/10964/how-to-fix-sound-issues-in-ubuntu-9.10/)
Worked for me.

---

