---
title: "[SOLVED] Cant enable desktop effects"
date: 2008-12-30
forum: New to Ubuntu
---

### Post by k33bz on 2008-12-30
I am running Hardy 8.04 with Compiz-fusion and cario-dock. Yesterday everything was working fine, until I installed sumolinux to one of my USBs and booted from it. Since then Compiz dont seem to work right no more. (resolution, desktop effects, proper dual monitor clone, etc, etc) Here is my output:

compiz-check
```
Gathering information about your system...

 Distribution:          Ubuntu 8.04
 Desktop environment:   GNOME
 Graphics chip:         Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
 Driver in use:         vesa
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...  [SKIP]

 Checking for hardware/setup problems...           [SKIP]

At least one check had to be skipped:
 Error: vesa driver in use 

Would you like to know more? (Y/n) y

 The vesa driver is not capable of running Compiz, you need to install
 the proper driver for your graphics card. 

Check if there's an alternate (proprietary) driver available? (Y/n) y

```

Vesa wasnt the Driver I was using before.

COMPIZ
```
keebler@mobile:~$ compiz
Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity 
Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x2a00021 (keebler@mo)
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.

```

and finally LSPCI
```
keebler@mobile:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8038 PCI-E Fast Ethernet Controller (rev 14)
03:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
0a:09.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
0a:09.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)

```

Can someone please help me with this, all the threads I have seen are nto very helpful with this problem of mine.

---

### Post by tech9 on 2008-12-30
does your graphics card have direct rendering turned on...
 ```
glxinfo | grep direct
```

It should display 
```
direct rendering: Yes
```

you will need direct rendering turned on in order to enable desktop effects.

---

### Post by k33bz on 2008-12-30
```
keebler@mobile:~$ glxinfo | grep direct
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
OpenGL renderer string: Mesa GLX Indirect

```

i see that is off, do not know how to change that, besides as stated my vid card is running with the vesa driver, which is not compatible for compiz, and is not the driver I originally had on there.

---

### Post by k33bz on 2008-12-30
Ok I just fixed it, I had to reconfigure my Xserver.

---

### Post by tech9 on 2008-12-30
excellent!

just curious - after installing xserver - is rendering turned on?

---

