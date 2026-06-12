---
title: "screen res resets"
date: 2009-10-08
forum: New to Ubuntu
---

### Post by moondoggy17 on 2009-10-08
every time i restart my laptop the screen res resets
i'm using jaunty on a Acer Aspire 4520 with a nvidia geforce 7000m

heres xorg.log

```

X.Org X Server 1.6.0
Release Date: 2009-2-25
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-15-server x86_64 Ubuntu
Current Operating System: Linux dude-laptop 2.6.28-15-generic #52-Ubuntu SMP Wed Sep 9 10:48:52 UTC 2009 x86_64
Build Date: 09 April 2009  02:11:54AM
xorg-server 2:1.6.0-0ubuntu14 (buildd@crested.buildd) 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Thu Oct  8 16:50:04 2009
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Layout0"
(**) |-->Screen "Screen0" (0)
(**) |   |-->Monitor "Monitor0"
(**) |   |-->Device "Device0"
(**) |-->Input Device "Keyboard0"
(**) |-->Input Device "Mouse0"
(**) Option "Xinerama" "0"
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
(WW) AllowEmptyInput is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
(WW) Disabling Keyboard0
(WW) Disabling Mouse0
(II) Loader magic: 0xb40
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 5.0
	X.Org XInput driver : 4.0
	X.Org Server Extension : 2.0
(II) Loader running on linux
(++) using VT number 7

(--) PCI:*(0@0:18:0) nVidia Corporation GeForce 7000M (rev a2) rev 162, Mem @ 0xf3000000/16777216, 0xd0000000/268435456, 0xf2000000/16777216, BIOS @ 0x????????/131072
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
(II) "extmod" will be loaded. This was enabled by default and also specified in the config file.
(II) "dbe" will be loaded. This was enabled by default and also specified in the config file.
(II) "glx" will be loaded. This was enabled by default and also specified in the config file.
(II) "record" will be loaded by default.
(II) "dri" will be loaded by default.
(II) "dri2" will be loaded by default.
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
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
(II) LoadModule: "type1"
(WW) Warning, couldn't open module type1
(II) UnloadModule: "type1"
(EE) Failed to load module "type1" (module does not exist, 0)
(II) LoadModule: "freetype"
(WW) Warning, couldn't open module freetype
(II) UnloadModule: "freetype"
(EE) Failed to load module "freetype" (module does not exist, 0)
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Server Extension
(II) NVIDIA GLX Module  180.44  Tue Mar 24 06:11:47 PST 2009
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
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Video Driver
(II) NVIDIA dlloader X Driver  180.44  Tue Mar 24 05:51:43 PST 2009
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 00@00:12:0
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "wfb"
(II) LoadModule: "wfb"
(II) Loading /usr/lib/xorg/modules//libwfb.so
(II) Module wfb: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
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
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "TwinView" "0"
(**) NVIDIA(0): Option "MetaModes" "1280x800_60 +0+0"
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(II) NVIDIA(0): NVIDIA GPU GeForce 7000M / nForce 610M (C67) at PCI:0:18:0
(II) NVIDIA(0):     (GPU-0)
(--) NVIDIA(0): Memory: 524288 kBytes
(--) NVIDIA(0): VideoBIOS: 05.67.32.20.09
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce 7000M / nForce 610M at
(--) NVIDIA(0):     PCI:0:18:0:
(--) NVIDIA(0):     Seiko (DFP-0)
(--) NVIDIA(0): Seiko (DFP-0): 310.0 MHz maximum pixel clock
(--) NVIDIA(0): Seiko (DFP-0): Internal Dual Link LVDS
(II) NVIDIA(0): Assigned Display Device: DFP-0
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "1280x800_60+0+0"
(II) NVIDIA(0): Virtual screen size determined to be 1280 x 800
(--) NVIDIA(0): DPI set to (108, 106); computed from "UseEdidDpi" X config
(--) NVIDIA(0):     option
(==) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
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
(II) NVIDIA(0): Initialized GPU GART.
(II) NVIDIA(0): ACPI display change hotkey events enabled: the X server is new
(II) NVIDIA(0):     enough to receive ACPI display change hotkey events.
(II) NVIDIA(0): Setting mode "1280x800_60+0+0"
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(==) NVIDIA(0): Disabling shared memory pixmaps
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(**) Option "dpms"
(**) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
(II) Loading extension XINERAMA
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
(II) Initializing extension GLX
(II) config/hal: Adding input device AT Translated Set 2 keyboard
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 2.1.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 4.0
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event5"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) AT Translated Set 2 keyboard: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) AT Translated Set 2 keyboard: xkb_model: "pc105"
(**) Option "xkb_layout" "us"
(**) AT Translated Set 2 keyboard: xkb_layout: "us"
(II) config/hal: Adding input device Video Bus
(**) Video Bus: always reports core events
(**) Video Bus: Device: "/dev/input/event7"
(II) Video Bus: Found keys
(II) Video Bus: Configuring as keyboard
(II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Video Bus: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) Video Bus: xkb_model: "pc105"
(**) Option "xkb_layout" "us"
(**) Video Bus: xkb_layout: "us"
(II) config/hal: Adding input device Macintosh mouse button emulation
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event4"
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
(II) config/hal: Adding input device SynPS/2 Synaptics TouchPad
(II) LoadModule: "synaptics"
(II) Loading /usr/lib/xorg/modules/input//synaptics_drv.so
(II) Module synaptics: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 0.99.3
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 4.0
(II) Synaptics touchpad driver version 0.99.3
(**) Option "Device" "/dev/input/event9"
(II) SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5472
(II) SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4448
(II) SynPS/2 Synaptics TouchPad: pressure range 0 - 255
(II) SynPS/2 Synaptics TouchPad: finger width range 0 - 0
(II) SynPS/2 Synaptics TouchPad: buttons: left right middle
(--) SynPS/2 Synaptics TouchPad touchpad found
(**) SynPS/2 Synaptics TouchPad: always reports core events
(II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD)
(**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
(**) SynPS/2 Synaptics TouchPad: (accel) filter chain progression: 2.00
(**) SynPS/2 Synaptics TouchPad: (accel) filter stage 0: 20.00 ms
(**) SynPS/2 Synaptics TouchPad: (accel) set acceleration profile 0
(--) SynPS/2 Synaptics TouchPad touchpad found
(II) NVIDIA(0): Setting mode "800x600"
(II) NVIDIA(0): Setting mode "1280x800_60+0+0"
(II) NVIDIA(0): Setting mode "1024x768"
(II) NVIDIA(0): Setting mode "1280x800_60+0+0"
(II) NVIDIA(0): Setting mode "DFP-0:1280x800@1280x800+0+0"
(WW) AT Translated Set 2 keyboard: unable to handle keycode 
```


and xorg.conf

```
# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildd@crested)  Sun Feb  1 20:25:37 UTC 2009

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Seiko"
    HorizSync       30.0 - 75.0
    VertRefresh     60.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7000M / nForce 610M"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "1280x800_60 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```

---

### Post by wojox on 2009-10-08
Well you can:

```
gksudo gedit /etc/X11/xorg.conf
```

And remove these modules causing these errors from Xorg.log:

```
(II) LoadModule: "type1"
(WW) Warning, couldn't open module type1
(II) UnloadModule: "type1"
(EE) Failed to load module "type1" (module does not exist, 0)
(II) LoadModule: "freetype"
(WW) Warning, couldn't open module freetype
(II) UnloadModule: "freetype"
(EE) Failed to load module "freetype" (module does not exist, 0)

```

xorg.conf:
```
[COLOR="Red"]
Load           "type1"
Load           "freetype"
[/COLOR]
```

What resolution are you going for?

---

### Post by moondoggy17 on 2009-10-08
i want  at max 1280 by 800

---

### Post by wojox on 2009-10-08
I don't know moondogggy, everything looks like it's setting to that resolution. You're using:

```
gksudo nvidia-settings
```

To configure and save it I presume.

---

### Post by moondoggy17 on 2009-10-08
yes i'm using nvidia-settings

---

### Post by pj_kare on 2009-10-08
As I'm just a newbie I can only offer you my fix....

I have a GeForce 6200, and every time I booted/rebooted my pc the screen res would revert back to what it was before I changed it using Nvidia X server settings (Nvidia Control Panel). To fix it I had to ensure that both xorg.conf and xorg.conf.backup were exactly the same. 

"Save to X configuration File" on the Nvidia Control Panel brings up this error on my pc: 

"Unable to remove old X config backup file '/etc/X11/xorg.conf.backup'."

So I used the "Show Preview button", copied the text and pasted it over the text in xorg.conf.backup using terminal.

(I could probably have done the same thing by opening both xorg.conf and xorg.conf.backup in gedit through terminal.)

Hope this is of some use. :P

---

### Post by moondoggy17 on 2009-10-09
ok i fixed it by opening nvidia-settings setting my res then going to pref>display and clicking save

---

