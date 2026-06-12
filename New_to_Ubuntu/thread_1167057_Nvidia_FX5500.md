---
title: "Nvidia FX5500"
date: 2009-05-22
forum: New to Ubuntu
---

### Post by gilmesh on 2009-05-22
Hi
I've spent the last couple of days trying to get this to work.  I did a fresh install of Ubuntu Studio 9.04 and can't get my geForce FX5500 working.  I've been trying all of the fixes i could find in the forums, but none have worked yet.

I've tried...

Restricted Hardware ( 173.14.16 )
EnvyNG
Nvidia website ( 173.14.18 )

I think I've isolated the problem with my xorg.conf file.  No matter how I try to rebuild it, it always comes out the same.

xorg.conf
```
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection
```

If I manually add the HorizSync and VertRefresh, nothing changes except my resolution goes to 1600x1200.  I have tried dpkg-reconfigure xserver-xorg and it only asks me about the keyboard.  Also dpkg-reconfigure -phigh xserver-xorg does nothing.

Xorg.0.log
```

X.Org X Server 1.6.0
Release Date: 2009-2-25
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux host 2.6.28-3-rt #12-Ubuntu SMP PREEMPT RT Fri Apr 17 10:09:11 UTC 2009 i686
Build Date: 09 April 2009  02:10:02AM
xorg-server 2:1.6.0-0ubuntu14 (buildd@rothera.buildd) 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Fri May 22 11:34:02 2009
(==) Using config file: "/etc/X11/xorg.conf"
(==) No Layout section.  Using the first Screen section.
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Configured Monitor"
(**) |   |-->Device "Configured Video Device"
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
(II) Loader magic: 0x3bc0
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 5.0
	X.Org XInput driver : 4.0
	X.Org Server Extension : 2.0
(II) Loader running on linux
(++) using VT number 7

(--) PCI:*(0@1:0:0) nVidia Corporation NV34 [GeForce FX 5500] rev 161, Mem @ 0xe8000000/16777216, 0xd0000000/268435456, BIOS @ 0x????????/131072
(II) Open ACPI successful (/var/run/acpid.socket)
(II) System resource ranges:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
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
	compiled for 1.6.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Server Extension
(II) NVIDIA GLX Module  173.14.16  Sat Jan 24 20:08:33 PST 2009
(II) Loading extension GLX
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions//libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) Scanning /usr/share/xserver-xorg/pci directory for additional PCI ID's supported by the drivers
(II) Matched nv from file name nv.ids
(==) Matched nv for the autoconfigured driver
(==) Assigned the driver to the xf86ConfigLayout
(II) LoadModule: "nv"
(II) Loading /usr/lib/xorg/modules/drivers//nv_drv.so
(II) Module nv: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 2.1.12
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 5.0
(II) NV: driver for NVIDIA chipsets: RIVA 128, RIVA TNT, RIVA TNT2,
	Unknown TNT2, Vanta, RIVA TNT2 Ultra, RIVA TNT2 Model 64,
	Aladdin TNT2, GeForce 256, GeForce DDR, Quadro, GeForce2 MX/MX 400,
	GeForce2 MX 100/200, GeForce2 Go, Quadro2 MXR/EX/Go,
	GeForce2 Integrated GPU, GeForce2 GTS, GeForce2 Ti, GeForce2 Ultra,
	Quadro2 Pro, GeForce4 MX 460, GeForce4 MX 440, GeForce4 MX 420,
	GeForce4 MX 440-SE, GeForce4 440 Go, GeForce4 420 Go,
	GeForce4 420 Go 32M, GeForce4 460 Go, Quadro4 550 XGL,
	GeForce4 440 Go 64M, Quadro NVS, Quadro4 500 GoGL,
	GeForce4 410 Go 16M, GeForce4 MX 440 with AGP8X,
	GeForce4 MX 440SE with AGP8X, GeForce4 MX 420 with AGP8X,
	GeForce4 MX 4000, GeForce4 448 Go, GeForce4 488 Go, Quadro4 580 XGL,
	Quadro4 NVS 280 SD, Quadro4 380 XGL, Quadro NVS 50 PCI,
	GeForce4 448 Go, GeForce4 MX Integrated GPU, GeForce3,
	GeForce3 Ti 200, GeForce3 Ti 500, Quadro DCC, GeForce4 Ti 4600,
	GeForce4 Ti 4400, GeForce4 Ti 4200, Quadro4 900 XGL, Quadro4 750 XGL,
	Quadro4 700 XGL, GeForce4 Ti 4800, GeForce4 Ti 4200 with AGP8X,
	GeForce4 Ti 4800 SE, GeForce4 4200 Go, Quadro4 700 GoGL,
	Quadro4 980 XGL, Quadro4 780 XGL, GeForce FX 5800 Ultra,
	GeForce FX 5800, Quadro FX 2000, Quadro FX 1000,
	GeForce FX 5600 Ultra, GeForce FX 5600, GeForce FX 5600XT,
	GeForce FX Go5600, GeForce FX Go5650, Quadro FX Go700,
	GeForce FX 5200, GeForce FX 5200 Ultra, GeForce FX 5200,
	GeForce FX 5200LE, GeForce FX Go5200, GeForce FX Go5250,
	GeForce FX 5500, GeForce FX 5100, GeForce FX Go5200 32M/64M,
	Quadro NVS 55/280 PCI, Quadro FX 500/600 PCI,
	GeForce FX Go53xx Series, GeForce FX Go5100, GeForce FX 5900 Ultra,
	GeForce FX 5900, GeForce FX 5900XT, GeForce FX 5950 Ultra,
	GeForce FX 5900ZT, Quadro FX 3000, Quadro FX 700,
	GeForce FX 5700 Ultra, GeForce FX 5700, GeForce FX 5700LE,
	GeForce FX 5700VE, GeForce FX Go5700, GeForce FX Go5700,
	Quadro FX Go1000, Quadro FX 1100, GeForce 6800 Ultra, GeForce 6800,
	GeForce 6800 LE, GeForce 6800 XE, GeForce 6800 XT, GeForce 6800 GT,
	GeForce 6800 GT, GeForce 6800 GS, GeForce 6800 XT, Quadro FX 4000,
	GeForce 6800 GS, GeForce 6800, GeForce 6800 LE, GeForce 6800 XT,
	GeForce Go 6800, GeForce Go 6800 Ultra, Quadro FX Go1400,
	Quadro FX 3450/4000 SDI, Quadro FX 1400, GeForce 6600 GT,
	GeForce 6600, GeForce 6600 LE, GeForce 6600 VE, GeForce Go 6600,
	GeForce 6610 XL, GeForce Go 6600 TE/6200 TE, GeForce 6700 XL,
	GeForce Go 6600, GeForce Go 6600 GT, Quadro FX 550, Quadro FX 550,
	Quadro FX 540, GeForce 6200, GeForce 6500,
	GeForce 6200 TurboCache(TM), GeForce 6200SE TurboCache(TM),
	GeForce 6200 LE, GeForce Go 6200, Quadro NVS 285, GeForce Go 6400,
	GeForce Go 6200, GeForce Go 6400, GeForce 6250, GeForce 7100 GS,
	GeForce 6800, GeForce 6800 LE, GeForce 6800 GT, GeForce 6800 XT,
	GeForce 6200, GeForce 6200 A-LE, GeForce 7800 GTX, GeForce 7800 GTX,
	GeForce 7800 GT, GeForce 7800 GS, GeForce 7800 SLI, GeForce Go 7800,
	GeForce Go 7800 GTX, Quadro FX 4500, GeForce 7300 LE,
	GeForce 7300 SE, GeForce Go 7200, GeForce Go 7300, GeForce Go 7400,
	GeForce Go 7400 GS, Quadro NVS 110M, Quadro NVS 120M, Quadro FX 350M,
	GeForce 7500 LE, Quadro FX 350, GeForce 7300 GS, GeForce 7300 GT,
	GeForce 7600 GT, GeForce 7600 GS, GeForce 7300 GT, GeForce 7600 LE,
	GeForce 7300 GT, GeForce Go 7700, GeForce Go 7600,
	GeForce Go 7600 GT, Quadro NVS 300M, GeForce Go 7900 SE,
	Quadro FX 550M, Quadro FX 560, GeForce 7900 GTX, GeForce 7900 GT,
	GeForce 7900 GS, GeForce Go 7900 GS, GeForce Go 7900 GTX,
	Quadro FX 2500M, Quadro FX 1500M, Quadro FX 5500, Quadro FX 3500,
	Quadro FX 1500, Quadro FX 4500 X2, GeForce 6150, GeForce 6150 LE,
	GeForce 6100, GeForce Go 6150, GeForce Go 6100, GeForce 8800 GTX,
	GeForce 8800 GTS, GeForce 8800 Ultra, Quadro FX 5600, Quadro FX 4600,
	GeForce 8600 GTS, GeForce 8600 GT, GeForce 8600 GT, GeForce 8600 GS,
	GeForce 8400 GS, GeForce 9500M GS, GeForce 8600M GT,
	GeForce 9650M GS, GeForce 8700M GT, Quadro FX 370, Quadro NVS 320M,
	Quadro FX 570M, Quadro FX 1600M, Quadro FX 570, Quadro FX 1700,
	GeForce 8400 SE, GeForce 8500 GT, GeForce 8400 GS, GeForce 8300 GS,
	GeForce 8400 GS, GeForce 8600M GS, GeForce 8400M GT,
	GeForce 8400M GS, GeForce 8400M G, Quadro NVS 140M, Quadro NVS 130M,
	Quadro NVS 135M, GeForce 9400 GT, Quadro FX 360M, GeForce 9300M G,
	Quadro NVS 290, GeForce GTX 280, GeForce GTX 260,
	GeForce 8800 GTS 512, GeForce 8800 GT, GeForce 9800 GX2,
	GeForce 8800 GS, GeForce 8800M GTS, GeForce 8800M GTX,
	GeForce 8800 GS, GeForce 9600 GSO, GeForce 8800 GT, GeForce 9800 GTX,
	GeForce 9800 GTK+, GeForce 9800 GT, GeForce GTS 250, Quadro FX 3700,
	Quadro FX 3600M, GeForce 9600 GT, GeForce 9600 GS, GeForce 9800M GTS,
	GeForce 9700M GTS, GeForce 9800M GTS, GeForce 9500 GT,
	GeForce 9600M GT, GeForce 9600M GS, GeForce 9600M GT,
	GeForce 9500M G, GeForce 9300 GS, GeForce 8400 GS, GeForce 9300M GS,
	GeForce 9200M GS, GeForce 9300M GS, Quadro NVS 150M, Quadro NVS 160M
(II) Primary Device is: PCI 01@00:00:0
(--) NV: Found NVIDIA GeForce FX 5500 at 01@00:00:0
(II) resource ranges after probing:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 5.0
(II) NV(0): Initializing int10
(II) NV(0): Primary V_BIOS segment is: 0xc000
(--) NV(0): Chipset: "GeForce FX 5500"
(II) NV(0): Creating default Display subsection in Screen section
	"Default Screen" for depth/fbbpp 24/32
(==) NV(0): Depth 24, (--) framebuffer bpp 32
(==) NV(0): RGB weight 888
(==) NV(0): Default visual is TrueColor
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 0.1.0
	ABI class: X.Org Video Driver, version 5.0
(==) NV(0): Using HW cursor
(--) NV(0): Linear framebuffer at 0xD0000000
(--) NV(0): MMIO registers at 0xE8000000
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
(--) NV(0):   ...can't find one
(II) NV(0): Probing for EDID on I2C bus A...
(II) NV(0): I2C device "DDC:E-EDID segment register" registered at address 0x60.
(II) NV(0): I2C device "DDC:ddc2" registered at address 0xA0.
(II) NV(0):   ... none found
(II) NV(0): Probing for EDID on I2C bus B...
(II) NV(0):   ... none found
(--) NV(0): CRTC 0 appears to have a CRT attached
(II) NV(0): Using CRT on CRTC 0
(--) NV(0): VideoRAM: 262144 kBytes
(==) NV(0): Using gamma correction (1.0, 1.0, 1.0)
(II) NV(0): Configured Monitor: Using default hsync range of 31.50-37.90 kHz
(II) NV(0): Configured Monitor: Using default vrefresh range of 50.00-70.00 Hz
(WW) NV(0): Unable to estimate virtual size
(II) NV(0): Clock range:  12.00 to 350.00 MHz
(II) NV(0): Not using default mode "640x350" (vrefresh out of range)
(II) NV(0): Not using default mode "320x175" (vrefresh out of range)
(II) NV(0): Not using default mode "640x400" (vrefresh out of range)
(II) NV(0): Not using default mode "320x200" (vrefresh out of range)
(II) NV(0): Not using default mode "720x400" (vrefresh out of range)
(II) NV(0): Not using default mode "360x200" (vrefresh out of range)
(II) NV(0): Not using default mode "640x480" (vrefresh out of range)
(II) NV(0): Not using default mode "320x240" (vrefresh out of range)
(II) NV(0): Not using default mode "640x480" (vrefresh out of range)
(II) NV(0): Not using default mode "320x240" (vrefresh out of range)
(II) NV(0): Not using default mode "640x480" (hsync out of range)
(II) NV(0): Not using default mode "320x240" (hsync out of range)
(II) NV(0): Not using default mode "800x600" (hsync out of range)
(II) NV(0): Not using default mode "400x300" (hsync out of range)
(II) NV(0): Not using default mode "800x600" (hsync out of range)
(II) NV(0): Not using default mode "400x300" (hsync out of range)
(II) NV(0): Not using default mode "800x600" (hsync out of range)
(II) NV(0): Not using default mode "400x300" (hsync out of range)
(II) NV(0): Not using default mode "1024x768" (vrefresh out of range)
(II) NV(0): Not using default mode "512x384" (vrefresh out of range)
(II) NV(0): Not using default mode "1024x768" (hsync out of range)
(II) NV(0): Not using default mode "512x384" (hsync out of range)
(II) NV(0): Not using default mode "1024x768" (hsync out of range)
(II) NV(0): Not using default mode "512x384" (hsync out of range)
(II) NV(0): Not using default mode "1024x768" (hsync out of range)
(II) NV(0): Not using default mode "512x384" (hsync out of range)
(II) NV(0): Not using default mode "1024x768" (hsync out of range)
(II) NV(0): Not using default mode "512x384" (hsync out of range)
(II) NV(0): Not using default mode "1152x864" (hsync out of range)
(II) NV(0): Not using default mode "576x432" (hsync out of range)
(II) NV(0): Not using default mode "1280x960" (hsync out of range)
(II) NV(0): Not using default mode "640x480" (hsync out of range)
(II) NV(0): Not using default mode "1280x960" (hsync out of range)
(II) NV(0): Not using default mode "640x480" (hsync out of range)
(II) NV(0): Not using default mode "1280x1024" (hsync out of range)
(II) NV(0): Not using default mode "640x512" (hsync out of range)
(II) NV(0): Not using default mode "1280x1024" (hsync out of range)
(II) NV(0): Not using default mode "640x512" (hsync out of range)
(II) NV(0): Not using default mode "1280x1024" (hsync out of range)
(II) NV(0): Not using default mode "640x512" (hsync out of range)
(II) NV(0): Not using default mode "1600x1200" (hsync out of range)
(II) NV(0): Not using default mode "800x600" (hsync out of range)
(II) NV(0): Not using default mode "1600x1200" (hsync out of range)
(II) NV(0): Not using default mode "800x600" (hsync out of range)
(II) NV(0): Not using default mode "1600x1200" (hsync out of range)
(II) NV(0): Not using default mode "800x600" (hsync out of range)
(II) NV(0): Not using default mode "1600x1200" (hsync out of range)
(II) NV(0): Not using default mode "800x600" (hsync out of range)
(II) NV(0): Not using default mode "1600x1200" (hsync out of range)
(II) NV(0): Not using default mode "800x600" (hsync out of range)
(II) NV(0): Not using default mode "1792x1344" (hsync out of range)
(II) NV(0): Not using default mode "896x672" (hsync out of range)
(II) NV(0): Not using default mode "1792x1344" (hsync out of range)
(II) NV(0): Not using default mode "896x672" (hsync out of range)
(II) NV(0): Not using default mode "1856x1392" (hsync out of range)
(II) NV(0): Not using default mode "928x696" (hsync out of range)
(II) NV(0): Not using default mode "1856x1392" (hsync out of range)
(II) NV(0): Not using default mode "928x696" (hsync out of range)
(II) NV(0): Not using default mode "1920x1440" (hsync out of range)
(II) NV(0): Not using default mode "960x720" (hsync out of range)
(II) NV(0): Not using default mode "1920x1440" (hsync out of range)
(II) NV(0): Not using default mode "960x720" (hsync out of range)
(II) NV(0): Not using default mode "832x624" (hsync out of range)
(II) NV(0): Not using default mode "416x312" (hsync out of range)
(II) NV(0): Not using default mode "1152x864" (hsync out of range)
(II) NV(0): Not using default mode "576x432" (hsync out of range)
(II) NV(0): Not using default mode "1152x864" (hsync out of range)
(II) NV(0): Not using default mode "576x432" (hsync out of range)
(II) NV(0): Not using default mode "1152x864" (hsync out of range)
(II) NV(0): Not using default mode "576x432" (hsync out of range)
(II) NV(0): Not using default mode "1152x864" (hsync out of range)
(II) NV(0): Not using default mode "576x432" (hsync out of range)
(II) NV(0): Not using default mode "1152x864" (hsync out of range)
(II) NV(0): Not using default mode "576x432" (hsync out of range)
(II) NV(0): Not using default mode "1152x864" (hsync out of range)
(II) NV(0): Not using default mode "576x432" (hsync out of range)
(II) NV(0): Not using default mode "1360x768" (hsync out of range)
(II) NV(0): Not using default mode "680x384" (hsync out of range)
(II) NV(0): Not using default mode "1360x768" (hsync out of range)
(II) NV(0): Not using default mode "680x384" (hsync out of range)
(II) NV(0): Not using default mode "1400x1050" (hsync out of range)
(II) NV(0): Not using default mode "700x525" (hsync out of range)
(II) NV(0): Not using default mode "1400x1050" (hsync out of range)
(II) NV(0): Not using default mode "700x525" (hsync out of range)
(II) NV(0): Not using default mode "1400x1050" (hsync out of range)
(II) NV(0): Not using default mode "700x525" (hsync out of range)
(II) NV(0): Not using default mode "1400x1050" (hsync out of range)
(II) NV(0): Not using default mode "700x525" (hsync out of range)
(II) NV(0): Not using default mode "1440x900" (hsync out of range)
(II) NV(0): Not using default mode "720x450" (hsync out of range)
(II) NV(0): Not using default mode "1600x1024" (hsync out of range)
(II) NV(0): Not using default mode "800x512" (hsync out of range)
(II) NV(0): Not using default mode "1680x1050" (hsync out of range)
(II) NV(0): Not using default mode "840x525" (hsync out of range)
(II) NV(0): Not using default mode "1680x1050" (hsync out of range)
(II) NV(0): Not using default mode "840x525" (hsync out of range)
(II) NV(0): Not using default mode "1680x1050" (hsync out of range)
(II) NV(0): Not using default mode "840x525" (hsync out of range)
(II) NV(0): Not using default mode "1680x1050" (hsync out of range)
(II) NV(0): Not using default mode "840x525" (hsync out of range)
(II) NV(0): Not using default mode "1680x1050" (hsync out of range)
(II) NV(0): Not using default mode "840x525" (hsync out of range)
(II) NV(0): Not using default mode "1920x1080" (hsync out of range)
(II) NV(0): Not using default mode "960x540" (hsync out of range)
(II) NV(0): Not using default mode "1920x1200" (hsync out of range)
(II) NV(0): Not using default mode "960x600" (hsync out of range)
(II) NV(0): Not using default mode "1920x1440" (hsync out of range)
(II) NV(0): Not using default mode "960x720" (hsync out of range)
(II) NV(0): Not using default mode "2048x1536" (hsync out of range)
(II) NV(0): Not using default mode "1024x768" (hsync out of range)
(II) NV(0): Not using default mode "2048x1536" (hsync out of range)
(II) NV(0): Not using default mode "1024x768" (hsync out of range)
(II) NV(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1024x768" (hsync out of range)
(--) NV(0): Virtual size is 800x600 (pitch 800)
(**) NV(0): *Default mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
(II) NV(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(**) NV(0): *Default mode "800x600": 36.0 MHz, 35.2 kHz, 56.2 Hz
(II) NV(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(**) NV(0): *Default mode "640x480": 25.2 MHz, 31.5 kHz, 59.9 Hz
(II) NV(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(**) NV(0): *Default mode "400x300": 20.0 MHz, 37.9 kHz, 60.3 Hz (D)
(II) NV(0): Modeline "400x300"x60.3   20.00  400 420 484 528  300 300 302 314 doublescan +hsync +vsync (37.9 kHz)
(**) NV(0): *Default mode "400x300": 18.0 MHz, 35.2 kHz, 56.3 Hz (D)
(II) NV(0): Modeline "400x300"x56.3   18.00  400 412 448 512  300 300 301 312 doublescan +hsync +vsync (35.2 kHz)
(**) NV(0): *Default mode "320x240": 12.6 MHz, 31.5 kHz, 60.1 Hz (D)
(II) NV(0): Modeline "320x240"x60.1   12.59  320 328 376 400  240 245 246 262 doublescan -hsync -vsync (31.5 kHz)
(==) NV(0): DPI set to (96, 96)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.2.1
	ABI class: X.Org Video Driver, version 5.0
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
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
(II) config/hal: Adding input device Razer Razer Lycosa
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 2.1.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 4.0
(**) Razer Razer Lycosa: always reports core events
(**) Razer Razer Lycosa: Device: "/dev/input/event4"
(II) Razer Razer Lycosa: Found 1 mouse buttons
(II) Razer Razer Lycosa: Found keys
(II) Razer Razer Lycosa: Configuring as keyboard
(**) Razer Razer Lycosa: YAxisMapping: buttons 4 and 5
(**) Razer Razer Lycosa: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Razer Razer Lycosa" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Razer Razer Lycosa: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) Razer Razer Lycosa: xkb_model: "pc105"
(**) Option "xkb_layout" "us"
(**) Razer Razer Lycosa: xkb_layout: "us"
(II) config/hal: Adding input device Razer Razer Lycosa
(**) Razer Razer Lycosa: always reports core events
(**) Razer Razer Lycosa: Device: "/dev/input/event3"
(II) Razer Razer Lycosa: Found keys
(II) Razer Razer Lycosa: Configuring as keyboard
(II) XINPUT: Adding extended input device "Razer Razer Lycosa" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Razer Razer Lycosa: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) Razer Razer Lycosa: xkb_model: "pc105"
(**) Option "xkb_layout" "us"
(**) Razer Razer Lycosa: xkb_layout: "us"
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
(II) config/hal: Adding input device Logitech USB-PS/2 Optical Mouse
(**) Logitech USB-PS/2 Optical Mouse: always reports core events
(**) Logitech USB-PS/2 Optical Mouse: Device: "/dev/input/event5"
(II) Logitech USB-PS/2 Optical Mouse: Found 3 mouse buttons
(II) Logitech USB-PS/2 Optical Mouse: Found x and y relative axes
(II) Logitech USB-PS/2 Optical Mouse: Configuring as mouse
(**) Logitech USB-PS/2 Optical Mouse: YAxisMapping: buttons 4 and 5
(**) Logitech USB-PS/2 Optical Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Logitech USB-PS/2 Optical Mouse" (type: MOUSE)
(**) Logitech USB-PS/2 Optical Mouse: (accel) keeping acceleration scheme 1
(**) Logitech USB-PS/2 Optical Mouse: (accel) filter chain progression: 2.00
(**) Logitech USB-PS/2 Optical Mouse: (accel) filter stage 0: 20.00 ms
(**) Logitech USB-PS/2 Optical Mouse: (accel) set acceleration profile 0
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Razer Razer Lycosa: Device reopened after 1 attempts.
(II) Razer Razer Lycosa: Device reopened after 1 attempts.
(II) Macintosh mouse button emulation: Device reopened after 1 attempts.
(II) Logitech USB-PS/2 Optical Mouse: Device reopened after 1 attempts.
```

How can I get it to detect my monitor?  I've removed the vid card and booted with the onboard video to try and get it that way, but nothing changed even after running the dpkg-reconfigure commands again.  My onboard video cannot be disabled in bios.

When I stop the gdm and run the 173.14.18 driver, I get the Nvidia utility that says it needs to build a kernel for me.  It errors out and says it was unable to build the kernel.

nvidia-installer.log
```
nvidia-installer log file '/var/log/nvidia-installer.log'
creation time: Fri May 22 11:23:34 2009
installer version: 1.0.7

option status:
  license pre-accepted    : false
  update                  : false
  force update            : false
  expert                  : false
  uninstall               : false
  driver info             : false
  precompiled interfaces  : true
  no ncurses color        : false
  query latest version    : false
  OpenGL header files     : true
  no questions            : false
  silent                  : false
  no recursion            : false
  no backup               : false
  kernel module only      : false
  sanity                  : false
  add this kernel         : false
  no runlevel check       : false
  no network              : false
  no ABI note             : false
  no RPMs                 : false
  no kernel module        : false
  force SELinux           : default
  no X server check       : false
  no cc version check     : false
  force tls               : (not specified)
  X install prefix        : (not specified)
  X library install path  : (not specified)
  X module install path   : (not specified)
  OpenGL install prefix   : (not specified)
  OpenGL install libdir   : (not specified)
  utility install prefix  : (not specified)
  utility install libdir  : (not specified)
  doc install prefix      : (not specified)
  kernel name             : (not specified)
  kernel include path     : (not specified)
  kernel source path      : (not specified)
  kernel output path      : (not specified)
  kernel install path     : (not specified)
  proc mount point        : /proc
  ui                      : (not specified)
  tmpdir                  : /tmp
  ftp mirror              : ftp://download.nvidia.com
  RPM file list           : (not specified)

Using: nvidia-installer ncurses user interface
-> License accepted.
-> Installing NVIDIA driver version 173.14.18.
-> No precompiled kernel interface was found to match your kernel; would you li
   ke the installer to attempt to download a kernel interface for your kernel f
   rom the NVIDIA ftp site (ftp://download.nvidia.com)? (Answer: Yes)
-> No matching precompiled kernel interface was found on the NVIDIA ftp site;
   this means that the installer will need to compile a kernel interface for
   your kernel.
-> Performing CC sanity check with CC="cc".
-> Performing CC version check with CC="cc".
-> Kernel source path: '/lib/modules/2.6.28-3-rt/build'
-> Kernel output path: '/lib/modules/2.6.28-3-rt/build'
-> Performing rivafb check.
-> Performing nvidiafb check.
-> Performing Xen check.
-> Cleaning kernel module build directory.
   executing: 'cd ./usr/src/nv; make clean'...
-> Building kernel module:
   executing: 'cd ./usr/src/nv; make module SYSSRC=/lib/modules/2.6.28-3-rt/bui
   ld SYSOUT=/lib/modules/2.6.28-3-rt/build'...
   NVIDIA: calling KBUILD...
   make CC=cc  KBUILD_VERBOSE=1 -C /lib/modules/2.6.28-3-rt/build SUBDIRS=/tmp/
   selfgz4102/NVIDIA-Linux-x86-173.14.18-pkg1/usr/src/nv modules
   test -e include/linux/autoconf.h -a -e include/config/auto.conf || (		\
   	echo;								\
   	echo "  ERROR: Kernel configuration is invalid.";		\
   	echo "         include/linux/autoconf.h or include/config/auto.conf are mis
   sing.";	\
   	echo "         Run 'make oldconfig && make prepare' on kernel src to fix it
   .";	\
   	echo;								\
   	/bin/false)
   mkdir -p /tmp/selfgz4102/NVIDIA-Linux-x86-173.14.18-pkg1/usr/src/nv/.tmp_ver
   sions ; rm -f /tmp/selfgz4102/NVIDIA-Linux-x86-173.14.18-pkg1/usr/src/nv/.tm
   p_versions/*
   make -f scripts/Makefile.build obj=/tmp/selfgz4102/NVIDIA-Linux-x86-173.14.1
   8-pkg1/usr/src/nv
     cc -Wp,-MD,/tmp/selfgz4102/NVIDIA-Linux-x86-173.14.18-pkg1/usr/src/nv/.nv.
   o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.3.3/include -D__KERNEL
   __  -Iinclude  -I/usr/src/linux-headers-2.6.28-3-rt/arch/x86/include -includ
   e include/linux/autoconf.h -Iubun
   tu/include  -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-ali
   asing -fno-common -Werror-implicit-function-declaration -O2 -m32 -msoft-floa
   t -mregparm=3 -freg-struct-return -mpreferred-stack-boundary=2 -march=i586 -
   mtune=generic -Wa,-mtune=generic32 -ffreestanding -pipe -Wno-sign-compare -f
   no-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Iarch/
   x86/include/asm/mach-default -fno-stack-protector -fno-omit-frame-pointer -f
   no-optimize-sibling-calls -Wdeclaration-after-statement -Wno-pointer-sign -f
   wrapv -I/tmp/selfgz4102/NVIDIA-Linux-x86-173.14.18-pkg1/usr/src/nv -Wall -Wi
   mplicit -Wreturn-type -Wswitch -Wformat -Wchar-subscripts -Wparentheses -Wpo
   inter-arith -Wno-multichar -Werror -MD -Wsign-compare -Wno-cast-qual -Wno-er
   ror -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"173.14.18\" -UDEBUG -
   U_DEBUG -DNDEBUG -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR
   (nv)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)"  -c -o /tmp/selfgz4102/NVIDIA-L
   inux-x86-173.14.18-pkg1/usr/src/nv/.
   tmp_nv.o /tmp/selfgz4102/NVIDIA-Linux-x86-173.14.18-pkg1/usr/src/nv/nv.c
   In file included from include/linux/bitops.h:17,
                    from include/linux/kernel.h:15,
                    from include/linux/sched.h:52,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz4102/NVIDIA-Linux-x86-173.14.18-pkg1/usr/sr
   c/nv/nv-linux.h:19,
                    from /tmp/selfgz4102/NVIDIA-Linux-x86-173.14.18-pkg1/usr/sr
   c/nv/nv.c:14:
   /usr/src/linux-headers-2.6.28-3-rt/arch/x86/include/asm/bitops.h: In functio
   n ‘set_bit’:
   /usr/src/linux-headers-2.6.28-3-rt/arch/x86/include/asm/bitops.h:60: warning
   : pointer of type ‘void *’ used in arithmetic
   /usr/src/linux-headers-2.6.28-3-rt/arch/x86/include/asm/bitops.h: In functio
   n ‘clear_bit’:
   /usr/src/linux-headers-2.6.28-3-rt/arch/x86/include/asm/bitops.h:97: warning
   : pointer of type ‘void *’ used in arithmetic
   In file included from include/linux/list.h:6,
                    from include/linux/preempt.h:11,
                    from include/linux/spinlock.h:50,
                    from include/linux/seqlock.h:29,
                    from include/linux/time.h:8,
                    from include/linux/timex.h:57,
                    from include/linux/sched.h:54,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz4102/NVIDIA-Linux-x86-173.14.18-pkg1/usr/sr
   c/nv/nv-linux.h:19,
                    from /tmp/selfgz4102/NVIDIA-Linux-x86-173.14.18-pkg1/usr/sr
   c/nv/nv.c:14:
   include/linux/prefetch.h: In function ‘prefetch_range’:
   include/linux/prefetch.h:57: warning: pointer of type ‘void *’ used in a
   rithmetic
   In file included from include/linux/utsname.h:35,
                    from /tmp/selfgz4102/NVIDIA-Linux-x86-173.14.18-pkg1/usr/sr
   c/nv/nv-linux.h:19,
                    from /tmp/selfgz4102/NVIDIA-Linux-x86-173.14.18-pkg1/usr/sr
   c/nv/nv.c:14:
   include/linux/sched.h: In function ‘object_is_on_stack’:
   include/linux/sched.h:2124: warning: pointer of type ‘void *’ used in ar
   ithmetic
   In file included from /usr/src/linux-headers-2.6.28-3-rt/arch/x86/include/as
   m/dma-mapping.h:9,
                    from include/linux/dma-mapping.h:57,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from /usr/src/linux-headers-2.6.28-3-rt/arch/x86/include/as
   m/pci.h:94,
                    from include/linux/pci.h:1002,
                    from /tmp/selfgz4102/NVIDIA-Linux-x86-173.14.18-pkg1/usr/sr
   c/nv/nv-linux.h:86,
                    from /tmp/selfgz4102/NVIDIA-Linux-x86-173.14.18-pkg1/usr/sr
   c/nv/nv.c:14:
   include/linux/scatterlist.h: In function ‘sg_virt’:
   include/linux/scatterlist.h:199: warning: pointer of type ‘void *’ used 
   in arithmetic
   In file included from /usr/src/linux-headers-2.6.28-3-rt/arch/x86/include/as
   m/hardirq_32.h:5,
                    from /usr/src/linux-headers-2.6.28-3-rt/arch/x86/include/as
   m/hardirq.h:2,
                    from include/linux/hardirq.h:7,
                    from include/linux/interrupt.h:12,
                    from /tmp/selfgz4102/NVIDIA-Linux-x86-173.14.18-pkg1/usr/sr
   c/nv/nv-linux.h:87,
                    from /tmp/selfgz4102/NVIDIA-Linux-x86-173.14.18-pkg1/usr/sr
   c/nv/nv.c:14:
   include/linux/irq.h: In function ‘irq_to_desc’:
   include/linux/irq.h:203: warning: comparison between signed and unsigned
   In file included from /tmp/selfgz4102/NVIDIA-Linux-x86-173.14.18-pkg1/usr/sr
   c/nv/nv-linux.h:113,
                    from /tmp/selfgz4102/NVIDIA-Linux-x86-173.14.18-pkg1/usr/sr
   c/nv/nv.c:14:
   include/linux/highmem.h: In function ‘zero_user_segments’:
   include/linux/highmem.h:136: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:136: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:136: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:136: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:139: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:139: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:139: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:139: warning: pointer of type ‘void *’ used in a
   rithmetic
     cc -Wp,-MD,/tmp/selfgz4102/NVIDIA-Linux-x86-173.14.18-pkg1/usr/src/nv/.nv-
   vm.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.3.3/include -D__KER
   NEL__  -Iinclude  -I/usr/src/linux-headers-2.6.28-3-rt/arch/x86/include -inc
   lude include/linux/autoconf.h -Iubuntu/include  -Wall -Wundef -Wstrict-proto
   types -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-funct
   ion-declaration -O2 -m32 -msoft-float -mregparm=3 -freg-struct-return -mpref
   erred-stack-boundary=2 -march=i586 -mtune=generic -Wa,-mtune=generic32 -ffre
   estanding -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -
   mno-mmx -mno-sse2 -mno-3dnow -Iarch/x86/include/asm/mach-default -fno-stack-
   protector -fno-omit-frame-pointer -fno-optimize-sibling-calls -Wdeclaration-
   after-statement -Wno-pointer-sign -fwrapv -I/tmp/selfgz4102/NVIDIA-Linux-x86
   -173.14.18-pkg1/usr/src/nv -Wall -Wimplicit -Wreturn-type -Wswitch -Wfor
   mat -Wchar-subscripts -Wparentheses -Wpointer-arith -Wno-multichar -Werror -
   MD -Wsign-compare -Wno-cast-qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DN
   V_VERSION_STRING=\"173.14.18\" -UDEBUG -U_DEBUG -DNDEBUG -DMODULE -D"KBUILD_
   STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nv_vm)"  -D"KBUILD_MODNAME=KBUILD_S
   TR(nvidia)"  -c -o /tmp/selfgz4102/NVIDIA-Linux-x86-173.14.18-pkg1/usr/src/n
   v/.tmp_nv-vm.o /tmp/selfgz4102/NVIDIA-Linux-x86-173.14.18-pkg1/usr/src/nv/nv
   -vm.c
   In file included from include/linux/bitops.h:17,
                    from include/linux/kernel.h:15,
                    from include/linux/sched.h:52,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz4102/NVIDIA-Linux-x86-173.14.18-pkg1/usr/sr
   c/nv/nv-linux.h:19,
                    from /tmp/selfgz4102/NVIDIA-Linux-x86-173.14.18-pkg1/usr/sr
   c/nv/nv-vm.c:14:
   /usr/src/linux-headers-2.6.28-3-rt/arch/x86/include/asm/bitops.h: In functio
   n ‘set_bit’:
   /usr/src/linux-headers-2.6.28-3-rt/arch/x86/include/asm/bitops.h:60: warning
   : pointer of type ‘void *’ used in arithmetic
   /usr/src/linux-headers-2.6.28-3-rt/arch/x86/include/asm/bitops.h: In functio
   n ‘clear_bit’:
   /usr/src/linux-headers-2.6.28-3-rt/arch/x86/include/asm/bitops.h:97: warning
   : pointer of type ‘void *’ used in arithmetic
   In file included from include/linux/list.h:6,
                    from include/linux/preempt.h:11,
                    from include/linux/spinlock.h:50,
                    from include/linux/seqlock.h:29,
                    from include/linux/time.h:8,
                    from include/linux/timex.h:57,
                    from include/linux/sched.h:54,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz4102/NVIDIA-Linux-x86-173.14.18-pkg1/usr/sr
   c/nv/nv-linux.h:19,
                    from /tmp/selfgz4102/NVIDIA-Linux-x86-173.14.18-pkg1/usr/sr
   c/nv/nv-vm.c:14:
   include/linux/prefetch.h: In function ‘prefetch_range’:
   include/linux/prefetch.h:57: warning: pointer of type ‘void *’ used in a
   rithmetic
   In file included from include/linux/utsname.h:35,
                    from /tmp/selfgz4102/NVIDIA-Linux-x86-173.14.18-pkg1/usr/sr
   c/nv/nv-linux.h:19,
                    from /tmp/selfgz4102/NVIDIA-Linux-x86-173.14.18-pkg1/usr/sr
   c/nv/nv-vm.c:14:
   include/linux/sched.h: In function ‘object_is_on_stack’:
   include/linux/sched.h:2124: warning: pointer of type ‘void *’ used in ar
   ithmetic
   In file included from /usr/src/linux-headers-2.6.28-3-rt/arch/x86/include/as
   m/dma-mapping.h:9,
                    from include/linux/dma-mapping.h:57,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from /usr/src/linux-headers-2.6.28-3-rt/arch/x86/include/as
   m/pci.h:94,
                    from include/linux/pci.h:1002,
                    from /tmp/selfgz4102/NVIDIA-Linux-x86-173.14.18-pkg1/usr/sr
   c/nv/nv-linux.h:86,
                    from /tmp/selfgz4102/NVIDIA-Linux-x86-173.14.18-pkg1/usr/sr
   c/nv/nv-vm.c:14:
   include/linux/scatterlist.h: In function ‘sg_virt’:
   include/linux/scatterlist.h:199: warning: pointer of type ‘void *’ used 
   in arithmetic
   In file included from /usr/src/linux-headers-2.6.28-3-rt/arch/x86/include/as
   m/hardirq_32.h:5,
                    from /usr/src/linux-headers-2.6.28-3-rt/arch/x86/include/as
   m/hardirq.h:2,
                    from include/linux/hardirq.h:7,
                    from include/linux/interrupt.h:12,
                    from /tmp/selfgz4102/NVIDIA-Linux-x86-173.14.18-pkg1/usr/sr
   c/nv/nv-linux.h:87,
                    from /tmp/selfgz4102/NVIDIA-Linux-x86-173.14.18-pkg1/usr/sr
   c/nv/nv-vm.c:14:
   include/linux/irq.h: In function ‘irq_to_desc’:
   include/linux/irq.h:203: warning: comparison between signed and unsigned
   In file included from /tmp/selfgz4102/NVIDIA-Linux-x86-173.14.18-pkg1/usr/sr
   c/nv/nv-linux.h:113,
                    from /tmp/selfgz4102/NVIDIA-Linux-x86-173.14.18-pkg1/usr/sr
   c/nv/nv-vm.c:14:
   include/linux/highmem.h: In function ‘zero_user_segments’:
   include/linux/highmem.h:136: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:136: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:136: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:136: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:139: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:139: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:139: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:139: warning: pointer of type ‘void *’ used in a
   rithmetic
     cc -Wp,-MD,/tmp/selfgz4102/NVIDIA-Linux-x86-173.14.18-pkg1/usr/src/nv/.os-
   agp.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.3.3/include -D__KE
   RNEL__  -Iinclude  -I/usr/src/linux-headers-2.6.28-3-rt/arch/x86/include -in
   clude include/linux/autoconf.h -Iubuntu/include  -Wall -Wundef -Wstrict-prot
   otypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-func
   tion-declaration -O2 -m32 -msoft-float -mregparm=3 -freg-struct-return -mpre
   ferred-stack-boundary=2 -march=i586 -mtune=ge
   neric -Wa,-mtune=generic32 -ffreestanding -pipe -Wno-sign-compare -fno-async
   hronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Iarch/x86/incl
   ude/asm/mach-default -fno-stack-protector -fno-omit-frame-pointer -fno-optim
   ize-sibling-calls -Wdeclaration-after-statement -Wno-pointer-sign -fwrapv -I
   /tmp/selfgz4102/NVIDIA-Linux-x86-173.14.18-pkg1/usr/src/nv -Wall -Wimplicit 
   -Wreturn-type -Wswitch -Wformat -Wchar-subscripts -Wparentheses -Wpointer-ar
   ith -Wno-multichar -Werror -MD -Wsign-compare -Wno-cast-qual -Wno-error -D__
   KERNEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"173.14.18\" -UDEBUG -U_DEBUG 
   -DNDEBUG -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(os_agp)
   "  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)"  -c -o /tmp/selfgz4102/NVIDIA-Linux
   -x86-173.14.18-pkg1/usr/src/nv/.tmp_os-agp.o /tmp/selfgz4102/NVIDIA-Linux-x8
   6-173.14.18-pkg1/usr/src/nv/os-agp.c
   In file included from include/linux/bitops.h:17,
                    from include/linux/kernel.h:15,
                    from include/linux/sched.h:52,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz4102/NVIDIA-Linux-x86-173.14.18-pkg1/usr/sr
   c/nv/nv-linux.h:19,
                    from /tmp/selfgz4102/NVIDIA-Linux-x86-173.14.18-pkg1/usr/sr
   c/nv/os-agp.c:24:
   /usr/src/linux-headers-2.6.28-3-rt/arch/x86/include/asm/bitops.h: In functio
   n ‘set_bit’:
   /usr/src/linux-headers-2.6.28-3-rt/arch/x86/include/asm/bitops.h:60: warning
   : pointer of type ‘void *’ used in arithmetic
   /usr/src/linux-headers-2.6.28-3-rt/arch/x86/include/asm/bitops.h: In functio
   n ‘clear_bit’:
   /usr/src/linux-headers-2.6.28-3-rt/arch/x86/include/asm/bitops.h:97: warning
   : pointer of type ‘void *’ used in arithmetic
   In file included from include/linux/list.h:6,
                    from include/linux/preempt.h:11,
                    from include/linux/spinlock.h:50,
                    from include/linux/seqlock.h:29,
                    from include/linux/time.h:8,
                    from include/linux/timex.h:57,
                    from include/linux/sched.h:54,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz4102/NVIDIA-Linux-x86-173.14.18-pkg1/usr/sr
   c/nv/nv-linux.h:19,
                    from /tmp/selfgz4102/NVIDIA-Linux-x86-173.14.18-pkg1/usr/sr
   c/nv/os-agp.c:24:
   include/linux/prefetch.h: In function ‘prefetch_range’:
   include/linux/prefetch.h:57: warning: pointer of type ‘void *’ used in a
   rithmetic
   In file included from include/linux/utsname.h:35,
                    from /tmp/selfgz4102/NVIDIA-Linux-x86-173.14.18-pkg1/usr/sr
   c/nv/nv-linux.h:19,
                    from /tmp/selfgz4102/NVIDIA-Linux-x86-173.14.18-pkg1/usr/sr
   c/nv/os-agp.c:24:
   include/linux/sched.h: In function ‘object_is_on_stack’:
   include/linux/sched.h:2124: warning: pointer of type ‘void *’ used in ar
   ithmetic
   In file included from /usr/src/linux-headers-2.6.28-3-rt/arch/x86/include/as
   m/dma-mapping.h:9,
                    from include/linux/dma-mapping.h:57,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from /usr/src/linux-headers-2.6.28-3-rt/arch/x86/include/as
   m/pci.h:94,
                    from include/linux/pci.h:1002,
                    from /tmp/selfgz4102/NVIDIA-Linux-x86-173.14.18-pkg1/usr/sr
   c/nv/nv-linux.h:86,
                    from /tmp/selfgz4102/NVIDIA-Linux-x86-173.14.18-pkg1/usr/sr
   c/nv/os-agp.c:24:
   include/linux/scatterlist.h: In function ‘sg_virt’:
   include/linux/scatterlist.h:199: warning: pointer of type ‘void *’ used 
   in arithmetic
   In file included from /usr/src/linux-headers-2.6.28-3-rt/arch/x86/include/as
   m/hardirq_32.h:5,
                    from /usr/src/linux-headers-2.6.28-3-rt/arch/x86/include/as
   m/hardirq.h:2,
                    from include/linux/hardirq.h:7,
                    from include/linux/interrupt.h:12,
                    from /tmp/selfgz4102/NVIDIA-Linux-x86-173.14.18-pkg1/usr/sr
   c/nv/nv-linux.h:87,
                    from /tmp/selfgz4102/NVIDIA-Linux-x86-173.14.18-pkg1/usr/sr
   c/nv/os-agp.c:24:
   include/linux/irq.h: In function ‘irq_to_desc’:
   include/linux/irq.h:203: warning: comparison between signed and unsigned
   In file included from /tmp/selfgz4102/NVIDIA-Linux-x86-173.14.18-pkg1/usr/sr
   c/nv/nv-linux.h:113,
                    from /tmp/selfgz4102/NVIDIA-Linux-x86-173.14.18-pkg1/usr/sr
   c/nv/os-agp.c:24:
   include/linux/highmem.h: In function ‘zero_user_segments’:
   include/linux/highmem.h:136: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:136: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:136: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:136: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:139: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:139: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:139: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:139: warning: pointer of type ‘void *’ used in a
   rithmetic
     cc -Wp,-MD,/tmp/selfgz4102/NVIDIA-Linux-x86-173.14.18-pkg1/usr/src/nv/.os-
   interface.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.3.3/include 
   -D__KERNEL__  -Iinclude  -I/usr/src/linux-headers-2.6.28-3-rt/arch/x86/inclu
   de -include include/linux/autoconf.h -Iubuntu/include  -Wall -Wundef -Wstric
   t-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implici
   t-function-declaration -O2 -m32 -msoft-float -mregparm=3 -freg-struct-return
   -mpreferred-stack-boundary=2 -march=i586 -mtune=generic -Wa,-mtune=generic32
   -ffreestanding -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-
   sse -mno-mmx -mno-sse2 -mno-3dnow -Iarch/x86/include/asm/mach-default -fno-s
   tack-protector -fno-omit-frame-pointer -fno-optimize-sibling-calls -Wdeclara
   tion-after-statement -Wno-pointer-sign -fwrapv -I/tmp/selfgz4102/NVIDIA-Linu
   x-x86-173.14.18-pkg1/usr/src/nv -Wall -Wimplicit -Wreturn-type -Wswitch -Wfo
   rmat -Wchar-subscripts -Wparentheses -Wpointer-arith -Wno-multichar -Werror 
   -MD -Wsign-compare -Wno-cast-qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -D
   NV_VERSION_STRING=\"173.14.18\" -UDEBUG -U
   _DEBUG -DNDEBUG -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(
   os_interface)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)"  -c -o /tmp/selfgz4102
   /NVIDIA-Linux-x86-173.14.18-pkg1/usr/src/nv/.tmp_os-interface.o /tmp/selfgz4
   102/NVIDIA-Linux-x86-173.14.18-pkg1/usr/src/nv/os-interface.c
   In file included from include/linux/bitops.h:17,
                    from include/linux/kernel.h:15,
                    from include/linux/sched.h:52,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz4102/NVIDIA-Linux-x86-173.14.18-pkg1/usr/sr
   c/nv/nv-linux.h:19,
                    from /tmp/selfgz4102/NVIDIA-Linux-x86-173.14.18-pkg1/usr/sr
   c/nv/os-interface.c:26:
   /usr/src/linux-headers-2.6.28-3-rt/arch/x86/include/asm/bitops.h: In functio
   n ‘set_bit’:
   /usr/src/linux-headers-2.6.28-3-rt/arch/x86/include/asm/bitops.h:60: warning
   : pointer of type ‘void *’ used in arithmetic
   /usr/src/linux-headers-2.6.28-3-rt/arch/x86/include/asm/bitops.h: In functio
   n ‘clear_bit’:
   /usr/src/linux-headers-2.6.28-3-rt/arch/x86/include/asm/bitops.h:97: warning
   : pointer of type ‘void *’ used in arithmetic
   In file included from include/linux/list.h:6,
                    from include/linux/preempt.h:11,
                    from include/linux/spinlock.h:50,
                    from include/linux/seqlock.h:29,
                    from include/linux/time.h:8,
                    from include/linux/timex.h:57,
                    from include/linux/sched.h:54,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz4102/NVIDIA-Linux-x86-173.14.18-pkg1/usr/sr
   c/nv/nv-linux.h:19,
                    from /tmp/selfgz4102/NVIDIA-Linux-x86-173.14.18-pkg1/usr/sr
   c/nv/os-interface.c:26:
   include/linux/prefetch.h: In function ‘prefetch_range’:
   include/linux/prefetch.h:57: warning: pointer of type ‘void *’ used in a
   rithmetic
   In file included from include/linux/utsname.h:35,
                    from /tmp/selfgz4102/NVIDIA-Linux-x86-173.14.18-pkg1/usr/sr
   c/nv/nv-linux.h:19,
                    from /tmp/selfgz4102/NVIDIA-Linux-x86-173.14.18-pkg1/usr/sr
   c/nv/os-interface.c:26:
   include/linux/sched.h: In function ‘object_is_on_stack’:
   include/linux/sched.h:2124: warning: pointer of type ‘void *’ used in ar
   ithmetic
   In file included from /usr/src/linux-headers-2.6.28-3-rt/arch/x86/include/as
   m/dma-mapping.h:9,
                    from include/linux/dma-mapping.h:57,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from /usr/src/linux-headers-2.6.28-3-rt/arch/x86/include/as
   m/pci.h:94,
                    from include/linux/pci.h:1002,
                    from /tmp/selfgz4102/NVIDIA-Linux-x86-173.14.18-pkg1/usr/sr
   c/nv/nv-linux.h:86,
                    from /tmp/selfgz4102/NVIDIA-Linux-x86-173.14.18-pkg1/usr/sr
   c/nv/os-interface.c:26:
   include/linux/scatterlist.h: In function ‘sg_virt’:
   include/linux/scatterlist.h:199: warning: pointer of type ‘void *’ used 
   in arithmetic
   In file included from /usr/src/linux-headers-2.6.28-3-rt/arch/x86/include/as
   m/hardirq_32.h:5,
                    from /usr/src/linux-headers-2.6.28-3-rt/arch/x86/include/as
   m/hardirq.h:2,
                    from include/linux/hardirq.h:7,
                    from include/linux/interrupt.h:12,
                    from /tmp/selfgz4102/NVIDIA-Linux-x86-173.14.18-pkg1/usr/sr
   c/nv/nv-linux.h:87,
                    from /tmp/selfgz4102/NVIDIA-Linux-x86-173.14.18-pkg1/usr/sr
   c/nv/os-interface.c:26:
   include/linux/irq.h: In function ‘irq_to_desc’:
   include/linux/irq.h:203: warning: comparison between signed and unsigned
   In file included from /tmp/selfgz4102/NVIDIA-Linux-x86-173.14.18-pkg1/usr/sr
   c/nv/nv-linux.h:113,
                    from /tmp/selfgz4102/NVIDIA-Linux-x86-173.14.18-pkg1/usr/sr
   c/nv/os-interface.c:26:
   include/linux/highmem.h: In function ‘zero_user_segments’:
   include/linux/highmem.h:136: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:136: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:136: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:136: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:139: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:139: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:139: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:139: warning: pointer of type ‘void *’ used in a
   rithmetic
   /tmp/selfgz4102/NVIDIA-Linux-x86-173.14.18-pkg1/usr/src/nv/os-interface.c: I
   n function ‘os_alloc_sema’:
   /tmp/selfgz4102/NVIDIA-Linux-x86-173.14.18-pkg1/usr/src/nv/os-interface.c:13
   0: error: incompatible types in assignment
   /tmp/selfgz4102/NVIDIA-Linux-x86-173.14.18-pkg1/usr/src/nv/os-interface.c: I
   n function ‘os_acquire_sema’:
   /tmp/selfgz4102/NVIDIA-Linux-x86-173.14.18-pkg1/usr/src/nv/os-interface.c:17
   4: warning: passing argument 1 of ‘_spin_lock_irqsave’ from incompatible
   pointer type
   /tmp/selfgz4102/NVIDIA-Linux-x86-173.14.18-pkg1/usr/src/nv/os-interface.c:17
   8: warning: passing argument 1 of ‘_spin_unlock_irqrestore’ from incompa
   tible pointer type
   /tmp/selfgz4102/NVIDIA-Linux-x86-173.14.18-pkg1/usr/src/nv/os-interface.c:18
   5: warning: passing argument 1 of ‘_spin_unlock_irqrestore’ from incompa
   tible pointer type
   /tmp/selfgz4102/NVIDIA-Linux-x86-173.14.18-pkg1/usr/src/nv/os-interface.c: I
   n function ‘os_cond_acquire_sema’:
   /tmp/selfgz4102/NVIDIA-Linux-x86-173.14.18-pkg1/usr/src/nv/os-interface.c:20
   8: warning: passing argument 1 of ‘_spin_lock_irqsave’ from incompatible
   pointer type
   /tmp/selfgz4102/NVIDIA-Linux-x86-173.14.18-pkg1/usr/src/nv/os-interface.c:21
   1: warning: passing argument 1 of ‘_spin_unlock_irqrestore’ from incompa
   tible pointer type
   /tmp/selfgz4102/NVIDIA-Linux-x86-173.14.18-pkg1/usr/src/nv/os-interface.c:21
   8: warning: passing argument 1 of ‘_spin_unlock_irqrestore’ from incompa
   tible pointer type
   /tmp/selfgz4102/NVIDIA-Linux-x86-173.14.18-pkg1/usr/src/nv/os-interface.c: I
   n function ‘os_release_sema’:
   /tmp/selfgz4102/NVIDIA-Linux-x86-173.14.18-pkg1/usr/src/nv/os-interface.c:24
   2: warning: passing argument 1 of ‘_spin_lock_irqsave’ from incompatible
   pointer type
   /tmp/selfgz4102/NVIDIA-Linux-x86-173.14.18-pkg1/usr/src/nv/os-interface.c:25
   3: warning: passing argument 1 of ‘_spin_unlock_irqrestore’ from incompa
   tible pointer type
   make[3]: *** [/tmp/selfgz4102/NVIDIA-Linux-x86-173.14.18-pkg1/usr/src/nv/os-
   interface.o] Error 1
   make[2]: *** [_module_/tmp/selfgz4102/NVIDIA-Linux-x86-173.14.18-pkg1/usr/sr
   c/nv] Error 2
   NVIDIA: left KBUILD.
   nvidia.ko failed to build!
   make[1]: *** [module] Error 1
   make: *** [module] Error 2
-> Error.
ERROR: Unable to build the NVIDIA kernel module.
ERROR: Installation has failed.  Please see the file
       '/var/log/nvidia-installer.log' for details.  You may find suggestions
       on fixing installation problems in the README available on the Linux
       driver download page at www.nvidia.com.
```

I think all of my problems stem from the xorg.conf but don't know what to do next.

One more thing that is just odd... if I go to System >> Preferences, there is no Screen Resolution listed. I tried editing the menu to see if it was just hidden but it's not there at all.

Thanks in advance

---

### Post by Nxion on 2009-05-22
I had a similar issue with my setup. Can you post the output of this command:

```
lspci
```

---

### Post by gilmesh on 2009-05-22
Hope this helps :)

lspci
```
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 661FX/M661FX/M661MX Host (rev 11)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SiS AGP Port (virtual PCI-to-PCI bridge)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS964 [MuTIOL Media IO] (rev 36)
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev 01)
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 90)
00:05.0 IDE interface: Silicon Integrated Systems [SiS] RAID bus controller 180 SATA/PATA  [SiS] (rev 01)
00:0a.0 Network controller: Intersil Corporation Prism 2.5 Wavelan chipset (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5500] (rev a1)

```

---

### Post by goxi on 2009-05-22
After I activated nVidia driver from "System"->"Administration"->"Hardvare drivers", I opened Nautilus from terminal with "sudo Nautilus" and changed permissions of xorg.conf file to be read/write for my user. After that I went to "System"->"Administration"->"NVIDIA X server settings" and from "x server display configuration" I changed resolution ex. 1152x864 with 75Hz, and pressed "Apply". After that I pressed "Save to X configuration file". On new window pressed "Show prewiev" and copied all content of text. 
After I opened xorg.conf file and deleted all current content and pasted alredy coppied previous text. At the end i put this section for my type of monitor:
[FONT=Courier New]Section "Monitor"
    Identifier     "Configured Monitor"
    VendorName     "Unknown"
    ModelName      "PHILIPS 107E6"
    HorizSync       30.0 - 71.0
    VertRefresh     50.0 - 160.0
    Option         "DPMS"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "CRT-0"
    HorizSync       30.0 - 71.0
    VertRefresh     50.0 - 160.0
EndSection[/FONT]

[FONT=Arial]and I changed BOLDED row with desired resolution and frequency:
Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    **Option         "metamodes" "CRT: 1152x864_75 +0+0"**
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection
 The trick is to "tell" to system what kind of monitor and screen you use. Only installing the driver don`t do the trick.

After all I saved xorg.conf , rebooted and had desired resoluton.

I HOPE THIS WILL HELP YOU ! ;)
[/FONT]

---

### Post by gilmesh on 2009-05-22
Thanks, I think I'm getting closer.  When I go to Restricted Hardware and activate the 173.14.16 driver, it looks like it is happening, but the gray circle next to the driver never turns green. When I boot, the system tries to load the driver selected in Restricted Hardware and then fails. I go to Nvidia X Server settings and I get a popup that says it appears that i'm not using a Nvidia driver and to run 'nvidia-xconfig'. I can't do anything in the X Server settings, and when I shut down the gdm, run nvidia-xconfig, it goes back to the prompt.  I assume it is doing what it is supposed to do without any errors, but the X Server settings still has that popup.

I've tried to write the xorg.conf and when I start the xserver I get unable to load the Nvidia kernel, and Screens were found, but none had a usable configuration.

Either my problem is in the xorg.conf, or I need to figure out how to get the Nvidia kernel to load.  

```
Section "Monitor"
	Identifier "Configured Monitor"
	VendorName "Unknown"
	ModelName "Elements"
	HorizSync 30.0 - 72.0
	VertRefresh 50.0 - 160.0
	Option "DPMS"
EndSection

Section "Monitor"
	Identifier "Monitor0"
	VendorName "Unknown"
	ModelName "CRT-0"
	HorizSync 30.0 - 72.0
	VertRefresh 50.0 - 160.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Option "metamodes" "CRT: 1024x768_75 +0+0"
	SubSection "Display"
		Depth 24
	EndSubSection
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection

```

---

### Post by goxi on 2009-05-25
Try to remove any nvidia drivers / files  through **synaptic** and **add/remowe** and reboot and after that try again to enable nvidia driver from "Hardware drivers".

I`ll try to find something in Fedora forums. I think they have something about this problem...

---

### Post by goxi on 2009-05-25
> **goxi said:**
> Try to remove any nvidia drivers / files  through **synaptic** and **add/remowe** and reboot and after that try again to enable nvidia driver from "Hardware drivers".

I`ll try to find something in Fedora forums. I think they have something about this problem...
  What ever you do , do not use downloaded nvidia drivers. On several configurations I had problem with kernel module.

---

### Post by goxi on 2009-05-25
> **goxi said:**
> After I activated nVidia driver from "System"->"Administration"->"Hardvare drivers", I opened Nautilus from terminal with "sudo Nautilus" and changed permissions of xorg.conf file to be read/write for my user. After that I went to "System"->"Administration"->"NVIDIA X server settings" and from "x server display configuration" I changed resolution ex. 1152x864 with 75Hz, and pressed "Apply". After that I pressed "Save to X configuration file". On new window pressed "Show prewiev" and copied all content of text. 
After I opened xorg.conf file and deleted all current content and pasted alredy coppied previous text. At the end i put this section for my type of monitor:
[FONT=Courier New]Section "Monitor"
    Identifier     "Configured Monitor"
    VendorName     "Unknown"
    ModelName      "PHILIPS 107E6"
    HorizSync       30.0 - 71.0
    VertRefresh     50.0 - 160.0
    Option         "DPMS"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "CRT-0"
    HorizSync       30.0 - 71.0
    VertRefresh     50.0 - 160.0
EndSection[/FONT]

[FONT=Arial]and I changed BOLDED row with desired resolution and frequency:
Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    **Option         "metamodes" "CRT: 1152x864_75 +0+0"**
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection
 The trick is to "tell" to system what kind of monitor and screen you use. Only installing the driver don`t do the trick.

After all I saved xorg.conf , rebooted and had desired resoluton.

I HOPE THIS WILL HELP YOU ! ;)
[/FONT]

Before you do anything read and try this [http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

---

### Post by gilmesh on 2009-05-28
Thank you goxi.  I just got back into town.  I have it working fine now, but I had to install ubuntu studio 8.10.  Once I did, the hardware driver activated right away, and then I edited xorg.conf to 

```
Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Device0"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection

Section "Monitor"
	Identifier "Monitor0"
	VendorName "Elements"
	ModelName "CRT-0"
	HorizSync 30.0 - 72.0
	VertRefresh 50.0 - 160.0
	Option "DPMS"
EndSection

Section "Screen"
	Identifier "Screen0"
	Device "Device0"
	Monitor "Monitor0"
	DefaultDepth 24
	SubSection "Display"
		Depth        24
		Modes      "1024x768_70.00"
	EndSubSection
EndSection
```

I have about 20 different resolutions to choose from now, and they all work great.  One note, I had two screen sections and it was taking the 1st one only.  Since this was the default info, I removed it and all is well.

---

### Post by anikrish23411599 on 2009-05-31
even icant do it.when i boot up ubuntu without my fx 5500 graphics card fixed it works fine.but when i insert my graphics card and start it the loading bar gets stuck in loadding harware drivers.someone please help me.
my computer is
pentium 4
ubuntu 9.04
384 mb ram
256 mb fx5500:(

---

### Post by goxi on 2009-06-02
> **anikrish23411599 said:**
> even icant do it.when i boot up ubuntu without my fx 5500 graphics card fixed it works fine.but when i insert my graphics card and start it the loading bar gets stuck in loadding harware drivers.someone please help me.
my computer is
pentium 4
ubuntu 9.04
384 mb ram
256 mb fx5500:(
Did you installed it with or without graphic card inserted in slot ?

---

### Post by kdi on 2009-06-07
I'm using ubuntu studio 8.10. i'm not sure if [this page]("http://paktamcyber.blogspot.com/2009/06/its-nearly-week-for-me-to-configure-my.html") could help you. the writer has listed down the steps from configuring xorg.conf file to blacklisting modules. gud luck.:D

---

