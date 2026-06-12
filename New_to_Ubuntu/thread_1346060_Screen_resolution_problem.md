---
title: "Screen resolution problem"
date: 2009-12-04
forum: New to Ubuntu
---

### Post by staffann on 2009-12-04
I installed Ubuntu 9.10 yesterday and I'm having problems with the screen resolution. 
I've got an LCD screen capable of 1600*1200 connected to a Nvidia Geforce 5200 card through a SVGA connector. I can only get a resolution of 800*600 and the utility under System->Preferences->Display doesn't give me any higher options. It also says that the monitor is Unknown.
Currently my xorg.conf is empty(!). I've tried the command "sudo dpkg-reconfigure -phigh xserver-xorg" but it doesn't seem to do anything. It doesn't change the resolution nor does it put anything into xorg.conf.

How should I proceed in order to solve this problem?

This is my /var/log/Xorg.0.log file:
```


X.Org X Server 1.6.4
Release Date: 2009-9-27
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux bilbo 2.6.31-15-generic #50-Ubuntu SMP Tue Nov 10 14:54:29 UTC 2009 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-15-generic root=UUID=09ea6619-71aa-44e5-a407-3b89e558ab86 ro quiet splash
Build Date: 26 October 2009  05:15:02PM
xorg-server 2:1.6.4-2ubuntu4 (buildd@) 
    Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Fri Dec  4 22:30:37 2009
(==) Using config file: "/etc/X11/xorg.conf"
(==) No Layout section.  Using the first Screen section.
(==) No screen section available. Using defaults.
(**) |-->Screen "Default Screen Section" (0)
(**) |   |-->Monitor "<default monitor>"
(==) No monitor specified for screen "Default Screen Section".
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
(II) Loader magic: 0x3bc0
(II) Module ABI versions:
    X.Org ANSI C Emulation: 0.4
    X.Org Video Driver: 5.0
    X.Org XInput driver : 4.0
    X.Org Server Extension : 2.0
(II) Loader running on linux
(++) using VT number 7

(--) PCI:*(0:4:0:0) 10de:0322:0000:0000 nVidia Corporation NV34 [GeForce FX 5200] rev 161, Mem @ 0xfd000000/16777216, 0xc8000000/134217728, BIOS @ 0x????????/131072
(II) Open ACPI successful (/var/run/acpid.socket)
(II) System resource ranges:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [4] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [5] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [6] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [7] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [8] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [9] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [10] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [11] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [12] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [13] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [14] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [15] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [16] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [17] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [18] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [19] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [20] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [21] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [22] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [23] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [24] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [25] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
    [26] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [27] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
    [28] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [29] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
    [30] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [31] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
    [32] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [33] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
    [34] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [35] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
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
(II) Module glx: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 1.0.0
    ABI class: X.Org Server Extension, version 2.0
(==) AIGLX enabled
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
(==) Matched nv for the autoconfigured driver
(==) Assigned the driver to the xf86ConfigLayout
(II) LoadModule: "nv"
(II) Loading /usr/lib/xorg/modules/drivers//nv_drv.so
(II) Module nv: vendor="X.Org Foundation"
    compiled for 1.6.3, module version = 2.1.14
    Module class: X.Org Video Driver
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
(II) Primary Device is: PCI 04@00:00:0
(--) NV: Found NVIDIA  GeForce FX 5200 at 04@00:00:0
(II) resource ranges after probing:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [4] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [5] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [6] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [7] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [8] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [9] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [10] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [11] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [12] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [13] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [14] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [15] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [16] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [17] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [18] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [19] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [20] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [21] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [22] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [23] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [24] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [25] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
    [26] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [27] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
    [28] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [29] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
    [30] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [31] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
    [32] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [33] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
    [34] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [35] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
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
    "Default Screen Section" for depth/fbbpp 24/32
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
(--) NV(0): Linear framebuffer at 0xC8000000
(--) NV(0): MMIO registers at 0xFD000000
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
(--) NV(0): VideoRAM: 131072 kBytes
(==) NV(0): Using gamma correction (1.0, 1.0, 1.0)
(II) NV(0): <default monitor>: Using default hsync range of 31.50-37.90 kHz
(II) NV(0): <default monitor>: Using default vrefresh range of 50.00-70.00 Hz
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
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [4] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [5] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [6] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [7] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [8] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [9] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [10] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [11] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [12] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [13] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [14] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [15] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [16] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [17] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [18] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [19] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [20] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [21] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [22] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [23] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [24] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [25] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
    [26] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [27] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
    [28] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [29] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
    [30] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [31] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
    [32] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [33] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
    [34] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [35] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
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
(II) AIGLX: Screen 0 is not DRI2 capable
(II) AIGLX: Screen 0 is not DRI capable
(II) AIGLX: Loaded and initialized /usr/lib/dri/swrast_dri.so
(II) GLX: Initialized DRISWRAST GL provider for screen 0
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
(**) Option "xkb_layout" "se"
(II) config/hal: Adding input device AT Translated Set 2 keyboard
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event3"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "se"
(II) config/hal: Adding input device Power Button
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event1"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "se"
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
(II) config/hal: Adding input device A4Tech PS/2+USB Mouse
(**) A4Tech PS/2+USB Mouse: always reports core events
(**) A4Tech PS/2+USB Mouse: Device: "/dev/input/event4"
(II) A4Tech PS/2+USB Mouse: Found 12 mouse buttons
(II) A4Tech PS/2+USB Mouse: Found x and y relative axes
(II) A4Tech PS/2+USB Mouse: Found scroll wheel(s)
(II) A4Tech PS/2+USB Mouse: Configuring as mouse
(**) A4Tech PS/2+USB Mouse: YAxisMapping: buttons 4 and 5
(**) A4Tech PS/2+USB Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "A4Tech PS/2+USB Mouse" (type: MOUSE)
(**) A4Tech PS/2+USB Mouse: (accel) keeping acceleration scheme 1
(**) A4Tech PS/2+USB Mouse: (accel) filter chain progression: 2.00
(**) A4Tech PS/2+USB Mouse: (accel) filter stage 0: 20.00 ms
(**) A4Tech PS/2+USB Mouse: (accel) set acceleration profile 0
(II) A4Tech PS/2+USB Mouse: initialized for relative axes.

```

---

### Post by jbrown96 on 2009-12-04
You need to install the Nvidia drivers. System-->Admin-->Hardware drivers.

---

### Post by staffann on 2009-12-04
Ok, done. I am now down to VGA resolution :( The Nvidia control panel doesn't let me choose a higher resolution either.
At least I now have something in the xorg.conf:

```


Section "Screen"
    Identifier    "Default Screen"
    DefaultDepth    24
EndSection

Section "Module"
    Load    "glx"
EndSection

Section "Device"
    Identifier    "Default Device"
    Driver    "nvidia"
    Option    "NoLogo"    "True"
EndSection


```

---

### Post by ed-koala on 2009-12-04
What is the make/model of your monitor?

---

### Post by ST3ALTHPSYCH0 on 2009-12-04
[This page]("http://ubuntuforums.org/showthread.php?t=1319491&page=4;%20postcount=38") has a couple of options. Post # 38 tells how to manually edit you Xorg.conf file. Post #34 has a link to my cheater's how-to.

---

### Post by staffann on 2009-12-04
My monitor is a LG Flatron L2010T. It's an LCD 20" screen (not wide-screen).

I'll check the other thread, the howto and so on but right now I haven't got the faintest idea what to do if I need to hack the xorg.conf.

---

### Post by thiebaude on 2009-12-04
sudo nvidia-settings then set your resolution, then close, and then do a gksudo gedit /etc/X11/xorg.conf under the screen section add   Device   "Default Device" and save then sudo nvidia-setttings and save to X configuration and exit.

---

### Post by staffann on 2009-12-04
I tried adding a monitor section according to the how-to linked earlier but the monitor complained and couldn't show the picture. I removed the monitor section so that the xorg.conf is back to original but now I still cannot start X because the monitor still says that the refresh rate is too high.
 
I cannot understand why ubuntu doesn't revert back to the VGA resolution that I had before now that I changed back the xorg.conf file!!! Gdm starts up but when I choose to log in as me the screen settings change to something that the monitor cannot handle. What can cause that???

---

### Post by staffann on 2009-12-05
So my status was that although gdm started, an invalid update frequency was selected as soon as I logged in. So what to do?
Well, I did at least have 800*600 when I didn't have any xorg.conf at all so I removed it again. Then I could log into X again. Surprisingly, this time I could change the resolution from the Nvidia applet. I've got no idea what was different this time. Anyway I've not got my desired resolution of 1600*1200. I just which I could understand what happend...

---

### Post by cjohnston on 2009-12-05
> **staffann said:**
> So my status was that although gdm started, an invalid update frequency was selected as soon as I logged in. So what to do?
Well, I did at least have 800*600 when I didn't have any xorg.conf at all so I removed it again. Then I could log into X again. Surprisingly, this time I could change the resolution from the Nvidia applet. I've got no idea what was different this time. Anyway I've not got my desired resolution of 1600*1200. I just which I could understand what happend...

Are you still having problems? If so, try running:

sudo nvidia-xconfig

And then run:

sudo nvidia-settings

You should then be able to make all your changes and save them in the nvidia-settings app.

---

### Post by staffann on 2009-12-05
No, it works now! I don't know why any more than I know why it didn't work before!

Actually I forgot that the nvidia app gave me a pop-up message saying that I should run nvidia-xconfig. I did but after I already had the correct resolution. It created a simple xorg.conf again.

```

Section "Screen"
    Identifier    "Configured Screen Device"
    DefaultDepth    24
EndSection

Section "Device"
    Identifier    "Configured Video Device"
    Driver    "nvidia"
EndSection

```

---

### Post by hnaqvi46 on 2010-04-25
Hi Staffan,

I'm new to ubuntu..i don't have any programming experience and I'm having the same problem you did. Could you please walk me through the steps to fix this in an instant messenger?

Please reply at [email]hnaqvi46@gmail.com[/email]

I'd really appreciate your help

Sincerely,
an ubuntu newbie :(

> **staffann said:**
> No, it works now! I don't know why any more than I know why it didn't work before!

Actually I forgot that the nvidia app gave me a pop-up message saying that I should run nvidia-xconfig. I did but after I already had the correct resolution. It created a simple xorg.conf again.

```

Section "Screen"
    Identifier    "Configured Screen Device"
    DefaultDepth    24
EndSection

Section "Device"
    Identifier    "Configured Video Device"
    Driver    "nvidia"
EndSection

```

---

