---
title: "USB touchscreen monitor MIMO UM-720s install/use?"
date: 2010-04-25
forum: New to Ubuntu
---

### Post by dragonneus on 2010-04-25
USB touchscreen monitor MIMO UM-720s install/use?

Hello,

Is there a way I can use this device on ubuntu? Ive found several links on the web but nothing comprehensive. NBR 9.10 does NOT have a xorg.conf file and attempting to auto create one fails. can anyone point me in the right direction? Has anyone successfully installed this device? Any help would be appreciated.

Thank you for your time,:)

Dragonneus

---

### Post by dragonneus on 2010-04-25
well made some headway..found this link

[http://www.pur3.co.uk/view.php?DisplayLink](http://www.pur3.co.uk/view.php?DisplayLink)

So far my screen will work with the command listed in the instructions, however its the wrong dimensions, still playing with it.

so far the text on the screen i shuge, wrong dimensions and touch does not work.

I will post my other findings, if anyone has somthing to add please do.

Dragonneus

---

### Post by dragonneus on 2010-04-26
Attempting to connect I recieve this 

dragonneus@DRAGON1:~$ sudo xinit firefox -- :1 -config /etc/X11/xorg_touch.conf -sharevts

X.Org X Server 1.6.4
Release Date: 2009-9-27
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux DRAGON1 2.6.31-20-generic #58-Ubuntu SMP Fri Mar 12 05:23:09 UTC 2010 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-20-generic root=UUID=c151cf61-da4f-4d7e-8570-e0dacdb9fa67 ro quiet splash
Build Date: 04 March 2010  09:56:47AM
xorg-server 2:1.6.4-2ubuntu4.2 (buildd@) 
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
(==) Log file: "/var/log/Xorg.1.log", Time: Mon Apr 26 09:38:20 2010
(++) Using config file: "/etc/X11/xorg_touch.conf"
(EE) Failed to load module "void" (module does not exist, 0)
(EE) Failed to load module "kbd" (module does not exist, 0)
(EE) Failed to load module "void" (module does not exist, 0)
(EE) No input driver matching `void'
State: S_UNTOUCHED	Action: No Action		Button: 0
State: S_TOUCHED	Action: No Action		Button: 0
State: S_LONGTOUCHED	Action: down		Button: 1
State: S_MOVING	Action: No Action		Button: 0
State: S_MAYBETAPPED	Action: click		Button: 1
State: S_ONEANDAHALFTAP	Action: down		Button: 3
(EE) Failed to load module "kbd" (module does not exist, 0)
(EE) No input driver matching `kbd'
(EE) config/hal: NewInputDeviceRequest failed (8)
(EE) config/hal: NewInputDeviceRequest failed (8)
(EE) config/hal: NewInputDeviceRequest failed (8)

---

### Post by dragonneus on 2010-04-26
Log file:

dragonneus@DRAGON1:/var/log$ cat Xorg.1.log

X.Org X Server 1.6.4
Release Date: 2009-9-27
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux DRAGON1 2.6.31-20-generic #58-Ubuntu SMP Fri Mar 12 05:23:09 UTC 2010 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-20-generic root=UUID=c151cf61-da4f-4d7e-8570-e0dacdb9fa67 ro quiet splash
Build Date: 04 March 2010  09:56:47AM
xorg-server 2:1.6.4-2ubuntu4.2 (buildd@) 
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.1.log", Time: Mon Apr 26 09:38:20 2010
(++) Using config file: "/etc/X11/xorg_touch.conf"
(==) ServerLayout "touchscreen"
 |-->Screen "DisplayLinkScreen" (0)
(**) |   |-->Monitor "DisplayLinkMonitor"
(**) |   |-->Device "DisplayLinkDevice"
(**) |-->Input Device "dummy"
(**) |-->Input Device "Touch0"
(**) Option "AllowEmptyInput" "False"
(**) Option "AutoAddDevices" "False"
(**) Not automatically adding devices
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
(**) ModulePath set to "/usr/lib/xorg/modules,/usr/local/lib/xorg/modules"
(==) |-->Input Device "<default keyboard>"
(==) The core keyboard device wasn't specified explicitly in the layout.
	Using the default keyboard configuration.
(II) Loader magic: 0x3bc0
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 5.0
	X.Org XInput driver : 4.0
	X.Org Server Extension : 2.0
(II) Loader running on linux
(--) using VT number 7

(--) PCI:*(0:0:2:0) 8086:27ae:1043:830f Intel Corporation Mobile 945GME Express Integrated Graphics Controller rev 3, Mem @ 0xf7f00000/524288, 0xd0000000/268435456, 0xf7ec0000/262144, I/O @ 0x0000dc80/8
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
(II) LoadModule: "displaylink"
(II) Loading /usr/lib/xorg/modules/drivers//displaylink_drv.so
(II) Module displaylink: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 0.0.1
	ABI class: X.Org Video Driver, version 5.0
(II) LoadModule: "void"
(WW) Warning, couldn't open module void
(II) UnloadModule: "void"
(EE) Failed to load module "void" (module does not exist, 0)
(II) LoadModule: "evtouch"
(II) Loading /usr/lib/xorg/modules/input//evtouch_drv.so
(II) Module evtouch: vendor="Kenan Esau"
	compiled for 1.6.4, module version = 0.8.8
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 4.0
(II) LoadModule: "kbd"
(WW) Warning, couldn't open module kbd
(II) UnloadModule: "kbd"
(EE) Failed to load module "kbd" (module does not exist, 0)
(II) DL: driver for : displaylink
(WW) Falling back to old probe method for displaylink
(II) Loading sub module "fbdevhw"
(II) LoadModule: "fbdevhw"
(II) Loading /usr/lib/xorg/modules/linux//libfbdevhw.so
(II) Module fbdevhw: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 0.0.2
	ABI class: X.Org Video Driver, version 5.0
(II) DL(0): using /dev/fb1
(II) resource ranges after probing:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) DL(0): Manufacturer: NAV  Model: 10  Serial#: 700
(II) DL(0): Year: 2008  Week: 30
(II) DL(0): EDID Version: 1.3
(II) DL(0): Digital Display Input
(II) DL(0): Max Image Size [cm]: horiz.: 8  vert.: 5
(II) DL(0): Gamma: 2.20
(II) DL(0): No DPMS capabilities specified
(II) DL(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) DL(0): First detailed timing is preferred mode
(II) DL(0): redX: 0.000 redY: 0.000   greenX: 0.000 greenY: 0.000
(II) DL(0): blueX: 0.000 blueY: 0.000   whiteX: 0.000 whiteY: 0.000
(II) DL(0): Manufacturer's mask: 0
(II) DL(0): Supported detailed timing:
(II) DL(0): clock: 33.0 MHz   Image Size:  152 x 91 mm
(II) DL(0): h_active: 800  h_sync: 840  h_sync_end 968 h_blank_end 1056 h_border: 0
(II) DL(0): v_active: 480  v_sync: 481  v_sync_end 484 v_blanking: 505 v_border: 0
(II) DL(0): Ranges: V min: 59 V max: 63 Hz, H min: 29 H max: 33 kHz, PixClock max 40 MHz
(II) DL(0): Monitor name: MIMO
(II) DL(0): Serial No: 7000832
(II) DL(0): EDID (in hex):
(II) DL(0): 	00ffffffffffff0038361000bc020000
(II) DL(0): 	1e120103800805780a00000000000000
(II) DL(0): 	00000000000001010101010101010101
(II) DL(0): 	010101010101e40c200031e019102880
(II) DL(0): 	1300985b00000018000000fd003b3f1d
(II) DL(0): 	2104000a202020202020000000fc004d
(II) DL(0): 	494d4f0a0a0a0a0a0a0a0a0a000000ff
(II) DL(0): 	00373030303833320a2020202020004f
(II) DL(0): Creating default Display subsection in Screen section
	"DisplayLinkScreen" for depth/fbbpp 16/16
(==) DL(0): Depth 16, (==) framebuffer bpp 16
(==) DL(0): RGB weight 565
(==) DL(0): Default visual is TrueColor
(==) DL(0): Using gamma correction (1.0, 1.0, 1.0)
(II) DL(0): hardware: mimo inc (video memory: 752kB)
(**) DL(0): Option "fbdev" "/dev/fb1"
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) DL(0): Output mimo inc using monitor section DisplayLinkMonitor
(II) DL(0): EDID vendor "NAV", prod id 16
(II) DL(0): Using EDID range info for horizontal sync
(II) DL(0): Using EDID range info for vertical refresh
(II) DL(0): Printing DDC gathered Modelines:
(II) DL(0): Modeline "800x480"x0.0   33.00  800 840 968 1056  480 481 484 505 -hsync -vsync (31.2 kHz)
(II) DL(0): EDID vendor "NAV", prod id 16
(II) DL(0): EDID for output mimo inc
(II) DL(0): Manufacturer: NAV  Model: 10  Serial#: 700
(II) DL(0): Year: 2008  Week: 30
(II) DL(0): EDID Version: 1.3
(II) DL(0): Digital Display Input
(II) DL(0): Max Image Size [cm]: horiz.: 8  vert.: 5
(II) DL(0): Gamma: 2.20
(II) DL(0): No DPMS capabilities specified
(II) DL(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) DL(0): First detailed timing is preferred mode
(II) DL(0): redX: 0.000 redY: 0.000   greenX: 0.000 greenY: 0.000
(II) DL(0): blueX: 0.000 blueY: 0.000   whiteX: 0.000 whiteY: 0.000
(II) DL(0): Manufacturer's mask: 0
(II) DL(0): Supported detailed timing:
(II) DL(0): clock: 33.0 MHz   Image Size:  152 x 91 mm
(II) DL(0): h_active: 800  h_sync: 840  h_sync_end 968 h_blank_end 1056 h_border: 0
(II) DL(0): v_active: 480  v_sync: 481  v_sync_end 484 v_blanking: 505 v_border: 0
(II) DL(0): Ranges: V min: 59 V max: 63 Hz, H min: 29 H max: 33 kHz, PixClock max 40 MHz
(II) DL(0): Monitor name: MIMO
(II) DL(0): Serial No: 7000832
(II) DL(0): EDID (in hex):
(II) DL(0): 	00ffffffffffff0038361000bc020000
(II) DL(0): 	1e120103800805780a00000000000000
(II) DL(0): 	00000000000001010101010101010101
(II) DL(0): 	010101010101e40c200031e019102880
(II) DL(0): 	1300985b00000018000000fd003b3f1d
(II) DL(0): 	2104000a202020202020000000fc004d
(II) DL(0): 	494d4f0a0a0a0a0a0a0a0a0a000000ff
(II) DL(0): 	00373030303833320a2020202020004f
(II) DL(0): EDID vendor "NAV", prod id 16
(II) DL(0): Using hsync ranges from config file
(II) DL(0): Using vrefresh ranges from config file
(II) DL(0): Printing DDC gathered Modelines:
(II) DL(0): Modeline "800x480"x0.0   33.00  800 840 968 1056  480 481 484 505 -hsync -vsync (31.2 kHz)
(II) DL(0): EDID vendor "NAV", prod id 16
(II) DL(0): Printing probed modes for output mimo inc
(II) DL(0): Modeline "800x480"x61.9   33.00  800 840 968 1056  480 481 484 505 -hsync -vsync (31.2 kHz)
(II) DL(0): Output mimo inc connected
(II) DL(0): Using exact sizes for initial modes
(II) DL(0): Output mimo inc using initial mode 800x480
(--) DL(0): Virtual size is 800x480 (pitch 0)
(**) DL(0):  Driver mode "800x480": 33.0 MHz (scaled from 0.0 MHz), 31.2 kHz, 61.9 Hz
(II) DL(0): Modeline "800x480"x61.9   33.00  800 840 968 1056  480 481 484 505 -hsync -vsync (31.2 kHz)
(**) DL(0): Display dimensions: (80, 50) mm
(**) DL(0): DPI set to (253, 243)
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(==) DL(0): Backing store disabled
(II) DL(0): DPMS enabled
(II) DL(0): RandR 1.2 enabled, ignore the following RandR disabled message.
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
(II) AIGLX: Screen 0 is not DRI2 capable
(II) AIGLX: Screen 0 is not DRI capable
(II) AIGLX: Loaded and initialized /usr/lib/dri/swrast_dri.so
(II) GLX: Initialized DRISWRAST GL provider for screen 0
(II) LoadModule: "void"
(WW) Warning, couldn't open module void
(II) UnloadModule: "void"
(EE) Failed to load module "void" (module does not exist, 0)
(EE) No input driver matching `void'
State: S_UNTOUCHED	Action: No Action		Button: 0
State: S_TOUCHED	Action: No Action		Button: 0
State: S_LONGTOUCHED	Action: down		Button: 1
State: S_MOVING	Action: No Action		Button: 0
State: S_MAYBETAPPED	Action: click		Button: 1
State: S_ONEANDAHALFTAP	Action: down		Button: 3
(**) Option "MinX" "630"
(**) Option "MaxX" "31700"
(**) Option "MinY" "31000"
(**) Option "MaxY" "1000"
(**) Option "MoveLimit" "600"
(**) Option "DeviceName" "touchscreen"
(**) Option "CorePointer"
(**) touchscreen: always reports core events
(II) XINPUT: Adding extended input device "touchscreen" (type: TOUCHSCREEN)
(**) touchscreen: (accel) keeping acceleration scheme 1
(**) touchscreen: (accel) filter chain progression: 2.00
(**) touchscreen: (accel) filter stage 0: 20.00 ms
(**) touchscreen: (accel) set acceleration profile 0
(**) Option "Device" "/dev/input/by-id/usb-Chicony_Electronics_Co.__Ltd._CNF7129_SN0001-event-if00"
(II) LoadModule: "kbd"
(WW) Warning, couldn't open module kbd
(II) UnloadModule: "kbd"
(EE) Failed to load module "kbd" (module does not exist, 0)
(EE) No input driver matching `kbd'
(II) config/hal: Adding input device Power Button
(EE) config/hal: NewInputDeviceRequest failed (8)
(II) config/hal: Adding input device AT Translated Set 2 keyboard
(EE) config/hal: NewInputDeviceRequest failed (8)
(II) config/hal: Adding input device CNF7129
(EE) config/hal: NewInputDeviceRequest failed (8)
(II) config/hal: Adding input device Sleep Button
(EE) config/hal: NewInputDeviceRequest failed (8)
(II) config/hal: Adding input device Video Bus
(EE) config/hal: NewInputDeviceRequest failed (8)
(II) config/hal: Adding input device Power Button
(EE) config/hal: NewInputDeviceRequest failed (8)
(II) config/hal: Adding input device Asus EeePC extra buttons
(EE) config/hal: NewInputDeviceRequest failed (8)
(II) config/hal: Adding input device ETPS/2 Elantech Touchpad
(EE) config/hal: NewInputDeviceRequest failed (8)
(II) config/hal: Adding input device Macintosh mouse button emulation
(EE) config/hal: NewInputDeviceRequest failed 
(II) UnloadModule: "evtouch"
 ddxSigGiveUp: Closing log
dragonneus@DRAGON1:/var/log$

---

### Post by mcoleman44 on 2010-04-26
Even if there isnt an xorg.conf you can still make one and X will use it. 
You can edit it with this command. 
```
gksudo gedit /etc/X11/xorg.conf
```

---

