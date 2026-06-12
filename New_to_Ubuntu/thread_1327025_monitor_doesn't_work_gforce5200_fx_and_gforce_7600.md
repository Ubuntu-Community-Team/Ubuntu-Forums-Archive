---
title: "monitor doesn't work gforce5200 fx and gforce 7600"
date: 2009-11-15
forum: New to Ubuntu
---

### Post by anothrguitarist on 2009-11-15
I just plugged in a second graphics card, ultimately trying to get a triple monitor setup, but that's not my main concern right now. After I plugged in this second graphics card (which is in use), I can't get the monitors to show up. I just tried booting from a live cd, and it worked fine.

I tried to reconfigure xorg with sudo dpkg-reconfigure xserver-xorg, but it did nothing. Then I tried something like Xorg :1 -configure, but it said that the number of screens did not match the number of devices.

I also tried editing xorg.conf manually, but I don't think I had the right PCI ID. I tried lspci, but I don't think it gave me the PCI ID. Is there any other way to get the PCI ID, or is there any other way to reconfigure xorg automatically? Thanks.

---

### Post by Jon Monreal on 2009-11-15
> **anothrguitarist said:**
> I just plugged in a second graphics card, ultimately trying to get a triple monitor setup, but that's not my main concern right now. After I plugged in this second graphics card (which is in use), I can't get the monitors to show up. I just tried booting from a live cd, and it worked fine.

I tried to reconfigure xorg with sudo dpkg-reconfigure xserver-xorg, but it did nothing. Then I tried something like Xorg :1 -configure, but it said that the number of screens did not match the number of devices.

I also tried editing xorg.conf manually, but I don't think I had the right PCI ID. I tried lspci, but I don't think it gave me the PCI ID. Is there any other way to get the PCI ID, or is there any other way to reconfigure xorg automatically? Thanks.

You could try typing "sudo lshw" into a terminal to get the PCI ID.

---

### Post by anothrguitarist on 2009-11-15
Is the xorg config file still used in karmic?

---

### Post by Jon Monreal on 2009-11-15
> **anothrguitarist said:**
> Is the xorg config file still used in karmic?

See [http://ubuntuforums.org/showthread.php?t=1260518](http://ubuntuforums.org/showthread.php?t=1260518):

> If the file is present xserver will read from it. If not it will stick with defauts

---

### Post by anothrguitarist on 2009-11-15
Alright, deleting the xorg.conf file worked. 

Now, can someone tell me how to setup triple monitors?

---

### Post by Jon Monreal on 2009-11-15
Take a look at [this]("http://ubuntuforums.org/showthread.php?t=700551") for some information. If you need additional help, please don't hesitate to ask.

---

### Post by anothrguitarist on 2009-11-15
I followed a template on the link you gave me, but it didn't work. When I restarted X, the monitors kept turning on and off, never showing the screen. Here's my xorg.conf file:

```
Section "Files"
	RgbPath      "/usr/X11R6/lib/X11/rgb"
	FontPath     "unix/:7100"
EndSection

Section "Module"
	Load  "dbe"
	Load  "extmod"
	Load  "fbdevhw"
	Load  "glx"
	Load  "record"
	Load  "freetype"
	Load  "type1"
## for nVidia driver
#	Load  "dri"
EndSection

Section "InputDevice"
	Identifier  "Keyboard0"
	Driver      "kbd"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "us"
EndSection

Section "InputDevice"
	Identifier  "Mouse0"
	Driver      "mouse"
	Option	    "Protocol" "IMPS/2"
	Option	    "Device" "/dev/input/mice"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "yes"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "DELL E773c"
    HorizSync       30.0 - 70.0
    VertRefresh     50.0 - 160.0
    Option         "DPMS"
EndSection

Section "Monitor"
	Identifier     "Monitor1"
	VendorName     "Unknown"
	ModelName      "DELL E151FPb"
	HorizSync       31.0 - 60.0
	VertRefresh     56.0 - 76.0
	Option         "DPMS"
EndSection

Section "Monitor"
	Identifier     "Monitor2"
	VendorName     "Unknown"
	ModelName      "ViewSonic A75f"
	HorizSync       30.0 - 70.0
	VertRefresh     50.0 - 160.0
	Option         "DPMS"
EndSection

Section "Device"
    Identifier     "NV PCIX"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce FX 5200"
    BusID          "PCI:3:10:0"
EndSection

Section "Device"
    Identifier     "NV PCIX TwinView"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce FX 5200"
    BusID          "PCI:3:10:0"

	Option      "TwinView"
        Option      "NoTwinViewXineramaInfo"   "true"
        Option      "SecondMonitorHorizSync"   "30.0-95.0"
        Option      "SecondMonitorVertRefresh" "50.0-160.0"
        Option      "TwinViewOrientation"      "RightOf"
        Option      "MetaModes"                "1024x768,1024x768"
        Option      "ConnectedMonitor"         "crt,crt"       
EndSection

Section "Device"
	Identifier     "NV PCI"
	Driver	"nvidia"
	VendorName     "NVIDIA Corporation"
	BoardName      "GeForce 7600 GT"
	BusID          "PCI:2:0:0"
EndSection

Section "Screen"
	Identifier  "Screen PCIX"
	Device      "NV PCIX"
	Monitor     "Monitor0"
	DefaultDepth     24
	SubSection "Display"
		Viewport 0 0
		Depth    24
		Modes    "1024x768" 
	EndSubSection
EndSection

Section "Screen"
	Identifier  "Screen PCIX TwinView"
	Device      "NV PCIX TwinView"
	Monitor     "Monitor1"
	DefaultDepth     24
	SubSection "Display"
		Viewport 0 0
		Depth    24
		Modes    "1024x768" 
	EndSubSection
EndSection

Section "Screen"
	Identifier  "Screen PCI"
	Device      "NV PCI"
	Monitor     "Monitor2"
	DefaultDepth     24
	SubSection "Display"
		Viewport 0 0
		Depth    24
		Modes    "1024x768" 
	EndSubSection
EndSection

Section "ServerLayout"
    Identifier  "BothTwinView"
    Screen      "Screen PCIX TwinView"
    Screen      "Screen PCI" RightOf "Screen PCIX TwinView"
    Option	"Xinerama"	
    InputDevice "Mouse0" "CorePointer"
    InputDevice "Keyboard0" "CoreKeyboard"
EndSection
```

I'm not sure what's wrong with it, although it might be the horizontal and vertical sync areas. I didn't know what mine were, so I just left them as they were in the template.

This also might be of use, the xorg log:


```
X.Org X Server 1.6.4
Release Date: 2009-9-27
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux EnigmaticLinux 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:04:26 UTC 2009 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-14-generic root=UUID=98fdfda3-2f9c-4eb7-9367-c4a1421f86bd ro quiet splash
Build Date: 26 October 2009  05:15:02PM
xorg-server 2:1.6.4-2ubuntu4 (buildd@) 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sun Nov 15 12:26:35 2009
(II) Loader magic: 0x3bc0
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 5.0
	X.Org XInput driver : 4.0
	X.Org Server Extension : 2.0
(II) Loader running on linux
(++) using VT number 7

(--) PCI: (0:2:0:0) 10de:0391:3842:c554 nVidia Corporation G73 [GeForce 7600 GT] rev 161, Mem @ 0xfa000000/16777216, 0xd0000000/268435456, 0xfb000000/16777216, I/O @ 0x00009c00/128, BIOS @ 0x????????/131072
(--) PCI:*(0:3:10:0) 10de:0322:0000:0000 nVidia Corporation NV34 [GeForce FX 5200] rev 161, Mem @ 0xf8000000/16777216, 0xe8000000/134217728, BIOS @ 0x????????/131072
(==) Using default built-in configuration (30 lines)
(==) --- Start of built-in configuration ---
	Section "Device"
		Identifier	"Builtin Default nv Device 0"
		Driver	"nv"
	EndSection
	Section "Screen"
		Identifier	"Builtin Default nv Screen 0"
		Device	"Builtin Default nv Device 0"
	EndSection
	Section "Device"
		Identifier	"Builtin Default vesa Device 0"
		Driver	"vesa"
	EndSection
	Section "Screen"
		Identifier	"Builtin Default vesa Screen 0"
		Device	"Builtin Default vesa Device 0"
	EndSection
	Section "Device"
		Identifier	"Builtin Default fbdev Device 0"
		Driver	"fbdev"
	EndSection
	Section "Screen"
		Identifier	"Builtin Default fbdev Screen 0"
		Device	"Builtin Default fbdev Device 0"
	EndSection
	Section "ServerLayout"
		Identifier	"Builtin Default Layout"
		Screen	"Builtin Default nv Screen 0"
		Screen	"Builtin Default vesa Screen 0"
		Screen	"Builtin Default fbdev Screen 0"
	EndSection
(==) --- End of built-in configuration ---
(==) ServerLayout "Builtin Default Layout"
(**) |-->Screen "Builtin Default nv Screen 0" (0)
(**) |   |-->Monitor "<default monitor>"
(**) |   |-->Device "Builtin Default nv Device 0"
(==) No monitor specified for screen "Builtin Default nv Screen 0".
	Using a default monitor configuration.
(**) |-->Screen "Builtin Default vesa Screen 0" (1)
(**) |   |-->Monitor "<default monitor>"
(**) |   |-->Device "Builtin Default vesa Device 0"
(==) No monitor specified for screen "Builtin Default vesa Screen 0".
	Using a default monitor configuration.
(**) |-->Screen "Builtin Default fbdev Screen 0" (2)
(**) |   |-->Monitor "<default monitor>"
(**) |   |-->Device "Builtin Default fbdev Device 0"
(==) No monitor specified for screen "Builtin Default fbdev Screen 0".
	Using a default monitor configuration.
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
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Cannot locate a core pointer device.
(II) Cannot locate a core keyboard device.
(II) The server relies on HAL to provide the list of input devices.
	If no devices become available, reconfigure HAL or disable AllowEmptyInput.
(II) Open ACPI successful (/var/run/acpid.socket)
(II) System resource ranges:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[5] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[6] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[7] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[8] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[9] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[10] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[11] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[12] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[13] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[14] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[15] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[18] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[19] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[20] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[21] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[22] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[23] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Server Extension
(II) NVIDIA GLX Module  173.14.20  Thu Jun 25 19:49:59 PDT 2009
(II) Loading extension GLX
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions//libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.1.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) LoadModule: "nv"
(II) Loading /usr/lib/xorg/modules/drivers//nv_drv.so
(II) Module nv: vendor="X.Org Foundation"
	compiled for 1.6.3, module version = 2.1.14
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 5.0
(II) LoadModule: "vesa"
(II) Loading /usr/lib/xorg/modules/drivers//vesa_drv.so
(II) Module vesa: vendor="X.Org Foundation"
	compiled for 1.6.3, module version = 2.2.1
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 5.0
(II) LoadModule: "fbdev"
(II) Loading /usr/lib/xorg/modules/drivers//fbdev_drv.so
(II) Module fbdev: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 0.4.0
	ABI class: X.Org Video Driver, version 5.0
(II) NV: driver for NVIDIA chipsets:  RIVA 128,  RIVA TNT,  RIVA TNT2,
	 RIVA TNT2 Ultra,  Unknown TNT2,  Vanta,  RIVA TNT2 Model 64,
	 GeForce 6800 Ultra,  GeForce 6800,  GeForce 6800 LE,
	 GeForce 6800 XE,  GeForce 6800 XT,  GeForce 6800 GT,
	 GeForce 6800 GT,  GeForce 6800 GS,  GeForce 6800 XT,
	 Quadro FX 4000,  GeForce 7800 GTX,  GeForce 7800 GTX,
	 GeForce 7800 GT,  GeForce 7800 GS,  GeForce 7800 SLI,
	 GeForce Go 7800,  GeForce Go 7800 GTX,  Quadro FX 4500,
	 Aladdin TNT2,  GeForce 6800 GS,  GeForce 6800,  GeForce 6800 LE,
	 GeForce 6800 XT,  GeForce Go 6800,  GeForce Go 6800 Ultra,
	 Quadro FX Go1400,  Quadro FX 3450/4000 SDI,  Quadro FX 1400,
	 GeForce 256,  GeForce DDR,  Quadro,  GeForce2 MX/MX 400,
	 GeForce2 MX 100/200,  GeForce2 Go,  Quadro2 MXR/EX/Go,
	 GeForce 6600 GT,  GeForce 6600,  GeForce 6600 LE,  GeForce 6600 VE,
	 GeForce Go 6600,  GeForce 6610 XL,  GeForce Go 6600 TE/6200 TE,
	 GeForce 6700 XL,  GeForce Go 6600,  GeForce Go 6600 GT,
	 Quadro NVS 440,  Quadro FX 550,  Quadro FX 550,  Quadro FX 540,
	 GeForce 6200,  GeForce2 GTS,  GeForce2 Ti,  GeForce2 Ultra,
	 Quadro2 Pro,  GeForce 6500,  GeForce 6200 TurboCache(TM),
	 GeForce 6200SE TurboCache(TM),  GeForce 6200 LE,  GeForce Go 6200,
	 Quadro NVS 285,  GeForce Go 6400,  GeForce Go 6200,
	 GeForce Go 6400,  GeForce 6250,  GeForce 7100 GS,  GeForce4 MX 460,
	 GeForce4 MX 440,  GeForce4 MX 420,  GeForce4 MX 440-SE,
	 GeForce4 440 Go,  GeForce4 420 Go,  GeForce4 420 Go 32M,
	 GeForce4 460 Go,  Quadro4 550 XGL,  GeForce4 440 Go 64M,
	 Quadro NVS,  Quadro4 500 GoGL,  GeForce4 410 Go 16M,
	 GeForce4 MX 440 with AGP8X,  GeForce4 MX 440SE with AGP8X,
	 GeForce4 MX 420 with AGP8X,  GeForce4 MX 4000,  GeForce4 448 Go,
	 GeForce4 488 Go,  Quadro4 580 XGL,  Quadro4 NVS 280 SD,
	 Quadro4 380 XGL,  Quadro NVS 50 PCI,  GeForce4 448 Go,
	 GeForce 8800 GTX,  GeForce 8800 GTS,  GeForce 8800 Ultra,
	 Quadro FX 5600,  Quadro FX 4600,  GeForce2 Integrated GPU,
	 GeForce 7350 LE,  GeForce 7300 LE,  GeForce 7300 SE,
	 GeForce Go 7200,  GeForce Go 7300,  GeForce Go 7400,
	 GeForce Go 7400 GS,  Quadro NVS 110M,  Quadro NVS 120M,
	 Quadro FX 350M,  GeForce 7500 LE,  Quadro FX 350,  GeForce 7300 GS,
	 GeForce4 MX Integrated GPU,  GeForce3,  GeForce3 Ti 200,
	 GeForce3 Ti 500,  Quadro DCC,  GeForce 6800,  GeForce 6800 LE,
	 GeForce 6800 GT,  GeForce 6800 XT,  GeForce 6200,
	 GeForce 6200 A-LE,  GeForce 6150,  GeForce 6150 LE,  GeForce 6100,
	 GeForce Go 6150,  Quadro NVS 210S / NVIDIA GeForce 6150LE,
	 GeForce Go 6100,  GeForce4 Ti 4600,  GeForce4 Ti 4400,
	 GeForce4 Ti 4200,  Quadro4 900 XGL,  Quadro4 750 XGL,
	 Quadro4 700 XGL,  GeForce4 Ti 4800,  GeForce4 Ti 4200 with AGP8X,
	 GeForce4 Ti 4800 SE,  GeForce4 4200 Go,  Quadro4 980 XGL,
	 Quadro4 780 XGL,  Quadro4 700 GoGL,  GeForce 7900 GTX,
	 GeForce 7900 GT,  GeForce 7900 GS,  GeForce 7950 GX2,
	 GeForce 7950 GX2,  GeForce 7950 GT},  GeForce Go 7950 GTX,
	 GeForce Go 7900 GS,  GeForce Go 7900 GTX,  Quadro FX 2500M,
	 Quadro FX 1500M,  Quadro FX 5500,  Quadro FX 3500,  Quadro FX 1500,
	 Quadro FX 4500 X2,  GeForce FX 5800 Ultra,  GeForce FX 5800,
	 Quadro FX 2000,  Quadro FX 1000,  GeForce FX 5600 Ultra,
	 GeForce FX 5600,  GeForce FX 560T,  GeForce FX Go5600,
	 GeForce FX Go5650,  Quadro FX Go700,  GeForce FX 5200,
	 GeForce FX 5200 Ultra,  GeForce FX 5200,  GeForce FX 5200LE,
	 GeForce FX Go5200,  GeForce FX Go5250,  GeForce FX 5500,
	 GeForce FX 5100,  GeForce FX Go5200 32M/64M,  Quadro NVS 55/280 PCI,
	 Quadro FX 500/600 PCI,  GeForce FX Go53xx Series,
	 GeForce FX Go5100,  GeForce FX 5900 Ultra,  GeForce FX 5900,
	 GeForce FX 590T,  GeForce FX 5950 Ultra,  GeForce FX 5900ZT,
	 Quadro FX 3000,  Quadro FX 700,  GeForce FX 5700 Ultra,
	 GeForce FX 5700,  GeForce FX 5700LE,  GeForce FX 5700VE,
	 GeForce FX Go5700,  GeForce FX Go5700,  Quadro FX Go1000,
	 Quadro FX 1100,  GeForce 7650 GS,  GeForce 7600 GT,
	 GeForce 7600 GS,  GeForce 7300 GT,  GeForce 7600 LE,
	 GeForce 7300 GT,  GeForce Go 7700,  GeForce Go 7600,
	 GeForce Go 7600 GT},  Quadro NVS 300M,  GeForce Go 7900 SE,
	 Quadro FX 550M,  Quadro FX 560,  GeForce 6150SE,
	 GeForce 6100 nForce 405,  GeForce 6100 nForce 400,
	 GeForce 6100 nForce 420,  GeForce 8600 GTS,  GeForce 8600 GT,
	 GeForce 8600 GT,  GeForce 8600 GS,  GeForce 8400 GS,
	 GeForce 9500M GS,  GeForce 8600M GT,  GeForce 9650M GS,
	 GeForce 8700M GT,  Quadro FX 370,  Quadro NVS 320M,  Quadro FX 570M,
	 Quadro FX 1600M,  Quadro FX 570,  Quadro FX 1700,  GeForce 8400 SE,
	 GeForce 8500 GT,  GeForce 8400 GS,  GeForce 8300 GS,
	 GeForce 8400 GS,  GeForce 8600M GS,  GeForce 8400M GT,
	 GeForce 8400M GS,  GeForce 8400M G,  Quadro NVS 140M,
	 Quadro NVS 130M,  Quadro NVS 135M,  GeForce 9400 GT,
	 Quadro FX 360M,  GeForce 9300M G,  Quadro NVS 290,  GeForce GTX 295,
	 GeForce GTX 280,  GeForce GTX 260,  GeForce GTX 285,  GeForce 7050,
	 GeForce 7025,  Quadro CX,  Quadro FX 5800,  Quadro FX 4800,
	 Quadro FX 3800,  GeForce 8800 GTS 512,  GeForce 9800 GT,
	 GeForce 8800 GT,  GeForce 9800 GX2,  GeForce 9800 GT,
	 GeForce 8800 GS,  GeForce 9800M GTX,  GeForce 8800M GTS,
	 GeForce 9800M GT,  GeForce 8800M GTX,  GeForce 8800 GS,
	 GeForce 9600 GSO,  GeForce 8800 GT,  GeForce 9800 GTX,
	 GeForce 9800 GTX+,  GeForce 9800 GT,  GeForce GTS 250,
	 GeForce 9800M GTX,  Quadro FX 3700,  Quadro FX 3600M,
	 Quadro FX 3700M,  GeForce 9600 GT,  GeForce 9600 GS,
	 GeForce 9600 GSO 512,  GeForce GT 130,  GeForce GT 140,
	 GeForce 9800M GTS,  GeForce 9700M GTS,  GeForce 9800M GS,
	 GeForce 9800M GTS,  Quadro FX 1800,  Quadro FX 2700M,
	 GeForce 9500 GT,  GeForce 9400 GT,  GeForce 9500 GT,
	 GeForce GT 120,  GeForce 9600M GT,  GeForce 9600M GS,
	 GeForce 9600M GT,  GeForce 9700M GT,  GeForce 9500M G,
	 GeForce 9650M GT,  GeForce 9500 GT,  Quadro FX 380,  Quadro FX 580,
	 Quadro FX 770M,  GeForce 9300 GE,  GeForce 9300 GS,
	 GeForce 8400 GS,  GeForce 9300M GS,  GeForce G100,
	 GeForce 9200M GS,  GeForce 9300M GS,  Quadro NVS 150M,
	 Quadro NVS 160M,  Quadro NVS 420,  Quadro FX 370 LP,
	 Quadro NVS 450,  Quadro NVS 295
(II) VESA: driver for VESA chipsets: vesa
(II) FBDEV: driver for framebuffer: fbdev
(II) Primary Device is: PCI 03@00:0a:0
(--) NV: Found NVIDIA  GeForce FX 5200 at 03@00:0a:0
(WW) Falling back to old probe method for vesa
(WW) Falling back to old probe method for fbdev
(II) Loading sub module "fbdevhw"
(II) LoadModule: "fbdevhw"
(II) Loading /usr/lib/xorg/modules/linux//libfbdevhw.so
(II) Module fbdevhw: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 0.0.2
	ABI class: X.Org Video Driver, version 5.0
(EE) open /dev/fb0: No such file or directory
(II) resource ranges after probing:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[5] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[6] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[7] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[8] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[9] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[10] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[11] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[12] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[13] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[14] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[15] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[18] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[19] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[20] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[21] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[22] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[23] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.0.0
	ABI class: X.Org Video Driver, version 5.0
(II) NV(0): Initializing int10
(II) NV(0): Primary V_BIOS segment is: 0xc000
(--) NV(0): Chipset: " GeForce FX 5200"
(II) NV(0): Creating default Display subsection in Screen section
	"Builtin Default nv Screen 0" for depth/fbbpp 24/32
(==) NV(0): Depth 24, (--) framebuffer bpp 32
(==) NV(0): RGB weight 888
(==) NV(0): Default visual is TrueColor
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 0.1.0
	ABI class: X.Org Video Driver, version 5.0
(==) NV(0): Using HW cursor
(--) NV(0): Linear framebuffer at 0xE8000000
(--) NV(0): MMIO registers at 0xF8000000
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"
(II) Module "i2c" already built-in
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(II) NV(0): I2C bus "DDC" initialized.
(II) NV(0): Probing for analog device on output A...
(--) NV(0):   ...found one
(II) NV(0): Probing for analog device on output B...
(--) NV(0):   ...found one
(II) NV(0): Probing for EDID on I2C bus A...
(II) NV(0): I2C device "DDC:E-EDID segment register" registered at address 0x60.
(II) NV(0): I2C device "DDC:ddc2" registered at address 0xA0.
(--) NV(0): DDC detected a CRT:
(II) NV(0): Manufacturer: DEL  Model: d005  Serial#: 808665942
(II) NV(0): Year: 2004  Week: 41
(II) NV(0): EDID Version: 1.3
(II) NV(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) NV(0): Sync:  Separate
(II) NV(0): Max Image Size [cm]: horiz.: 32  vert.: 24
(II) NV(0): Gamma: 2.20
(II) NV(0): DPMS capabilities: Off; RGB/Color Display
(II) NV(0): Default color space is primary color space
(II) NV(0): First detailed timing is preferred mode
(II) NV(0): redX: 0.631 redY: 0.328   greenX: 0.275 greenY: 0.600
(II) NV(0): blueX: 0.143 blueY: 0.057   whiteX: 0.283 whiteY: 0.298
(II) NV(0): Supported established timings:
(II) NV(0): 720x400@70Hz
(II) NV(0): 640x480@60Hz
(II) NV(0): 640x480@75Hz
(II) NV(0): 800x600@75Hz
(II) NV(0): 1024x768@75Hz
(II) NV(0): Manufacturer's mask: 0
(II) NV(0): Supported standard timings:
(II) NV(0): #0: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) NV(0): #1: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) NV(0): #2: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) NV(0): #3: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) NV(0): #4: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) NV(0): Supported detailed timing:
(II) NV(0): clock: 78.8 MHz   Image Size:  310 x 230 mm
(II) NV(0): h_active: 1024  h_sync: 1040  h_sync_end 1136 h_blank_end 1312 h_border: 0
(II) NV(0): v_active: 768  v_sync: 769  v_sync_end 772 v_blanking: 800 v_border: 0
(II) NV(0): Serial No: 641804A803CV
(II) NV(0): Monitor name: DELL E773c
(II) NV(0): Ranges: V min: 50 V max: 160 Hz, H min: 30 H max: 70 kHz, PixClock max 110 MHz
(II) NV(0): EDID (in hex):
(II) NV(0): 	00ffffffffffff0010ac05d056433330
(II) NV(0): 	290e0103682018782e8aa9a154469924
(II) NV(0): 	0e484ca442003159455961598180714f
(II) NV(0): 	010101010101c31e0020410020301060
(II) NV(0): 	130036e61000001e000000ff00363431
(II) NV(0): 	3830344138303343560a000000fc0044
(II) NV(0): 	454c4c2045373733630a2020000000fd
(II) NV(0): 	0032a01e460b000a20202020202000b0
(II) NV(0): Probing for EDID on I2C bus B...
(--) NV(0): DDC detected a CRT:
(II) NV(0): Manufacturer: DEL  Model: a005  Serial#: 808736596
(II) NV(0): Year: 2003  Week: 32
(II) NV(0): EDID Version: 1.3
(II) NV(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) NV(0): Sync:  Separate
(II) NV(0): Max Image Size [cm]: horiz.: 31  vert.: 23
(II) NV(0): Gamma: 2.20
(II) NV(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) NV(0): Default color space is primary color space
(II) NV(0): First detailed timing is preferred mode
(II) NV(0): redX: 0.640 redY: 0.340   greenX: 0.279 greenY: 0.619
(II) NV(0): blueX: 0.140 blueY: 0.069   whiteX: 0.310 whiteY: 0.330
(II) NV(0): Supported established timings:
(II) NV(0): 720x400@70Hz
(II) NV(0): 640x480@60Hz
(II) NV(0): 640x480@75Hz
(II) NV(0): 800x600@60Hz
(II) NV(0): 800x600@75Hz
(II) NV(0): 1024x768@60Hz
(II) NV(0): 1024x768@75Hz
(II) NV(0): Manufacturer's mask: 0
(II) NV(0): Supported detailed timing:
(II) NV(0): clock: 65.0 MHz   Image Size:  304 x 228 mm
(II) NV(0): h_active: 1024  h_sync: 1048  h_sync_end 1184 h_blank_end 1344 h_border: 0
(II) NV(0): v_active: 768  v_sync: 771  v_sync_end 777 v_blanking: 806 v_border: 0
(II) NV(0): Serial No: 8W23438804WT
(II) NV(0): Monitor name: DELL E151FPb
(II) NV(0): Ranges: V min: 56 V max: 76 Hz, H min: 31 H max: 60 kHz, PixClock max 80 MHz
(II) NV(0): EDID (in hex):
(II) NV(0): 	00ffffffffffff0010ac05a054573430
(II) NV(0): 	200d0103681f1778eecaf6a357479e23
(II) NV(0): 	114f54a54a0001010101010101010101
(II) NV(0): 	01010101010164190040410026301888
(II) NV(0): 	360030e410000018000000ff00385732
(II) NV(0): 	33343338383034575420000000fc0044
(II) NV(0): 	454c4c20453135314650620a000000fd
(II) NV(0): 	00384c1f3c08000a20202020202000c4
(--) NV(0): CRTC 0 appears to have a CRT attached
(II) NV(0): Using CRT on CRTC 0
(II) NV(0): EDID vendor "DEL", prod id 53253
(II) NV(0): Using EDID range info for horizontal sync
(II) NV(0): Using EDID range info for vertical refresh
(II) NV(0): Printing DDC gathered Modelines:
(II) NV(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) NV(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) NV(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) NV(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) NV(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) NV(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) NV(0): Modeline "640x480"x0.0   36.00  640 696 752 832  480 481 484 509 -hsync -vsync (43.3 kHz)
(II) NV(0): Modeline "800x600"x0.0   56.25  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
(II) NV(0): Modeline "1024x768"x0.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
(II) NV(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) NV(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(--) NV(0): VideoRAM: 131072 kBytes
(==) NV(0): Using gamma correction (1.0, 1.0, 1.0)
(II) NV(0): <default monitor>: Using hsync range of 30.00-70.00 kHz
(II) NV(0): <default monitor>: Using vrefresh range of 50.00-160.00 Hz
(II) NV(0): <default monitor>: Using maximum pixel clock of 110.00 MHz
(II) NV(0): Estimated virtual size for aspect ratio 1.3333 is 1152x864
(II) NV(0): Clock range:  12.00 to 350.00 MHz
(II) NV(0): Not using default mode "1280x960" (width too large for virtual size)
(II) NV(0): Not using default mode "1280x960" (width too large for virtual size)
(II) NV(0): Not using default mode "640x480" (hsync out of range)
(II) NV(0): Not using default mode "1280x1024" (width too large for virtual size)
(II) NV(0): Not using default mode "1280x1024" (width too large for virtual size)
(II) NV(0): Not using default mode "640x512" (hsync out of range)
(II) NV(0): Not using default mode "1280x1024" (width too large for virtual size)
(II) NV(0): Not using default mode "640x512" (hsync out of range)
(II) NV(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) NV(0): Not using default mode "800x600" (hsync out of range)
(II) NV(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) NV(0): Not using default mode "800x600" (hsync out of range)
(II) NV(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) NV(0): Not using default mode "800x600" (hsync out of range)
(II) NV(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) NV(0): Not using default mode "800x600" (hsync out of range)
(II) NV(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) NV(0): Not using default mode "800x600" (hsync out of range)
(II) NV(0): Not using default mode "1792x1344" (width too large for virtual size)
(II) NV(0): Not using default mode "896x672" (hsync out of range)
(II) NV(0): Not using default mode "1792x1344" (width too large for virtual size)
(II) NV(0): Not using default mode "896x672" (hsync out of range)
(II) NV(0): Not using default mode "1856x1392" (width too large for virtual size)
(II) NV(0): Not using default mode "928x696" (hsync out of range)
(II) NV(0): Not using default mode "1856x1392" (width too large for virtual size)
(II) NV(0): Not using default mode "928x696" (hsync out of range)
(II) NV(0): Not using default mode "1920x1440" (width too large for virtual size)
(II) NV(0): Not using default mode "960x720" (hsync out of range)
(II) NV(0): Not using default mode "1920x1440" (width too large for virtual size)
(II) NV(0): Not using default mode "960x720" (hsync out of range)
(II) NV(0): Not using default mode "1152x864" (hsync out of range)
(II) NV(0): Not using default mode "576x432" (hsync out of range)
(II) NV(0): Not using default mode "1152x864" (hsync out of range)
(II) NV(0): Not using default mode "576x432" (hsync out of range)
(II) NV(0): Not using default mode "1152x864" (hsync out of range)
(II) NV(0): Not using default mode "576x432" (hsync out of range)
(II) NV(0): Not using default mode "1360x768" (width too large for virtual size)
(II) NV(0): Not using default mode "1360x768" (width too large for virtual size)
(II) NV(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) NV(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) NV(0): Not using default mode "700x525" (hsync out of range)
(II) NV(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) NV(0): Not using default mode "700x525" (hsync out of range)
(II) NV(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) NV(0): Not using default mode "700x525" (hsync out of range)
(II) NV(0): Not using default mode "1440x900" (width too large for virtual size)
(II) NV(0): Not using default mode "1600x1024" (width too large for virtual size)
(II) NV(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) NV(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) NV(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) NV(0): Not using default mode "840x525" (hsync out of range)
(II) NV(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) NV(0): Not using default mode "840x525" (hsync out of range)
(II) NV(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) NV(0): Not using default mode "840x525" (hsync out of range)
(II) NV(0): Not using default mode "1920x1080" (width too large for virtual size)
(II) NV(0): Not using default mode "1920x1200" (width too large for virtual size)
(II) NV(0): Not using default mode "960x600" (hsync out of range)
(II) NV(0): Not using default mode "1920x1440" (width too large for virtual size)
(II) NV(0): Not using default mode "960x720" (hsync out of range)
(II) NV(0): Not using default mode "2048x1536" (width too large for virtual size)
(II) NV(0): Not using default mode "1024x768" (hsync out of range)
(II) NV(0): Not using default mode "2048x1536" (width too large for virtual size)
(II) NV(0): Not using default mode "1024x768" (hsync out of range)
(II) NV(0): Not using default mode "2048x1536" (width too large for virtual size)
(II) NV(0): Not using default mode "1024x768" (hsync out of range)
(II) NV(0): Not using driver mode "1280x1024" (width too large for virtual size)
(--) NV(0): Virtual size is 1152x864 (pitch 1152)
(**) NV(0): *Driver mode "1152x864": 108.0 MHz, 67.5 kHz, 75.0 Hz
(II) NV(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(**) NV(0): *Default mode "1152x864": 108.0 MHz, 67.5 kHz, 75.0 Hz
(II) NV(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(**) NV(0): *Default mode "1152x864": 105.0 MHz, 67.6 kHz, 75.0 Hz
(II) NV(0): Modeline "1152x864"x75.0  104.99  1152 1224 1352 1552  864 865 868 902 -hsync +vsync (67.6 kHz)
(**) NV(0): *Default mode "1152x864": 96.8 MHz, 63.0 kHz, 70.0 Hz
(II) NV(0): Modeline "1152x864"x70.0   96.77  1152 1224 1344 1536  864 865 868 900 -hsync +vsync (63.0 kHz)
(**) NV(0): *Default mode "1152x864": 81.6 MHz, 53.7 kHz, 60.0 Hz
(II) NV(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 -hsync +vsync (53.7 kHz)
(**) NV(0): *Driver mode "1024x768": 78.8 MHz, 60.0 kHz, 75.0 Hz
(II) NV(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(**) NV(0): *Driver mode "1024x768": 94.5 MHz, 68.7 kHz, 85.0 Hz
(II) NV(0): Modeline "1024x768"x85.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
(**) NV(0): *Driver mode "1024x768": 78.8 MHz, 60.0 kHz, 75.0 Hz
(II) NV(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(**) NV(0): *Default mode "1024x768": 94.5 MHz, 68.7 kHz, 85.0 Hz
(II) NV(0): Modeline "1024x768"x85.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
(**) NV(0): *Default mode "1024x768": 78.8 MHz, 60.0 kHz, 75.0 Hz
(II) NV(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(**) NV(0): *Default mode "1024x768": 75.0 MHz, 56.5 kHz, 70.1 Hz
(II) NV(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(**) NV(0): *Default mode "1024x768": 65.0 MHz, 48.4 kHz, 60.0 Hz
(II) NV(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(**) NV(0): *Default mode "1024x768": 44.9 MHz, 35.5 kHz, 86.9 Hz (I)
(II) NV(0): Modeline "1024x768"x86.9   44.90  1024 1032 1208 1264  768 768 776 817 interlace +hsync +vsync (35.5 kHz)
(**) NV(0): *Default mode "832x624": 57.3 MHz, 49.7 kHz, 74.6 Hz
(II) NV(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(**) NV(0): *Driver mode "800x600": 56.2 MHz, 53.7 kHz, 85.1 Hz
(II) NV(0): Modeline "800x600"x85.1   56.25  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
(**) NV(0): *Driver mode "800x600": 49.5 MHz, 46.9 kHz, 75.0 Hz
(II) NV(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(**) NV(0): *Default mode "800x600": 56.3 MHz, 53.7 kHz, 85.1 Hz
(II) NV(0): Modeline "800x600"x85.1   56.30  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
(**) NV(0): *Default mode "800x600": 49.5 MHz, 46.9 kHz, 75.0 Hz
(II) NV(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(**) NV(0): *Default mode "800x600": 50.0 MHz, 48.1 kHz, 72.2 Hz
(II) NV(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(**) NV(0): *Default mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
(II) NV(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(**) NV(0): *Default mode "800x600": 36.0 MHz, 35.2 kHz, 56.2 Hz
(II) NV(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(**) NV(0): *Default mode "840x525": 73.1 MHz, 65.3 kHz, 60.0 Hz (D)
(II) NV(0): Modeline "840x525"x60.0   73.12  840 892 980 1120  525 526 529 544 doublescan -hsync +vsync (65.3 kHz)
(**) NV(0): *Default mode "700x525": 61.0 MHz, 64.9 kHz, 60.0 Hz (D)
(II) NV(0): Modeline "700x525"x60.0   61.00  700 744 820 940  525 526 532 541 doublescan +hsync +vsync (64.9 kHz)
(**) NV(0): *Default mode "640x512": 54.0 MHz, 64.0 kHz, 60.0 Hz (D)
(II) NV(0): Modeline "640x512"x60.0   54.00  640 664 720 844  512 512 514 533 doublescan +hsync +vsync (64.0 kHz)
(**) NV(0): *Default mode "720x450": 53.2 MHz, 55.9 kHz, 59.9 Hz (D)
(II) NV(0): Modeline "720x450"x59.9   53.25  720 760 836 952  450 451 454 467 doublescan -hsync +vsync (55.9 kHz)
(**) NV(0): *Driver mode "640x480": 36.0 MHz, 43.3 kHz, 85.0 Hz
(II) NV(0): Modeline "640x480"x85.0   36.00  640 696 752 832  480 481 484 509 -hsync -vsync (43.3 kHz)
(**) NV(0): *Driver mode "640x480": 31.5 MHz, 37.5 kHz, 75.0 Hz
(II) NV(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(**) NV(0): *Driver mode "640x480": 25.2 MHz, 31.5 kHz, 59.9 Hz
(II) NV(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(**) NV(0): *Default mode "640x480": 36.0 MHz, 43.3 kHz, 85.0 Hz
(II) NV(0): Modeline "640x480"x85.0   36.00  640 696 752 832  480 481 484 509 -hsync -vsync (43.3 kHz)
(**) NV(0): *Default mode "640x480": 31.5 MHz, 37.5 kHz, 75.0 Hz
(II) NV(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(**) NV(0): *Default mode "640x480": 31.5 MHz, 37.9 kHz, 72.8 Hz
(II) NV(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(**) NV(0): *Default mode "640x480": 54.0 MHz, 60.0 kHz, 60.0 Hz (D)
(II) NV(0): Modeline "640x480"x60.0   54.00  640 688 744 900  480 480 482 500 doublescan +hsync +vsync (60.0 kHz)
(**) NV(0): *Default mode "640x480": 25.2 MHz, 31.5 kHz, 59.9 Hz
(II) NV(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(**) NV(0): *Driver mode "720x400": 28.3 MHz, 31.5 kHz, 70.1 Hz
(II) NV(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(**) NV(0): *Default mode "720x400": 35.5 MHz, 37.9 kHz, 85.0 Hz
(II) NV(0): Modeline "720x400"x85.0   35.50  720 756 828 936  400 401 404 446 -hsync +vsync (37.9 kHz)
(**) NV(0): *Default mode "680x384": 36.0 MHz, 47.4 kHz, 60.0 Hz (D)
(II) NV(0): Modeline "680x384"x60.0   36.00  680 704 720 760  384 385 390 395 doublescan +hsync -vsync (47.4 kHz)
(**) NV(0): *Default mode "680x384": 42.4 MHz, 47.7 kHz, 59.8 Hz (D)
(II) NV(0): Modeline "680x384"x59.8   42.38  680 716 784 888  384 385 390 399 doublescan -hsync +vsync (47.7 kHz)
(**) NV(0): *Default mode "640x400": 31.5 MHz, 37.9 kHz, 85.1 Hz
(II) NV(0): Modeline "640x400"x85.1   31.50  640 672 736 832  400 401 404 445 -hsync +vsync (37.9 kHz)
(**) NV(0): *Default mode "576x432": 54.0 MHz, 67.5 kHz, 75.0 Hz (D)
(II) NV(0): Modeline "576x432"x75.0   54.00  576 608 672 800  432 432 434 450 doublescan +hsync +vsync (67.5 kHz)
(**) NV(0): *Default mode "576x432": 52.5 MHz, 67.6 kHz, 75.0 Hz (D)
(II) NV(0): Modeline "576x432"x75.0   52.49  576 612 676 776  432 432 434 451 doublescan -hsync +vsync (67.6 kHz)
(**) NV(0): *Default mode "576x432": 48.4 MHz, 63.0 kHz, 70.0 Hz (D)
(II) NV(0): Modeline "576x432"x70.0   48.38  576 612 672 768  432 432 434 450 doublescan -hsync +vsync (63.0 kHz)
(**) NV(0): *Default mode "576x432": 40.8 MHz, 53.7 kHz, 60.1 Hz (D)
(II) NV(0): Modeline "576x432"x60.1   40.81  576 608 668 760  432 432 434 447 doublescan -hsync +vsync (53.7 kHz)
(**) NV(0): *Default mode "640x350": 31.5 MHz, 37.9 kHz, 85.1 Hz
(II) NV(0): Modeline "640x350"x85.1   31.50  640 672 736 832  350 382 385 445 +hsync -vsync (37.9 kHz)
(**) NV(0): *Default mode "512x384": 47.2 MHz, 68.7 kHz, 85.0 Hz (D)
(II) NV(0): Modeline "512x384"x85.0   47.25  512 536 584 688  384 384 386 404 doublescan +hsync +vsync (68.7 kHz)
(**) NV(0): *Default mode "512x384": 39.4 MHz, 60.0 kHz, 75.0 Hz (D)
(II) NV(0): Modeline "512x384"x75.0   39.38  512 520 568 656  384 384 386 400 doublescan +hsync +vsync (60.0 kHz)
(**) NV(0): *Default mode "512x384": 37.5 MHz, 56.5 kHz, 70.1 Hz (D)
(II) NV(0): Modeline "512x384"x70.1   37.50  512 524 592 664  384 385 388 403 doublescan -hsync -vsync (56.5 kHz)
(**) NV(0): *Default mode "512x384": 32.5 MHz, 48.4 kHz, 60.0 Hz (D)
(II) NV(0): Modeline "512x384"x60.0   32.50  512 524 592 672  384 385 388 403 doublescan -hsync -vsync (48.4 kHz)
(**) NV(0): *Default mode "512x384": 22.4 MHz, 35.5 kHz, 86.6 Hz (D)
(II) NV(0): Modeline "512x384"x86.6   22.45  512 516 604 632  384 384 388 409 interlace doublescan +hsync +vsync (35.5 kHz)
(**) NV(0): *Default mode "416x312": 28.6 MHz, 49.7 kHz, 74.7 Hz (D)
(II) NV(0): Modeline "416x312"x74.7   28.64  416 432 464 576  312 312 314 333 doublescan -hsync -vsync (49.7 kHz)
(**) NV(0): *Default mode "400x300": 28.1 MHz, 53.7 kHz, 85.3 Hz (D)
(II) NV(0): Modeline "400x300"x85.3   28.15  400 416 448 524  300 300 302 315 doublescan +hsync +vsync (53.7 kHz)
(**) NV(0): *Default mode "400x300": 24.8 MHz, 46.9 kHz, 75.1 Hz (D)
(II) NV(0): Modeline "400x300"x75.1   24.75  400 408 448 528  300 300 302 312 doublescan +hsync +vsync (46.9 kHz)
(**) NV(0): *Default mode "400x300": 25.0 MHz, 48.1 kHz, 72.2 Hz (D)
(II) NV(0): Modeline "400x300"x72.2   25.00  400 428 488 520  300 318 321 333 doublescan +hsync +vsync (48.1 kHz)
(**) NV(0): *Default mode "400x300": 20.0 MHz, 37.9 kHz, 60.3 Hz (D)
(II) NV(0): Modeline "400x300"x60.3   20.00  400 420 484 528  300 300 302 314 doublescan +hsync +vsync (37.9 kHz)
(**) NV(0): *Default mode "400x300": 18.0 MHz, 35.2 kHz, 56.3 Hz (D)
(II) NV(0): Modeline "400x300"x56.3   18.00  400 412 448 512  300 300 301 312 doublescan +hsync +vsync (35.2 kHz)
(**) NV(0): *Default mode "320x240": 18.0 MHz, 43.3 kHz, 85.2 Hz (D)
(II) NV(0): Modeline "320x240"x85.2   18.00  320 348 376 416  240 240 242 254 doublescan -hsync -vsync (43.3 kHz)
(**) NV(0): *Default mode "320x240": 15.8 MHz, 37.5 kHz, 75.0 Hz (D)
(II) NV(0): Modeline "320x240"x75.0   15.75  320 328 360 420  240 240 242 250 doublescan -hsync -vsync (37.5 kHz)
(**) NV(0): *Default mode "320x240": 15.8 MHz, 37.9 kHz, 72.8 Hz (D)
(II) NV(0): Modeline "320x240"x72.8   15.75  320 332 352 416  240 244 246 260 doublescan -hsync -vsync (37.9 kHz)
(**) NV(0): *Default mode "320x240": 12.6 MHz, 31.5 kHz, 60.1 Hz (D)
(II) NV(0): Modeline "320x240"x60.1   12.59  320 328 376 400  240 245 246 262 doublescan -hsync -vsync (31.5 kHz)
(**) NV(0): *Default mode "360x200": 17.8 MHz, 37.9 kHz, 85.0 Hz (D)
(II) NV(0): Modeline "360x200"x85.0   17.75  360 378 414 468  200 200 202 223 doublescan -hsync +vsync (37.9 kHz)
(**) NV(0): *Default mode "320x200": 15.8 MHz, 37.9 kHz, 85.3 Hz (D)
(II) NV(0): Modeline "320x200"x85.3   15.75  320 336 368 416  200 200 202 222 doublescan -hsync +vsync (37.9 kHz)
(**) NV(0): *Default mode "320x175": 15.8 MHz, 37.9 kHz, 85.3 Hz (D)
(II) NV(0): Modeline "320x175"x85.3   15.75  320 336 368 416  175 191 192 222 doublescan +hsync -vsync (37.9 kHz)
(**) NV(0): Display dimensions: (320, 240) mm
(**) NV(0): DPI set to (91, 91)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.2.1
	ABI class: X.Org Video Driver, version 5.0
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(II) UnloadModule: "vesa"
(II) Unloading /usr/lib/xorg/modules/drivers//vesa_drv.so
(II) UnloadModule: "fbdev"
(II) Unloading /usr/lib/xorg/modules/drivers//fbdev_drv.so
(II) UnloadModule: "fbdevhw"
(II) Unloading /usr/lib/xorg/modules/linux//libfbdevhw.so
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[5] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[6] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[7] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[8] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[9] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[10] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[11] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[12] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[13] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[14] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[15] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[18] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[19] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[20] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[21] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[22] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[23] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) NV(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	8x8 mono pattern filled rectangles
	Indirect CPU to Screen color expansion
	Solid Lines
	Scanline Image Writes
	Setting up tile and stipple cache:
		32 128x128 slots
		32 256x256 slots
		16 512x512 slots
(==) NV(0): Backing store disabled
(==) NV(0): Silken mouse enabled
(II) NV(0): DPMS enabled
(==) RandR enabled
(II) Initializing built-in extension Generic Event Extension
(II) Initializing built-in extension SHAPE
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension BIG-REQUESTS
(II) Initializing built-in extension SYNC
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-MISC
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)
(II) config/hal: Adding input device Power Button
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 2.2.5
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 4.0
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event0"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/hal: Adding input device Microsoft Natural Keyboard Elite
(**) Microsoft Natural Keyboard Elite: always reports core events
(**) Microsoft Natural Keyboard Elite: Device: "/dev/input/event4"
(II) Microsoft Natural Keyboard Elite: Found keys
(II) Microsoft Natural Keyboard Elite: Configuring as keyboard
(II) XINPUT: Adding extended input device "Microsoft Natural Keyboard Elite" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/hal: Adding input device Power Button
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event1"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/hal: Adding input device Macintosh mouse button emulation
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event2"
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Configuring as mouse
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(**) Macintosh mouse button emulation: (accel) keeping acceleration scheme 1
(**) Macintosh mouse button emulation: (accel) filter chain progression: 2.00
(**) Macintosh mouse button emulation: (accel) filter stage 0: 20.00 ms
(**) Macintosh mouse button emulation: (accel) set acceleration profile 0
(II) Macintosh mouse button emulation: initialized for relative axes.
(II) config/hal: Adding input device A4Tech USB Optical Mouse
(**) A4Tech USB Optical Mouse: always reports core events
(**) A4Tech USB Optical Mouse: Device: "/dev/input/event3"
(II) A4Tech USB Optical Mouse: Found 10 mouse buttons
(II) A4Tech USB Optical Mouse: Found x and y relative axes
(II) A4Tech USB Optical Mouse: Found scroll wheel(s)
(II) A4Tech USB Optical Mouse: Configuring as mouse
(**) A4Tech USB Optical Mouse: YAxisMapping: buttons 4 and 5
(**) A4Tech USB Optical Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "A4Tech USB Optical Mouse" (type: MOUSE)
(**) A4Tech USB Optical Mouse: (accel) keeping acceleration scheme 1
(**) A4Tech USB Optical Mouse: (accel) filter chain progression: 2.00
(**) A4Tech USB Optical Mouse: (accel) filter stage 0: 20.00 ms
(**) A4Tech USB Optical Mouse: (accel) set acceleration profile 0
(II) A4Tech USB Optical Mouse: initialized for relative axes.
```

---

### Post by anothrguitarist on 2009-11-15
I just got nvidia-settings to save the xorg.conf file correctly, but it only works for two monitors on the same video card. When I try three, I run into the same problem that I did before: the monitors turn off and on. Anyone know what's going on?

---

### Post by anothrguitarist on 2009-11-15
Wow I got it to work!!!

I read a few other threads and learned that I couldn't use xinerama, so I disabled it. Now it works! Woohoo!

---

### Post by Jon Monreal on 2009-11-15
> **anothrguitarist said:**
> Wow I got it to work!!!

I read a few other threads and learned that I couldn't use xinerama, so I disabled it. Now it works! Woohoo!

Sounds great! I apologize for not being able to help earlier, but I'm glad you managed to get it working.

It would be great if you could mark the thread as solved.

Thanks.

---

