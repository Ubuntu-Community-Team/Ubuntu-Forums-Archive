---
title: "Get more resolution in my Laptop"
date: 2010-07-23
forum: New to Ubuntu
---

### Post by GuAnAtoS on 2010-07-23
I People..

I just install 10.04 LTS in to my Laptop Compaq nx6320, everything works fine except my resolution.. I just can reach 1024x768 60Hz..

Is there any solution to have more resolution?

:popcorn:

---

### Post by ubunterooster on 2010-07-23
go to system>preferences>monitor. Change the resolution if possible

---

### Post by GuAnAtoS on 2010-07-23
> **ubunterooster said:**
> go to system>preferences>monitor. Change the resolution if possible


I already do that, but I just have until 1024x768.. When I was using windows with same lap i can reach more than that....

---

### Post by Zeike on 2010-07-23
What graphics card are you using?

---

### Post by GuAnAtoS on 2010-07-23
> **Zeike said:**
> What graphics card are you using?

Intel 945GM Express graphics chip, The 15in screen has a maximum resolution of 1400x1050 pixels

---

### Post by GuAnAtoS on 2010-07-23
any Idea??

---

### Post by pwabrahams on 2010-07-23
I have the same problem as the original poster, but more information.  There are a number of reported bugs relating to screen resolution in Lucid, both with nouveau and with the proprietary NVidia drivers.  In fact, with the proprietary drivers I can't get resolution greater than 640x480!  My video card as reported by **hwinfo** is:
```

wa@Suillus:/etc/X11$ hwinfo --gfxcard
21: PCI 0d.0: 0300 VGA compatible controller (VGA)              
  [Created at pci.318]
  UDI: /org/freedesktop/Hal/devices/pci_10de_3d6
  Unique ID: qnJ_.QtW+3nZHS_5
  SysFS ID: /devices/pci0000:00/0000:00:0d.0
  SysFS BusID: 0000:00:0d.0
  Hardware Class: graphics card
  Model: "nVidia VGA compatible controller"
  Vendor: pci 0x10de "nVidia Corporation"
  Device: pci 0x03d6 
  SubVendor: pci 0x1043 "ASUSTeK Computer Inc."
  SubDevice: pci 0x83a4 
  Revision: 0xa2
  Driver: "nouveau"
  Driver Modules: "drm"
  Memory Range: 0xde000000-0xdeffffff (rw,non-prefetchable)
  Memory Range: 0xc0000000-0xcfffffff (rw,prefetchable)
  Memory Range: 0xdd000000-0xddffffff (rw,non-prefetchable)
  Memory Range: 0xdffc0000-0xdffdffff (ro,prefetchable,disabled)
  IRQ: 23 (23207 events)
  I/O Ports: 0x3c0-0x3df (rw)
  Module Alias: "pci:v000010DEd000003D6sv00001043sd000083A4bc03sc00i00"
  Driver Info #0:
    Driver Status: nouveau is active
    Driver Activation Cmd: "modprobe nouveau"
  Driver Info #1:
    Driver Status: nvidiafb is not active
    Driver Activation Cmd: "modprobe nvidiafb"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

Primary display adapter: #21

```
The **Xorg.0.log** file reports the video card as **GeForce 7025 / nForce 630a**.

I've tried various tweaks to **xorg.conf** but none of them have helped and some have made matters worse.  Needless to say, I had no such trouble with Karmic or with the other OS's I have on this machine.  

Here are what seem to be the useful lines of **Xorg.0.log**.  I'm not posting the whole thing because it's huge.
```
(II) [drm] DRM interface version 1.3
(II) [drm] DRM open master succeeded.
(--) NOUVEAU(0): Chipset: "NVIDIA NV4c"
(II) NOUVEAU(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
(==) NOUVEAU(0): Depth 24, (--) framebuffer bpp 32
(==) NOUVEAU(0): RGB weight 888
(==) NOUVEAU(0): Default visual is TrueColor
(==) NOUVEAU(0): Using HW cursor
(II) NOUVEAU(0): Output VGA-1 has no monitor section
(II) NOUVEAU(0): EDID for output VGA-1
(II) NOUVEAU(0): Printing probed modes for output VGA-1
(II) NOUVEAU(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) NOUVEAU(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) NOUVEAU(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) NOUVEAU(0): Modeline "848x480"x60.0   33.75  848 864 976 1088  480 486 494 517 +hsync +vsync (31.0 kHz)
(II) NOUVEAU(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 489 492 525 -hsync -vsync (31.5 kHz)
(II) NOUVEAU(0): Output VGA-1 connected
(II) NOUVEAU(0): Using fuzzy aspect match for initial modes
(II) NOUVEAU(0): Output VGA-1 using initial mode 1024x768
(II) NOUVEAU(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
(--) NOUVEAU(0): Virtual size is 1024x768 (pitch 1024)
(**) NOUVEAU(0):  Driver mode "1024x768": 65.0 MHz (scaled from 0.0 MHz), 48.4 kHz, 60.0 Hz
(II) NOUVEAU(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(**) NOUVEAU(0):  Driver mode "800x600": 40.0 MHz (scaled from 0.0 MHz), 37.9 kHz, 60.3 Hz
(II) NOUVEAU(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(**) NOUVEAU(0):  Driver mode "800x600": 36.0 MHz (scaled from 0.0 MHz), 35.2 kHz, 56.2 Hz
(II) NOUVEAU(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(**) NOUVEAU(0):  Driver mode "848x480": 33.8 MHz (scaled from 0.0 MHz), 31.0 kHz, 60.0 Hz
(II) NOUVEAU(0): Modeline "848x480"x60.0   33.75  848 864 976 1088  480 486 494 517 +hsync +vsync (31.0 kHz)
(**) NOUVEAU(0):  Driver mode "640x480": 25.2 MHz (scaled from 0.0 MHz), 31.5 kHz, 59.9 Hz
(II) NOUVEAU(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 489 492 525 -hsync -vsync (31.5 kHz)
(==) NOUVEAU(0): DPI set to (96, 96)
(II) NOUVEAU(0): NVEnterVT is called.
(==) NOUVEAU(0): DPMS enabled
(II) NOUVEAU(0): RandR 1.2 enabled, ignore the following RandR disabled message.
(--) RandR disabled
(II) AIGLX error: dlopen of /usr/lib/dri/nouveau_dri.so failed (/usr/lib/dri/nouveau_dri.so: cannot open shared object file: No such file or directory)
(II) AIGLX: reverting to software rendering
(II) AIGLX: Screen 0 is not DRI capable
(II) AIGLX: Loaded and initialized /usr/lib/dri/swrast_dri.so
(II) GLX: Initialized DRISWRAST GL provider for screen 0
(II) NOUVEAU(0): Setting screen physical size to 270 x 203
resize called 1024 768

```

---

### Post by GuAnAtoS on 2010-07-30
Still having this prob.. :(

---

### Post by heyandy889 on 2010-07-30
One move that helped me was

System-Administration-Hardware Drivers

My resolution options were 640x420 and 420x200, lower than I had on Windows. I updated the hardware drivers and was allowed 1024x768.

Might be relevant to read the man page for xrandr. You can read this by running "man xrandr" in the terminal. I believe xrandr lets you choose screen resolution, as well as choose the video output.

---

### Post by GuAnAtoS on 2010-07-30
hmmm... nop...


[IMG]http://www.guanasworld.com/gallery3/var/resizes/Ventas/Pantallazo.png[/IMG]

---

