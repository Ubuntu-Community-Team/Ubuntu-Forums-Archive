---
title: "Changing screen resolution"
date: 2010-06-03
forum: New to Ubuntu
---

### Post by paul6 on 2010-06-03
I am trying to change my laptop's main resolution to 1280x800 (16:10). This resolution is not an option in Ubuntu's Monitor GUI app.

Do I need to create an xorg.conf file or is there another way? What do I need to put in the xorg.conf file to change my resolution?

Thanks,
Paul
( My laptop: Gateway P-7811FX )

---

### Post by jms1989 on 2010-06-04
depending on your video hardware, you may need to install the proper video drivers to get the desired resolution.

Can you post the output of lspci to tell us what hardware you have?

---

### Post by paul6 on 2010-06-04
Hi jms1989, it appears Ubuntu correctly recognizes my laptop's graphics card:

```
paul@paul-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M-E LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
**01:00.0 VGA compatible controller: nVidia Corporation G94 [GeForce 9800M GTS] (rev a1)**
02:00.0 Ethernet controller: Marvell Technology Group Ltd. Device 4380 (rev 10)
04:00.0 Network controller: Intel Corporation Wireless WiFi Link 5100
0d:06.0 FireWire (IEEE 1394): O2 Micro, Inc. Firewire (IEEE 1394) (rev 02)
0d:06.2 SD Host controller: O2 Micro, Inc. Integrated MMC/SD Controller (rev 02)
0d:06.3 Mass storage controller: O2 Micro, Inc. Integrated MS/xD Controller (rev 01)
paul@paul-laptop:~$ 
```

My current resolution is the largest possible (1920x1200), which is too large for me to read text. The Monitor app does not offer me 1280x800 as a dropdown. So I think I just need a way to input 1280x800 manually.

---

### Post by sandyd on 2010-06-04
did you install the nvidia drivers? (system -> Administration -> hardware drivers?)

---

### Post by paul6 on 2010-06-04
> **carlee said:**
> did you install the nvidia drivers? (system -> Administration -> hardware drivers?)

Hey carlee,

I just installed the nvidia drivers - once I rebooted, I ran the nvidia app and I was able to adjust my screen resolution down to 1440x900.

For some reason 1280x800 still isn't an option, but I got what I wanted - a lower resolution so I can read text easier, and it's still a 16/10 widescreen ratio.

Thanks guys! :)

---

