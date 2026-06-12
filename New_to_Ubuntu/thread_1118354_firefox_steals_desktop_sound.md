---
title: "firefox steals desktop sound"
date: 2009-04-06
forum: New to Ubuntu
---

### Post by hungryOrb on 2009-04-06
hi,
Just thought I'd post this again coz, couldn't solve it last time.
When I load Ubuntu, sound works fine, and then when I open browser, which plays a sample, the sound on all other applications mutes, and I have no idea how to restore it..
Interesting to note is that, sound embedded in flash in firefox doesn't seem to steal the sound. But the sounds for example, used in googletalk to remind you of an instant message will steal the sound. 
Weird :(
TFC ;]
Robin

---

### Post by hungryOrb on 2009-04-06
Can I bump?

---

### Post by Crafty Kisses on 2009-04-07
What are the results of the following command?
```
lspci
```

---

### Post by hungryOrb on 2009-04-07
> **Codename said:**
> What are the results of the following command?
```
lspci
```

Thanks for reply :)
Here is the result!

```
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8400M GS (rev a1)
05:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8039 PCI-E Fast Ethernet Controller (rev 14)
07:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
08:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
08:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
08:09.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
08:09.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
```

TFC.. 
Robin

---

### Post by TheLions on 2009-04-07
do you have enabled pulseaudio???

(you can enable it in System=>Settings=>Sound)

---

