---
title: "unexpected crash!"
date: 2010-01-07
forum: New to Ubuntu
---

### Post by abhe on 2010-01-07
when I quit any game , my system crash and nothing happen or even can move
and i cant log off or restart  ,unless by heart kill
help ?:KS

---

### Post by iponeverything on 2010-01-07
Not much to go on here. How do you expect to get help, when you provide no useful information? No os, no hardware, no games, nothing. 

People here are good, but not that good.

---

### Post by abhe on 2010-01-07
> **iponeverything said:**
> Not much to go on here. How do you expect to get help, when you provide no useful information? No os, no hardware, no games, nothing. 

People here are good, but not that good.


maybe some 1 had face this trouble , im noob you know
games : teeworld  ,  assault cube  ,  tuxracer
ubuntu 9.10 karmic koala , gnome desktop , 

i dont know what drivers i have , but i took a screenshot for Hardware Drivers manager


[[IMG]http://up4.m5zn.com/9bjndthcm6y53q1w0kvpz47xgs82rf/2010/1/6/11/7lpghfgi9.png[/IMG]]("http://www.tobikat.com") 


and sorry for bothoring you :D

---

### Post by abhe on 2010-01-07
im waiting -_-

---

### Post by Soul-Sing on 2010-01-07
your Xorg.0.log should give us some important information.

---

### Post by abhe on 2010-01-07
> **leoquant said:**
> your Xorg.0.log should give us some important information.

here is the Xorg.0.log

[php]
X.Org X Server 1.6.4
Release Date: 2009-9-27
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux mohsen-laptop 2.6.31-16-generic #53-Ubuntu SMP Tue Dec 8 04:01:29 UTC 2009 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-16-generic root=UUID=59064e78-2224-4687-9390-1b67bd43584c ro quiet splash
Build Date: 26 October 2009  05:15:02PM
xorg-server 2:1.6.4-2ubuntu4 (buildd@) 
    Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Thu Jan  7 02:01:20 2010
(II) Loader magic: 0x3bc0
(II) Module ABI versions:
    X.Org ANSI C Emulation: 0.4
    X.Org Video Driver: 5.0
    X.Org XInput driver : 4.0
    X.Org Server Extension : 2.0
(II) Loader running on linux
(++) using VT number 7

(--) PCI:*(0:0:2:0) 8086:2a02:1179:ff00 Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller rev 12, Mem @ 0xfc000000/1048576, 0xd0000000/268435456, I/O @ 0x00001800/8
(==) Using default built-in configuration (39 lines)
(==) --- Start of built-in configuration ---
    Section "Device"
        Identifier    "Builtin Default intel Device 0"
        Driver    "intel"
    EndSection
    Section "Screen"
        Identifier    "Builtin Default intel Screen 0"
        Device    "Builtin Default intel Device 0"
    EndSection
    Section "Device"
        Identifier    "Builtin Default i810 Device 0"
        Driver    "i810"
    EndSection
    Section "Screen"
        Identifier    "Builtin Default i810 Screen 0"
        Device    "Builtin Default i810 Device 0"
    EndSection
    Section "Device"
        Identifier    "Builtin Default vesa Device 0"
        Driver    "vesa"
    EndSection
    Section "Screen"
        Identifier    "Builtin Default vesa Screen 0"
        Device    "Builtin Default vesa Device 0"
    EndSection
    Section "Device"
        Identifier    "Builtin Default fbdev Device 0"
        Driver    "fbdev"
    EndSection
    Section "Screen"
        Identifier    "Builtin Default fbdev Screen 0"
        Device    "Builtin Default fbdev Device 0"
    EndSection
    Section "ServerLayout"
        Identifier    "Builtin Default Layout"
        Screen    "Builtin Default intel Screen 0"
        Screen    "Builtin Default i810 Screen 0"
        Screen    "Builtin Default vesa Screen 0"
        Screen    "Builtin Default fbdev Screen 0"
    EndSection
(==) --- End of built-in configuration ---
(==) ServerLayout "Builtin Default Layout"
(**) |-->Screen "Builtin Default intel Screen 0" (0)
(**) |   |-->Monitor "<default monitor>"
(**) |   |-->Device "Builtin Default intel Device 0"
(==) No monitor specified for screen "Builtin Default intel Screen 0".
    Using a default monitor configuration.
(**) |-->Screen "Builtin Default i810 Screen 0" (1)
(**) |   |-->Monitor "<default monitor>"
(**) |   |-->Device "Builtin Default i810 Device 0"
(==) No monitor specified for screen "Builtin Default i810 Screen 0".
    Using a default monitor configuration.
(**) |-->Screen "Builtin Default vesa Screen 0" (2)
(**) |   |-->Monitor "<default monitor>"
(**) |   |-->Device "Builtin Default vesa Device 0"
(==) No monitor specified for screen "Builtin Default vesa Screen 0".
    Using a default monitor configuration.
(**) |-->Screen "Builtin Default fbdev Screen 0" (3)
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
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [4] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [5] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
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
(II) LoadModule: "intel"
(II) Loading /usr/lib/xorg/modules/drivers//intel_drv.so
(II) Module intel: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 2.9.0
    Module class: X.Org Video Driver
    ABI class: X.Org Video Driver, version 5.0
(II) LoadModule: "i810"
(WW) Warning, couldn't open module i810
(II) UnloadModule: "i810"
(EE) Failed to load module "i810" (module does not exist, 0)
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
(II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
    i810-dc100, i810e, i815, i830M, 845G, 852GM/855GM, 865G, 915G,
    E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
    965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
    4 Series, G45/G43, Q45/Q43, G41, B43, Clarkdale, Arrandale
(II) VESA: driver for VESA chipsets: vesa
(II) FBDEV: driver for framebuffer: fbdev
(II) Primary Device is: PCI 00@00:02:0
(WW) Falling back to old probe method for vesa
(WW) Falling back to old probe method for fbdev
(II) Loading sub module "fbdevhw"
(II) LoadModule: "fbdevhw"
(II) Loading /usr/lib/xorg/modules/linux//libfbdevhw.so
(II) Module fbdevhw: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 0.0.2
    ABI class: X.Org Video Driver, version 5.0
(II) resource ranges after probing:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [4] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [5] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: Searching for BusID pci:0000:00:02.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: drmOpenMinor returns 8
drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
(II) intel(0): Creating default Display subsection in Screen section
    "Builtin Default intel Screen 0" for depth/fbbpp 24/32
(==) intel(0): Depth 24, (--) framebuffer bpp 32
(==) intel(0): RGB weight 888
(==) intel(0): Default visual is TrueColor
(II) intel(0): Integrated Graphics Chipset: Intel(R) 965GM
(--) intel(0): Chipset: "965GM"
(II) intel(0): Output VGA1 has no monitor section
(II) intel(0): Output LVDS1 has no monitor section
(II) intel(0): found backlight control interface /sys/class/backlight/acpi_video0
(II) intel(0): Output TV1 has no monitor section
(II) intel(0): EDID for output VGA1
(II) intel(0): EDID for output LVDS1
(II) intel(0): Manufacturer: AUO  Model: 2574  Serial#: 0
(II) intel(0): Year: 2006  Week: 1
(II) intel(0): EDID Version: 1.3
(II) intel(0): Digital Display Input
(II) intel(0): Max Image Size [cm]: horiz.: 33  vert.: 21
(II) intel(0): Gamma: 2.20
(II) intel(0): No DPMS capabilities specified
(II) intel(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) intel(0): First detailed timing is preferred mode
(II) intel(0): redX: 0.590 redY: 0.345   greenX: 0.315 greenY: 0.555
(II) intel(0): blueX: 0.155 blueY: 0.155   whiteX: 0.313 whiteY: 0.329
(II) intel(0): Manufacturer's mask: 0
(II) intel(0): Supported detailed timing:
(II) intel(0): clock: 71.1 MHz   Image Size:  331 x 207 mm
(II) intel(0): h_active: 1280  h_sync: 1328  h_sync_end 1360 h_blank_end 1440 h_border: 0
(II) intel(0): v_active: 800  v_sync: 803  v_sync_end 809 v_blanking: 823 v_border: 0
(WW) intel(0): Unknown vendor-specific block f
(II) intel(0):  AUO
(II) intel(0):  B154EW02 V5
(II) intel(0): EDID (in hex):
(II) intel(0):     00ffffffffffff0006af742500000000
(II) intel(0):     01100103802115780a1cf59758508e27
(II) intel(0):     27505400000001010101010101010101
(II) intel(0):     010101010101c71b00a0502017303020
(II) intel(0):     36004bcf100000180000000f00000000
(II) intel(0):     00000000000000000020000000fe0041
(II) intel(0):     554f0a202020202020202020000000fe
(II) intel(0):     004231353445573032205635200a00a1
(II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1280x960" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1280x960" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1280x1024" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1280x1024" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1280x1024" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1792x1344" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1792x1344" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1856x1392" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1856x1392" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1920x1440" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1920x1440" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1360x768" (monitor doesn't support reduced blanking)
(II) intel(0): Not using default mode "1360x768" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1400x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1400x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1400x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1400x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1440x900" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1600x1024" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1680x1050" (monitor doesn't support reduced blanking)
(II) intel(0): Not using default mode "1680x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1680x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1680x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1680x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1920x1080" (monitor doesn't support reduced blanking)
(II) intel(0): Not using default mode "1920x1200" (monitor doesn't support reduced blanking)
(II) intel(0): Not using default mode "1920x1440" (exceeds panel dimensions)
(II) intel(0): Not using default mode "2048x1536" (exceeds panel dimensions)
(II) intel(0): Not using default mode "2048x1536" (exceeds panel dimensions)
(II) intel(0): Not using default mode "2048x1536" (exceeds panel dimensions)
(II) intel(0): Printing probed modes for output LVDS1
(II) intel(0): Modeline "1280x800"x60.0   71.11  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.4 kHz)
(II) intel(0): Modeline "1024x768"x85.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
(II) intel(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) intel(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) intel(0): Modeline "800x600"x85.1   56.30  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
(II) intel(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) intel(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x85.0   36.00  640 696 752 832  480 481 484 509 -hsync -vsync (43.3 kHz)
(II) intel(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) intel(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x85.0   35.50  720 756 828 936  400 401 404 446 -hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "640x400"x85.1   31.50  640 672 736 832  400 401 404 445 -hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "640x350"x85.1   31.50  640 672 736 832  350 382 385 445 +hsync -vsync (37.9 kHz)
(II) intel(0): EDID for output TV1
(II) intel(0): Output VGA1 disconnected
(II) intel(0): Output LVDS1 connected
(II) intel(0): Output TV1 disconnected
(II) intel(0): Using exact sizes for initial modes
(II) intel(0): Output LVDS1 using initial mode 1280x800
(==) intel(0): video overlay key set to 0x101fe
(==) intel(0): Using gamma correction (1.0, 1.0, 1.0)
(==) intel(0): DPI set to (96, 96)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.4
(II) UnloadModule: "vesa"
(II) Unloading /usr/lib/xorg/modules/drivers//vesa_drv.so
(II) UnloadModule: "fbdev"
(II) Unloading /usr/lib/xorg/modules/drivers//fbdev_drv.so
(II) UnloadModule: "fbdevhw"
(II) Unloading /usr/lib/xorg/modules/linux//libfbdevhw.so
(==) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [4] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [5] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
(II) intel(0): [DRI2] Setup complete
(**) intel(0): Framebuffer compression disabled
(**) intel(0): Tiling enabled
(**) intel(0): SwapBuffers wait enabled
(==) intel(0): VideoRam: 262144 KB
(II) intel(0): Attempting memory allocation with tiled buffers.
(II) intel(0): Tiled allocation successful.
(II) UXA(0): Driver registered support for the following operations:
(II)         solid
(II)         copy
(II)         composite (RENDER acceleration)
(==) intel(0): Backing store disabled
(==) intel(0): Silken mouse enabled
(II) intel(0): Initializing HW Cursor
(II) intel(0): No memory allocations
(II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
(II) intel(0): DPMS enabled
(==) intel(0): Intel XvMC decoder disabled
(II) intel(0): Set up textured video
(II) intel(0): direct rendering: DRI2 Enabled
(--) RandR disabled
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
(II) AIGLX: enabled GLX_MESA_copy_sub_buffer
(II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
(II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
(II) AIGLX: Loaded and initialized /usr/lib/dri/i965_dri.so
(II) GLX: Initialized DRI2 GL provider for screen 0
(II) intel(0): Setting screen physical size to 331 x 207
(II) config/hal: Adding input device Chicony USB 2.0 Camera
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 2.2.5
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 4.0
(**) Chicony USB 2.0 Camera: always reports core events
(**) Chicony USB 2.0 Camera: Device: "/dev/input/event6"
(II) Chicony USB 2.0 Camera: Found keys
(II) Chicony USB 2.0 Camera: Configuring as keyboard
(II) XINPUT: Adding extended input device "Chicony USB 2.0 Camera" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us,ara"
(**) Option "xkb_variant" ","
(**) Option "xkb_options" "grp:alt_shift_toggle,grp_led:scroll"
(II) config/hal: Adding input device Power Button
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event2"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us,ara"
(**) Option "xkb_variant" ","
(**) Option "xkb_options" "grp:alt_shift_toggle,grp_led:scroll"
(II) config/hal: Adding input device AT Translated Set 2 keyboard
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event4"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us,ara"
(**) Option "xkb_variant" ","
(**) Option "xkb_options" "grp:alt_shift_toggle,grp_led:scroll"
(II) config/hal: Adding input device Video Bus
(**) Video Bus: always reports core events
(**) Video Bus: Device: "/dev/input/event5"
(II) Video Bus: Found keys
(II) Video Bus: Configuring as keyboard
(II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us,ara"
(**) Option "xkb_variant" ","
(**) Option "xkb_options" "grp:alt_shift_toggle,grp_led:scroll"
(II) config/hal: Adding input device Power Button
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event0"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us,ara"
(**) Option "xkb_variant" ","
(**) Option "xkb_options" "grp:alt_shift_toggle,grp_led:scroll"
(II) config/hal: Adding input device AlpsPS/2 ALPS GlidePoint
(II) LoadModule: "synaptics"
(II) Loading /usr/lib/xorg/modules/input//synaptics_drv.so
(II) Module synaptics: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 1.1.2
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 4.0
(II) Synaptics touchpad driver version 1.1.2
(**) Option "Device" "/dev/input/event9"
(II) AlpsPS/2 ALPS GlidePoint: x-axis range 0 - 1023
(II) AlpsPS/2 ALPS GlidePoint: y-axis range 0 - 767
(II) AlpsPS/2 ALPS GlidePoint: pressure range 0 - 127
(II) AlpsPS/2 ALPS GlidePoint: finger width range 0 - 0
(II) AlpsPS/2 ALPS GlidePoint: buttons: left right middle
(--) AlpsPS/2 ALPS GlidePoint: touchpad found
(**) AlpsPS/2 ALPS GlidePoint: always reports core events
(II) XINPUT: Adding extended input device "AlpsPS/2 ALPS GlidePoint" (type: TOUCHPAD)
(**) AlpsPS/2 ALPS GlidePoint: (accel) keeping acceleration scheme 1
(**) AlpsPS/2 ALPS GlidePoint: (accel) filter chain progression: 2.00
(**) AlpsPS/2 ALPS GlidePoint: (accel) filter stage 0: 20.00 ms
(**) AlpsPS/2 ALPS GlidePoint: (accel) set acceleration profile 0
(--) AlpsPS/2 ALPS GlidePoint: touchpad found
(II) config/hal: Adding input device PS/2 Mouse
(**) PS/2 Mouse: always reports core events
(**) PS/2 Mouse: Device: "/dev/input/event8"
(II) PS/2 Mouse: Found 3 mouse buttons
(II) PS/2 Mouse: Found x and y relative axes
(II) PS/2 Mouse: Configuring as mouse
(**) PS/2 Mouse: YAxisMapping: buttons 4 and 5
(**) PS/2 Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "PS/2 Mouse" (type: MOUSE)
(**) PS/2 Mouse: (accel) keeping acceleration scheme 1
(**) PS/2 Mouse: (accel) filter chain progression: 2.00
(**) PS/2 Mouse: (accel) filter stage 0: 20.00 ms
(**) PS/2 Mouse: (accel) set acceleration profile 0
(II) PS/2 Mouse: initialized for relative axes.
(II) config/hal: Adding input device Macintosh mouse button emulation
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event3"
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
(II) intel(0): EDID for output VGA1
(II) intel(0): EDID for output LVDS1
(II) intel(0): Manufacturer: AUO  Model: 2574  Serial#: 0
(II) intel(0): Year: 2006  Week: 1
(II) intel(0): EDID Version: 1.3
(II) intel(0): Digital Display Input
(II) intel(0): Max Image Size [cm]: horiz.: 33  vert.: 21
(II) intel(0): Gamma: 2.20
(II) intel(0): No DPMS capabilities specified
(II) intel(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) intel(0): First detailed timing is preferred mode
(II) intel(0): redX: 0.590 redY: 0.345   greenX: 0.315 greenY: 0.555
(II) intel(0): blueX: 0.155 blueY: 0.155   whiteX: 0.313 whiteY: 0.329
(II) intel(0): Manufacturer's mask: 0
(II) intel(0): Supported detailed timing:
(II) intel(0): clock: 71.1 MHz   Image Size:  331 x 207 mm
(II) intel(0): h_active: 1280  h_sync: 1328  h_sync_end 1360 h_blank_end 1440 h_border: 0
(II) intel(0): v_active: 800  v_sync: 803  v_sync_end 809 v_blanking: 823 v_border: 0
(WW) intel(0): Unknown vendor-specific block f
(II) intel(0):  AUO
(II) intel(0):  B154EW02 V5
(II) intel(0): EDID (in hex):
(II) intel(0):     00ffffffffffff0006af742500000000
(II) intel(0):     01100103802115780a1cf59758508e27
(II) intel(0):     27505400000001010101010101010101
(II) intel(0):     010101010101c71b00a0502017303020
(II) intel(0):     36004bcf100000180000000f00000000
(II) intel(0):     00000000000000000020000000fe0041
(II) intel(0):     554f0a202020202020202020000000fe
(II) intel(0):     004231353445573032205635200a00a1
(II) intel(0): EDID vendor "AUO", prod id 9588
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1280x800"x0.0   71.11  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.4 kHz)
(II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1280x960" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1280x960" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1280x1024" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1280x1024" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1280x1024" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1792x1344" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1792x1344" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1856x1392" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1856x1392" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1920x1440" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1920x1440" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1360x768" (monitor doesn't support reduced blanking)
(II) intel(0): Not using default mode "1360x768" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1400x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1400x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1400x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1400x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1440x900" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1600x1024" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1680x1050" (monitor doesn't support reduced blanking)
(II) intel(0): Not using default mode "1680x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1680x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1680x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1680x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1920x1080" (monitor doesn't support reduced blanking)
(II) intel(0): Not using default mode "1920x1200" (monitor doesn't support reduced blanking)
(II) intel(0): Not using default mode "1920x1440" (exceeds panel dimensions)
(II) intel(0): Not using default mode "2048x1536" (exceeds panel dimensions)
(II) intel(0): Not using default mode "2048x1536" (exceeds panel dimensions)
(II) intel(0): Not using default mode "2048x1536" (exceeds panel dimensions)
(II) intel(0): Printing probed modes for output LVDS1
(II) intel(0): Modeline "1280x800"x60.0   71.11  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.4 kHz)
(II) intel(0): Modeline "1024x768"x85.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
(II) intel(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) intel(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) intel(0): Modeline "800x600"x85.1   56.30  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
(II) intel(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) intel(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x85.0   36.00  640 696 752 832  480 481 484 509 -hsync -vsync (43.3 kHz)
(II) intel(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) intel(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x85.0   35.50  720 756 828 936  400 401 404 446 -hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "640x400"x85.1   31.50  640 672 736 832  400 401 404 445 -hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "640x350"x85.1   31.50  640 672 736 832  350 382 385 445 +hsync -vsync (37.9 kHz)
(II) intel(0): EDID for output TV1
(II) intel(0): EDID for output VGA1
(II) intel(0): EDID for output LVDS1
(II) intel(0): Manufacturer: AUO  Model: 2574  Serial#: 0
(II) intel(0): Year: 2006  Week: 1
(II) intel(0): EDID Version: 1.3
(II) intel(0): Digital Display Input
(II) intel(0): Max Image Size [cm]: horiz.: 33  vert.: 21
(II) intel(0): Gamma: 2.20
(II) intel(0): No DPMS capabilities specified
(II) intel(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) intel(0): First detailed timing is preferred mode
(II) intel(0): redX: 0.590 redY: 0.345   greenX: 0.315 greenY: 0.555
(II) intel(0): blueX: 0.155 blueY: 0.155   whiteX: 0.313 whiteY: 0.329
(II) intel(0): Manufacturer's mask: 0
(II) intel(0): Supported detailed timing:
(II) intel(0): clock: 71.1 MHz   Image Size:  331 x 207 mm
(II) intel(0): h_active: 1280  h_sync: 1328  h_sync_end 1360 h_blank_end 1440 h_border: 0
(II) intel(0): v_active: 800  v_sync: 803  v_sync_end 809 v_blanking: 823 v_border: 0
(WW) intel(0): Unknown vendor-specific block f
(II) intel(0):  AUO
(II) intel(0):  B154EW02 V5
(II) intel(0): EDID (in hex):
(II) intel(0):     00ffffffffffff0006af742500000000
(II) intel(0):     01100103802115780a1cf59758508e27
(II) intel(0):     27505400000001010101010101010101
(II) intel(0):     010101010101c71b00a0502017303020
(II) intel(0):     36004bcf100000180000000f00000000
(II) intel(0):     00000000000000000020000000fe0041
(II) intel(0):     554f0a202020202020202020000000fe
(II) intel(0):     004231353445573032205635200a00a1
(II) intel(0): EDID vendor "AUO", prod id 9588
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1280x800"x0.0   71.11  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.4 kHz)
(II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1280x960" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1280x960" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1280x1024" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1280x1024" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1280x1024" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1792x1344" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1792x1344" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1856x1392" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1856x1392" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1920x1440" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1920x1440" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1360x768" (monitor doesn't support reduced blanking)
(II) intel(0): Not using default mode "1360x768" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1400x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1400x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1400x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1400x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1440x900" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1600x1024" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1680x1050" (monitor doesn't support reduced blanking)
(II) intel(0): Not using default mode "1680x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1680x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1680x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1680x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1920x1080" (monitor doesn't support reduced blanking)
(II) intel(0): Not using default mode "1920x1200" (monitor doesn't support reduced blanking)
(II) intel(0): Not using default mode "1920x1440" (exceeds panel dimensions)
(II) intel(0): Not using default mode "2048x1536" (exceeds panel dimensions)
(II) intel(0): Not using default mode "2048x1536" (exceeds panel dimensions)
(II) intel(0): Not using default mode "2048x1536" (exceeds panel dimensions)
(II) intel(0): Printing probed modes for output LVDS1
(II) intel(0): Modeline "1280x800"x60.0   71.11  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.4 kHz)
(II) intel(0): Modeline "1024x768"x85.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
(II) intel(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) intel(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) intel(0): Modeline "800x600"x85.1   56.30  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
(II) intel(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) intel(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x85.0   36.00  640 696 752 832  480 481 484 509 -hsync -vsync (43.3 kHz)
(II) intel(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) intel(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x85.0   35.50  720 756 828 936  400 401 404 446 -hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "640x400"x85.1   31.50  640 672 736 832  400 401 404 445 -hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "640x350"x85.1   31.50  640 672 736 832  350 382 385 445 +hsync -vsync (37.9 kHz)
(II) intel(0): EDID for output TV1
(II) intel(0): EDID for output VGA1
(II) intel(0): EDID for output LVDS1
(II) intel(0): Manufacturer: AUO  Model: 2574  Serial#: 0
(II) intel(0): Year: 2006  Week: 1
(II) intel(0): EDID Version: 1.3
(II) intel(0): Digital Display Input
(II) intel(0): Max Image Size [cm]: horiz.: 33  vert.: 21
(II) intel(0): Gamma: 2.20
(II) intel(0): No DPMS capabilities specified
(II) intel(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) intel(0): First detailed timing is preferred mode
(II) intel(0): redX: 0.590 redY: 0.345   greenX: 0.315 greenY: 0.555
(II) intel(0): blueX: 0.155 blueY: 0.155   whiteX: 0.313 whiteY: 0.329
(II) intel(0): Manufacturer's mask: 0
(II) intel(0): Supported detailed timing:
(II) intel(0): clock: 71.1 MHz   Image Size:  331 x 207 mm
(II) intel(0): h_active: 1280  h_sync: 1328  h_sync_end 1360 h_blank_end 1440 h_border: 0
(II) intel(0): v_active: 800  v_sync: 803  v_sync_end 809 v_blanking: 823 v_border: 0
(WW) intel(0): Unknown vendor-specific block f
(II) intel(0):  AUO
(II) intel(0):  B154EW02 V5
(II) intel(0): EDID (in hex):
(II) intel(0):     00ffffffffffff0006af742500000000
(II) intel(0):     01100103802115780a1cf59758508e27
(II) intel(0):     27505400000001010101010101010101
(II) intel(0):     010101010101c71b00a0502017303020
(II) intel(0):     36004bcf100000180000000f00000000
(II) intel(0):     00000000000000000020000000fe0041
(II) intel(0):     554f0a202020202020202020000000fe
(II) intel(0):     004231353445573032205635200a00a1
(II) intel(0): EDID vendor "AUO", prod id 9588
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1280x800"x0.0   71.11  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.4 kHz)
(II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1280x960" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1280x960" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1280x1024" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1280x1024" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1280x1024" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1792x1344" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1792x1344" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1856x1392" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1856x1392" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1920x1440" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1920x1440" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1360x768" (monitor doesn't support reduced blanking)
(II) intel(0): Not using default mode "1360x768" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1400x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1400x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1400x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1400x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1440x900" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1600x1024" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1680x1050" (monitor doesn't support reduced blanking)
(II) intel(0): Not using default mode "1680x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1680x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1680x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1680x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1920x1080" (monitor doesn't support reduced blanking)
(II) intel(0): Not using default mode "1920x1200" (monitor doesn't support reduced blanking)
(II) intel(0): Not using default mode "1920x1440" (exceeds panel dimensions)
(II) intel(0): Not using default mode "2048x1536" (exceeds panel dimensions)
(II) intel(0): Not using default mode "2048x1536" (exceeds panel dimensions)
(II) intel(0): Not using default mode "2048x1536" (exceeds panel dimensions)
(II) intel(0): Printing probed modes for output LVDS1
(II) intel(0): Modeline "1280x800"x60.0   71.11  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.4 kHz)
(II) intel(0): Modeline "1024x768"x85.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
(II) intel(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) intel(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) intel(0): Modeline "800x600"x85.1   56.30  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
(II) intel(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) intel(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x85.0   36.00  640 696 752 832  480 481 484 509 -hsync -vsync (43.3 kHz)
(II) intel(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) intel(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x85.0   35.50  720 756 828 936  400 401 404 446 -hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "640x400"x85.1   31.50  640 672 736 832  400 401 404 445 -hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "640x350"x85.1   31.50  640 672 736 832  350 382 385 445 +hsync -vsync (37.9 kHz)
(II) intel(0): EDID for output TV1
(II) intel(0): EDID for output VGA1
(II) intel(0): EDID for output LVDS1
(II) intel(0): Manufacturer: AUO  Model: 2574  Serial#: 0
(II) intel(0): Year: 2006  Week: 1
(II) intel(0): EDID Version: 1.3
(II) intel(0): Digital Display Input
(II) intel(0): Max Image Size [cm]: horiz.: 33  vert.: 21
(II) intel(0): Gamma: 2.20
(II) intel(0): No DPMS capabilities specified
(II) intel(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) intel(0): First detailed timing is preferred mode
(II) intel(0): redX: 0.590 redY: 0.345   greenX: 0.315 greenY: 0.555
(II) intel(0): blueX: 0.155 blueY: 0.155   whiteX: 0.313 whiteY: 0.329
(II) intel(0): Manufacturer's mask: 0
(II) intel(0): Supported detailed timing:
(II) intel(0): clock: 71.1 MHz   Image Size:  331 x 207 mm
(II) intel(0): h_active: 1280  h_sync: 1328  h_sync_end 1360 h_blank_end 1440 h_border: 0
(II) intel(0): v_active: 800  v_sync: 803  v_sync_end 809 v_blanking: 823 v_border: 0
(WW) intel(0): Unknown vendor-specific block f
(II) intel(0):  AUO
(II) intel(0):  B154EW02 V5
(II) intel(0): EDID (in hex):
(II) intel(0):     00ffffffffffff0006af742500000000
(II) intel(0):     01100103802115780a1cf59758508e27
(II) intel(0):     27505400000001010101010101010101
(II) intel(0):     010101010101c71b00a0502017303020
(II) intel(0):     36004bcf100000180000000f00000000
(II) intel(0):     00000000000000000020000000fe0041
(II) intel(0):     554f0a202020202020202020000000fe
(II) intel(0):     004231353445573032205635200a00a1
(II) intel(0): EDID vendor "AUO", prod id 9588
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1280x800"x0.0   71.11  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.4 kHz)
(II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1280x960" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1280x960" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1280x1024" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1280x1024" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1280x1024" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1792x1344" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1792x1344" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1856x1392" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1856x1392" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1920x1440" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1920x1440" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1360x768" (monitor doesn't support reduced blanking)
(II) intel(0): Not using default mode "1360x768" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1400x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1400x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1400x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1400x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1440x900" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1600x1024" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1680x1050" (monitor doesn't support reduced blanking)
(II) intel(0): Not using default mode "1680x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1680x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1680x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1680x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1920x1080" (monitor doesn't support reduced blanking)
(II) intel(0): Not using default mode "1920x1200" (monitor doesn't support reduced blanking)
(II) intel(0): Not using default mode "1920x1440" (exceeds panel dimensions)
(II) intel(0): Not using default mode "2048x1536" (exceeds panel dimensions)
(II) intel(0): Not using default mode "2048x1536" (exceeds panel dimensions)
(II) intel(0): Not using default mode "2048x1536" (exceeds panel dimensions)
(II) intel(0): Printing probed modes for output LVDS1
(II) intel(0): Modeline "1280x800"x60.0   71.11  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.4 kHz)
(II) intel(0): Modeline "1024x768"x85.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
(II) intel(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) intel(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) intel(0): Modeline "800x600"x85.1   56.30  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
(II) intel(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) intel(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x85.0   36.00  640 696 752 832  480 481 484 509 -hsync -vsync (43.3 kHz)
(II) intel(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) intel(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x85.0   35.50  720 756 828 936  400 401 404 446 -hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "640x400"x85.1   31.50  640 672 736 832  400 401 404 445 -hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "640x350"x85.1   31.50  640 672 736 832  350 382 385 445 +hsync -vsync (37.9 kHz)
(II) intel(0): EDID for output TV1
(II) intel(0): EDID for output VGA1
(II) intel(0): EDID for output LVDS1
(II) intel(0): Manufacturer: AUO  Model: 2574  Serial#: 0
(II) intel(0): Year: 2006  Week: 1
(II) intel(0): EDID Version: 1.3
(II) intel(0): Digital Display Input
(II) intel(0): Max Image Size [cm]: horiz.: 33  vert.: 21
(II) intel(0): Gamma: 2.20
(II) intel(0): No DPMS capabilities specified
(II) intel(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) intel(0): First detailed timing is preferred mode
(II) intel(0): redX: 0.590 redY: 0.345   greenX: 0.315 greenY: 0.555
(II) intel(0): blueX: 0.155 blueY: 0.155   whiteX: 0.313 whiteY: 0.329
(II) intel(0): Manufacturer's mask: 0
(II) intel(0): Supported detailed timing:
(II) intel(0): clock: 71.1 MHz   Image Size:  331 x 207 mm
(II) intel(0): h_active: 1280  h_sync: 1328  h_sync_end 1360 h_blank_end 1440 h_border: 0
(II) intel(0): v_active: 800  v_sync: 803  v_sync_end 809 v_blanking: 823 v_border: 0
(WW) intel(0): Unknown vendor-specific block f
(II) intel(0):  AUO
(II) intel(0):  B154EW02 V5
(II) intel(0): EDID (in hex):
(II) intel(0):     00ffffffffffff0006af742500000000
(II) intel(0):     01100103802115780a1cf59758508e27
(II) intel(0):     27505400000001010101010101010101
(II) intel(0):     010101010101c71b00a0502017303020
(II) intel(0):     36004bcf100000180000000f00000000
(II) intel(0):     00000000000000000020000000fe0041
(II) intel(0):     554f0a202020202020202020000000fe
(II) intel(0):     004231353445573032205635200a00a1
(II) intel(0): EDID vendor "AUO", prod id 9588
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1280x800"x0.0   71.11  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.4 kHz)
(II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1280x960" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1280x960" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1280x1024" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1280x1024" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1280x1024" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1792x1344" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1792x1344" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1856x1392" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1856x1392" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1920x1440" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1920x1440" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1360x768" (monitor doesn't support reduced blanking)
(II) intel(0): Not using default mode "1360x768" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1400x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1400x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1400x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1400x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1440x900" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1600x1024" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1680x1050" (monitor doesn't support reduced blanking)
(II) intel(0): Not using default mode "1680x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1680x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1680x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1680x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1920x1080" (monitor doesn't support reduced blanking)
(II) intel(0): Not using default mode "1920x1200" (monitor doesn't support reduced blanking)
(II) intel(0): Not using default mode "1920x1440" (exceeds panel dimensions)
(II) intel(0): Not using default mode "2048x1536" (exceeds panel dimensions)
(II) intel(0): Not using default mode "2048x1536" (exceeds panel dimensions)
(II) intel(0): Not using default mode "2048x1536" (exceeds panel dimensions)
(II) intel(0): Printing probed modes for output LVDS1
(II) intel(0): Modeline "1280x800"x60.0   71.11  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.4 kHz)
(II) intel(0): Modeline "1024x768"x85.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
(II) intel(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) intel(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) intel(0): Modeline "800x600"x85.1   56.30  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
(II) intel(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) intel(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x85.0   36.00  640 696 752 832  480 481 484 509 -hsync -vsync (43.3 kHz)
(II) intel(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) intel(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x85.0   35.50  720 756 828 936  400 401 404 446 -hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "640x400"x85.1   31.50  640 672 736 832  400 401 404 445 -hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "640x350"x85.1   31.50  640 672 736 832  350 382 385 445 +hsync -vsync (37.9 kHz)
(II) intel(0): EDID for output TV1
(II) intel(0): EDID for output VGA1
(II) intel(0): EDID for output LVDS1
(II) intel(0): Manufacturer: AUO  Model: 2574  Serial#: 0
(II) intel(0): Year: 2006  Week: 1
(II) intel(0): EDID Version: 1.3
(II) intel(0): Digital Display Input
(II) intel(0): Max Image Size [cm]: horiz.: 33  vert.: 21
(II) intel(0): Gamma: 2.20
(II) intel(0): No DPMS capabilities specified
(II) intel(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) intel(0): First detailed timing is preferred mode
(II) intel(0): redX: 0.590 redY: 0.345   greenX: 0.315 greenY: 0.555
(II) intel(0): blueX: 0.155 blueY: 0.155   whiteX: 0.313 whiteY: 0.329
(II) intel(0): Manufacturer's mask: 0
(II) intel(0): Supported detailed timing:
(II) intel(0): clock: 71.1 MHz   Image Size:  331 x 207 mm
(II) intel(0): h_active: 1280  h_sync: 1328  h_sync_end 1360 h_blank_end 1440 h_border: 0
(II) intel(0): v_active: 800  v_sync: 803  v_sync_end 809 v_blanking: 823 v_border: 0
(WW) intel(0): Unknown vendor-specific block f
(II) intel(0):  AUO
(II) intel(0):  B154EW02 V5
(II) intel(0): EDID (in hex):
(II) intel(0):     00ffffffffffff0006af742500000000
(II) intel(0):     01100103802115780a1cf59758508e27
(II) intel(0):     27505400000001010101010101010101
(II) intel(0):     010101010101c71b00a0502017303020
(II) intel(0):     36004bcf100000180000000f00000000
(II) intel(0):     00000000000000000020000000fe0041
(II) intel(0):     554f0a202020202020202020000000fe
(II) intel(0):     004231353445573032205635200a00a1
(II) intel(0): EDID vendor "AUO", prod id 9588
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1280x800"x0.0   71.11  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.4 kHz)
(II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1280x960" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1280x960" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1280x1024" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1280x1024" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1280x1024" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1792x1344" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1792x1344" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1856x1392" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1856x1392" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1920x1440" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1920x1440" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1360x768" (monitor doesn't support reduced blanking)
(II) intel(0): Not using default mode "1360x768" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1400x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1400x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1400x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1400x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1440x900" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1600x1024" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1680x1050" (monitor doesn't support reduced blanking)
(II) intel(0): Not using default mode "1680x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1680x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1680x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1680x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1920x1080" (monitor doesn't support reduced blanking)
(II) intel(0): Not using default mode "1920x1200" (monitor doesn't support reduced blanking)
(II) intel(0): Not using default mode "1920x1440" (exceeds panel dimensions)
(II) intel(0): Not using default mode "2048x1536" (exceeds panel dimensions)
(II) intel(0): Not using default mode "2048x1536" (exceeds panel dimensions)
(II) intel(0): Not using default mode "2048x1536" (exceeds panel dimensions)
(II) intel(0): Printing probed modes for output LVDS1
(II) intel(0): Modeline "1280x800"x60.0   71.11  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.4 kHz)
(II) intel(0): Modeline "1024x768"x85.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
(II) intel(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) intel(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) intel(0): Modeline "800x600"x85.1   56.30  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
(II) intel(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) intel(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x85.0   36.00  640 696 752 832  480 481 484 509 -hsync -vsync (43.3 kHz)
(II) intel(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) intel(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x85.0   35.50  720 756 828 936  400 401 404 446 -hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "640x400"x85.1   31.50  640 672 736 832  400 401 404 445 -hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "640x350"x85.1   31.50  640 672 736 832  350 382 385 445 +hsync -vsync (37.9 kHz)
(II) intel(0): EDID for output TV1
(II) intel(0): EDID for output VGA1
(II) intel(0): EDID for output LVDS1
(II) intel(0): Manufacturer: AUO  Model: 2574  Serial#: 0
(II) intel(0): Year: 2006  Week: 1
(II) intel(0): EDID Version: 1.3
(II) intel(0): Digital Display Input
(II) intel(0): Max Image Size [cm]: horiz.: 33  vert.: 21
(II) intel(0): Gamma: 2.20
(II) intel(0): No DPMS capabilities specified
(II) intel(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) intel(0): First detailed timing is preferred mode
(II) intel(0): redX: 0.590 redY: 0.345   greenX: 0.315 greenY: 0.555
(II) intel(0): blueX: 0.155 blueY: 0.155   whiteX: 0.313 whiteY: 0.329
(II) intel(0): Manufacturer's mask: 0
(II) intel(0): Supported detailed timing:
(II) intel(0): clock: 71.1 MHz   Image Size:  331 x 207 mm
(II) intel(0): h_active: 1280  h_sync: 1328  h_sync_end 1360 h_blank_end 1440 h_border: 0
(II) intel(0): v_active: 800  v_sync: 803  v_sync_end 809 v_blanking: 823 v_border: 0
(WW) intel(0): Unknown vendor-specific block f
(II) intel(0):  AUO
(II) intel(0):  B154EW02 V5
(II) intel(0): EDID (in hex):
(II) intel(0):     00ffffffffffff0006af742500000000
(II) intel(0):     01100103802115780a1cf59758508e27
(II) intel(0):     27505400000001010101010101010101
(II) intel(0):     010101010101c71b00a0502017303020
(II) intel(0):     36004bcf100000180000000f00000000
(II) intel(0):     00000000000000000020000000fe0041
(II) intel(0):     554f0a202020202020202020000000fe
(II) intel(0):     004231353445573032205635200a00a1
(II) intel(0): EDID vendor "AUO", prod id 9588
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1280x800"x0.0   71.11  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.4 kHz)
(II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1280x960" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1280x960" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1280x1024" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1280x1024" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1280x1024" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1792x1344" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1792x1344" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1856x1392" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1856x1392" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1920x1440" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1920x1440" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1360x768" (monitor doesn't support reduced blanking)
(II) intel(0): Not using default mode "1360x768" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1400x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1400x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1400x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1400x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1440x900" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1600x1024" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1680x1050" (monitor doesn't support reduced blanking)
(II) intel(0): Not using default mode "1680x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1680x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1680x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1680x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1920x1080" (monitor doesn't support reduced blanking)
(II) intel(0): Not using default mode "1920x1200" (monitor doesn't support reduced blanking)
(II) intel(0): Not using default mode "1920x1440" (exceeds panel dimensions)
(II) intel(0): Not using default mode "2048x1536" (exceeds panel dimensions)
(II) intel(0): Not using default mode "2048x1536" (exceeds panel dimensions)
(II) intel(0): Not using default mode "2048x1536" (exceeds panel dimensions)
(II) intel(0): Printing probed modes for output LVDS1
(II) intel(0): Modeline "1280x800"x60.0   71.11  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.4 kHz)
(II) intel(0): Modeline "1024x768"x85.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
(II) intel(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) intel(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) intel(0): Modeline "800x600"x85.1   56.30  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
(II) intel(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) intel(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x85.0   36.00  640 696 752 832  480 481 484 509 -hsync -vsync (43.3 kHz)
(II) intel(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) intel(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x85.0   35.50  720 756 828 936  400 401 404 446 -hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "640x400"x85.1   31.50  640 672 736 832  400 401 404 445 -hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "640x350"x85.1   31.50  640 672 736 832  350 382 385 445 +hsync -vsync (37.9 kHz)
(II) intel(0): EDID for output TV1
(II) intel(0): EDID for output VGA1
(II) intel(0): EDID for output LVDS1
(II) intel(0): Manufacturer: AUO  Model: 2574  Serial#: 0
(II) intel(0): Year: 2006  Week: 1
(II) intel(0): EDID Version: 1.3
(II) intel(0): Digital Display Input
(II) intel(0): Max Image Size [cm]: horiz.: 33  vert.: 21
(II) intel(0): Gamma: 2.20
(II) intel(0): No DPMS capabilities specified
(II) intel(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) intel(0): First detailed timing is preferred mode
(II) intel(0): redX: 0.590 redY: 0.345   greenX: 0.315 greenY: 0.555
(II) intel(0): blueX: 0.155 blueY: 0.155   whiteX: 0.313 whiteY: 0.329
(II) intel(0): Manufacturer's mask: 0
(II) intel(0): Supported detailed timing:
(II) intel(0): clock: 71.1 MHz   Image Size:  331 x 207 mm
(II) intel(0): h_active: 1280  h_sync: 1328  h_sync_end 1360 h_blank_end 1440 h_border: 0
(II) intel(0): v_active: 800  v_sync: 803  v_sync_end 809 v_blanking: 823 v_border: 0
(WW) intel(0): Unknown vendor-specific block f
(II) intel(0):  AUO
(II) intel(0):  B154EW02 V5
(II) intel(0): EDID (in hex):
(II) intel(0):     00ffffffffffff0006af742500000000
(II) intel(0):     01100103802115780a1cf59758508e27
(II) intel(0):     27505400000001010101010101010101
(II) intel(0):     010101010101c71b00a0502017303020
(II) intel(0):     36004bcf100000180000000f00000000
(II) intel(0):     00000000000000000020000000fe0041
(II) intel(0):     554f0a202020202020202020000000fe
(II) intel(0):     004231353445573032205635200a00a1
(II) intel(0): EDID vendor "AUO", prod id 9588
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1280x800"x0.0   71.11  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.4 kHz)
(II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1280x960" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1280x960" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1280x1024" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1280x1024" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1280x1024" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1792x1344" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1792x1344" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1856x1392" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1856x1392" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1920x1440" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1920x1440" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1360x768" (monitor doesn't support reduced blanking)
(II) intel(0): Not using default mode "1360x768" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1400x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1400x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1400x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1400x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1440x900" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1600x1024" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1680x1050" (monitor doesn't support reduced blanking)
(II) intel(0): Not using default mode "1680x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1680x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1680x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1680x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1920x1080" (monitor doesn't support reduced blanking)
(II) intel(0): Not using default mode "1920x1200" (monitor doesn't support reduced blanking)
(II) intel(0): Not using default mode "1920x1440" (exceeds panel dimensions)
(II) intel(0): Not using default mode "2048x1536" (exceeds panel dimensions)
(II) intel(0): Not using default mode "2048x1536" (exceeds panel dimensions)
(II) intel(0): Not using default mode "2048x1536" (exceeds panel dimensions)
(II) intel(0): Printing probed modes for output LVDS1
(II) intel(0): Modeline "1280x800"x60.0   71.11  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.4 kHz)
(II) intel(0): Modeline "1024x768"x85.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
(II) intel(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) intel(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) intel(0): Modeline "800x600"x85.1   56.30  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
(II) intel(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) intel(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x85.0   36.00  640 696 752 832  480 481 484 509 -hsync -vsync (43.3 kHz)
(II) intel(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) intel(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x85.0   35.50  720 756 828 936  400 401 404 446 -hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "640x400"x85.1   31.50  640 672 736 832  400 401 404 445 -hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "640x350"x85.1   31.50  640 672 736 832  350 382 385 445 +hsync -vsync (37.9 kHz)
(II) intel(0): EDID for output TV1
(II) intel(0): EDID for output VGA1
(II) intel(0): EDID for output LVDS1
(II) intel(0): Manufacturer: AUO  Model: 2574  Serial#: 0
(II) intel(0): Year: 2006  Week: 1
(II) intel(0): EDID Version: 1.3
(II) intel(0): Digital Display Input
(II) intel(0): Max Image Size [cm]: horiz.: 33  vert.: 21
(II) intel(0): Gamma: 2.20
(II) intel(0): No DPMS capabilities specified
(II) intel(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) intel(0): First detailed timing is preferred mode
(II) intel(0): redX: 0.590 redY: 0.345   greenX: 0.315 greenY: 0.555
(II) intel(0): blueX: 0.155 blueY: 0.155   whiteX: 0.313 whiteY: 0.329
(II) intel(0): Manufacturer's mask: 0
(II) intel(0): Supported detailed timing:
(II) intel(0): clock: 71.1 MHz   Image Size:  331 x 207 mm
(II) intel(0): h_active: 1280  h_sync: 1328  h_sync_end 1360 h_blank_end 1440 h_border: 0
(II) intel(0): v_active: 800  v_sync: 803  v_sync_end 809 v_blanking: 823 v_border: 0
(WW) intel(0): Unknown vendor-specific block f
(II) intel(0):  AUO
(II) intel(0):  B154EW02 V5
(II) intel(0): EDID (in hex):
(II) intel(0):     00ffffffffffff0006af742500000000
(II) intel(0):     01100103802115780a1cf59758508e27
(II) intel(0):     27505400000001010101010101010101
(II) intel(0):     010101010101c71b00a0502017303020
(II) intel(0):     36004bcf100000180000000f00000000
(II) intel(0):     00000000000000000020000000fe0041
(II) intel(0):     554f0a202020202020202020000000fe
(II) intel(0):     004231353445573032205635200a00a1
(II) intel(0): EDID vendor "AUO", prod id 9588
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1280x800"x0.0   71.11  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.4 kHz)
(II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1280x960" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1280x960" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1280x1024" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1280x1024" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1280x1024" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1792x1344" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1792x1344" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1856x1392" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1856x1392" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1920x1440" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1920x1440" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1360x768" (monitor doesn't support reduced blanking)
(II) intel(0): Not using default mode "1360x768" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1400x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1400x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1400x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1400x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1440x900" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1600x1024" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1680x1050" (monitor doesn't support reduced blanking)
(II) intel(0): Not using default mode "1680x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1680x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1680x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1680x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1920x1080" (monitor doesn't support reduced blanking)
(II) intel(0): Not using default mode "1920x1200" (monitor doesn't support reduced blanking)
(II) intel(0): Not using default mode "1920x1440" (exceeds panel dimensions)
(II) intel(0): Not using default mode "2048x1536" (exceeds panel dimensions)
(II) intel(0): Not using default mode "2048x1536" (exceeds panel dimensions)
(II) intel(0): Not using default mode "2048x1536" (exceeds panel dimensions)
(II) intel(0): Printing probed modes for output LVDS1
(II) intel(0): Modeline "1280x800"x60.0   71.11  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.4 kHz)
(II) intel(0): Modeline "1024x768"x85.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
(II) intel(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) intel(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) intel(0): Modeline "800x600"x85.1   56.30  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
(II) intel(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) intel(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x85.0   36.00  640 696 752 832  480 481 484 509 -hsync -vsync (43.3 kHz)
(II) intel(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) intel(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x85.0   35.50  720 756 828 936  400 401 404 446 -hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "640x400"x85.1   31.50  640 672 736 832  400 401 404 445 -hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "640x350"x85.1   31.50  640 672 736 832  350 382 385 445 +hsync -vsync (37.9 kHz)
(II) intel(0): EDID for output TV1
(II) intel(0): EDID for output VGA1
(II) intel(0): EDID for output LVDS1
(II) intel(0): Manufacturer: AUO  Model: 2574  Serial#: 0
(II) intel(0): Year: 2006  Week: 1
(II) intel(0): EDID Version: 1.3
(II) intel(0): Digital Display Input
(II) intel(0): Max Image Size [cm]: horiz.: 33  vert.: 21
(II) intel(0): Gamma: 2.20
(II) intel(0): No DPMS capabilities specified
(II) intel(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) intel(0): First detailed timing is preferred mode
(II) intel(0): redX: 0.590 redY: 0.345   greenX: 0.315 greenY: 0.555
(II) intel(0): blueX: 0.155 blueY: 0.155   whiteX: 0.313 whiteY: 0.329
(II) intel(0): Manufacturer's mask: 0
(II) intel(0): Supported detailed timing:
(II) intel(0): clock: 71.1 MHz   Image Size:  331 x 207 mm
(II) intel(0): h_active: 1280  h_sync: 1328  h_sync_end 1360 h_blank_end 1440 h_border: 0
(II) intel(0): v_active: 800  v_sync: 803  v_sync_end 809 v_blanking: 823 v_border: 0
(WW) intel(0): Unknown vendor-specific block f
(II) intel(0):  AUO
(II) intel(0):  B154EW02 V5
(II) intel(0): EDID (in hex):
(II) intel(0):     00ffffffffffff0006af742500000000
(II) intel(0):     01100103802115780a1cf59758508e27
(II) intel(0):     27505400000001010101010101010101
(II) intel(0):     010101010101c71b00a0502017303020
(II) intel(0):     36004bcf100000180000000f00000000
(II) intel(0):     00000000000000000020000000fe0041
(II) intel(0):     554f0a202020202020202020000000fe
(II) intel(0):     004231353445573032205635200a00a1
(II) intel(0): EDID vendor "AUO", prod id 9588
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1280x800"x0.0   71.11  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.4 kHz)
(II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1280x960" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1280x960" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1280x1024" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1280x1024" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1280x1024" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1792x1344" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1792x1344" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1856x1392" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1856x1392" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1920x1440" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1920x1440" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1360x768" (monitor doesn't support reduced blanking)
(II) intel(0): Not using default mode "1360x768" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1400x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1400x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1400x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1400x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1440x900" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1600x1024" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1680x1050" (monitor doesn't support reduced blanking)
(II) intel(0): Not using default mode "1680x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1680x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1680x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1680x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1920x1080" (monitor doesn't support reduced blanking)
(II) intel(0): Not using default mode "1920x1200" (monitor doesn't support reduced blanking)
(II) intel(0): Not using default mode "1920x1440" (exceeds panel dimensions)
(II) intel(0): Not using default mode "2048x1536" (exceeds panel dimensions)
(II) intel(0): Not using default mode "2048x1536" (exceeds panel dimensions)
(II) intel(0): Not using default mode "2048x1536" (exceeds panel dimensions)
(II) intel(0): Printing probed modes for output LVDS1
(II) intel(0): Modeline "1280x800"x60.0   71.11  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.4 kHz)
(II) intel(0): Modeline "1024x768"x85.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
(II) intel(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) intel(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) intel(0): Modeline "800x600"x85.1   56.30  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
(II) intel(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) intel(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x85.0   36.00  640 696 752 832  480 481 484 509 -hsync -vsync (43.3 kHz)
(II) intel(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) intel(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x85.0   35.50  720 756 828 936  400 401 404 446 -hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "640x400"x85.1   31.50  640 672 736 832  400 401 404 445 -hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "640x350"x85.1   31.50  640 672 736 832  350 382 385 445 +hsync -vsync (37.9 kHz)
(II) intel(0): EDID for output TV1
(II) intel(0): EDID for output VGA1
(II) intel(0): EDID for output LVDS1
(II) intel(0): Manufacturer: AUO  Model: 2574  Serial#: 0
(II) intel(0): Year: 2006  Week: 1
(II) intel(0): EDID Version: 1.3
(II) intel(0): Digital Display Input
(II) intel(0): Max Image Size [cm]: horiz.: 33  vert.: 21
(II) intel(0): Gamma: 2.20
(II) intel(0): No DPMS capabilities specified
(II) intel(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) intel(0): First detailed timing is preferred mode
(II) intel(0): redX: 0.590 redY: 0.345   greenX: 0.315 greenY: 0.555
(II) intel(0): blueX: 0.155 blueY: 0.155   whiteX: 0.313 whiteY: 0.329
(II) intel(0): Manufacturer's mask: 0
(II) intel(0): Supported detailed timing:
(II) intel(0): clock: 71.1 MHz   Image Size:  331 x 207 mm
(II) intel(0): h_active: 1280  h_sync: 1328  h_sync_end 1360 h_blank_end 1440 h_border: 0
(II) intel(0): v_active: 800  v_sync: 803  v_sync_end 809 v_blanking: 823 v_border: 0
(WW) intel(0): Unknown vendor-specific block f
(II) intel(0):  AUO
(II) intel(0):  B154EW02 V5
(II) intel(0): EDID (in hex):
(II) intel(0):     00ffffffffffff0006af742500000000
(II) intel(0):     01100103802115780a1cf59758508e27
(II) intel(0):     27505400000001010101010101010101
(II) intel(0):     010101010101c71b00a0502017303020
(II) intel(0):     36004bcf100000180000000f00000000
(II) intel(0):     00000000000000000020000000fe0041
(II) intel(0):     554f0a202020202020202020000000fe
(II) intel(0):     004231353445573032205635200a00a1
(II) intel(0): EDID vendor "AUO", prod id 9588
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1280x800"x0.0   71.11  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.4 kHz)
(II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1280x960" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1280x960" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1280x1024" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1280x1024" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1280x1024" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1792x1344" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1792x1344" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1856x1392" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1856x1392" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1920x1440" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1920x1440" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1360x768" (monitor doesn't support reduced blanking)
(II) intel(0): Not using default mode "1360x768" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1400x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1400x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1400x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1400x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1440x900" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1600x1024" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1680x1050" (monitor doesn't support reduced blanking)
(II) intel(0): Not using default mode "1680x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1680x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1680x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1680x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1920x1080" (monitor doesn't support reduced blanking)
(II) intel(0): Not using default mode "1920x1200" (monitor doesn't support reduced blanking)
(II) intel(0): Not using default mode "1920x1440" (exceeds panel dimensions)
(II) intel(0): Not using default mode "2048x1536" (exceeds panel dimensions)
(II) intel(0): Not using default mode "2048x1536" (exceeds panel dimensions)
(II) intel(0): Not using default mode "2048x1536" (exceeds panel dimensions)
(II) intel(0): Printing probed modes for output LVDS1
(II) intel(0): Modeline "1280x800"x60.0   71.11  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.4 kHz)
(II) intel(0): Modeline "1024x768"x85.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
(II) intel(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) intel(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) intel(0): Modeline "800x600"x85.1   56.30  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
(II) intel(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) intel(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x85.0   36.00  640 696 752 832  480 481 484 509 -hsync -vsync (43.3 kHz)
(II) intel(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) intel(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x85.0   35.50  720 756 828 936  400 401 404 446 -hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "640x400"x85.1   31.50  640 672 736 832  400 401 404 445 -hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "640x350"x85.1   31.50  640 672 736 832  350 382 385 445 +hsync -vsync (37.9 kHz)
(II) intel(0): EDID for output TV1
(II) intel(0): EDID for output VGA1
(II) intel(0): EDID for output LVDS1
(II) intel(0): Manufacturer: AUO  Model: 2574  Serial#: 0
(II) intel(0): Year: 2006  Week: 1
(II) intel(0): EDID Version: 1.3
(II) intel(0): Digital Display Input
(II) intel(0): Max Image Size [cm]: horiz.: 33  vert.: 21
(II) intel(0): Gamma: 2.20
(II) intel(0): No DPMS capabilities specified
(II) intel(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) intel(0): First detailed timing is preferred mode
(II) intel(0): redX: 0.590 redY: 0.345   greenX: 0.315 greenY: 0.555
(II) intel(0): blueX: 0.155 blueY: 0.155   whiteX: 0.313 whiteY: 0.329
(II) intel(0): Manufacturer's mask: 0
(II) intel(0): Supported detailed timing:
(II) intel(0): clock: 71.1 MHz   Image Size:  331 x 207 mm
(II) intel(0): h_active: 1280  h_sync: 1328  h_sync_end 1360 h_blank_end 1440 h_border: 0
(II) intel(0): v_active: 800  v_sync: 803  v_sync_end 809 v_blanking: 823 v_border: 0
(WW) intel(0): Unknown vendor-specific block f
(II) intel(0):  AUO
(II) intel(0):  B154EW02 V5
(II) intel(0): EDID (in hex):
(II) intel(0):     00ffffffffffff0006af742500000000
(II) intel(0):     01100103802115780a1cf59758508e27
(II) intel(0):     27505400000001010101010101010101
(II) intel(0):     010101010101c71b00a0502017303020
(II) intel(0):     36004bcf100000180000000f00000000
(II) intel(0):     00000000000000000020000000fe0041
(II) intel(0):     554f0a202020202020202020000000fe
(II) intel(0):     004231353445573032205635200a00a1
(II) intel(0): EDID vendor "AUO", prod id 9588
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1280x800"x0.0   71.11  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.4 kHz)
(II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1280x960" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1280x960" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1280x1024" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1280x1024" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1280x1024" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1792x1344" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1792x1344" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1856x1392" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1856x1392" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1920x1440" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1920x1440" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1360x768" (monitor doesn't support reduced blanking)
(II) intel(0): Not using default mode "1360x768" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1400x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1400x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1400x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1400x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1440x900" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1600x1024" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1680x1050" (monitor doesn't support reduced blanking)
(II) intel(0): Not using default mode "1680x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1680x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1680x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1680x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1920x1080" (monitor doesn't support reduced blanking)
(II) intel(0): Not using default mode "1920x1200" (monitor doesn't support reduced blanking)
(II) intel(0): Not using default mode "1920x1440" (exceeds panel dimensions)
(II) intel(0): Not using default mode "2048x1536" (exceeds panel dimensions)
(II) intel(0): Not using default mode "2048x1536" (exceeds panel dimensions)
(II) intel(0): Not using default mode "2048x1536" (exceeds panel dimensions)
(II) intel(0): Printing probed modes for output LVDS1
(II) intel(0): Modeline "1280x800"x60.0   71.11  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.4 kHz)
(II) intel(0): Modeline "1024x768"x85.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
(II) intel(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) intel(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) intel(0): Modeline "800x600"x85.1   56.30  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
(II) intel(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) intel(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x85.0   36.00  640 696 752 832  480 481 484 509 -hsync -vsync (43.3 kHz)
(II) intel(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) intel(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x85.0   35.50  720 756 828 936  400 401 404 446 -hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "640x400"x85.1   31.50  640 672 736 832  400 401 404 445 -hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "640x350"x85.1   31.50  640 672 736 832  350 382 385 445 +hsync -vsync (37.9 kHz)
(II) intel(0): EDID for output TV1
[/php]

---

### Post by Soul-Sing on 2010-01-07
if you run ```
modprobe i810
``` whats the outcome/result?

(II) LoadModule: "i810"
(WW) Warning, couldn't open module i810
(II) UnloadModule: "i810"
(EE) Failed to load module "i810" (module does not exist, 0)

is the key-error in your log

---

### Post by abhe on 2010-01-07
mohsen@mohsen-laptop:~$ modprobe i810
FATAL: Error inserting i810 (/lib/modules/2.6.31-17-generic/kernel/drivers/gpu/drm/i810/i810.ko): Operation not permitted

---

### Post by Soul-Sing on 2010-01-07
did this error came after a kernel update?
are the i810 drivers installed? take a look at synaptic package manager.

---

### Post by Methuselah on 2010-01-07
Abhe, what happens if you hit CRTL+ALT+F2?
Hopefully a black screen will come up ith a login prompt.
If that happens I can tell you how to reboot through there.

---

### Post by abhe on 2010-01-07
> **Methuselah said:**
> Abhe, what happens if you hit CRTL+ALT+F2?
Hopefully a black screen will come up ith a login prompt.
If that happens I can tell you how to reboot through there.

yes its a black screen but, when my computer crash it doesn't response even if i hit ctrl+alt+f2

---

### Post by Methuselah on 2010-01-07
> **abhe said:**
> yes its a black screen but, when my computer crash it doesn't response even if i hit ctrl+alt+f2

Try holding ALT+Printscreen and while holding them type REISUB in sequence.
It should reboot your machine without having to pull the power (which is bad).

---

### Post by abhe on 2010-01-07
> **Methuselah said:**
> Try holding ALT+Printscreen and while holding them type REISUB in sequence.
It should reboot your machine without having to pull the power (which is bad).

thank you thats was verry helpful but
the problem still there:o

---

### Post by abhe on 2010-01-07
up up plz

---

### Post by Soul-Sing on 2010-01-07
sorry, i did ask if this all happend after a kernel update, sometimes a kernelupdate "errors" or isn't complete: causes X troubles.

---

### Post by abhe on 2010-01-07
what is kernel ?
my sys is up-to-date

---

### Post by abhe on 2010-01-07
this happend since i install the os

---

### Post by Soul-Sing on 2010-01-07
> **abhe said:**
> this happend since i install the os

ok, i have no idea, hope someone else can help you with this.

---

### Post by abhe on 2010-01-07
> **leoquant said:**
> ok, i have no idea, hope someone else can help you with this.

no problem, thank u for being helpful

---

### Post by abhe on 2010-01-09
the same as ***_[here ]("http://www.google.com/search?q=ubuntu+game+crash+quit&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:official&client=firefox-a")_***
neeeed helpppp! ... SOS ..

graphic card : intel croporation Mobile GM965/GL960 graphics controller (rev 0c)

---

### Post by abhe on 2010-01-09
up UP up UP up UP:popcorn:

---

### Post by abhe on 2010-01-10
so , no 1 gona answer me ?

---

### Post by ceguel on 2010-01-18
Same problem closing AssaultCube. I have an Intel 855GM video card, I use kernel 2.6.31-14, Xorg 7.4, Gnome 2.28.1.

I have solved the Xorg intel driver problem following this: [http://osdir.com/ml/debian-bugs-dist/2009-05/msg04136.html](http://osdir.com/ml/debian-bugs-dist/2009-05/msg04136.html),  i810 driver is now incorporated in the intel driver but Xorg try to load i810 explicitly. Basicly edit/create /etc/X11/xorg.conf adding this:
```
Section "Device"
   Identifier "i855GME"
   Driver "intel"
EndSection
```But that not solves the problem at all, it still freezes when closing. Note: Restart the window server works.

---

### Post by abhe on 2010-01-21
> **ceguel said:**
> Same problem closing AssaultCube. I have an Intel 855GM video card, I use kernel 2.6.31-14, Xorg 7.4, Gnome 2.28.1.

I have solved the Xorg intel driver problem following this: [http://osdir.com/ml/debian-bugs-dist/2009-05/msg04136.html](http://osdir.com/ml/debian-bugs-dist/2009-05/msg04136.html),  i810 driver is now incorporated in the intel driver but Xorg try to load i810 explicitly. Basicly edit/create /etc/X11/xorg.conf adding this:
```
Section "Device"
   Identifier "i855GME"
   Driver "intel"
EndSection
```But that not solves the problem at all, it still freezes when closing. Note: Restart the window server works.


can you expline easely what should i do , im still newbe
now i've created the corg.conf then i added the code what next ?

---

### Post by abhe on 2010-01-21
> **abhe said:**
> the same as ***_[here ]("http://www.google.com/search?q=ubuntu+game+crash+quit&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:official&client=firefox-a")_***
neeeed helpppp! ... SOS ..

graphic card : intel croporation Mobile GM965/GL960 graphics controller (rev 0c)
   

these are my ..........

---

