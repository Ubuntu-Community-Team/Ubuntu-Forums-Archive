---
title: "Ubuntu 10.04 Xserver fail to start"
date: 2010-05-23
forum: New to Ubuntu
---

### Post by margemoosh on 2010-05-23
i just installed w3m and then i had to restart laptop and then ubuntu stop on loading screen and do nothing!
i pressed esc there was no error and last line was something about my laptop battery(i pluged in to power source)
in recovery mode when i run startx it doesn't do anything special and return without any error and there is not error in log files also.
my logs are something like this logs(in fact i think my logs are the same)

```
X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-27-server x86_64 Ubuntu
Current Operating System: Linux phanta 2.6.32-21-generic #32-Ubuntu SMP Fri Apr 16 08:09:38 UTC 2010 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-21-generic root=UUID=9b83f6de-9fa2-4c54-abda-aa0d2e713eb6 ro quiet splash
Build Date: 23 April 2010  05:11:46PM
xorg-server 2:1.7.6-2ubuntu7 (Bryce Harrington <bryce@ubuntu.com>) 
Current version of pixman: 0.16.4
    Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Thu May  6 22:33:26 2010
(==) Using config file: "/etc/X11/xorg.conf"
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"
 
Waiting for X server to shut down .. ddxSigGiveUp: Closing log
``````
X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-27-server x86_64 Ubuntu
Current Operating System: Linux phanta 2.6.32-21-generic #32-Ubuntu SMP Fri Apr 16 08:09:38 UTC 2010 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-21-generic root=UUID=9b83f6de-9fa2-4c54-abda-aa0d2e713eb6 ro quiet splash
Build Date: 23 April 2010  05:11:46PM
xorg-server 2:1.7.6-2ubuntu7 (Bryce Harrington <bryce@ubuntu.com>) 
Current version of pixman: 0.16.4
    Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Thu May  6 22:33:26 2010
(==) Using config file: "/etc/X11/xorg.conf"
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"
(==) No Layout section.  Using the first Screen section.
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "<default monitor>"
(==) No device specified for screen "Default Screen".
    Using the first device section listed.
(**) |   |-->Device "Default Device"
(==) No monitor specified for screen "Default Screen".
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
(==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
(II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
(II) Loader magic: 0x7ca300
(II) Module ABI versions:
    X.Org ANSI C Emulation: 0.4
    X.Org Video Driver: 6.0
    X.Org XInput driver : 7.0
    X.Org Server Extension : 2.0
(--) using VT number 7

(--) PCI:*(0:1:0:0) 10de:0407:1028:022e nVidia Corporation G84 [GeForce 8600M GT] rev 161, Mem @ 0xf5000000/16777216, 0xe0000000/268435456, 0xf2000000/33554432, I/O @ 0x0000ef00/128, BIOS @ 0x????????/131072
(II) Open ACPI successful (/var/run/acpid.socket)
(II) "extmod" will be loaded by default.
(II) "dbe" will be loaded by default.
(II) "glx" will be loaded. This was enabled by default and also specified in the config file.
(II) "record" will be loaded by default.
(II) "dri" will be loaded by default.
(II) "dri2" will be loaded by default.
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/extra-modules/libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
    compiled for 4.0.2, module version = 1.0.0
    Module class: X.Org Server Extension
(II) NVIDIA GLX Module  195.36.15  Fri Mar 12 01:17:05 PST 2010
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
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions/librecord.so
(II) Module record: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.13.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions/libdri.so
(II) Module dri: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.1.0
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/extra-modules/nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
    compiled for 4.0.2, module version = 1.0.0
    Module class: X.Org Video Driver
(II) NVIDIA dlloader X Driver  195.36.15  Fri Mar 12 00:38:50 PST 2010
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
(II) NVIDIA(0): Creating default Display subsection in Screen section
    "Default Screen" for depth/fbbpp 24/32
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "NoLogo" "True"
(**) May 06 22:33:26 NVIDIA(0): Enabling RENDER acceleration
(II) May 06 22:33:26 NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) May 06 22:33:26 NVIDIA(0):     enabled.
(II) May 06 22:33:27 NVIDIA(0): NVIDIA GPU GeForce 8600M GT (G84) at PCI:1:0:0 (GPU-0)
(--) May 06 22:33:27 NVIDIA(0): Memory: 524288 kBytes
(--) May 06 22:33:27 NVIDIA(0): VideoBIOS: 60.84.5e.00.08
(II) May 06 22:33:27 NVIDIA(0): Detected PCI Express Link width: 16X
(--) May 06 22:33:27 NVIDIA(0): Interlaced video modes are supported on this GPU
(--) May 06 22:33:27 NVIDIA(0): Connected display device(s) on GeForce 8600M GT at PCI:1:0:0:
(--) May 06 22:33:27 NVIDIA(0):     Seiko (DFP-0)
(--) May 06 22:33:27 NVIDIA(0): Seiko (DFP-0): 330.0 MHz maximum pixel clock
(--) May 06 22:33:27 NVIDIA(0): Seiko (DFP-0): Internal Dual Link LVDS
(II) May 06 22:33:27 NVIDIA(0): Assigned Display Device: DFP-0
(==) May 06 22:33:27 NVIDIA(0): 
(==) May 06 22:33:27 NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
(==) May 06 22:33:27 NVIDIA(0):     will be used as the requested mode.
(==) May 06 22:33:27 NVIDIA(0): 
(II) May 06 22:33:27 NVIDIA(0): Validated modes:
(II) May 06 22:33:27 NVIDIA(0):     "nvidia-auto-select"
(II) May 06 22:33:27 NVIDIA(0): Virtual screen size determined to be 1280 x 800
(--) May 06 22:33:28 NVIDIA(0): DPI set to (98, 96); computed from "UseEdidDpi" X config
(--) May 06 22:33:28 NVIDIA(0):     option
(==) May 06 22:33:28 NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
(--) Depth 24 pixmap format is 32 bpp
(II) May 06 22:33:28 NVIDIA: Using 768.00 MB of virtual memory for indirect framebuffer
(II) May 06 22:33:28 NVIDIA:     access.
(II) May 06 22:33:28 NVIDIA(0): Initialized GPU GART.
(II) May 06 22:33:28 NVIDIA(0): ACPI display change hotkey events enabled: the X server is new
(II) May 06 22:33:28 NVIDIA(0):     enough to receive ACPI hotkey events.
(II) May 06 22:33:28 NVIDIA(0): ACPI brightness change hotkey events enabled.
(II) May 06 22:33:28 NVIDIA(0): Setting mode "nvidia-auto-select"
(II) Loading extension NV-GLX
(II) May 06 22:33:28 NVIDIA(0): Initialized OpenGL Acceleration
(==) NVIDIA(0): Disabling shared memory pixmaps
(II) May 06 22:33:28 NVIDIA(0): Initialized X Rendering Acceleration
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
(II) Initializing extension GLX
(II) XKB: reuse xkmfile /tmp/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
(II) config/udev: Adding input device Video Bus (/dev/input/event5)
(**) Video Bus: Applying InputClass "evdev keyboard catchall"
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 2.3.2
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 7.0
(**) Video Bus: always reports core events
(**) Video Bus: Device: "/dev/input/event5"
(II) Video Bus: Found keys
(II) Video Bus: Configuring as keyboard
(II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/udev: Adding input device Power Button (/dev/input/event1)
(**) Power Button: Applying InputClass "evdev keyboard catchall"
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event1"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/udev: Adding input device Lid Switch (/dev/input/event0)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device Sleep Button (/dev/input/event2)
(**) Sleep Button: Applying InputClass "evdev keyboard catchall"
(**) Sleep Button: always reports core events
(**) Sleep Button: Device: "/dev/input/event2"
(II) Sleep Button: Found keys
(II) Sleep Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/udev: Adding input device Laptop Integrated Webcam (/dev/input/event6)
(**) Laptop Integrated Webcam: Applying InputClass "evdev keyboard catchall"
(**) Laptop Integrated Webcam: always reports core events
(**) Laptop Integrated Webcam: Device: "/dev/input/event6"
(II) Laptop Integrated Webcam: Found keys
(II) Laptop Integrated Webcam: Configuring as keyboard
(II) XINPUT: Adding extended input device "Laptop Integrated Webcam" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/udev: Adding input device HDA Digital PCBeep (/dev/input/event12)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device HDA Intel Mic at Ext Front Jack (/dev/input/event15)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device HDA Intel HP Out at Ext Front Jack (/dev/input/event16)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device HDA Intel HP Out at Ext Front Jack (/dev/input/event17)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device Logitech USB Receiver (/dev/input/event7)
(**) Logitech USB Receiver: Applying InputClass "evdev pointer catchall"
(**) Logitech USB Receiver: always reports core events
(**) Logitech USB Receiver: Device: "/dev/input/event7"
(II) Logitech USB Receiver: Found 20 mouse buttons
(II) Logitech USB Receiver: Found scroll wheel(s)
(II) Logitech USB Receiver: Found relative axes
(II) Logitech USB Receiver: Found x and y relative axes
(II) Logitech USB Receiver: Configuring as mouse
(**) Logitech USB Receiver: YAxisMapping: buttons 4 and 5
(**) Logitech USB Receiver: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: MOUSE)
(II) Logitech USB Receiver: initialized for relative axes.
(II) config/udev: Adding input device Logitech USB Receiver (/dev/input/mouse1)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device Logitech USB Receiver (/dev/input/event8)
(**) Logitech USB Receiver: Applying InputClass "evdev keyboard catchall"
(**) Logitech USB Receiver: always reports core events
(**) Logitech USB Receiver: Device: "/dev/input/event8"
(II) Logitech USB Receiver: Found 1 mouse buttons
(II) Logitech USB Receiver: Found scroll wheel(s)
(II) Logitech USB Receiver: Found relative axes
(II) Logitech USB Receiver: Found absolute axes
(II) Logitech USB Receiver: Found keys
(II) Logitech USB Receiver: Configuring as mouse
(II) Logitech USB Receiver: Configuring as keyboard
(**) Logitech USB Receiver: YAxisMapping: buttons 4 and 5
(**) Logitech USB Receiver: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(EE) Logitech USB Receiver: failed to initialize for relative axes.
(II) Logitech USB Receiver: initialized for absolute axes.
(II) config/udev: Adding input device Broadcom Corp (/dev/input/event9)
(**) Broadcom Corp: Applying InputClass "evdev keyboard catchall"
(**) Broadcom Corp: always reports core events
(**) Broadcom Corp: Device: "/dev/input/event9"
(II) Broadcom Corp: Found keys
(II) Broadcom Corp: Configuring as keyboard
(II) XINPUT: Adding extended input device "Broadcom Corp" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/udev: Adding input device Broadcom Corp (/dev/input/event10)
(**) Broadcom Corp: Applying InputClass "evdev pointer catchall"
(**) Broadcom Corp: always reports core events
(**) Broadcom Corp: Device: "/dev/input/event10"
(II) Broadcom Corp: Found 3 mouse buttons
(II) Broadcom Corp: Found relative axes
(II) Broadcom Corp: Found x and y relative axes
(II) Broadcom Corp: Configuring as mouse
(**) Broadcom Corp: YAxisMapping: buttons 4 and 5
(**) Broadcom Corp: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Broadcom Corp" (type: MOUSE)
(II) Broadcom Corp: initialized for relative axes.
(II) config/udev: Adding input device Broadcom Corp (/dev/input/mouse2)
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
(II) config/udev: Adding input device PS/2 Mouse (/dev/input/event13)
(**) PS/2 Mouse: Applying InputClass "evdev pointer catchall"
(**) PS/2 Mouse: always reports core events
(**) PS/2 Mouse: Device: "/dev/input/event13"
(II) PS/2 Mouse: Found 3 mouse buttons
(II) PS/2 Mouse: Found relative axes
(II) PS/2 Mouse: Found x and y relative axes
(II) PS/2 Mouse: Configuring as mouse
(**) PS/2 Mouse: YAxisMapping: buttons 4 and 5
(**) PS/2 Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "PS/2 Mouse" (type: MOUSE)
(II) PS/2 Mouse: initialized for relative axes.
(II) config/udev: Adding input device PS/2 Mouse (/dev/input/mouse3)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device AlpsPS/2 ALPS GlidePoint (/dev/input/event14)
(**) AlpsPS/2 ALPS GlidePoint: Applying InputClass "evdev pointer catchall"
(**) AlpsPS/2 ALPS GlidePoint: Applying InputClass "evdev touchpad catchall"
(**) AlpsPS/2 ALPS GlidePoint: Applying InputClass "touchpad catchall"
(II) LoadModule: "synaptics"
(II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
(II) Module synaptics: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.2.2
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 7.0
(II) Synaptics touchpad driver version 1.2.2
(**) Option "Device" "/dev/input/event14"
(II) AlpsPS/2 ALPS GlidePoint: x-axis range 0 - 1023
(II) AlpsPS/2 ALPS GlidePoint: y-axis range 0 - 767
(II) AlpsPS/2 ALPS GlidePoint: pressure range 0 - 127
(II) AlpsPS/2 ALPS GlidePoint: finger width range 0 - 0
(II) AlpsPS/2 ALPS GlidePoint: buttons: left right middle
(--) AlpsPS/2 ALPS GlidePoint: touchpad found
(**) AlpsPS/2 ALPS GlidePoint: always reports core events
(II) XINPUT: Adding extended input device "AlpsPS/2 ALPS GlidePoint" (type: TOUCHPAD)
(**) AlpsPS/2 ALPS GlidePoint: (accel) keeping acceleration scheme 1
(**) AlpsPS/2 ALPS GlidePoint: (accel) acceleration profile 0
(**) AlpsPS/2 ALPS GlidePoint: (accel) acceleration factor: 2.000
(**) AlpsPS/2 ALPS GlidePoint: (accel) acceleration threshold: 4
(--) AlpsPS/2 ALPS GlidePoint: touchpad found
(II) config/udev: Adding input device AlpsPS/2 ALPS GlidePoint (/dev/input/mouse4)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device Dell WMI hotkeys (/dev/input/event11)
(**) Dell WMI hotkeys: Applying InputClass "evdev keyboard catchall"
(**) Dell WMI hotkeys: always reports core events
(**) Dell WMI hotkeys: Device: "/dev/input/event11"
(II) Dell WMI hotkeys: Found keys
(II) Dell WMI hotkeys: Configuring as keyboard
(II) XINPUT: Adding extended input device "Dell WMI hotkeys" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
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
(II) Video Bus: Close
(II) UnloadModule: "evdev"
(II) Power Button: Close
(II) UnloadModule: "evdev"
(II) Sleep Button: Close
(II) UnloadModule: "evdev"
(II) Laptop Integrated Webcam: Close
(II) UnloadModule: "evdev"
(II) Logitech USB Receiver: Close
(II) UnloadModule: "evdev"
(II) Logitech USB Receiver: Close
(II) UnloadModule: "evdev"
(II) Broadcom Corp: Close
(II) UnloadModule: "evdev"
(II) Broadcom Corp: Close
(II) UnloadModule: "evdev"
(II) AT Translated Set 2 keyboard: Close
(II) UnloadModule: "evdev"
(II) PS/2 Mouse: Close
(II) UnloadModule: "evdev"
(II) UnloadModule: "synaptics"
(II) Dell WMI hotkeys: Close
(II) UnloadModule: "evdev"
(II) Macintosh mouse button emulation: Close
(II) UnloadModule: "evdev"
 ddxSigGiveUp: Closing log
```

---

### Post by sylvester_0 on 2010-05-23
Have you tried running with no xorg.conf?

```
sudo mv /etc/X11/xorg.conf{,.old}
```

It's really odd that there are no errors. Also, I see that you're running an older kernel, you should try updating.

---

### Post by afrodeity on 2010-05-24
Mine starts okay in normal mode, but its an overlong boot, and there are issues with the nvidia driver in the KDE session, but Gnome is okay.

However, in recovery mode, startx has exactly the same problem as reported above. Fails to start the x server.

---

