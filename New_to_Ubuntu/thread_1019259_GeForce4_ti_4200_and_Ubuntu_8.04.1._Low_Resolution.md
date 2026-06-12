---
title: "GeForce4 ti 4200 and Ubuntu 8.04.1. Low Resolution and LCD detected as CRT"
date: 2008-12-22
forum: New to Ubuntu
---

### Post by thebloggu on 2008-12-22
I did a fresh install of Ubuntu 8.04.1 and immediately upgraded to 8.10. In 8.10 no restricted driver appeared on the list, so i tried to install them through Synaptic (nvidia-glx-96 since my card is supported in 71 and 96). Simply, the nvidia driver, didn't appear to be in use. Then i tried envy. I could install the drivers and they worked, but with low resolution and my LCD monitor detected as CRT. Then, because i was told on ubuntu irc channel, i uninstalled envy as well as the drivers and tried to install them through Synaptic again. They did work but the result was the same as of envy. From there i tried to edit xorg.conf both manually and from Xorg -configure and dpgk-reconfigure xserver-xorg with the help of some people in the channel. Still the same.

I then decided to do a fresh install of 8.04.1. This time drivers appeared in restrited drivers and installed normally. After restart everything was the same as I stated above.

My xorg.conf

```
Section "ServerLayout"
	Identifier     "X.org Configured"
	Screen      0  "Screen0" 0 0
	InputDevice    "Mouse0" "CorePointer"
	InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
	RgbPath      "/etc/X11/rgb"
	ModulePath   "/usr/lib/xorg/modules"
	FontPath     "/usr/share/fonts/X11/misc"
	FontPath     "/usr/share/fonts/X11/cyrillic"
	FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/Type1"
	FontPath     "/usr/share/fonts/X11/100dpi"
	FontPath     "/usr/share/fonts/X11/75dpi"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load  "extmod"
	Load  "record"
	Load  "GLcore"
	Load  "dbe"
	Load  "dri"
	Load  "xtrap"
	Load  "glx"
EndSection

Section "InputDevice"
	Identifier  "Keyboard0"
	Driver      "kbd"
EndSection

Section "InputDevice"
	Identifier  "Mouse0"
	Driver      "mouse"
	Option	    "Protocol" "auto"
	Option	    "Device" "/dev/input/mice"
	Option	    "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
	Identifier   "Monitor0"
	VendorName   "Monitor Vendor"
	ModelName    "Monitor Model"
EndSection

Section "Device"
	Identifier  "Card0"
	Driver      "nvidia"
	VendorName  "nVidia Corporation"
	BoardName   "NV25 [GeForce4 Ti 4200]"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "Screen0"
	Device     "Card0"
	Monitor    "Monitor0"
	SubSection "Display"
		Viewport   0 0
		Depth     1
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     4
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     8
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     15
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     16
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

```

My Xor.0.log

```
This is a pre-release version of the X server from The X.Org Foundation.
It is not supported in any way.
Bugs may be filed in the bugzilla at http://bugs.freedesktop.org/.
Select the "xorg" product for bugs you find in this release.
Before reporting bugs in pre-release versions please check the
latest version in the X.Org Foundation git repository.
See http://wiki.x.org/wiki/GitPage for git access instructions.

X.Org X Server 1.4.0.90
Release Date: 5 September 2007
X Protocol Version 11, Revision 0
Build Operating System: Linux Ubuntu (xorg-server 2:1.4.1~git20080131-1ubuntu9.2)
Current Operating System: Linux gu 2.6.24-22-generic #1 SMP Mon Nov 24 18:32:42 UTC 2008 i686
Build Date: 13 June 2008  01:08:21AM
 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Tue Dec 23 03:15:32 2008
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "X.org Configured"
(**) |-->Screen "Screen0" (0)
(**) |   |-->Monitor "Monitor0"
(**) |   |-->Device "Card0"
(**) |-->Input Device "Mouse0"
(**) |-->Input Device "Keyboard0"
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(==) Including the default font path /usr/share/fonts/X11/misc,/usr/share/fonts/X11/cyrillic,/usr/share/fonts/X11/100dpi/:unscaled,/usr/share/fonts/X11/75dpi/:unscaled,/usr/share/fonts/X11/Type1,/usr/share/fonts/X11/100dpi,/usr/share/fonts/X11/75dpi,/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType.
(**) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/cyrillic,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(**) RgbPath set to "/etc/X11/rgb"
(**) ModulePath set to "/usr/lib/xorg/modules"
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
(II) PCI: 00:00:0: chip 8086,2530 card 1043,8030 rev 04 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 8086,2532 card 0000,0000 rev 04 class 06,04,00 hdr 01
(II) PCI: 00:1e:0: chip 8086,244e card 0000,0000 rev 04 class 06,04,00 hdr 01
(II) PCI: 00:1f:0: chip 8086,2440 card 0000,0000 rev 04 class 06,01,00 hdr 80
(II) PCI: 00:1f:1: chip 8086,244b card 1043,8028 rev 04 class 01,01,80 hdr 00
(II) PCI: 00:1f:2: chip 8086,2442 card 1043,8028 rev 04 class 0c,03,00 hdr 00
(II) PCI: 00:1f:3: chip 8086,2443 card 1043,8028 rev 04 class 0c,05,00 hdr 00
(II) PCI: 00:1f:4: chip 8086,2444 card 1043,8028 rev 04 class 0c,03,00 hdr 00
(II) PCI: 01:00:0: chip 10de,0253 card 1462,8702 rev a3 class 03,00,00 hdr 00
(II) PCI: 02:02:0: chip 105a,5275 card 1043,807e rev 01 class 01,04,85 hdr 00
(II) PCI: 02:03:0: chip 13f6,0111 card 1043,80e2 rev 10 class 04,01,00 hdr 00
(II) PCI: 02:04:0: chip 1033,0035 card 807d,0035 rev 41 class 0c,03,10 hdr 80
(II) PCI: 02:04:1: chip 1033,0035 card 807d,0035 rev 41 class 0c,03,10 hdr 00
(II) PCI: 02:04:2: chip 1033,00e0 card 807d,1043 rev 02 class 0c,03,20 hdr 00
(II) PCI: 02:0b:0: chip 10ec,8139 card 10ec,8139 rev 10 class 02,00,00 hdr 00
(II) PCI: 02:0c:0: chip 1102,0002 card 1102,8064 rev 07 class 04,01,00 hdr 80
(II) PCI: 02:0c:1: chip 1102,7002 card 1102,0020 rev 07 class 09,80,00 hdr 80
(II) PCI: End of PCI scan
(II) Intel Bridge workaround enabled
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,2), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xee000000 - 0xef5fffff (0x1600000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xef700000 - 0xf7ffffff (0x8900000) MX[B]
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:30:0), (0,2,2), BCTRL: 0x0006 (VGA_EN is cleared)
(II) Bus 2 I/O range:
	[0] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B]
	[1] -1	0	0x0000a400 - 0x0000a4ff (0x100) IX[B]
	[2] -1	0	0x0000a800 - 0x0000a8ff (0x100) IX[B]
	[3] -1	0	0x0000ac00 - 0x0000acff (0x100) IX[B]
	[4] -1	0	0x0000b000 - 0x0000b0ff (0x100) IX[B]
	[5] -1	0	0x0000b400 - 0x0000b4ff (0x100) IX[B]
	[6] -1	0	0x0000b800 - 0x0000b8ff (0x100) IX[B]
	[7] -1	0	0x0000bc00 - 0x0000bcff (0x100) IX[B]
	[8] -1	0	0x0000c000 - 0x0000c0ff (0x100) IX[B]
	[9] -1	0	0x0000c400 - 0x0000c4ff (0x100) IX[B]
	[10] -1	0	0x0000c800 - 0x0000c8ff (0x100) IX[B]
	[11] -1	0	0x0000cc00 - 0x0000ccff (0x100) IX[B]
	[12] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B]
	[13] -1	0	0x0000d400 - 0x0000d4ff (0x100) IX[B]
	[14] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[15] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B]
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0xeb800000 - 0xedffffff (0x2800000) MX[B]
(II) Bus 2 prefetchable memory range:
	[0] -1	0	0xef600000 - 0xef6fffff (0x100000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(1:0:0) nVidia Corporation NV25 [GeForce4 Ti 4200] rev 163, Mem @ 0xee000000/24, 0xf0000000/27, 0xef800000/19, BIOS @ 0xef7e0000/17
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
(II) PCI Memory resource overlap reduced 0xf8000000 from 0xfbffffff to 0xf7ffffff
(II) Active PCI resource ranges:
	[0] -1	0	0xeb800000 - 0xeb8000ff (0x100) MX[B]
	[1] -1	0	0xec000000 - 0xec0000ff (0x100) MX[B]
	[2] -1	0	0xec800000 - 0xec800fff (0x1000) MX[B]
	[3] -1	0	0xed000000 - 0xed000fff (0x1000) MX[B]
	[4] -1	0	0xed800000 - 0xed803fff (0x4000) MX[B]
	[5] -1	0	0xf8000000 - 0xf7ffffff (0x0) MX[B]O
	[6] -1	0	0xef7e0000 - 0xef7fffff (0x20000) MX[B](B)
	[7] -1	0	0xef800000 - 0xef87ffff (0x80000) MX[B](B)
	[8] -1	0	0xf0000000 - 0xf7ffffff (0x8000000) MX[B](B)
	[9] -1	0	0xee000000 - 0xeeffffff (0x1000000) MX[B](B)
	[10] -1	0	0x0000a000 - 0x0000a007 (0x8) IX[B]
	[11] -1	0	0x0000a400 - 0x0000a41f (0x20) IX[B]
	[12] -1	0	0x0000a800 - 0x0000a8ff (0x100) IX[B]
	[13] -1	0	0x0000b000 - 0x0000b0ff (0x100) IX[B]
	[14] -1	0	0x0000b400 - 0x0000b40f (0x10) IX[B]
	[15] -1	0	0x0000b800 - 0x0000b803 (0x4) IX[B]
	[16] -1	0	0x0000d000 - 0x0000d007 (0x8) IX[B]
	[17] -1	0	0x0000d400 - 0x0000d403 (0x4) IX[B]
	[18] -1	0	0x0000d800 - 0x0000d807 (0x8) IX[B]
	[19] -1	0	0x00009000 - 0x0000901f (0x20) IX[B]
	[20] -1	0	0x0000e800 - 0x0000e80f (0x10) IX[B]
	[21] -1	0	0x00009400 - 0x0000941f (0x20) IX[B]
	[22] -1	0	0x00009800 - 0x0000980f (0x10) IX[B]
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xeb800000 - 0xeb8000ff (0x100) MX[B]
	[1] -1	0	0xec000000 - 0xec0000ff (0x100) MX[B]
	[2] -1	0	0xec800000 - 0xec800fff (0x1000) MX[B]
	[3] -1	0	0xed000000 - 0xed000fff (0x1000) MX[B]
	[4] -1	0	0xed800000 - 0xed803fff (0x4000) MX[B]
	[5] -1	0	0xf8000000 - 0xf7ffffff (0x0) MX[B]O
	[6] -1	0	0xef7e0000 - 0xef7fffff (0x20000) MX[B](B)
	[7] -1	0	0xef800000 - 0xef87ffff (0x80000) MX[B](B)
	[8] -1	0	0xf0000000 - 0xf7ffffff (0x8000000) MX[B](B)
	[9] -1	0	0xee000000 - 0xeeffffff (0x1000000) MX[B](B)
	[10] -1	0	0x0000a000 - 0x0000a007 (0x8) IX[B]
	[11] -1	0	0x0000a400 - 0x0000a41f (0x20) IX[B]
	[12] -1	0	0x0000a800 - 0x0000a8ff (0x100) IX[B]
	[13] -1	0	0x0000b000 - 0x0000b0ff (0x100) IX[B]
	[14] -1	0	0x0000b400 - 0x0000b40f (0x10) IX[B]
	[15] -1	0	0x0000b800 - 0x0000b803 (0x4) IX[B]
	[16] -1	0	0x0000d000 - 0x0000d007 (0x8) IX[B]
	[17] -1	0	0x0000d400 - 0x0000d403 (0x4) IX[B]
	[18] -1	0	0x0000d800 - 0x0000d807 (0x8) IX[B]
	[19] -1	0	0x00009000 - 0x0000901f (0x20) IX[B]
	[20] -1	0	0x0000e800 - 0x0000e80f (0x10) IX[B]
	[21] -1	0	0x00009400 - 0x0000941f (0x20) IX[B]
	[22] -1	0	0x00009800 - 0x0000980f (0x10) IX[B]
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
	[4] -1	0	0xeb800000 - 0xeb8000ff (0x100) MX[B]
	[5] -1	0	0xec000000 - 0xec0000ff (0x100) MX[B]
	[6] -1	0	0xec800000 - 0xec800fff (0x1000) MX[B]
	[7] -1	0	0xed000000 - 0xed000fff (0x1000) MX[B]
	[8] -1	0	0xed800000 - 0xed803fff (0x4000) MX[B]
	[9] -1	0	0xf8000000 - 0xf7ffffff (0x0) MX[B]O
	[10] -1	0	0xef7e0000 - 0xef7fffff (0x20000) MX[B](B)
	[11] -1	0	0xef800000 - 0xef87ffff (0x80000) MX[B](B)
	[12] -1	0	0xf0000000 - 0xf7ffffff (0x8000000) MX[B](B)
	[13] -1	0	0xee000000 - 0xeeffffff (0x1000000) MX[B](B)
	[14] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[15] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[16] -1	0	0x0000a000 - 0x0000a007 (0x8) IX[B]
	[17] -1	0	0x0000a400 - 0x0000a41f (0x20) IX[B]
	[18] -1	0	0x0000a800 - 0x0000a8ff (0x100) IX[B]
	[19] -1	0	0x0000b000 - 0x0000b0ff (0x100) IX[B]
	[20] -1	0	0x0000b400 - 0x0000b40f (0x10) IX[B]
	[21] -1	0	0x0000b800 - 0x0000b803 (0x4) IX[B]
	[22] -1	0	0x0000d000 - 0x0000d007 (0x8) IX[B]
	[23] -1	0	0x0000d400 - 0x0000d403 (0x4) IX[B]
	[24] -1	0	0x0000d800 - 0x0000d807 (0x8) IX[B]
	[25] -1	0	0x00009000 - 0x0000901f (0x20) IX[B]
	[26] -1	0	0x0000e800 - 0x0000e80f (0x10) IX[B]
	[27] -1	0	0x00009400 - 0x0000941f (0x20) IX[B]
	[28] -1	0	0x00009800 - 0x0000980f (0x10) IX[B]
(II) "extmod" will be loaded. This was enabled by default and also specified in the config file.
(II) "dbe" will be loaded. This was enabled by default and also specified in the config file.
(II) "glx" will be loaded. This was enabled by default and also specified in the config file.
(II) "freetype" will be loaded by default.
(II) "record" will be loaded. This was enabled by default and also specified in the config file.
(II) "dri" will be loaded. This was enabled by default and also specified in the config file.
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
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension RECORD
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
(II) LoadModule: "xtrap"
(II) Loading /usr/lib/xorg/modules/extensions//libxtrap.so
(II) Module xtrap: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension DEC-XTRAP
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.1
(II) NVIDIA GLX Module  96.43.05  Tue Jan 22 20:11:30 PST 2008
(II) Loading extension GLX
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 1.4.0.90, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Video Driver
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 1.4.0, module version = 1.2.3
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.0
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 1.4.0, module version = 1.2.2
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.0
(II) NVIDIA dlloader X Driver  96.43.05  Tue Jan 22 19:38:46 PST 2008
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 01:00:0
(--) Chipset NVIDIA GPU found
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"(II) Module "ramdac" already built-in
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.2.0
	ABI class: X.Org Video Driver, version 2.0
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xeb800000 - 0xeb8000ff (0x100) MX[B]
	[5] -1	0	0xec000000 - 0xec0000ff (0x100) MX[B]
	[6] -1	0	0xec800000 - 0xec800fff (0x1000) MX[B]
	[7] -1	0	0xed000000 - 0xed000fff (0x1000) MX[B]
	[8] -1	0	0xed800000 - 0xed803fff (0x4000) MX[B]
	[9] -1	0	0xf8000000 - 0xf7ffffff (0x0) MX[B]O
	[10] -1	0	0xef7e0000 - 0xef7fffff (0x20000) MX[B](B)
	[11] -1	0	0xef800000 - 0xef87ffff (0x80000) MX[B](B)
	[12] -1	0	0xf0000000 - 0xf7ffffff (0x8000000) MX[B](B)
	[13] -1	0	0xee000000 - 0xeeffffff (0x1000000) MX[B](B)
	[14] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[15] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[16] -1	0	0x0000a000 - 0x0000a007 (0x8) IX[B]
	[17] -1	0	0x0000a400 - 0x0000a41f (0x20) IX[B]
	[18] -1	0	0x0000a800 - 0x0000a8ff (0x100) IX[B]
	[19] -1	0	0x0000b000 - 0x0000b0ff (0x100) IX[B]
	[20] -1	0	0x0000b400 - 0x0000b40f (0x10) IX[B]
	[21] -1	0	0x0000b800 - 0x0000b803 (0x4) IX[B]
	[22] -1	0	0x0000d000 - 0x0000d007 (0x8) IX[B]
	[23] -1	0	0x0000d400 - 0x0000d403 (0x4) IX[B]
	[24] -1	0	0x0000d800 - 0x0000d807 (0x8) IX[B]
	[25] -1	0	0x00009000 - 0x0000901f (0x20) IX[B]
	[26] -1	0	0x0000e800 - 0x0000e80f (0x10) IX[B]
	[27] -1	0	0x00009400 - 0x0000941f (0x20) IX[B]
	[28] -1	0	0x00009800 - 0x0000980f (0x10) IX[B]
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xeb800000 - 0xeb8000ff (0x100) MX[B]
	[5] -1	0	0xec000000 - 0xec0000ff (0x100) MX[B]
	[6] -1	0	0xec800000 - 0xec800fff (0x1000) MX[B]
	[7] -1	0	0xed000000 - 0xed000fff (0x1000) MX[B]
	[8] -1	0	0xed800000 - 0xed803fff (0x4000) MX[B]
	[9] -1	0	0xf8000000 - 0xf7ffffff (0x0) MX[B]O
	[10] -1	0	0xef7e0000 - 0xef7fffff (0x20000) MX[B](B)
	[11] -1	0	0xef800000 - 0xef87ffff (0x80000) MX[B](B)
	[12] -1	0	0xf0000000 - 0xf7ffffff (0x8000000) MX[B](B)
	[13] -1	0	0xee000000 - 0xeeffffff (0x1000000) MX[B](B)
	[14] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[15] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[16] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[17] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[18] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[19] -1	0	0x0000a000 - 0x0000a007 (0x8) IX[B]
	[20] -1	0	0x0000a400 - 0x0000a41f (0x20) IX[B]
	[21] -1	0	0x0000a800 - 0x0000a8ff (0x100) IX[B]
	[22] -1	0	0x0000b000 - 0x0000b0ff (0x100) IX[B]
	[23] -1	0	0x0000b400 - 0x0000b40f (0x10) IX[B]
	[24] -1	0	0x0000b800 - 0x0000b803 (0x4) IX[B]
	[25] -1	0	0x0000d000 - 0x0000d007 (0x8) IX[B]
	[26] -1	0	0x0000d400 - 0x0000d403 (0x4) IX[B]
	[27] -1	0	0x0000d800 - 0x0000d807 (0x8) IX[B]
	[28] -1	0	0x00009000 - 0x0000901f (0x20) IX[B]
	[29] -1	0	0x0000e800 - 0x0000e80f (0x10) IX[B]
	[30] -1	0	0x00009400 - 0x0000941f (0x20) IX[B]
	[31] -1	0	0x00009800 - 0x0000980f (0x10) IX[B]
	[32] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[33] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(==) NVIDIA(0): Depth 24, (==) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(WW) NVIDIA(GPU-0): Unable to read EDID for display device CRT-1
(II) NVIDIA(0): NVIDIA GPU GeForce4 Ti 4200 at PCI:1:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 131072 kBytes
(--) NVIDIA(0): VideoBIOS: 04.25.00.29.00
(II) NVIDIA(0): Detected AGP rate: 4X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce4 Ti 4200 at PCI:1:0:0:
(--) NVIDIA(0):     CRT-1
(--) NVIDIA(0): CRT-1: 350.0 MHz maximum pixel clock
(II) NVIDIA(0): Assigned Display Device: CRT-1
(WW) NVIDIA(0): 
(WW) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
(WW) NVIDIA(0):     will be used as the requested mode.
(WW) NVIDIA(0): 
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "nvidia-auto-select"
(II) NVIDIA(0): Virtual screen size determined to be 640 x 480
(WW) NVIDIA(0): Unable to get display device CRT-1's EDID; cannot compute DPI
(WW) NVIDIA(0):     from CRT-1's EDID.
(==) NVIDIA(0): DPI set to (75, 75); computed from built-in default
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xef800000 - 0xef87ffff (0x80000) MX[B]
	[1] 0	0	0xf0000000 - 0xf7ffffff (0x8000000) MX[B]
	[2] 0	0	0xee000000 - 0xeeffffff (0x1000000) MX[B]
	[3] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[4] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[5] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[6] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[7] -1	0	0xeb800000 - 0xeb8000ff (0x100) MX[B]
	[8] -1	0	0xec000000 - 0xec0000ff (0x100) MX[B]
	[9] -1	0	0xec800000 - 0xec800fff (0x1000) MX[B]
	[10] -1	0	0xed000000 - 0xed000fff (0x1000) MX[B]
	[11] -1	0	0xed800000 - 0xed803fff (0x4000) MX[B]
	[12] -1	0	0xf8000000 - 0xf7ffffff (0x0) MX[B]O
	[13] -1	0	0xef7e0000 - 0xef7fffff (0x20000) MX[B](B)
	[14] -1	0	0xef800000 - 0xef87ffff (0x80000) MX[B](B)
	[15] -1	0	0xf0000000 - 0xf7ffffff (0x8000000) MX[B](B)
	[16] -1	0	0xee000000 - 0xeeffffff (0x1000000) MX[B](B)
	[17] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
	[18] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
	[19] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
	[20] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[21] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[22] -1	0	0x0000a000 - 0x0000a007 (0x8) IX[B]
	[23] -1	0	0x0000a400 - 0x0000a41f (0x20) IX[B]
	[24] -1	0	0x0000a800 - 0x0000a8ff (0x100) IX[B]
	[25] -1	0	0x0000b000 - 0x0000b0ff (0x100) IX[B]
	[26] -1	0	0x0000b400 - 0x0000b40f (0x10) IX[B]
	[27] -1	0	0x0000b800 - 0x0000b803 (0x4) IX[B]
	[28] -1	0	0x0000d000 - 0x0000d007 (0x8) IX[B]
	[29] -1	0	0x0000d400 - 0x0000d403 (0x4) IX[B]
	[30] -1	0	0x0000d800 - 0x0000d807 (0x8) IX[B]
	[31] -1	0	0x00009000 - 0x0000901f (0x20) IX[B]
	[32] -1	0	0x0000e800 - 0x0000e80f (0x10) IX[B]
	[33] -1	0	0x00009400 - 0x0000941f (0x20) IX[B]
	[34] -1	0	0x00009800 - 0x0000980f (0x10) IX[B]
	[35] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[36] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) NVIDIA(0): Initialized GART.
(II) NVIDIA(0): Built-in logo is bigger than the screen.
(II) NVIDIA(0): Setting mode "nvidia-auto-select"
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(II) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
(==) RandR enabled
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
(II) Initializing extension GLX
(**) Option "Protocol" "auto"
(**) Mouse0: Device: "/dev/input/mice"
(**) Mouse0: Protocol: "auto"
(**) Option "CorePointer"
(**) Mouse0: always reports core events
(**) Option "Device" "/dev/input/mice"
(==) Mouse0: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5 6 7"
(**) Mouse0: ZAxisMapping: buttons 4, 5, 6 and 7
(**) Mouse0: Buttons: 11
(**) Mouse0: Sensitivity: 1
(**) Option "CoreKeyboard"
(**) Keyboard0: always reports core events
(**) Option "Protocol" "standard"
(**) Keyboard0: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Keyboard0: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Keyboard0: XkbModel: "pc105"
(**) Option "XkbLayout" "us"
(**) Keyboard0: XkbLayout: "us"
(**) Option "CustomKeycodes" "off"
(**) Keyboard0: CustomKeycodes disabled
(II) evaluating device (Keyboard0)
(II) XINPUT: Adding extended input device "Keyboard0" (type: KEYBOARD)
(II) evaluating device (Mouse0)
(II) XINPUT: Adding extended input device "Mouse0" (type: MOUSE)
(--) Mouse0: PnP-detected protocol: "ExplorerPS/2"
(II) Mouse0: ps2EnableDataReporting: succeeded
Could not init font path element /usr/share/fonts/X11/cyrillic, removing from list!
(II) Mouse autoprobe: Disabling secondary wheel
```

---

### Post by overdrank on 2008-12-22
Hi and have you tried using the command ```
gksu displayconfig-gtk
``` and adjust.

---

### Post by thebloggu on 2008-12-23
Thank you ! It worked

---

