---
title: "Compiz won't start on 10.04 LTS"
date: 2010-06-21
forum: New to Ubuntu
---

### Post by Blodskaal on 2010-06-21
[FONT=System]Hi everybody,

I've got an annoying problem on my HP EliteBook 8530w. I had no problem running compiz on 9.10. After I upgraded to 10.04, compiz ran when I used "compiz --replace ccp&". However now it doesn't work anymore at all. It is set up to run at boot.[/FONT] 
[FONT=System]My graphics driver is NVIDIA Linux-x86 256.25 and my graphics card is a Nvidia Quadro 770M[/FONT]

[FONT=System]I'll post some outputs for information.[/FONT]
[FONT=System]
Compiz isn't running according to this:

[/FONT]```
ps ax | grep compiz
 4325 pts/1    S+     0:00 grep --color=auto compiz
```[FONT=System]

This is what it shows when I try to start compiz:

 [/FONT]```
compiz --replace ccp&
[1] 4298
user@laptop:~$ compiz (core) - Fatal: glXCreateContext failed
compiz (core) - Error: Failed to manage screen: 0
compiz (core) - Fatal: No manageable screens found on display :0.0

Launching fallback window manager 
```This is what compiz-check says:

```
./compiz-check

Gathering information about your system...

 Distribution:          Ubuntu 10.04
 Desktop environment:   GNOME
 Graphics chip:         nVidia Corporation G96M [Quadro FX 770M] (rev a1)
 Driver in use:         nvidia
 Rendering method:      Nvidia

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [FAIL]
 Checking for non power of two support...          [FAIL]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [SKIP]

At least one check had to be skipped:
 Error: Unable to detect maximum 3D texture size 
```[FONT=Verdana]This is my xorg.conf file:[/FONT]

```
cat /etc/X11/xorg.conf
Section "ServerLayout"
    Identifier     "X.org Configured"
    Screen      0  "Screen0" 0 0
    InputDevice    "Mouse0" "CorePointer"
    InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
    ModulePath   "/usr/lib/xorg/modules"
    ModulePath   "/usr/lib/xorg/modules/extensions/nvidia"
    ModulePath   "/usr/lib/xorg/modules/drivers"
    FontPath     "/usr/share/fonts/X11/misc"
    FontPath     "/usr/share/fonts/X11/cyrillic"
    FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath     "/usr/share/fonts/X11/Type1"
    FontPath     "/usr/share/fonts/X11/100dpi"
    FontPath     "/usr/share/fonts/X11/75dpi"
    FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
    FontPath     "built-ins"
EndSection

Section "Module"
    Load  "record"
    Load  "dbe"
    Load  "dri"
    Load  "glx"
    Load  "extmod"
    Load  "dri2"
EndSection

Section "InputDevice"
    Identifier  "Keyboard0"
    Driver      "kbd"
EndSection

Section "InputDevice"
    Identifier  "Mouse0"
    Driver      "mouse"
    Option        "Protocol" "auto"
    Option        "Device" "/dev/input/mice"
    Option        "ZAxisMapping" "4 5 6 7"
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
    BoardName   "G96M [Quadro FX 770M]"
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
```This is my X server log:

```
 cat /var/log/Xorg.0.log

X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-27-server i686 Ubuntu
Current Operating System: Linux laptop 2.6.32-22-generic #36-Ubuntu SMP Thu Jun 3 22:02:19 UTC 2010 i686
Kernel command line: BOOT_IMAGE=/vmlinuz-2.6.32-22-generic root=UUID=22f3c4a0-c092-482f-a54f-70a910036177 ro 795 quiet splash
Build Date: 09 June 2010  10:55:28AM
xorg-server 2:1.7.6-2ubuntu7.1 (For technical support please see http://www.ubuntu.com/support) 
Current version of pixman: 0.16.4
    Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Mon Jun 21 09:09:00 2010
(==) Using config file: "/etc/X11/xorg.conf"
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"
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
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
    Entry deleted from font path.
(**) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/75dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    /usr/share/fonts/X11/75dpi,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins,
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/75dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    /usr/share/fonts/X11/75dpi,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
(**) ModulePath set to "/usr/lib/xorg/modules"
(WW) AllowEmptyInput is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
(WW) Disabling Mouse0
(WW) Disabling Keyboard0
(II) Loader magic: 0x81f0e80
(II) Module ABI versions:
    X.Org ANSI C Emulation: 0.4
    X.Org Video Driver: 6.0
    X.Org XInput driver : 7.0
    X.Org Server Extension : 2.0
(--) using VT number 8

(--) PCI:*(0:1:0:0) 10de:065c:103c:30e7 nVidia Corporation G96M [Quadro FX 770M] rev 161, Mem @ 0xd2000000/16777216, 0xc0000000/268435456, 0xd0000000/33554432, I/O @ 0x00007000/128
(II) Open ACPI successful (/var/run/acpid.socket)
(II) "extmod" will be loaded. This was enabled by default and also specified in the config file.
(II) "dbe" will be loaded. This was enabled by default and also specified in the config file.
(II) "glx" will be loaded. This was enabled by default and also specified in the config file.
(II) "record" will be loaded. This was enabled by default and also specified in the config file.
(II) "dri" will be loaded. This was enabled by default and also specified in the config file.
(II) "dri2" will be loaded. This was enabled by default and also specified in the config file.
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions/librecord.so
(II) Module record: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.13.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions/libdri.so
(II) Module dri: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions/libglx.so
(II) Module glx: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    ABI class: X.Org Server Extension, version 2.0
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.1.0
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers/nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
    compiled for 4.0.2, module version = 1.0.0
    Module class: X.Org Video Driver
(II) NVIDIA dlloader X Driver  256.25  Tue May 18 20:40:43 PDT 2010
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 01@00:00:0
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "wfb"
(II) LoadModule: "wfb"
(II) Loading /usr/lib/xorg/modules/libwfb.so
(II) Module wfb: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(==) NVIDIA(0): Depth 24, (==) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) Jun 21 09:09:00 NVIDIA(0): Enabling RENDER acceleration
(EE) Jun 21 09:09:00 NVIDIA(0): Failed to initialize the GLX module; please check in your X
(EE) Jun 21 09:09:00 NVIDIA(0):     log file that the GLX module has been loaded in your X
(EE) Jun 21 09:09:00 NVIDIA(0):     server, and that the module is the NVIDIA GLX module.  If
(EE) Jun 21 09:09:00 NVIDIA(0):     you continue to encounter problems, Please try
(EE) Jun 21 09:09:00 NVIDIA(0):     reinstalling the NVIDIA driver.
(II) Jun 21 09:09:02 NVIDIA(0): NVIDIA GPU Quadro FX 770M (G96GL) at PCI:1:0:0 (GPU-0)
(--) Jun 21 09:09:02 NVIDIA(0): Memory: 524288 kBytes
(--) Jun 21 09:09:02 NVIDIA(0): VideoBIOS: 62.94.7a.01.06
(II) Jun 21 09:09:02 NVIDIA(0): Detected PCI Express Link width: 16X
(--) Jun 21 09:09:02 NVIDIA(0): Interlaced video modes are supported on this GPU
(--) Jun 21 09:09:02 NVIDIA(0): Connected display device(s) on Quadro FX 770M at PCI:1:0:0:
(--) Jun 21 09:09:02 NVIDIA(0):     LGD (DFP-0)
(--) Jun 21 09:09:02 NVIDIA(0): LGD (DFP-0): 330.0 MHz maximum pixel clock
(--) Jun 21 09:09:02 NVIDIA(0): LGD (DFP-0): Internal Dual Link LVDS
(II) Jun 21 09:09:02 NVIDIA(0): Assigned Display Device: DFP-0
(==) Jun 21 09:09:02 NVIDIA(0): 
(==) Jun 21 09:09:02 NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
(==) Jun 21 09:09:02 NVIDIA(0):     will be used as the requested mode.
(==) Jun 21 09:09:02 NVIDIA(0): 
(II) Jun 21 09:09:02 NVIDIA(0): Validated modes:
(II) Jun 21 09:09:02 NVIDIA(0):     "nvidia-auto-select"
(II) Jun 21 09:09:02 NVIDIA(0): Virtual screen size determined to be 1680 x 1050
(--) Jun 21 09:09:03 NVIDIA(0): DPI set to (129, 126); computed from "UseEdidDpi" X config
(--) Jun 21 09:09:03 NVIDIA(0):     option
(==) Jun 21 09:09:03 NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
(--) Depth 24 pixmap format is 32 bpp
(II) Jun 21 09:09:03 NVIDIA: Using 768.00 MB of virtual memory for indirect memory access.
(II) Jun 21 09:09:03 NVIDIA(0): Initialized GPU GART.
(II) Jun 21 09:09:03 NVIDIA(0): ACPI display change hotkey events enabled: the X server is new
(II) Jun 21 09:09:03 NVIDIA(0):     enough to receive ACPI hotkey events.
(II) Jun 21 09:09:03 NVIDIA(0): ACPI brightness change hotkey events enabled.
(II) Jun 21 09:09:03 NVIDIA(0): Setting mode "nvidia-auto-select"
(II) Loading extension NV-GLX
(II) Jun 21 09:09:03 NVIDIA(0): Initialized OpenGL Acceleration
(==) NVIDIA(0): Disabling shared memory pixmaps
(II) Jun 21 09:09:03 NVIDIA(0): Initialized X Rendering Acceleration
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(==) NVIDIA(0): DPMS enabled
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
(II) AIGLX: Screen 0 is not DRI2 capable
(II) AIGLX: Screen 0 is not DRI capable
(II) AIGLX: Loaded and initialized /usr/lib/dri/swrast_dri.so
(II) GLX: Initialized DRISWRAST GL provider for screen 0
(II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
(II) config/udev: Adding input device Power Button (/dev/input/event2)
(**) Power Button: Applying InputClass "evdev keyboard catchall"
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 2.3.2
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 7.0
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event2"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/udev: Adding input device Video Bus (/dev/input/event6)
(**) Video Bus: Applying InputClass "evdev keyboard catchall"
(**) Video Bus: always reports core events
(**) Video Bus: Device: "/dev/input/event6"
(II) Video Bus: Found keys
(II) Video Bus: Configuring as keyboard
(II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/udev: Adding input device Lid Switch (/dev/input/event1)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device Sleep Button (/dev/input/event0)
(**) Sleep Button: Applying InputClass "evdev keyboard catchall"
(**) Sleep Button: always reports core events
(**) Sleep Button: Device: "/dev/input/event0"
(II) Sleep Button: Found keys
(II) Sleep Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/udev: Adding input device CKA7216 (/dev/input/event8)
(**) CKA7216: Applying InputClass "evdev keyboard catchall"
(**) CKA7216: always reports core events
(**) CKA7216: Device: "/dev/input/event8"
(II) CKA7216: Found keys
(II) CKA7216: Configuring as keyboard
(II) XINPUT: Adding extended input device "CKA7216" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/udev: Adding input device HDA Digital PCBeep (/dev/input/event10)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device USB Optical Mouse (/dev/input/event5)
(**) USB Optical Mouse: Applying InputClass "evdev pointer catchall"
(**) USB Optical Mouse: always reports core events
(**) USB Optical Mouse: Device: "/dev/input/event5"
(II) USB Optical Mouse: Found 3 mouse buttons
(II) USB Optical Mouse: Found scroll wheel(s)
(II) USB Optical Mouse: Found relative axes
(II) USB Optical Mouse: Found x and y relative axes
(II) USB Optical Mouse: Configuring as mouse
(**) USB Optical Mouse: YAxisMapping: buttons 4 and 5
(**) USB Optical Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "USB Optical Mouse" (type: MOUSE)
(II) USB Optical Mouse: initialized for relative axes.
(II) config/udev: Adding input device USB Optical Mouse (/dev/input/mouse1)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event4)
(**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event4"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event9)
(**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
(**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
(II) LoadModule: "synaptics"
(II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
(II) Module synaptics: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.2.2
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 7.0
(II) Synaptics touchpad driver version 1.2.2
(**) Option "Device" "/dev/input/event9"
(II) SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5472
(II) SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4448
(II) SynPS/2 Synaptics TouchPad: pressure range 0 - 255
(II) SynPS/2 Synaptics TouchPad: finger width range 0 - 0
(II) SynPS/2 Synaptics TouchPad: buttons: left right middle
(--) SynPS/2 Synaptics TouchPad: touchpad found
(**) SynPS/2 Synaptics TouchPad: always reports core events
(II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD)
(**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
(**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 0
(**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
(**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
(--) SynPS/2 Synaptics TouchPad: touchpad found
(II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse2)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device PS/2 Generic Mouse (/dev/input/event11)
(**) PS/2 Generic Mouse: Applying InputClass "evdev pointer catchall"
(**) PS/2 Generic Mouse: always reports core events
(**) PS/2 Generic Mouse: Device: "/dev/input/event11"
(II) PS/2 Generic Mouse: Found 3 mouse buttons
(II) PS/2 Generic Mouse: Found relative axes
(II) PS/2 Generic Mouse: Found x and y relative axes
(II) PS/2 Generic Mouse: Configuring as mouse
(**) PS/2 Generic Mouse: YAxisMapping: buttons 4 and 5
(**) PS/2 Generic Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "PS/2 Generic Mouse" (type: MOUSE)
(II) PS/2 Generic Mouse: initialized for relative axes.
(II) config/udev: Adding input device PS/2 Generic Mouse (/dev/input/mouse3)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device ST LIS3LV02DL Accelerometer (/dev/input/event7)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device ST LIS3LV02DL Accelerometer (/dev/input/js0)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device Macintosh mouse button emulation (/dev/input/event3)
(**) Macintosh mouse button emulation: Applying InputClass "evdev pointer catchall"
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event3"
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Found relative axes
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Configuring as mouse
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(II) Macintosh mouse button emulation: initialized for relative axes.
(II) config/udev: Adding input device Macintosh mouse button emulation (/dev/input/mouse0)
(II) No input driver/identifier specified (ignoring)

```As far as I can see it comes down to this part of the log.

```
(EE) Jun 21 09:09:00 NVIDIA(0): Failed to initialize the GLX module;  please check in your X
(EE) Jun 21 09:09:00 NVIDIA(0):     log file that the GLX module has  been loaded in your X
(EE) Jun 21 09:09:00 NVIDIA(0):     server, and that the module is the  NVIDIA GLX module.  If
(EE) Jun 21 09:09:00 NVIDIA(0):     you continue to encounter problems,  Please try
(EE) Jun 21 09:09:00 NVIDIA(0):     reinstalling the NVIDIA driver.
```I've no idea how to fix this, except the obvious advice of reinstalling the NVIDIA driver, which I doubt would work, since everything went fine during the install. I doubt it would do better on a new install. Also it's the last thing I'm willing to try since installing NVIDIA drivers on 10.04 LTS is an even greater pain in various body parts* than it was on 9.10.

* carpal tunnel and a headache

---

### Post by diablo75 on 2010-06-21
I can say that on one system in particular that I did some work on, disabling the drivers, downloading all the latest updates for the system, and then re-enabling the drivers seems to iron out a couple kinks and I was able to get compiz working so if you haven't tried that yet you should.

I have seen it come up where you can download newer drivers that are not being deployed via the built in Hardware Drivers manager but it requires manual installation and crossing your fingers.  Visit [www.nvidia.com](www.nvidia.com) to look for a download for Linux.  I wouldn't be able to tell you how to do the installation with them as I've not done it before but I'm sure others have; google is your friend.

Edit to add:  I did a quick search for you to see what comes up for Linux drivers for Quadro FX (laptop) chipsets, and I found this:  [http://www.nvidia.com/object/linux-display-ia32-195.36.31-driver.html](http://www.nvidia.com/object/linux-display-ia32-195.36.31-driver.html)

That's a 32-bit edition, btw.

---

### Post by Blodskaal on 2010-06-21
@diablo75: I did install a custom NVIDIA driver from nvidia.com, after I installed and updated 10.04 LTS. So I guess in doing that, I already did what you suggested. (note: you could see that because my listed driver is 256.25 which is a proprietary driver that cannot be installed by Ubuntu itself.)

EDIT: @diablo75's edit. Thanks for the link, but I think you missed this. I already have the 256.25 installed, the 195 you link to is the newest release, but the 256.25 is the newest driver in beta. It has additional GLX support, while this may be a problem with the Ubuntu config, it only adds more options. It might be harder to set up, but it has all the GLX options of the 195 and more. It also fixes some problems that older Nvidia drivers have with compiz.

---

### Post by Blodskaal on 2010-06-22
Ok, I'm gonna keep my big mouth shut now, the install of 195 went smoothly and worked immediately.

Thanks for the help.

EDIT: I see someone already set this to "solved" when I forgot to, I accidentally unsolved it, but solved it again.

---

