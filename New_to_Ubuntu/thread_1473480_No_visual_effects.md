---
title: "No visual effects"
date: 2010-05-05
forum: New to Ubuntu
---

### Post by cbbnewbie on 2010-05-05
i recently installed compiz fusion on my slow laptop with ubuntu 10.04 and it worked fine so i was happy and went to bed, when i turned my laptop on a while ago i notice that compiz isn't working and that my visual effects cant even be set to normal i dont see any error messages so i dont know whats wrong please help thanks

---

### Post by halitech on 2010-05-05
what kind of laptop and what video card does the machine have in it?

post the output of
```
lspci
```

---

### Post by cbbnewbie on 2010-05-05
thanks for the reply here it is

charlie@charlie-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82815 815 Chipset Host Bridge and Memory Controller Hub (rev 04)
00:01.0 PCI bridge: Intel Corporation 82815 815 Chipset AGP Bridge (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801BAM ISA Bridge (LPC) (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801BAM IDE U100 Controller (rev 03)
00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation NV11 [GeForce2 Go] (rev b2)
02:03.0 Multimedia audio controller: ESS Technology ES1983S Maestro-3i PCI Audio Accelerator (rev 10)
02:06.0 PCI bridge: Actiontec Electronics Inc Mini-PCI bridge (rev 11)
02:0f.0 CardBus bridge: Texas Instruments PCI4451 PC card Cardbus Controller
02:0f.1 CardBus bridge: Texas Instruments PCI4451 PC card Cardbus Controller
02:0f.2 FireWire (IEEE 1394): Texas Instruments PCI4451 IEEE-1394 Controller
08:04.0 Ethernet controller: Intel Corporation 82557/8/9/0/1 Ethernet Pro 100 (rev 08)
08:08.0 Communication controller: Agere Systems WinModem 56k (rev 01)
charlie@charlie-laptop:~$

i have installed my graphics driver successfully thats why i have made compiz worked but now i dont know what happened :(

---

### Post by PriceChild on 2010-05-05
How did you install your graphics drivers? Using nvidia.com downloads or the menu in system > administration?

Could you post your Xorg.log?

---

### Post by cbbnewbie on 2010-05-05
using the hardware drivers in the administration menu

im a new linux user sorry, how do i chek Xorg.log??

---

### Post by PriceChild on 2010-05-05
Hmm then that is odd.

Could you post your Xorg.log please?

Its in /var/log

---

### Post by cbbnewbie on 2010-05-05
is this it sorry if I'm slow thanks for your patience


```
X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-25-server i686 Ubuntu
Current Operating System: Linux charlie-laptop 2.6.32-21-generic #32-Ubuntu SMP Fri Apr 16 08:10:02 UTC 2010 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-21-generic root=/dev/sda1 ro quiet splash
Build Date: 23 April 2010  05:11:50PM
xorg-server 2:1.7.6-2ubuntu7 (Bryce Harrington <bryce@ubuntu.com>) 
Current version of pixman: 0.16.4
    Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Wed May  5 20:30:16 2010
(==) Using config file: "/etc/X11/xorg.conf"
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"
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
(==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
(WW) AllowEmptyInput is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
(WW) Disabling Keyboard0
(WW) Disabling Mouse0
(II) Loader magic: 0x81f0e80
(II) Module ABI versions:
    X.Org ANSI C Emulation: 0.4
    X.Org Video Driver: 6.0
    X.Org XInput driver : 7.0
    X.Org Server Extension : 2.0
(++) using VT number 7

(--) PCI:*(0:1:0:0) 10de:0112:1028:00e6 nVidia Corporation NV11 [GeForce2 Go] rev 178, Mem @ 0xfc000000/16777216, 0xe0000000/134217728, BIOS @ 0x????????/65536
(II) Open ACPI successful (/var/run/acpid.socket)
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
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/extra-modules/libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
    compiled for 4.0.2, module version = 1.0.0
    Module class: X.Org Server Extension
(II) NVIDIA GLX Module  96.43.17  Thu Apr 15 05:52:20 PDT 2010
(II) Loading extension GLX
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
(II) NVIDIA dlloader X Driver  96.43.17  Thu Apr 15 05:35:23 PDT 2010
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 01@00:00:0
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "TwinView" "0"
(**) NVIDIA(0): Option "MetaModes" "CRT: 1024x768_60 +0+0"
(**) NVIDIA(0): Option "TwinViewXineramaInfoOrder" "CRT-0"
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(II) NVIDIA(0): NVIDIA GPU GeForce2 Go at PCI:1:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 16384 kBytes
(--) NVIDIA(0): VideoBIOS: 03.11.01.13.12
(II) NVIDIA(0): Detected AGP rate: 4X
(--) NVIDIA(0): Interlaced video modes are not supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce2 Go at PCI:1:0:0:
(--) NVIDIA(0):     AOC 5En (CRT-0)
(--) NVIDIA(0):     NVIDIA_SXGA (DFP-0)
(--) NVIDIA(0): AOC 5En (CRT-0): 350.0 MHz maximum pixel clock
(--) NVIDIA(0): NVIDIA_SXGA (DFP-0): 162.0 MHz maximum pixel clock
(--) NVIDIA(0): NVIDIA_SXGA (DFP-0): Internal Dual Link LVDS
(II) NVIDIA(0): Display Device found referenced in MetaMode: CRT-0
(II) NVIDIA(0): Assigned Display Device: CRT-0
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "CRT:1024x768_60+0+0"
(II) NVIDIA(0): Virtual screen size determined to be 1024 x 768
(--) NVIDIA(0): DPI set to (92, 92); computed from "UseEdidDpi" X config
(--) NVIDIA(0):     option
(--) Depth 24 pixmap format is 32 bpp
(II) NVIDIA(0): Initialized GART.
(II) NVIDIA(0): Setting mode "CRT:1024x768_60+0+0"
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(**) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
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
(II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
(II) config/udev: Adding input device Video Bus (/dev/input/event6)
(**) Video Bus: Applying InputClass "evdev keyboard catchall"
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 2.3.2
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 7.0
(**) Video Bus: always reports core events
(**) Video Bus: Device: "/dev/input/event6"
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
(II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event7)
(**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
(**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
(II) LoadModule: "synaptics"
(II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
(II) Module synaptics: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.2.2
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 7.0
(II) Synaptics touchpad driver version 1.2.2
(**) Option "Device" "/dev/input/event7"
(II) SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5472
(II) SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4448
(II) SynPS/2 Synaptics TouchPad: pressure range 0 - 255
(II) SynPS/2 Synaptics TouchPad: finger width range 0 - 0
(II) SynPS/2 Synaptics TouchPad: buttons: left right middle double triple
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
(II) config/udev: Adding input device TPPS/2 IBM TrackPoint (/dev/input/event8)
(**) TPPS/2 IBM TrackPoint: Applying InputClass "evdev pointer catchall"
(**) TPPS/2 IBM TrackPoint: always reports core events
(**) TPPS/2 IBM TrackPoint: Device: "/dev/input/event8"
(II) TPPS/2 IBM TrackPoint: Found 3 mouse buttons
(II) TPPS/2 IBM TrackPoint: Found relative axes
(II) TPPS/2 IBM TrackPoint: Found x and y relative axes
(II) TPPS/2 IBM TrackPoint: Configuring as mouse
(**) TPPS/2 IBM TrackPoint: YAxisMapping: buttons 4 and 5
(**) TPPS/2 IBM TrackPoint: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "TPPS/2 IBM TrackPoint" (type: MOUSE)
(II) TPPS/2 IBM TrackPoint: initialized for relative axes.
(II) config/udev: Adding input device TPPS/2 IBM TrackPoint (/dev/input/mouse3)
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
```

---

### Post by cbbnewbie on 2010-05-05
what should i do next??

---

### Post by PriceChild on 2010-05-05
Perfect, just what I wanted. And don't worry about being slow, this is a forum, you could post tomorrow and people would read the thread and continue trying to help :-)

I haven't messed much with desktop effects for a few years, but reading your xorg log I 'believe' that at least that side is all set up and working fine.

I don't think the issue is that something is broken... I'm think that the switch that needs to be flicked to turn compiz on, simply isn't!

Unfortunately I'm not sure how Lucid starts compiz so I'm going to have to defer until I get the chance to investigate, hoping someone else can bring that to the table before I find out myself.

---

### Post by cbbnewbie on 2010-05-05
i used this guide to install compiz

[http://www.hackourlives.com/?p=1922](http://www.hackourlives.com/?p=1922)

my compiz is turned on but the effects are not showing what odd is that when i go to appearance settings everytime i set the visual effects to normal it always goes back to none...

---

### Post by _0R10N on 2010-05-05
I went through a similar problem. In my case it was just compiz not starting a system startup. I solved that adding the following as startup application
```
/usr/bin/compiz --replace
```

I hope this helps!

Kind regards!

---

### Post by cbbnewbie on 2010-05-05
hmm nothing changed,, i think the main problem is in appearance settings i cant set the visual effect to normal it just show a tiny window saying searching for available drivers then flickers the windows and turn the settings back to none.. im completely clueless of what to do next..

or should i reinstall ubuntu instead,,??

---

### Post by cbbnewbie on 2010-05-05
i think i had fixed my problem for a moment,, what i did is in hardware drivers i removed my graphics driver and re enable it again after that it required me to restart after restarting i checked appearance settings i set visual effects to normal, it went to normal so i was happy i can again use compiz effects but then i tried to shutdown and upon restart again my problem occurred i can not set the visual effects to normal again it always goes back to none so now no effects again... is there a way to fix this now??? i dont think reinstalling my graphics driver every time i  turn on my laptop is the only solution, please anyone any other suggestions?? thanks

---

### Post by cbbnewbie on 2010-05-07
hmm i think nobody has any solutions atm,, well i made compiz work again and things stays as i left them before i shutdown as long as i dont touch the resolution settings at nvidia X server settings, i was not that happy though because my resolution is just 800x600 and its quite hard using firefox at this resolution... hope someday my problem would be solved thanks all for your time ^_^

---

