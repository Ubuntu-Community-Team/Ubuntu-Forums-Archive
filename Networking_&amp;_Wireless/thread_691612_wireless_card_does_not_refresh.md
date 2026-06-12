---
title: "wireless card does not refresh"
date: 2008-02-08
forum: Networking &amp; Wireless
---

### Post by soviet911 on 2008-02-08
Hi, i got hp omnibook 6100 with ubunto 7.10 running and so far the only problem i got is  my wirless card doesnt refresh the networks, i need to restart the pc for it to catch a new network. I dont know what the problem is but is there a way to make it forcefully refresh ( alt ctrl backspace doesnt help) lspci info.  

soviet911@soviet911:~$ lspci
00:00.0 Host bridge: Intel Corporation 82830 830 Chipset Host Bridge (rev 02)
00:01.0 PCI bridge: Intel Corporation 82830 830 Chipset AGP Bridge (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801CA/CAM USB Controller #1 (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 41)
00:1f.0 ISA bridge: Intel Corporation 82801CAM ISA Bridge (LPC) (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801CAM IDE U100 Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801CA/CAM SMBus Controller (rev 01)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M6 LY
02:02.0 Communication controller: 3Com Corporation Mini PCI 56k Winmodem
02:03.0 Multimedia audio controller: ESS Technology ES1988 Allegro-1 (rev 12)
02:04.0 Network controller: Intersil Corporation Prism 2.5 Wavelan chipset (rev 01)
02:05.0 CardBus bridge: Texas Instruments PCI1420 PC card Cardbus Controller
02:05.1 CardBus bridge: Texas Instruments PCI1420 PC card Cardbus Controller
02:08.0 Ethernet controller: Intel Corporation 82801CAM (ICH3) PRO/100 VM (KM) Ethernet Controller (rev 41)

---

### Post by K.Mandla on 2008-02-09
What happens if you bring the device down, then back up again? Does it refresh then?

---

### Post by soviet911 on 2008-02-09
the button on the side of the pc that turns it on and off doesnt do anything, it seems like its on all the time regardless if its pushed in or out, and i dont know how to turn it off in ubunto and then turn it back on when i want to.

---

