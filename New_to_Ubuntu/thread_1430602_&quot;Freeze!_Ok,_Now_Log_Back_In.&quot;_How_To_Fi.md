---
title: "&quot;Freeze! Ok, Now Log Back In.&quot; How To Find The Cause?"
date: 2010-03-15
forum: New to Ubuntu
---

### Post by Michael Kaiser on 2010-03-15
After a fresh re-install of 9.10 - thanks to the help of The Real Dave - I have a new issue (or two) that I need help with:

Every so often my computer freezes. I get no response from cursor, keyboard or mouse and have to do a hard shut-down.

Too, even more often, Ubuntu blacks out and takes me to the login screen where I have to punch in my password and restart what I was doing.

The question, besides the obvious "Why?!", is, how do I go about finding out what the problem is?

Keep in mind that this thread is in the "ABSOLUTE Beginner" thread, and treat me accordingly, please. :)

---

### Post by mcoleman44 on 2010-03-15
You could take a look at your xorg.0.log file.
system>admin>log file viewer>xorg.0.log. 
Look for EE.

Or better yet just post it.

---

### Post by Michael Kaiser on 2010-03-15
> **mcoleman44 said:**
> 

Or better yet just post it.

This one?

```

X.Org X Server 1.6.4
Release Date: 2009-9-27
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux hanfam-desktop 2.6.31-20-generic-pae #57-Ubuntu SMP Mon Feb 8 10:23:59 UTC 2010 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-20-generic-pae root=UUID=37e75716-810f-4396-8331-034e850af190 ro quiet splash
Build Date: 14 November 2009  05:48:26PM
xorg-server 2:1.6.4-2ubuntu4.1 (buildd@) 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Mon Mar 15 14:18:21 2010
(II) Loader magic: 0x3bc0
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 5.0
	X.Org XInput driver : 4.0
	X.Org Server Extension : 2.0
(II) Loader running on linux
(++) using VT number 7

(--) PCI:*(0:0:2:0) 8086:2582:103c:2a08 Intel Corporation 82915G/GV/910GL Integrated Graphics Controller rev 4, Mem @ 0xcfe00000/524288, 0xd0000000/268435456, 0xcfdc0000/262144, I/O @ 0x0000cc00/8
(==) Using default built-in configuration (39 lines)
(==) --- Start of built-in configuration ---
	Section "Device"
		Identifier	"Builtin Default intel Device 0"
		Driver	"intel"
	EndSection
	Section "Screen"
		Identifier	"Builtin Default intel Screen 0"
		Device	"Builtin Default intel Device 0"
	EndSection
	Section "Device"
		Identifier	"Builtin Default i810 Device 0"
		Driver	"i810"
	EndSection
	Section "Screen"
		Identifier	"Builtin Default i810 Screen 0"
		Device	"Builtin Default i810 Device 0"
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
		Screen	"Builtin Default intel Screen 0"
		Screen	"Builtin Default i810 Screen 0"
		Screen	"Builtin Default vesa Screen 0"
		Screen	"Builtin Default fbdev Screen 0"
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
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
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
(II) intel(0): Integrated Graphics Chipset: Intel(R) 915G
(--) intel(0): Chipset: "915G"
(II) intel(0): Output VGA1 has no monitor section
(II) intel(0): EDID for output VGA1
(II) intel(0): Manufacturer: HWP  Model: 2616  Serial#: 16843009
(II) intel(0): Year: 2004  Week: 24
(II) intel(0): EDID Version: 1.3
(II) intel(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) intel(0): Sync:  Separate
(II) intel(0): Max Image Size [cm]: horiz.: 32  vert.: 24
(II) intel(0): Gamma: 2.80
(II) intel(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) intel(0): First detailed timing is preferred mode
(II) intel(0): redX: 0.652 redY: 0.321   greenX: 0.281 greenY: 0.616
(II) intel(0): blueX: 0.141 blueY: 0.057   whiteX: 0.283 whiteY: 0.298
(II) intel(0): Supported established timings:
(II) intel(0): 720x400@70Hz
(II) intel(0): 640x480@60Hz
(II) intel(0): 640x480@75Hz
(II) intel(0): 800x600@75Hz
(II) intel(0): 1024x768@75Hz
(II) intel(0): Manufacturer's mask: 0
(II) intel(0): Supported standard timings:
(II) intel(0): #0: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) intel(0): #1: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) intel(0): #2: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) intel(0): #3: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) intel(0): Supported detailed timing:
(II) intel(0): clock: 94.5 MHz   Image Size:  312 x 234 mm
(II) intel(0): h_active: 1024  h_sync: 1072  h_sync_end 1168 h_blank_end 1376 h_border: 0
(II) intel(0): v_active: 768  v_sync: 769  v_sync_end 772 v_blanking: 808 v_border: 0
(II) intel(0): Ranges: V min: 50 V max: 140 Hz, H min: 30 H max: 70 kHz, PixClock max 110 MHz
(II) intel(0): Monitor name: hp v72
(II) intel(0): Serial No: CNQ42400BW
(II) intel(0): EDID (in hex):
(II) intel(0): 	00ffffffffffff0022f0162601010101
(II) intel(0): 	180e0103682018b4ea1329a752489d24
(II) intel(0): 	0e484ca4420031594559615981800101
(II) intel(0): 	010101010101ea240060410028303060
(II) intel(0): 	130038ea1000001e000000fd00328c1e
(II) intel(0): 	460b000a202020202020000000fc0068
(II) intel(0): 	70207637320a202020202020000000ff
(II) intel(0): 	00434e51343234303042570a20200052
(II) intel(0): EDID vendor "HWP", prod id 9750
(II) intel(0): Using EDID range info for horizontal sync
(II) intel(0): Using EDID range info for vertical refresh
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1024x768"x0.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(0): Modeline "640x480"x0.0   36.00  640 696 752 832  480 481 484 509 -hsync -vsync (43.3 kHz)
(II) intel(0): Modeline "800x600"x0.0   56.25  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
(II) intel(0): Modeline "1024x768"x0.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
(II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) intel(0): Printing probed modes for output VGA1
(II) intel(0): Modeline "1024x768"x85.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
(II) intel(0): Modeline "1024x768"x75.1   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) intel(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) intel(0): Output VGA1 connected
(II) intel(0): Using exact sizes for initial modes
(II) intel(0): Output VGA1 using initial mode 1024x768
(==) intel(0): video overlay key set to 0x101fe
(==) intel(0): Using gamma correction (1.0, 1.0, 1.0)
(**) intel(0): Display dimensions: (320, 240) mm
(**) intel(0): DPI set to (81, 81)
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
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
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
(II) AIGLX: Loaded and initialized /usr/lib/dri/i915_dri.so
(II) GLX: Initialized DRI2 GL provider for screen 0
(II) intel(0): Setting screen physical size to 312 x 234
(II) config/hal: Adding input device AT Translated Set 2 keyboard
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 2.2.5
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 4.0
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event3"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/hal: Adding input device ImExPS/2 Logitech Explorer Mouse
(**) ImExPS/2 Logitech Explorer Mouse: always reports core events
(**) ImExPS/2 Logitech Explorer Mouse: Device: "/dev/input/event4"
(II) ImExPS/2 Logitech Explorer Mouse: Found 9 mouse buttons
(II) ImExPS/2 Logitech Explorer Mouse: Found x and y relative axes
(II) ImExPS/2 Logitech Explorer Mouse: Found scroll wheel(s)
(II) ImExPS/2 Logitech Explorer Mouse: Configuring as mouse
(**) ImExPS/2 Logitech Explorer Mouse: YAxisMapping: buttons 4 and 5
(**) ImExPS/2 Logitech Explorer Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "ImExPS/2 Logitech Explorer Mouse" (type: MOUSE)
(**) ImExPS/2 Logitech Explorer Mouse: (accel) keeping acceleration scheme 1
(**) ImExPS/2 Logitech Explorer Mouse: (accel) filter chain progression: 2.00
(**) ImExPS/2 Logitech Explorer Mouse: (accel) filter stage 0: 20.00 ms
(**) ImExPS/2 Logitech Explorer Mouse: (accel) set acceleration profile 0
(II) ImExPS/2 Logitech Explorer Mouse: initialized for relative axes.
(II) config/hal: Adding input device Power Button
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event1"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/hal: Adding input device Power Button
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event0"
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
(II) intel(0): EDID for output VGA1
(II) intel(0): Manufacturer: HWP  Model: 2616  Serial#: 16843009
(II) intel(0): Year: 2004  Week: 24
(II) intel(0): EDID Version: 1.3
(II) intel(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) intel(0): Sync:  Separate
(II) intel(0): Max Image Size [cm]: horiz.: 32  vert.: 24
(II) intel(0): Gamma: 2.80
(II) intel(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) intel(0): First detailed timing is preferred mode
(II) intel(0): redX: 0.652 redY: 0.321   greenX: 0.281 greenY: 0.616
(II) intel(0): blueX: 0.141 blueY: 0.057   whiteX: 0.283 whiteY: 0.298
(II) intel(0): Supported established timings:
(II) intel(0): 720x400@70Hz
(II) intel(0): 640x480@60Hz
(II) intel(0): 640x480@75Hz
(II) intel(0): 800x600@75Hz
(II) intel(0): 1024x768@75Hz
(II) intel(0): Manufacturer's mask: 0
(II) intel(0): Supported standard timings:
(II) intel(0): #0: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) intel(0): #1: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) intel(0): #2: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) intel(0): #3: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) intel(0): Supported detailed timing:
(II) intel(0): clock: 94.5 MHz   Image Size:  312 x 234 mm
(II) intel(0): h_active: 1024  h_sync: 1072  h_sync_end 1168 h_blank_end 1376 h_border: 0
(II) intel(0): v_active: 768  v_sync: 769  v_sync_end 772 v_blanking: 808 v_border: 0
(II) intel(0): Ranges: V min: 50 V max: 140 Hz, H min: 30 H max: 70 kHz, PixClock max 110 MHz
(II) intel(0): Monitor name: hp v72
(II) intel(0): Serial No: CNQ42400BW
(II) intel(0): EDID (in hex):
(II) intel(0): 	00ffffffffffff0022f0162601010101
(II) intel(0): 	180e0103682018b4ea1329a752489d24
(II) intel(0): 	0e484ca4420031594559615981800101
(II) intel(0): 	010101010101ea240060410028303060
(II) intel(0): 	130038ea1000001e000000fd00328c1e
(II) intel(0): 	460b000a202020202020000000fc0068
(II) intel(0): 	70207637320a202020202020000000ff
(II) intel(0): 	00434e51343234303042570a20200052
(II) intel(0): EDID vendor "HWP", prod id 9750
(II) intel(0): Using hsync ranges from config file
(II) intel(0): Using vrefresh ranges from config file
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1024x768"x0.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(0): Modeline "640x480"x0.0   36.00  640 696 752 832  480 481 484 509 -hsync -vsync (43.3 kHz)
(II) intel(0): Modeline "800x600"x0.0   56.25  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
(II) intel(0): Modeline "1024x768"x0.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
(II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) intel(0): Printing probed modes for output VGA1
(II) intel(0): Modeline "1024x768"x85.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
(II) intel(0): Modeline "1024x768"x75.1   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) intel(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) intel(0): EDID for output VGA1
(II) intel(0): Manufacturer: HWP  Model: 2616  Serial#: 16843009
(II) intel(0): Year: 2004  Week: 24
(II) intel(0): EDID Version: 1.3
(II) intel(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) intel(0): Sync:  Separate
(II) intel(0): Max Image Size [cm]: horiz.: 32  vert.: 24
(II) intel(0): Gamma: 2.80
(II) intel(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) intel(0): First detailed timing is preferred mode
(II) intel(0): redX: 0.652 redY: 0.321   greenX: 0.281 greenY: 0.616
(II) intel(0): blueX: 0.141 blueY: 0.057   whiteX: 0.283 whiteY: 0.298
(II) intel(0): Supported established timings:
(II) intel(0): 720x400@70Hz
(II) intel(0): 640x480@60Hz
(II) intel(0): 640x480@75Hz
(II) intel(0): 800x600@75Hz
(II) intel(0): 1024x768@75Hz
(II) intel(0): Manufacturer's mask: 0
(II) intel(0): Supported standard timings:
(II) intel(0): #0: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) intel(0): #1: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) intel(0): #2: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) intel(0): #3: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) intel(0): Supported detailed timing:
(II) intel(0): clock: 94.5 MHz   Image Size:  312 x 234 mm
(II) intel(0): h_active: 1024  h_sync: 1072  h_sync_end 1168 h_blank_end 1376 h_border: 0
(II) intel(0): v_active: 768  v_sync: 769  v_sync_end 772 v_blanking: 808 v_border: 0
(II) intel(0): Ranges: V min: 50 V max: 140 Hz, H min: 30 H max: 70 kHz, PixClock max 110 MHz
(II) intel(0): Monitor name: hp v72
(II) intel(0): Serial No: CNQ42400BW
(II) intel(0): EDID (in hex):
(II) intel(0): 	00ffffffffffff0022f0162601010101
(II) intel(0): 	180e0103682018b4ea1329a752489d24
(II) intel(0): 	0e484ca4420031594559615981800101
(II) intel(0): 	010101010101ea240060410028303060
(II) intel(0): 	130038ea1000001e000000fd00328c1e
(II) intel(0): 	460b000a202020202020000000fc0068
(II) intel(0): 	70207637320a202020202020000000ff
(II) intel(0): 	00434e51343234303042570a20200052
(II) intel(0): EDID vendor "HWP", prod id 9750
(II) intel(0): Using hsync ranges from config file
(II) intel(0): Using vrefresh ranges from config file
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1024x768"x0.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(0): Modeline "640x480"x0.0   36.00  640 696 752 832  480 481 484 509 -hsync -vsync (43.3 kHz)
(II) intel(0): Modeline "800x600"x0.0   56.25  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
(II) intel(0): Modeline "1024x768"x0.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
(II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) intel(0): Printing probed modes for output VGA1
(II) intel(0): Modeline "1024x768"x85.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
(II) intel(0): Modeline "1024x768"x75.1   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) intel(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) intel(0): EDID for output VGA1
(II) intel(0): Manufacturer: HWP  Model: 2616  Serial#: 16843009
(II) intel(0): Year: 2004  Week: 24
(II) intel(0): EDID Version: 1.3
(II) intel(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) intel(0): Sync:  Separate
(II) intel(0): Max Image Size [cm]: horiz.: 32  vert.: 24
(II) intel(0): Gamma: 2.80
(II) intel(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) intel(0): First detailed timing is preferred mode
(II) intel(0): redX: 0.652 redY: 0.321   greenX: 0.281 greenY: 0.616
(II) intel(0): blueX: 0.141 blueY: 0.057   whiteX: 0.283 whiteY: 0.298
(II) intel(0): Supported established timings:
(II) intel(0): 720x400@70Hz
(II) intel(0): 640x480@60Hz
(II) intel(0): 640x480@75Hz
(II) intel(0): 800x600@75Hz
(II) intel(0): 1024x768@75Hz
(II) intel(0): Manufacturer's mask: 0
(II) intel(0): Supported standard timings:
(II) intel(0): #0: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) intel(0): #1: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) intel(0): #2: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) intel(0): #3: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) intel(0): Supported detailed timing:
(II) intel(0): clock: 94.5 MHz   Image Size:  312 x 234 mm
(II) intel(0): h_active: 1024  h_sync: 1072  h_sync_end 1168 h_blank_end 1376 h_border: 0
(II) intel(0): v_active: 768  v_sync: 769  v_sync_end 772 v_blanking: 808 v_border: 0
(II) intel(0): Ranges: V min: 50 V max: 140 Hz, H min: 30 H max: 70 kHz, PixClock max 110 MHz
(II) intel(0): Monitor name: hp v72
(II) intel(0): Serial No: CNQ42400BW
(II) intel(0): EDID (in hex):
(II) intel(0): 	00ffffffffffff0022f0162601010101
(II) intel(0): 	180e0103682018b4ea1329a752489d24
(II) intel(0): 	0e484ca4420031594559615981800101
(II) intel(0): 	010101010101ea240060410028303060
(II) intel(0): 	130038ea1000001e000000fd00328c1e
(II) intel(0): 	460b000a202020202020000000fc0068
(II) intel(0): 	70207637320a202020202020000000ff
(II) intel(0): 	00434e51343234303042570a20200052
(II) intel(0): EDID vendor "HWP", prod id 9750
(II) intel(0): Using hsync ranges from config file
(II) intel(0): Using vrefresh ranges from config file
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1024x768"x0.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(0): Modeline "640x480"x0.0   36.00  640 696 752 832  480 481 484 509 -hsync -vsync (43.3 kHz)
(II) intel(0): Modeline "800x600"x0.0   56.25  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
(II) intel(0): Modeline "1024x768"x0.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
(II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) intel(0): Printing probed modes for output VGA1
(II) intel(0): Modeline "1024x768"x85.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
(II) intel(0): Modeline "1024x768"x75.1   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) intel(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) intel(0): EDID for output VGA1
(II) intel(0): Manufacturer: HWP  Model: 2616  Serial#: 16843009
(II) intel(0): Year: 2004  Week: 24
(II) intel(0): EDID Version: 1.3
(II) intel(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) intel(0): Sync:  Separate
(II) intel(0): Max Image Size [cm]: horiz.: 32  vert.: 24
(II) intel(0): Gamma: 2.80
(II) intel(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) intel(0): First detailed timing is preferred mode
(II) intel(0): redX: 0.652 redY: 0.321   greenX: 0.281 greenY: 0.616
(II) intel(0): blueX: 0.141 blueY: 0.057   whiteX: 0.283 whiteY: 0.298
(II) intel(0): Supported established timings:
(II) intel(0): 720x400@70Hz
(II) intel(0): 640x480@60Hz
(II) intel(0): 640x480@75Hz
(II) intel(0): 800x600@75Hz
(II) intel(0): 1024x768@75Hz
(II) intel(0): Manufacturer's mask: 0
(II) intel(0): Supported standard timings:
(II) intel(0): #0: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) intel(0): #1: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) intel(0): #2: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) intel(0): #3: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) intel(0): Supported detailed timing:
(II) intel(0): clock: 94.5 MHz   Image Size:  312 x 234 mm
(II) intel(0): h_active: 1024  h_sync: 1072  h_sync_end 1168 h_blank_end 1376 h_border: 0
(II) intel(0): v_active: 768  v_sync: 769  v_sync_end 772 v_blanking: 808 v_border: 0
(II) intel(0): Ranges: V min: 50 V max: 140 Hz, H min: 30 H max: 70 kHz, PixClock max 110 MHz
(II) intel(0): Monitor name: hp v72
(II) intel(0): Serial No: CNQ42400BW
(II) intel(0): EDID (in hex):
(II) intel(0): 	00ffffffffffff0022f0162601010101
(II) intel(0): 	180e0103682018b4ea1329a752489d24
(II) intel(0): 	0e484ca4420031594559615981800101
(II) intel(0): 	010101010101ea240060410028303060
(II) intel(0): 	130038ea1000001e000000fd00328c1e
(II) intel(0): 	460b000a202020202020000000fc0068
(II) intel(0): 	70207637320a202020202020000000ff
(II) intel(0): 	00434e51343234303042570a20200052
(II) intel(0): EDID vendor "HWP", prod id 9750
(II) intel(0): Using hsync ranges from config file
(II) intel(0): Using vrefresh ranges from config file
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1024x768"x0.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(0): Modeline "640x480"x0.0   36.00  640 696 752 832  480 481 484 509 -hsync -vsync (43.3 kHz)
(II) intel(0): Modeline "800x600"x0.0   56.25  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
(II) intel(0): Modeline "1024x768"x0.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
(II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) intel(0): Printing probed modes for output VGA1
(II) intel(0): Modeline "1024x768"x85.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
(II) intel(0): Modeline "1024x768"x75.1   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) intel(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)

```

---

### Post by mcoleman44 on 2010-03-15
Yeah, thats the one, but I dont see anything that interesting in it. Have you installed all the updates? 

Open a terminal and type 
uname -r
If you get anything below 2.6.31-20 then try this:
sudo apt-get update
sudo apt-get upgrade

---

### Post by Michael Kaiser on 2010-03-15
> **mcoleman44 said:**
> Yeah, thats the one, but I dont see anything that interesting in it. Have you installed all the updates? 

Open a terminal and type 
uname -r
If you get anything below 2.6.31-20 then try this:
sudo apt-get update
sudo apt-get upgrade

I'm all up to date.

---

### Post by mcoleman44 on 2010-03-15
Ok, so are you still getting the same problem? If you are, do you have any symptoms before the blackout?

---

### Post by Michael Kaiser on 2010-03-15
> **mcoleman44 said:**
> Ok, so are you still getting the same problem? If you are, do you have any symptoms before the blackout?

Yes. Haven't been taken to the login screen in about an hour, but I just had to do a hard start due to freezing.

---

### Post by mcoleman44 on 2010-03-15
So are you saying you cant login to your desktop? Just describe everything that happens before it shuts down or freezes. And what type of video driver do you have?

---

### Post by Michael Kaiser on 2010-03-15
> **mcoleman44 said:**
> So are you saying you cant login to your desktop? Just describe everything that happens before it shuts down or freezes. And what type of video driver do you have?

In a nut shell: I'm using the computer in any capacity, then out of the blue - with no noises, smoke, nefarious laughter, or anything - it flat-out stops reponding in any way whatsoever, with the exception that my Caps Lock and Scroll Lock lights on my keyboard flash in unison at a steady beat (probably 120 bpm). This screen still looks beautiful, but nobody answers the door.

As far as video drivers? I run an integrated intel graphics. How would I check in Ubuntu?

---

### Post by mcoleman44 on 2010-03-15
To be honest Im not sure how to fix this, I had this same problem a while back but updating my kernel fixed the issue. 

Go to system>admin>hardwar drivers and see if there are any proprietary drivers listed. If there is a video driver install it  and restart.

Do me another favor: 
open a terminal and type:
top

Then post the results. Reason being, someone had this same thing happen to them and its because there CPU usage was randomly jumping to 100% and freezing.

---

### Post by Michael Kaiser on 2010-03-15
> **mcoleman44 said:**
> To be honest Im not sure how to fix this, I had this same problem a while back but updating my kernel fixed the issue. 

Go to system>admin>hardwar drivers and see if there are any proprietary drivers listed. If there is a video driver install it  and restart.

It said that there were no proprietary drivers in use.

> Do me another favor: 
open a terminal and type:
top

Then post the results. Reason being, someone had this same thing happen to them and its because there CPU usage was randomly jumping to 100% and freezing.

The info in constantly changing. Will that effect what you want to see?

---

### Post by mcoleman44 on 2010-03-15
You dont have to post it.
Is the CPU jumping randomly by any chance?

---

### Post by mcoleman44 on 2010-03-15
Ok, See if this helps.
```
sudo apt-get install xserver-xorg-video-intel
```Post the output please.

---

### Post by waynefoutz on 2010-03-15
> **Michael Kaiser said:**
> In a nut shell: I'm using the computer in any capacity, then out of the blue - with no noises, smoke, nefarious laughter, or anything - it flat-out stops reponding in any way whatsoever, with the exception that my Caps Lock and Scroll Lock lights on my keyboard flash in unison at a steady beat (probably 120 bpm). This screen still looks beautiful, but nobody answers the door.

As far as video drivers? I run an integrated intel graphics. How would I check in Ubuntu?

That's a kernel panic. 
try this guide:

[http://rhcelinuxguide.wordpress.com/2006/06/01/linux-kernel-panic-prevent-cardiac-arrest/]("http://rhcelinuxguide.wordpress.com/2006/06/01/linux-kernel-panic-prevent-cardiac-arrest/")

---

### Post by mcoleman44 on 2010-03-15
Well..... Didnt think about a kernel panic. Sorry.

---

### Post by Michael Kaiser on 2010-03-15
> **waynefoutz said:**
> That's a kernel panic. 
try this guide:

[http://rhcelinuxguide.wordpress.com/2006/06/01/linux-kernel-panic-prevent-cardiac-arrest/]("http://rhcelinuxguide.wordpress.com/2006/06/01/linux-kernel-panic-prevent-cardiac-arrest/")

Gadzooks! That article is making me woozie. It looks like my system is falling under the "Hard Panic", but I'm not sure what to do with all that info.

---

