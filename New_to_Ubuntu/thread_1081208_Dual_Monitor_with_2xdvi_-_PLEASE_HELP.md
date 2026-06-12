---
title: "Dual Monitor with 2xdvi - PLEASE HELP"
date: 2009-02-26
forum: New to Ubuntu
---

### Post by EDmonitor on 2009-02-26
Hi guys 

For the last few days I have been fighting to get my dual monitor to work on my Linux Mint 6 (Ubuntu 8.10). 

Now, after millions of attempts with different solutions, I surrender. I just can't do it anymore. Therefore I go to you for help. 

**Info about my machine:**

[LIST]
[*]OS Linux Mint 6  (Ubuntu 8.10)
[*]Asus-M3A78-T /motherboard
[*]AMD Athlon 65 x2 5600+ S.AM2 /CPU
[*]2x DDR2 2GB 1066Mhz HyperX R. /RAM
[*]Nvidia GeF 9800 GT DRR3 512GB PCI-E 2xDVI input only /Vcard
[*]1x Samsung SyncMaster 223BW 5ms /Monitor 1
[*]1x Samsung SyncMaster 226BW 2ms /Monitor 2
[/LIST]

**Nvidia driver info:**

**I installed Nvidia Graphics Driver 177 through Hardware Drivers.**

**Need help to:**

[LIST]
[*]To get the Dual Monitor functioning!
[/LIST]

**Troulbeshooting:**

[LIST]
[*]When I power up my computer only one of the screens show the Motherboard screen! is that normal?
[*]When I press Detect Displays in Nvidia X Server Settings - nothing happens!
[*]I can not choose TwinView in Nvidia X Server Settings / X Server Display Configuration / Configure...! - It states "TwinView (Require X Restart"
[*]I tested my monitors, and both of them work fine. 
[/LIST]

**My skill level:**

[LIST]
[*]PC skill level is very high.

[*]Ubuntu skill level is low - my first Ubuntu installation was for a week ago
[/LIST]

**My xorg.conf info:**

```
Section "ServerLayout"
Identifier "X.org Configured"
Screen 0 "Screen0" 0 0
Screen 1 "Screen1" 0 0
EndSection

Section "Module"
Load "dbe"
# Load "dri"
Load "extmod"
Load "glx"
Load "record"
Load "xtrap"
Load "freetype"
Load "type1"
EndSection

Section "ServerFlags"
Option "BlankTime" "20"
Option "Xinerama" "0"
EndSection


Section "Monitor"
Identifier "Configured Monitor"
EndSection

Section "Monitor"
Identifier "Monitor0"
VendorName "Unknown"
ModelName "Samsung SyncMaster"
HorizSync 30.0 - 81.0
VertRefresh 56.0 - 75.0
EndSection

Section "Monitor"
Identifier "Monitor1"

VendorName "Unknown"
ModelName "Samsung SyncMaster"
HorizSync 30.0 - 81.0
VertRefresh 56.0 - 75.0
EndSection


Section "Device"
Identifier "Configured Video Device"
Driver "nvidia"
VendorName "NVIDIA Corporation"
BoardName "GeForce 9800 GT"
Option "Coolbits" "1"
BusID "PCI:1:0:0"
EndSection

Section "Device"
Identifier "Videocard0"
Driver "nvidia"
VendorName "NVIDIA Corporation"
BoardName "GeForce 9800 GT"
BusID "PCI:1:0:0"
Screen 0
EndSection

Section "Device"
Identifier "Videocard1"
Driver "nvidia"
VendorName "NVIDIA Corporation"
BoardName "GeForce 9800 GT"
BusID "PCI:1:0:0"
Screen 1
EndSection

Section "Screen"
Identifier "Screen0"
Device "Device0"
Monitor "Monitor0"
DefaultDepth 24
Option "TwinView" "0"
Option "metamodes" "DFP: 1680x1050 +0+0"
SubSection "Display"
Depth 24
EndSubSection
EndSection

Section "Screen"
Identifier "Screen1"
Device "Videocard1"
Monitor "Monitor1"
DefaultDepth 24
Option "TwinView" "0"
Option "metamodes" "DFP: 1680x1050 +0+0"
EndSection
```


**My /var/log/Xorg.0.log:**

```
X.Org X Server 1.5.2
Release Date: 10 October 2008
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-19-server i686 Ubuntu
Current Operating System: Linux edHome 2.6.27-7-generic #1 SMP Fri Oct 24 06:42:44 UTC 2008 i686
Build Date: 24 October 2008  08:00:16AM
xorg-server 2:1.5.2-2ubuntu3 (buildd@rothera.buildd)
    Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Wed Feb 25 21:46:16 2009
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "X.org Configured"
(**) |-->Screen "Screen0" (0)
(**) |   |-->Monitor "Monitor0"
(==) No device specified for screen "Screen0".
    Using the first device section listed.
(**) |   |-->Device "Configured Video Device"
(**) |-->Screen "Screen1" (1)
(**) |   |-->Monitor "Monitor1"
(**) |   |-->Device "Videocard1"
(**) Option "BlankTime" "20"
(**) Option "Xinerama" "0"
(==) Automatically adding devices
(==) Automatically enabling devices
(==) No FontPath specified.  Using compiled-in default.
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
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Cannot locate a core pointer device.
(II) Cannot locate a core keyboard device.
(II) The server relies on HAL to provide the list of input devices.
    If no devices become available, reconfigure HAL or disable AllowEmptyInput.
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x81d9a40
(II) Module ABI versions:
    X.Org ANSI C Emulation: 0.4
    X.Org Video Driver: 4.1
    X.Org XInput driver : 2.1
    X.Org Server Extension : 1.1
    X.Org Font Renderer : 0.6
(II) Loader running on linux
(++) using VT number 7

(--) PCI:*(0@1:0:0) nVidia Corporation GeForce 9800 GT rev 162, Mem @ 0xfd000000/0, 0xd0000000/0, 0xfa000000/0, I/O @ 0x0000d800/0, BIOS @ 0x????????/131072
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
    [20] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [21] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
    [22] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [23] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
    [24] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [25] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
    [26] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [27] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
    [28] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [29] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
(II) "extmod" will be loaded. This was enabled by default and also specified in the config file.
(II) "dbe" will be loaded. This was enabled by default and also specified in the config file.
(II) "glx" will be loaded. This was enabled by default and also specified in the config file.
(II) "freetype" will be loaded. This was enabled by default and also specified in the config file.
(II) "record" will be loaded. This was enabled by default and also specified in the config file.
(II) "dri" will be loaded by default.
(II) LoadModule: "dbe"

(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
    compiled for 1.5.2, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 1.1
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "extmod"

(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
    compiled for 1.5.2, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 1.1
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
(II) LoadModule: "glx"

(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
    compiled for 4.0.2, module version = 1.0.0
    Module class: X.Org Server Extension
(II) NVIDIA GLX Module  177.82  Tue Nov  4 14:03:48 PST 2008
(II) Loading extension GLX
(II) LoadModule: "record"

(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
    compiled for 1.5.2, module version = 1.13.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 1.1
(II) Loading extension RECORD
(II) LoadModule: "xtrap"

(II) Loading /usr/lib/xorg/modules/extensions//libxtrap.so
(II) Module xtrap: vendor="X.Org Foundation"
    compiled for 1.5.2, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 1.1
(II) Loading extension DEC-XTRAP
(II) LoadModule: "freetype"

(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
    compiled for 1.5.2, module version = 2.1.0
    Module class: X.Org Font Renderer
    ABI class: X.Org Font Renderer, version 0.6
(II) Loading font FreeType
(II) LoadModule: "type1"

(WW) Warning, couldn't open module type1
(II) UnloadModule: "type1"
(EE) Failed to load module "type1" (module does not exist, 0)
(II) LoadModule: "dri"

(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
    compiled for 1.5.2, module version = 1.0.0
    ABI class: X.Org Server Extension, version 1.1
(II) Loading extension XFree86-DRI
(II) LoadModule: "nvidia"

(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
    compiled for 4.0.2, module version = 1.0.0
    Module class: X.Org Video Driver
(II) NVIDIA dlloader X Driver  177.82  Tue Nov  4 13:42:45 PST 2008
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 01@00:00:0
(II) Loading sub module "fb"
(II) LoadModule: "fb"

(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
    compiled for 1.5.2, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "wfb"
(II) LoadModule: "wfb"

(II) Loading /usr/lib/xorg/modules//libwfb.so
(II) Module wfb: vendor="X.Org Foundation"
    compiled for 1.5.2, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
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
    [20] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [21] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
    [22] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [23] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
    [24] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [25] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
    [26] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [27] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
    [28] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [29] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "TwinView" "0"
(**) NVIDIA(0): Option "MetaModes" "DFP: 1680x1050 +0+0"
(**) NVIDIA(0): Option "Coolbits" "1"
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(II) NVIDIA(0): NVIDIA GPU GeForce 9800 GT (G92) at PCI:1:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 524288 kBytes
(--) NVIDIA(0): VideoBIOS: 62.92.56.00.3a
(II) NVIDIA(0): Detected PCI Express Link width: 16X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce 9800 GT at PCI:1:0:0:
(--) NVIDIA(0):     Samsung SyncMaster (DFP-0)
(--) NVIDIA(0): Samsung SyncMaster (DFP-0): 330.0 MHz maximum pixel clock
(--) NVIDIA(0): Samsung SyncMaster (DFP-0): Internal Dual Link TMDS
(II) NVIDIA(0): Display Device found referenced in MetaMode: DFP-0
(II) NVIDIA(0): Assigned Display Device: DFP-0
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "DFP:1680x1050+0+0"
(II) NVIDIA(0): Virtual screen size determined to be 1680 x 1050
(--) NVIDIA(0): DPI set to (90, 88); computed from "UseEdidDpi" X config
(--) NVIDIA(0):     option
(==) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
(II) NVIDIA(1): Creating default Display subsection in Screen section
    "Screen1" for depth/fbbpp 24/32
(**) NVIDIA(1): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(1): RGB weight 888
(==) NVIDIA(1): Default visual is TrueColor
(==) NVIDIA(1): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(1): Option "TwinView" "0"
(**) NVIDIA(1): Option "MetaModes" "DFP: 1680x1050 +0+0"
(**) NVIDIA(1): Enabling RENDER acceleration
(II) NVIDIA(1): NVIDIA GPU GeForce 9800 GT (G92) at PCI:1:0:0 (GPU-0)
(--) NVIDIA(1): Memory: 524288 kBytes
(--) NVIDIA(1): VideoBIOS: 62.92.56.00.3a
(II) NVIDIA(1): Detected PCI Express Link width: 16X
(--) NVIDIA(1): Interlaced video modes are supported on this GPU
(--) NVIDIA(1): Connected display device(s) on GeForce 9800 GT at PCI:1:0:0:
(--) NVIDIA(1):     Samsung SyncMaster (DFP-0)
(--) NVIDIA(1): Samsung SyncMaster (DFP-0): 330.0 MHz maximum pixel clock
(--) NVIDIA(1): Samsung SyncMaster (DFP-0): Internal Dual Link TMDS
(EE) NVIDIA(1): Unable to find available Display Devices for screen 1.
(II) UnloadModule: "nvidia"
(II) UnloadModule: "wfb"
(II) UnloadModule: "fb"
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
    [20] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [21] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
    [22] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [23] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
    [24] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [25] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
    [26] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [27] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
    [28] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [29] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
(II) NVIDIA(0): Initialized GPU GART.
(II) NVIDIA(0): Setting mode "DFP:1680x1050+0+0"
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(II) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
(II) Loading extension XINERAMA
(==) RandR enabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
(II) Initializing extension GLX
(II) config/hal: Adding input device Macintosh mouse button emulation
(II) LoadModule: "evdev"

(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
    compiled for 1.5.2, module version = 2.0.99
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 2.1
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event0"
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Configuring as mouse
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) config/hal: Adding input device AT Translated Set 2 keyboard
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event1"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) AT Translated Set 2 keyboard: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) AT Translated Set 2 keyboard: xkb_model: "pc105"
(**) Option "xkb_layout" "dk"
(**) AT Translated Set 2 keyboard: xkb_layout: "dk"
(II) config/hal: Adding input device Microsoft Microsoft Wireless Optical Desktop? 1.00
(**) Microsoft Microsoft Wireless Optical Desktop? 1.00: always reports core events
(**) Microsoft Microsoft Wireless Optical Desktop? 1.00: Device: "/dev/input/event2"
(II) Microsoft Microsoft Wireless Optical Desktop? 1.00: Found x and y relative axes
(II) Microsoft Microsoft Wireless Optical Desktop? 1.00: Found 5 mouse buttons
(II) Microsoft Microsoft Wireless Optical Desktop? 1.00: Configuring as mouse
(II) XINPUT: Adding extended input device "Microsoft Microsoft Wireless Optical Desktop? 1.00" (type: MOUSE)
(**) Microsoft Microsoft Wireless Optical Desktop? 1.00: YAxisMapping: buttons 4 and 5
(**) Microsoft Microsoft Wireless Optical Desktop? 1.00: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
AUDIT: Wed Feb 25 21:46:18 2009: 7602 X: client 4 rejected from local host ( uid=0 gid=0 pid=7620 )
AUDIT: Wed Feb 25 21:46:23 2009: 7602 X: client 4 rejected from local host ( uid=1000 gid=1000 pid=7624 )
AUDIT: Wed Feb 25 21:46:23 2009: 7602 X: client 4 rejected from local host ( uid=1000 gid=1000 pid=7625 )
AUDIT: Wed Feb 25 21:46:23 2009: 7602 X: client 4 rejected from local host ( uid=1000 gid=1000 pid=7626 )
```

**The lspci test:**

[LIST]
[*]Result: 01:00.0 VGA compatible controller: nVidia Corporation GeForce 9800 GT (rev a2)
[/LIST]

**Please help - what do I do wrong, how do I get my dual monitor to work?**

---

### Post by NT4usB on 2009-02-26
Are you running nvidia-settings as root?```
sudo nvidia-settings
```

Are you wanting cloned displays?
Did you try adding a second xecreen?

---

### Post by EDmonitor on 2009-03-01
Hi

Yes I have been running X as root - but it does not change anything :(.

I would like the second screen to work as an extension to the first one.

---

