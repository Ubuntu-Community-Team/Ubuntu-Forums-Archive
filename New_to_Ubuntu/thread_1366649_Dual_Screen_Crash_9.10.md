---
title: "Dual Screen Crash 9.10"
date: 2009-12-28
forum: New to Ubuntu
---

### Post by BBlue on 2009-12-28
Whenever I connect a VGA or S-video cable to my laptop (Dell xps M140) both screens turn black except for the cursor-arrow. When I plug in the VGA, the cursor arrow freezes completely.
When I plug in the S-video, the cursor can still move.  The screen will change to this frozen state *as soon* as I plug in the VGA; I don't even have go to the "Display" settings.

I checked other display posts, and none seemed to address my problem. Sorry if this is a duplicate.

I seemed to pick up that the following information was needed:

```

00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 03)
02:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
02:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
02:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
02:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 0a)
02:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 05)
02:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
02:03.0 Network controller: Intel Corporation PRO/Wireless 2915ABG [Calexico2] Network Connection (rev 05)

```


Any help is greatly appreciated.
Thanks.

---

### Post by spiky001 on 2009-12-28
Dont no if this helps when i ran windows on my dell with s video it wouldn,t work unless i booted with cable in, unfortunatly i not tried it with ubuntu see if this helps

---

### Post by miamibc on 2010-03-16
Seems that I have the same hardware and the same problem. Did you found solution?

---

