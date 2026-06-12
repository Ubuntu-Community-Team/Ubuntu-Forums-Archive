---
title: "Scrolling problem with Intel graphics Card"
date: 2009-04-06
forum: New to Ubuntu
---

### Post by souravc83 on 2009-04-06
I have a problem scrolling in adobe pdf or firefox (the scolling is slow) I am using Ubuntu Hardy 8.04. 
My graphics card is 

Intel Corporation 82865G Integrated Graphics Controller

The xorg.conf file looks like this:


[I]Section "Device"
	Identifier	"Intel Corporation 82865G Integrated Graphics Controller"
	Driver		"intel"
	BusID		"PCI:0:2:0"[/I]

I have tried switching off the visual effects by switching from "normal" to "none" in system>Preference>Appearance (Visual Effects tab)
but it worsens the scrolling. I can literally see the page refreshing with each mouse scroll.

I have also tried to replace the window manager with metacity by using the "metacity --replace" command, but again, it only worsens the scrolling.

What can the issue be?
Do I need updated drivers? 
I tried to search the forum, and it says Intel drivers are open source and there should not be a problem. 

I am totally lost.

---

### Post by tjwoosta on 2009-04-09
hmm.. sounds like a strange problem

please post your /var/log/Xorg.0.log so we can help troubleshoot
```

sudo gedit /var/log/Xorg.0.log
```

---

### Post by souravc83 on 2009-04-09
(==) Log file: "/var/log/Xorg.0.log", Time: Tue Apr  7 11:18:27 2009
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "DELL E773c"
(**) |   |-->Device "Intel Corporation 82865G Integrated Graphics Controller"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x81dc500
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.3
	X.Org Video Driver: 2.0
	X.Org XInput driver : 2.0
	X.Org Server Extension : 0.3
	X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules//libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Video Driver, version 2.0
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 8086,2570 card 1028,019d rev 02 class 06,00,00 hdr 00
(II) PCI: 00:02:0: chip 8086,2572 card 1028,019d rev 02 class 03,00,00 hdr 00
(II) PCI: 00:1d:0: chip 8086,24d2 card 1028,019d rev 02 class 0c,03,00 hdr 80
(II) PCI: 00:1d:1: chip 8086,24d4 card 1028,019d rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:3: chip 8086,24de card 1028,019d rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:7: chip 8086,24dd card 1028,019d rev 02 class 0c,03,20 hdr 00
(II) PCI: 00:1e:0: chip 8086,244e card 0000,0000 rev c2 class 06,04,00 hdr 01
(II) PCI: 00:1f:0: chip 8086,24d0 card 0000,0000 rev 02 class 06,01,00 hdr 80
(II) PCI: 00:1f:1: chip 8086,24db card 1028,019d rev 02 class 01,01,8a hdr 00
(II) PCI: 00:1f:3: chip 8086,24d3 card 1028,019d rev 02 class 0c,05,00 hdr 00
(II) PCI: 00:1f:5: chip 8086,24d5 card 1028,019d rev 02 class 04,01,00 hdr 00
(II) PCI: 01:00:0: chip 1814,0201 card 1737,0032 rev 01 class 02,80,00 hdr 00
(II) PCI: 01:08:0: chip 8086,1050 card 1028,019d rev 02 class 02,00,00 hdr 00
(II) PCI: End of PCI scan
(II) Intel Bridge workaround enabled
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,1), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:30:0), (0,1,1), BCTRL: 0x0002 (VGA_EN is cleared)
(II) Bus 1 I/O range:
	[0] -1	0	0x0000d000 - 0x0000dfff (0x1000) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xfea00000 - 0xfeafffff (0x100000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(0:2:0) Intel Corporation 82865G Integrated Graphics Controller rev 2, Mem @ 0xe8000000/27, 0xfeb80000/19, I/O @ 0xed98/3
(II) Addressable bus resource ranges are
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
	[1] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) PCI Memory resource overlap reduced 0xf0000000 from 0xf7ffffff to 0xefffffff
(II) Active PCI resource ranges:
	[0] -1	0	0xfeafd000 - 0xfeafdfff (0x1000) MX[B]
	[1] -1	0	0xfeafe000 - 0xfeafffff (0x2000) MX[B]
	[2] -1	0	0xfeb7f900 - 0xfeb7f9ff (0x100) MX[B]
	[3] -1	0	0xfeb7fa00 - 0xfeb7fbff (0x200) MX[B]
	[4] -1	0	0xfeb7fc00 - 0xfeb7ffff (0x400) MX[B]
	[5] -1	0	0xffa80800 - 0xffa80bff (0x400) MX[B]
	[6] -1	0	0xf0000000 - 0xefffffff (0x0) MX[B]O
	[7] -1	0	0xfeb80000 - 0xfebfffff (0x80000) MX[B](B)
	[8] -1	0	0xe8000000 - 0xefffffff (0x8000000) MX[B](B)
	[9] -1	0	0x0000df40 - 0x0000df7f (0x40) IX[B]
	[10] -1	0	0x0000edc0 - 0x0000edff (0x40) IX[B]
	[11] -1	0	0x0000ee00 - 0x0000eeff (0x100) IX[B]
	[12] -1	0	0x0000eda0 - 0x0000edbf (0x20) IX[B]
	[13] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[14] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[15] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[16] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[17] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[18] -1	0	0x0000ff20 - 0x0000ff3f (0x20) IX[B]
	[19] -1	0	0x0000ff60 - 0x0000ff7f (0x20) IX[B]
	[20] -1	0	0x0000ff80 - 0x0000ff9f (0x20) IX[B]
	[21] -1	0	0x0000ed98 - 0x0000ed9f (0x8) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xfeafd000 - 0xfeafdfff (0x1000) MX[B]
	[1] -1	0	0xfeafe000 - 0xfeafffff (0x2000) MX[B]
	[2] -1	0	0xfeb7f900 - 0xfeb7f9ff (0x100) MX[B]
	[3] -1	0	0xfeb7fa00 - 0xfeb7fbff (0x200) MX[B]
	[4] -1	0	0xfeb7fc00 - 0xfeb7ffff (0x400) MX[B]
	[5] -1	0	0xffa80800 - 0xffa80bff (0x400) MX[B]
	[6] -1	0	0xf0000000 - 0xefffffff (0x0) MX[B]O
	[7] -1	0	0xfeb80000 - 0xfebfffff (0x80000) MX[B](B)
	[8] -1	0	0xe8000000 - 0xefffffff (0x8000000) MX[B](B)
	[9] -1	0	0x0000df40 - 0x0000df7f (0x40) IX[B]
	[10] -1	0	0x0000edc0 - 0x0000edff (0x40) IX[B]
	[11] -1	0	0x0000ee00 - 0x0000eeff (0x100) IX[B]
	[12] -1	0	0x0000eda0 - 0x0000edbf (0x20) IX[B]
	[13] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[14] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[15] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[16] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[17] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[18] -1	0	0x0000ff20 - 0x0000ff3f (0x20) IX[B]
	[19] -1	0	0x0000ff60 - 0x0000ff7f (0x20) IX[B]
	[20] -1	0	0x0000ff80 - 0x0000ff9f (0x20) IX[B]
	[21] -1	0	0x0000ed98 - 0x0000ed9f (0x8) IX[B](B)
(II) OS-reported resource ranges after removing overlaps with PCI:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfeafd000 - 0xfeafdfff (0x1000) MX[B]
	[5] -1	0	0xfeafe000 - 0xfeafffff (0x2000) MX[B]
	[6] -1	0	0xfeb7f900 - 0xfeb7f9ff (0x100) MX[B]
	[7] -1	0	0xfeb7fa00 - 0xfeb7fbff (0x200) MX[B]
	[8] -1	0	0xfeb7fc00 - 0xfeb7ffff (0x400) MX[B]
	[9] -1	0	0xffa80800 - 0xffa80bff (0x400) MX[B]
	[10] -1	0	0xf0000000 - 0xefffffff (0x0) MX[B]O
	[11] -1	0	0xfeb80000 - 0xfebfffff (0x80000) MX[B](B)
	[12] -1	0	0xe8000000 - 0xefffffff (0x8000000) MX[B](B)
	[13] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[14] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[15] -1	0	0x0000df40 - 0x0000df7f (0x40) IX[B]
	[16] -1	0	0x0000edc0 - 0x0000edff (0x40) IX[B]
	[17] -1	0	0x0000ee00 - 0x0000eeff (0x100) IX[B]
	[18] -1	0	0x0000eda0 - 0x0000edbf (0x20) IX[B]
	[19] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[20] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[21] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[22] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[23] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[24] -1	0	0x0000ff20 - 0x0000ff3f (0x20) IX[B]
	[25] -1	0	0x0000ff60 - 0x0000ff7f (0x20) IX[B]
	[26] -1	0	0x0000ff80 - 0x0000ff9f (0x20) IX[B]
	[27] -1	0	0x0000ed98 - 0x0000ed9f (0x8) IX[B](B)
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension SHAPE
(II) Loading extension MIT-SUNDRY-NONSTANDARD
(II) Loading extension BIG-REQUESTS
(II) Loading extension SYNC
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XC-MISC
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-Misc
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 1.4.0.90, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
(II) LoadModule: "intel"
(II) Loading /usr/lib/xorg/modules/drivers//intel_drv.so
(II) Module intel: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 2.2.1
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 2.0
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 1.4.0, module version = 1.2.2
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.0
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 1.4.0, module version = 1.2.3
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.0
(II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
	i810-dc100, i810e, i815, i830M, 845G, 852GM/855GM, 865G, 915G,
	E7221 (i915), 915GM, 945G, 945GM, 945GME, 965G, G35, 965Q, 946GZ,
	965GM, 965GME/GLE, G33, Q35, Q33, Intel Integrated Graphics Device
(II) Primary Device is: PCI 00:02:0
(--) Chipset 865G found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfeafd000 - 0xfeafdfff (0x1000) MX[B]
	[5] -1	0	0xfeafe000 - 0xfeafffff (0x2000) MX[B]
	[6] -1	0	0xfeb7f900 - 0xfeb7f9ff (0x100) MX[B]
	[7] -1	0	0xfeb7fa00 - 0xfeb7fbff (0x200) MX[B]
	[8] -1	0	0xfeb7fc00 - 0xfeb7ffff (0x400) MX[B]
	[9] -1	0	0xffa80800 - 0xffa80bff (0x400) MX[B]
	[10] -1	0	0xf0000000 - 0xefffffff (0x0) MX[B]O
	[11] -1	0	0xfeb80000 - 0xfebfffff (0x80000) MX[B](B)
	[12] -1	0	0xe8000000 - 0xefffffff (0x8000000) MX[B](B)
	[13] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[14] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[15] -1	0	0x0000df40 - 0x0000df7f (0x40) IX[B]
	[16] -1	0	0x0000edc0 - 0x0000edff (0x40) IX[B]
	[17] -1	0	0x0000ee00 - 0x0000eeff (0x100) IX[B]
	[18] -1	0	0x0000eda0 - 0x0000edbf (0x20) IX[B]
	[19] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[20] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[21] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[22] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[23] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[24] -1	0	0x0000ff20 - 0x0000ff3f (0x20) IX[B]
	[25] -1	0	0x0000ff60 - 0x0000ff7f (0x20) IX[B]
	[26] -1	0	0x0000ff80 - 0x0000ff9f (0x20) IX[B]
	[27] -1	0	0x0000ed98 - 0x0000ed9f (0x8) IX[B](B)
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfeafd000 - 0xfeafdfff (0x1000) MX[B]
	[5] -1	0	0xfeafe000 - 0xfeafffff (0x2000) MX[B]
	[6] -1	0	0xfeb7f900 - 0xfeb7f9ff (0x100) MX[B]
	[7] -1	0	0xfeb7fa00 - 0xfeb7fbff (0x200) MX[B]
	[8] -1	0	0xfeb7fc00 - 0xfeb7ffff (0x400) MX[B]
	[9] -1	0	0xffa80800 - 0xffa80bff (0x400) MX[B]
	[10] -1	0	0xf0000000 - 0xefffffff (0x0) MX[B]O
	[11] -1	0	0xfeb80000 - 0xfebfffff (0x80000) MX[B](B)
	[12] -1	0	0xe8000000 - 0xefffffff (0x8000000) MX[B](B)
	[13] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[14] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[15] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[18] -1	0	0x0000df40 - 0x0000df7f (0x40) IX[B]
	[19] -1	0	0x0000edc0 - 0x0000edff (0x40) IX[B]
	[20] -1	0	0x0000ee00 - 0x0000eeff (0x100) IX[B]
	[21] -1	0	0x0000eda0 - 0x0000edbf (0x20) IX[B]
	[22] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[23] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[24] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[25] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[26] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[27] -1	0	0x0000ff20 - 0x0000ff3f (0x20) IX[B]
	[28] -1	0	0x0000ff60 - 0x0000ff7f (0x20) IX[B]
	[29] -1	0	0x0000ff80 - 0x0000ff9f (0x20) IX[B]
	[30] -1	0	0x0000ed98 - 0x0000ed9f (0x8) IX[B](B)
	[31] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[32] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Video Driver, version 2.0
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.1.0
	ABI class: X.Org Video Driver, version 2.0
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 0.1.0
	ABI class: X.Org Video Driver, version 2.0
(**) intel(0): Depth 24, (--) framebuffer bpp 32
(==) intel(0): RGB weight 888
(==) intel(0): Default visual is TrueColor
(II) intel(0): Integrated Graphics Chipset: Intel(R) 865G
(--) intel(0): Chipset: "865G"
(--) intel(0): Linear framebuffer at 0xE8000000
(--) intel(0): IO registers at addr 0xFEB80000
(II) intel(0): 1 display pipe available.
(==) intel(0): Using EXA for acceleration
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"(II) Module "ddc" already built-in
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"(II) Module "i2c" already built-in
(II) intel(0): Output VGA using monitor section DELL E773c
(II) intel(0): I2C bus "CRTDDC_A" initialized.
(II) intel(0): I2C bus "DVODDC_D" initialized.
(II) Loading sub module "sil164"
(II) LoadModule: "sil164"
(II) Loading /usr/lib/xorg/modules/drivers//sil164.so
(II) Module sil164: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Video Driver, version 2.0
(II) intel(0): I2C bus "DVOI2C_E" initialized.
(II) Loading sub module "ch7xxx"
(II) LoadModule: "ch7xxx"
(II) Loading /usr/lib/xorg/modules/drivers//ch7xxx.so
(II) Module ch7xxx: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Video Driver, version 2.0
(II) intel(0): I2C bus "DVOI2C_E" removed.
(II) intel(0): I2C bus "DVOI2C_E" initialized.
(II) Loading sub module "ivch"
(II) LoadModule: "ivch"
(II) Loading /usr/lib/xorg/modules/drivers//ivch.so
(II) Module ivch: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Video Driver, version 2.0
(II) intel(0): I2C bus "DVOI2C_E" removed.
(II) intel(0): I2C bus "DVOI2C_B" initialized.
(EE) intel(0): ivch detect failed due to address mismatch (0 vs 2)
(II) Loading sub module "tfp410"
(II) LoadModule: "tfp410"
(II) Loading /usr/lib/xorg/modules/drivers//tfp410.so
(II) Module tfp410: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Video Driver, version 2.0
(II) intel(0): I2C bus "DVOI2C_B" removed.
(II) intel(0): I2C bus "DVOI2C_E" initialized.
(II) Loading sub module "ch7017"
(II) LoadModule: "ch7017"
(II) Loading /usr/lib/xorg/modules/drivers//ch7017.so
(II) Module ch7017: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Video Driver, version 2.0
(II) intel(0): I2C bus "DVOI2C_E" removed.
(II) intel(0): I2C bus "DVOI2C_E" initialized.
(II) intel(0): I2C bus "DVOI2C_E" removed.
(II) intel(0): I2C bus "DVODDC_D" removed.
(II) intel(0): I2C device "CRTDDC_A:ddc2" registered at address 0xA0.
(II) intel(0): EDID vendor "DEL", prod id 53253
(II) intel(0): Using EDID range info for horizontal sync
(II) intel(0): Using EDID range info for vertical refresh
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(0): Modeline "640x480"x84.6   35.00  640 664 728 816  480 483 487 507 -hsync +vsync (42.9 kHz)
(II) intel(0): Modeline "800x600"x84.9   56.75  800 848 928 1056  600 603 607 633 -hsync +vsync (53.7 kHz)
(II) intel(0): Modeline "1024x768"x84.9   94.50  1024 1096 1200 1376  768 771 775 809 -hsync +vsync (68.7 kHz)
(II) intel(0): Modeline "1280x1024"x59.9  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync (63.7 kHz)
(II) intel(0): Modeline "1152x864"x74.8  104.00  1152 1224 1344 1536  864 867 871 905 -hsync +vsync (67.7 kHz)
(II) intel(0): EDID vendor "DEL", prod id 53253
(II) intel(0): Output VGA connected
(II) intel(0): Output VGA using initial mode 1024x768
(II) intel(0): detected 128 kB GTT.
(II) intel(0): detected 892 kB stolen memory.
(==) intel(0): video overlay key set to 0x101fe
(==) intel(0): Will not try to enable page flipping
(==) intel(0): Triple buffering disabled
(==) intel(0): Using gamma correction (1.0, 1.0, 1.0)
(**) intel(0): Display dimensions: (320, 240) mm
(**) intel(0): DPI set to (101, 135)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "exa"
(II) LoadModule: "exa"
(II) Loading /usr/lib/xorg/modules//libexa.so
(II) Module exa: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 2.2.0
	ABI class: X.Org Video Driver, version 2.0
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"(II) Module "ramdac" already built-in
(II) intel(0): Comparing regs from server start up to After PreInit
(==) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xfeb80000 - 0xfebfffff (0x80000) MS[B]
	[1] 0	0	0xe8000000 - 0xefffffff (0x8000000) MS[B]
	[2] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[3] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[4] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[5] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[6] -1	0	0xfeafd000 - 0xfeafdfff (0x1000) MX[B]
	[7] -1	0	0xfeafe000 - 0xfeafffff (0x2000) MX[B]
	[8] -1	0	0xfeb7f900 - 0xfeb7f9ff (0x100) MX[B]
	[9] -1	0	0xfeb7fa00 - 0xfeb7fbff (0x200) MX[B]
	[10] -1	0	0xfeb7fc00 - 0xfeb7ffff (0x400) MX[B]
	[11] -1	0	0xffa80800 - 0xffa80bff (0x400) MX[B]
	[12] -1	0	0xf0000000 - 0xefffffff (0x0) MX[B]O
	[13] -1	0	0xfeb80000 - 0xfebfffff (0x80000) MX[B](B)
	[14] -1	0	0xe8000000 - 0xefffffff (0x8000000) MX[B](B)
	[15] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
	[16] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
	[17] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
	[18] 0	0	0x0000ed98 - 0x0000ed9f (0x8) IS[B]
	[19] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[20] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[21] -1	0	0x0000df40 - 0x0000df7f (0x40) IX[B]
	[22] -1	0	0x0000edc0 - 0x0000edff (0x40) IX[B]
	[23] -1	0	0x0000ee00 - 0x0000eeff (0x100) IX[B]
	[24] -1	0	0x0000eda0 - 0x0000edbf (0x20) IX[B]
	[25] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[26] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[27] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[28] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[29] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[30] -1	0	0x0000ff20 - 0x0000ff3f (0x20) IX[B]
	[31] -1	0	0x0000ff60 - 0x0000ff7f (0x20) IX[B]
	[32] -1	0	0x0000ff80 - 0x0000ff9f (0x20) IX[B]
	[33] -1	0	0x0000ed98 - 0x0000ed9f (0x8) IX[B](B)
	[34] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[35] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) intel(0): Kernel reported 240640 total, 1 used
(II) intel(0): I830CheckAvailableMemory: 962556 kB available
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: Searching for BusID pci:0000:00:02.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: drmOpenMinor returns 8
drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
(II) [drm] DRM interface version 1.3
(II) [drm] DRM open master succeeded.
(II) intel(0): [drm] Using the DRM lock SAREA also for drawables.
(II) intel(0): [drm] framebuffer mapped by ddx driver
(II) intel(0): [drm] added 1 reserved context for kernel
(II) intel(0): X context handle = 0x1
(II) intel(0): [drm] installed DRM signal handler
(==) intel(0): VideoRam: 131072 KB
(**) intel(0): Framebuffer compression disabled
(**) intel(0): Tiling enabled
(II) intel(0): Attempting memory allocation with tiled buffers.
(II) intel(0): Success.
(II) intel(0): Increasing the scanline pitch to allow tiling mode (1280 -> 2048).
(II) intel(0): [drm] Registers = 0xfeb80000
(II) intel(0): [drm] ring buffer = 0xe8000000
(II) intel(0): [drm] mapped front buffer at 0xe9000000, handle = 0xe9000000
(II) intel(0): [drm] mapped back buffer at 0xec000000, handle = 0xec000000
(II) intel(0): [drm] mapped depth buffer at 0xed000000, handle = 0xed000000
(II) intel(0): [drm] mapped classic textures at 0xee000000, handle = 0xee000000
(II) intel(0): [drm] Initialized kernel agp heap manager, 33554432
(II) intel(0): [dri] visual configs initialized
(II) intel(0): Page Flipping disabled
(==) intel(0): Write-combining range (0xe8000000,0x8000000)
(II) intel(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(WW) intel(0): EXA greedy migration mode enabled.
(II) EXA(0): Forcing greedy migration option
(II) EXA(0): Offscreen pixmap area of 31457280 bytes
(II) EXA(0): Driver registered support for the following operations:
(II)         Solid
(II)         Copy
(II)         Composite (RENDER acceleration)
(==) intel(0): Backing store disabled
(==) intel(0): Silken mouse enabled
(II) intel(0): Initializing HW Cursor
(II) intel(0): [DRI] installation complete
(II) intel(0): xf86BindGARTMemory: bind key 0 at 0x000df000 (pgoffset 223)
(II) intel(0): xf86BindGARTMemory: bind key 1 at 0x01000000 (pgoffset 4096)
(II) intel(0): xf86BindGARTMemory: bind key 2 at 0x02000000 (pgoffset 8192)
(II) intel(0): xf86BindGARTMemory: bind key 3 at 0x04000000 (pgoffset 16384)
(II) intel(0): xf86BindGARTMemory: bind key 4 at 0x05000000 (pgoffset 20480)
(II) intel(0): xf86BindGARTMemory: bind key 5 at 0x06000000 (pgoffset 24576)
(II) intel(0): Fixed memory allocation layout:
(II) intel(0): 0x00000000-0x0001ffff: ring buffer (128 kB)
(II) intel(0): 0x00020000-0x00024fff: HW cursors (20 kB)
(II) intel(0): 0x00025000-0x0002cfff: logical 3D context (32 kB)
(II) intel(0): 0x000df000:            end of stolen memory
(II) intel(0): 0x000df000-0x000dffff: overlay registers (4 kB, 0x0000000036cf9000 physical
)
(II) intel(0): 0x01000000-0x01ffffff: front buffer (10240 kB) X tiled
(II) intel(0): 0x02000000-0x03dfffff: exa offscreen (30720 kB)
(II) intel(0): 0x04000000-0x04ffffff: back buffer (10240 kB) X tiled
(II) intel(0): 0x05000000-0x05ffffff: depth buffer (10240 kB) X tiled
(II) intel(0): 0x06000000-0x07ffffff: classic textures (32768 kB)
(II) intel(0): 0x08000000:            end of aperture
(II) intel(0): Output configuration:
(II) intel(0):   Pipe A is on
(II) intel(0):   Display plane A is now enabled and connected to pipe A.
(II) intel(0):   Output VGA is connected to pipe A
(II) intel(0): [drm] dma control initialized, using IRQ 16
(II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
(**) Option "dpms"
(**) intel(0): DPMS enabled
(II) intel(0): Set up overlay video
(II) intel(0): direct rendering: Enabled
(--) RandR disabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension XAccessControlExtension
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 9, (OK)
drmOpenByBusid: Searching for BusID pci:0000:00:02.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 9, (OK)
drmOpenByBusid: drmOpenMinor returns 9
drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
(WW) AIGLX: 3D driver claims to not support visual 0x23
(WW) AIGLX: 3D driver claims to not support visual 0x24
(WW) AIGLX: 3D driver claims to not support visual 0x25
(WW) AIGLX: 3D driver claims to not support visual 0x26
(WW) AIGLX: 3D driver claims to not support visual 0x27
(WW) AIGLX: 3D driver claims to not support visual 0x28
(WW) AIGLX: 3D driver claims to not support visual 0x29
(WW) AIGLX: 3D driver claims to not support visual 0x2a
(WW) AIGLX: 3D driver claims to not support visual 0x2b
(WW) AIGLX: 3D driver claims to not support visual 0x2c
(WW) AIGLX: 3D driver claims to not support visual 0x2d
(WW) AIGLX: 3D driver claims to not support visual 0x2e
(WW) AIGLX: 3D driver claims to not support visual 0x2f
(WW) AIGLX: 3D driver claims to not support visual 0x30
(WW) AIGLX: 3D driver claims to not support visual 0x31
(WW) AIGLX: 3D driver claims to not support visual 0x32
(II) AIGLX: Loaded and initialized /usr/lib/dri/i915_dri.so
(II) GLX: Initialized DRI GL provider for screen 0
(II) intel(0): Setting screen physical size to 310 x 230
(**) Option "CoreKeyboard"
(**) Generic Keyboard: always reports core events
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Generic Keyboard: XkbModel: "pc105"
(**) Option "XkbLayout" "us"
(**) Generic Keyboard: XkbLayout: "us"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(**) Option "Protocol" "ImPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ImPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: always reports core events
(**) Option "Device" "/dev/input/mice"
(**) Option "Emulate3Buttons" "true"
(**) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(**) Configured Mouse: Sensitivity: 1
(II) evaluating device (Configured Mouse)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) evaluating device (Generic Keyboard)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) Configured Mouse: ps2EnableDataReporting: succeeded
(II) intel(0): EDID vendor "DEL", prod id 53253
(II) intel(0): Using hsync ranges from config file
(II) intel(0): Using vrefresh ranges from config file
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(0): Modeline "640x480"x84.6   35.00  640 664 728 816  480 483 487 507 -hsync +vsync (42.9 kHz)
(II) intel(0): Modeline "800x600"x84.9   56.75  800 848 928 1056  600 603 607 633 -hsync +vsync (53.7 kHz)
(II) intel(0): Modeline "1024x768"x84.9   94.50  1024 1096 1200 1376  768 771 775 809 -hsync +vsync (68.7 kHz)
(II) intel(0): Modeline "1280x1024"x59.9  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync (63.7 kHz)
(II) intel(0): Modeline "1152x864"x74.8  104.00  1152 1224 1344 1536  864 867 871 905 -hsync +vsync (67.7 kHz)
(II) intel(0): EDID vendor "DEL", prod id 53253
SetClientVersion: 0 9
(II) intel(0): EDID vendor "DEL", prod id 53253
(II) intel(0): Using hsync ranges from config file
(II) intel(0): Using vrefresh ranges from config file
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(0): Modeline "640x480"x84.6   35.00  640 664 728 816  480 483 487 507 -hsync +vsync (42.9 kHz)
(II) intel(0): Modeline "800x600"x84.9   56.75  800 848 928 1056  600 603 607 633 -hsync +vsync (53.7 kHz)
(II) intel(0): Modeline "1024x768"x84.9   94.50  1024 1096 1200 1376  768 771 775 809 -hsync +vsync (68.7 kHz)
(II) intel(0): Modeline "1280x1024"x59.9  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync (63.7 kHz)
(II) intel(0): Modeline "1152x864"x74.8  104.00  1152 1224 1344 1536  864 867 871 905 -hsync +vsync (67.7 kHz)
(II) intel(0): EDID vendor "DEL", prod id 53253
(II) intel(0): EDID vendor "DEL", prod id 53253
(II) intel(0): Using hsync ranges from config file
(II) intel(0): Using vrefresh ranges from config file
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(0): Modeline "640x480"x84.6   35.00  640 664 728 816  480 483 487 507 -hsync +vsync (42.9 kHz)
(II) intel(0): Modeline "800x600"x84.9   56.75  800 848 928 1056  600 603 607 633 -hsync +vsync (53.7 kHz)
(II) intel(0): Modeline "1024x768"x84.9   94.50  1024 1096 1200 1376  768 771 775 809 -hsync +vsync (68.7 kHz)
(II) intel(0): Modeline "1280x1024"x59.9  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync (63.7 kHz)
(II) intel(0): Modeline "1152x864"x74.8  104.00  1152 1224 1344 1536  864 867 871 905 -hsync +vsync (67.7 kHz)
(II) intel(0): EDID vendor "DEL", prod id 53253
(II) intel(0): EDID vendor "DEL", prod id 53253
(II) intel(0): Using hsync ranges from config file
(II) intel(0): Using vrefresh ranges from config file
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(0): Modeline "640x480"x84.6   35.00  640 664 728 816  480 483 487 507 -hsync +vsync (42.9 kHz)
(II) intel(0): Modeline "800x600"x84.9   56.75  800 848 928 1056  600 603 607 633 -hsync +vsync (53.7 kHz)
(II) intel(0): Modeline "1024x768"x84.9   94.50  1024 1096 1200 1376  768 771 775 809 -hsync +vsync (68.7 kHz)
(II) intel(0): Modeline "1280x1024"x59.9  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync (63.7 kHz)
(II) intel(0): Modeline "1152x864"x74.8  104.00  1152 1224 1344 1536  864 867 871 905 -hsync +vsync (67.7 kHz)
(II) intel(0): EDID vendor "DEL", prod id 53253

---

### Post by tjwoosta on 2009-04-09
well..

everything that starts with a (WW) is a warning message  (they can usually be safely ignored)


everything that starts with an (EE) is an error message  (this is usually what you should look for)


i can only see one error

(EE) intel(0): ivch detect failed due to address mismatch (0 vs 2)


what exactly this means is another question

i honestly have no idea what it means


there are only a handfull of things i can think of that might help

1. you could try to add   

Option      "NoAccel"

to your xorg.conf under the graphics driver

(so it looks like this)


Section "Device"

Identifier "Intel Corporation 82865G Integrated Graphics Controller"
Driver "intel"
BusID "PCI:0:2:0"
Option      "NoAccel"

EndSection

if this doesnt work i would try to remove and reinstall xf86-video-intel


if none of this works, im lost

maybe someone else can help though now that more information is available

---

