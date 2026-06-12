---
title: "Ubuntu 8.10 No Sound ATI Azalea"
date: 2009-02-08
forum: New to Ubuntu
---

### Post by kittley on 2009-02-08
I am getting no sound out of my sound card (works in Windows).

uname -a output:

Linux ubuntu 2.6.27-11-generic #1 SMP Thu Jan 29 19:24:39 UTC 2009 i686 GNU/Linux

hwinfo --sound output:

18: PCI 14.2: 0403 Audio device
[Created at pci.310]
UDI: /org/freedesktop/Hal/devices/pci_1002_4383
Unique ID: 5Dex.yp06cNbwF6E
SysFS ID: /devices/pci0000:00/0000:00:14.2
SysFS BusID: 0000:00:14.2
Hardware Class: sound
Model: "ATI SBx00 Azalia"
Vendor: pci 0x1002 "ATI Technologies Inc"
Device: pci 0x4383 "SBx00 Azalia"
SubVendor: pci 0x103c "Hewlett-Packard Company"
SubDevice: pci 0x3045
Driver: "HDA Intel"
Driver Modules: "snd_hda_intel"
Memory Range: 0xd2400000-0xd2403fff (rw,non-prefetchable)
IRQ: 16 (3651 events)
Module Alias: "pci:v00001002d00004383sv0000103Csd00003045bc04sc03i00"
Driver Info #0
Driver Status: snd_hda_intel is active
Driver Activation Cmd: "modprobe snd_hda_intel"
Config Status: cfg=new, avail=yes, need=no, active=unknown

Laptop is an HP TouchSmart tx2

Any help would be greatly appreciated. If more information is needed, please let me know, I will attempt to reply quickly.

---

### Post by skootar on 2009-02-08
I just got mine working using this info:

[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

See the section:

Part C: Intrepid Ibex (8.10)

---

### Post by kittley on 2009-02-08
I did go through all the steps one-by-one, but still no sound. :-\  Thank you for trying, though. :)

---

