---
title: "Resolution problems with my widescreen monitor (please help, you will be rewarded!)"
date: 2010-03-11
forum: New to Ubuntu
---

### Post by mystik_spiral on 2010-03-11
This is a continuation from [http://ubuntuforums.org/showthread.php?t=1426013](http://ubuntuforums.org/showthread.php?t=1426013) . I figure I would get more attention with a brand new thread. halitech was extremely helpful in my previous thread in figuring out my first problem but now I need *the rest of you* to try put your minds together and figure this out for me!

I am using a Samsung SyncMaster 2343BWX, 2048x1152. Here are the specifics:

[http://www.samsung.com/hk_en/consumer/computer-peripherals/monitors/giant-series/LS23MYZAFV/XSH/index.idx?pagetype=prd_detail&tab=spec&fullspec=F](http://www.samsung.com/hk_en/consumer/computer-peripherals/monitors/giant-series/LS23MYZAFV/XSH/index.idx?pagetype=prd_detail&tab=spec&fullspec=F)

I have an Intel chipset for the onboard video (VGA Compatible Controller: Intel Corporation 82865G Integrated Graphics Controller).

Here's the information that I have input in the gksudo gedit:

>                                   Section "Monitor"  
 Identifier "Monitor0"  
 VendorName "SAMSUNG"  
 ModelName "SyncMaster 2343BWX" 
 HorizSync 30 - 60  
 VertRefresh 55 - 75  
 Modeline "2048x1152@0" 0.00 2048 2080 2080 2112 1152 1181 1181 1210  
 EndSection  
 

 Section "Device"  
 Identifier "Device0"  
 Driver "intel"  
 VendorName "Intel 82865G"  
 EndSection  
 

 Section "Screen"  
 Identifier "Screen0"  
 Device "Device0"  
 Monitor "Monitor0"  
 DefaultDepth 24  
 SubSection "Display"  
 Depth 24  
 Modes "2048x1152" "1600x1200" "1024x768"  
 EndSubSection  
 EndSection  
 So far this has not helped me. According to this Modeline Generator, [http://xtiming.sourceforge.net/cgi-bin/xtiming.pl](http://xtiming.sourceforge.net/cgi-bin/xtiming.pl) , that should be the correct modeline that I am using in the code. 

In summary, everything is still too enlarged (zoomed in) for me and the screen actually doesn't stretch out all the way to the right side (nearly 2 inches of black showing). If anyone has any ideas me, then that would be terrific.

thanks

---

### Post by coffeecat on 2010-03-11
I may be wrong, but I have one thought.

> **mystik_spiral said:**
> I am using a Samsung SyncMaster 2343BWX, 2048x1152.

That is a 16x9 high-resolution format which is very recent. Don't forget that only about a year ago, most widescreen monitors were 16x10.

> **mystik_spiral said:**
> I have an Intel chipset for the onboard video (VGA Compatible Controller: Intel Corporation 82865G Integrated Graphics Controller).

That is an old chipset. I think it was before the days of even 16x10 widescreens. Even with the latest intel driver I would be surprised if it was capable of driving 2048x1152, or any widescreen resolution for that matter. I would guess you are getting 1280x1024, a 4x3 resolution at the moment - hence the black line at the side - and that could be as much as you'll get out of that chipset.

But I may be wrong. Let's see what others say.

---

### Post by mystik_spiral on 2010-03-11
> **coffeecat said:**
> I may be wrong, but I have one thought.



That is a 16x9 high-resolution format which is very recent. Don't forget that only about a year ago, most widescreen monitors were 16x10.



That is an old chipset. I think it was before the days of even 16x10 widescreens. Even with the latest intel driver I would be surprised if it was capable of driving 2048x1152, or any widescreen resolution for that matter. I would guess you are getting 1280x1024, a 4x3 resolution at the moment - hence the black line at the side - and that could be as much as you'll get out of that chipset.

But I may be wrong. Let's see what others say.
Thanks coffeecat. I should add that I've used this monitor for Windows and the resolution works perfectly. That's probably because in the graphics options section, I can actually select "2048x1152". In Nubuntu under Preferences > Display, the highest I can select is "1024x768" (4:3).

---

### Post by patchwork on 2010-03-11
Type in ```
cvt 2048 1152
``` in the terminal, and copy the modeline into your modeline in your xorg.conf.   The pixel clock in your current line can't be right...

Also,after making the change and restarting the x server,  can you post your /var/log/Xorg.0.log?

EDIT: also the "2048x1152" in your mode section must match the modeline name....one has @, one does not

---

### Post by shazbut on 2010-03-11
Have you tried the cvt/xrandr method described [here]("https://wiki.ubuntu.com/X/Config/Resolution") and [here]("http://www.ubuntugeek.com/how-change-display-resolution-settings-using-xrandr.html")?

I was of the understanding the whole xorg.conf setup was soon to go the way of the dodo.  Speaking of which, it's about time analogue VGA died a horrible death too, and most of these problems would disappear with it.

---

### Post by mystik_spiral on 2010-03-11
thanks...

here's the new modeline that I copy/pasted into xorg.conf

>                                   Modeline "2048x1152_60.00"  197.00  2048 2184 2400 2752  1152 1155 1160 1195 -hsync +vsyn
 And here's the /var/log/Xorg.0.log that you wanted:

> 
X.Org X Server 1.6.4
Release Date: 2009-9-27
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux beckie-desktop 2.6.31-20-generic #57-Ubuntu SMP Mon Feb 8 09:05:19 UTC 2010 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-20-generic root=UUID=aa199442-43f3-44ba-b70a-3bc870b1a4e3 ro quiet splash
Build Date: 14 November 2009  05:48:26PM
xorg-server 2:1.6.4-2ubuntu4.1 (buildd@) 
    Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Thu Mar 11 19:17:23 2010
(==) Using config file: "/etc/X11/xorg.conf"
(==) No Layout section.  Using the first Screen section.
(**) |-->Screen "Screen0" (0)
(**) |   |-->Monitor "Monitor0"
(**) |   |-->Device "Device0"
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

(--) PCI:*(0:0:2:0) 8086:2572:1028:019d Intel Corporation 82865G Integrated Graphics Controller rev 2, Mem @ 0xe8000000/134217728, 0xfeb80000/524288, I/O @ 0x0000ed98/8
(II) Open ACPI successful (/var/run/acpid.socket)
(II) System resource ranges:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [4] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [5] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
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
(II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
    i810-dc100, i810e, i815, i830M, 845G, 852GM/855GM, 865G, 915G,
    E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
    965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
    4 Series, G45/G43, Q45/Q43, G41, B43, Clarkdale, Arrandale
(II) Primary Device is: PCI 00@00:02:0
(II) resource ranges after probing:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [4] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [5] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: Searching for BusID pci:0000:00:02.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: drmOpenMinor returns 8
drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
(**) intel(0): Depth 24, (--) framebuffer bpp 32
(==) intel(0): RGB weight 888
(==) intel(0): Default visual is TrueColor
(II) intel(0): Integrated Graphics Chipset: Intel(R) 865G
(--) intel(0): Chipset: "865G"
(II) intel(0): Output VGA1 using monitor section Monitor0
(II) intel(0): EDID for output VGA1
(II) intel(0): Manufacturer: SAM  Model: 584  Serial#: 1297691187
(II) intel(0): Year: 2009  Week: 51
(II) intel(0): EDID Version: 1.3
(II) intel(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) intel(0): Sync:  Separate  Composite  SyncOnGreen
(II) intel(0): Max Image Size [cm]: horiz.: 51  vert.: 29
(II) intel(0): Gamma: 2.20
(II) intel(0): DPMS capabilities: Off; RGB/Color Display
(II) intel(0): First detailed timing is preferred mode
(II) intel(0): redX: 0.640 redY: 0.330   greenX: 0.300 greenY: 0.600
(II) intel(0): blueX: 0.150 blueY: 0.060   whiteX: 0.312 whiteY: 0.329
(II) intel(0): Supported established timings:
(II) intel(0): 640x480@60Hz
(II) intel(0): 800x600@56Hz
(II) intel(0): 800x600@60Hz
(II) intel(0): 1024x768@60Hz
(II) intel(0): Manufacturer's mask: 0
(II) intel(0): Supported standard timings:
(II) intel(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) intel(0): #1: hsize: 1280  vsize 960  refresh: 60  vid: 16513
(II) intel(0): #2: hsize: 1280  vsize 800  refresh: 60  vid: 129
(II) intel(0): #3: hsize: 1440  vsize 900  refresh: 60  vid: 149
(II) intel(0): #4: hsize: 1680  vsize 1050  refresh: 60  vid: 179
(II) intel(0): Supported detailed timing:
(II) intel(0): clock: 156.8 MHz   Image Size:  510 x 287 mm
(II) intel(0): h_active: 2048  h_sync: 2096  h_sync_end 2128 h_blank_end 2208 h_border: 0
(II) intel(0): v_active: 1152  v_sync: 1155  v_sync_end 1160 v_blanking: 1185 v_border: 0
(II) intel(0): Ranges: V min: 56 V max: 60 Hz, H min: 30 H max: 81 kHz, PixClock max 160 MHz
(II) intel(0): Monitor name: SyncMaster
(II) intel(0): Serial No: HVMSC01920
(II) intel(0): EDID (in hex):
(II) intel(0):     00ffffffffffff004c2d84053332594d
(II) intel(0):     331301030e331d782aee91a3544c9926
(II) intel(0):     0f50542308008180814081009500b300
(II) intel(0):     0101010101013b3d00a0808021403020
(II) intel(0):     3500fe1f1100001a000000fd00383c1e
(II) intel(0):     5110000a202020202020000000fc0053
(II) intel(0):     796e634d61737465720a2020000000ff
(II) intel(0):     0048564d534330313932300a202000aa
(II) intel(0): EDID vendor "SAM", prod id 1412
(II) intel(0): Using hsync ranges from config file
(II) intel(0): Using vrefresh ranges from config file
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "2048x1152"x0.0  156.75  2048 2096 2128 2208  1152 1155 1160 1185 +hsync -vsync (71.0 kHz)
(II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) intel(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
(II) intel(0): Modeline "1280x800"x0.0   83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync (49.7 kHz)
(II) intel(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
(II) intel(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
(II) intel(0): Not using mode "2048x1152_60.00" (hsync out of range)
(II) intel(0): Not using mode "2048x1152" (hsync out of range)
(II) intel(0): Printing probed modes for output VGA1
(II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Output VGA1 connected
(II) intel(0): Using fuzzy aspect match for initial modes
(II) intel(0): Output VGA1 using initial mode 1024x768
(==) intel(0): video overlay key set to 0x101fe
(==) intel(0): Using gamma correction (1.0, 1.0, 1.0)
(**) intel(0): Display dimensions: (510, 290) mm
(**) intel(0): DPI set to (50, 67)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.4
(==) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [4] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [5] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
(II) intel(0): [DRI2] Setup complete
(**) intel(0): Framebuffer compression disabled
(**) intel(0): Tiling enabled
(**) intel(0): SwapBuffers wait enabled
(==) intel(0): VideoRam: 131072 KB
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
(WW) intel(0): Disabling Xv because no adaptors could be initialized.
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
(II) intel(0): Setting screen physical size to 510 x 287
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
(**) Option "xkb_layout" "us"
(II) config/hal: Adding input device AT Translated Set 2 keyboard
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event3"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/hal: Adding input device Power Button
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event1"
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
(II) config/hal: Adding input device Logitech Optical USB Mouse
(**) Logitech Optical USB Mouse: always reports core events
(**) Logitech Optical USB Mouse: Device: "/dev/input/event4"
(II) Logitech Optical USB Mouse: Found 3 mouse buttons
(II) Logitech Optical USB Mouse: Found x and y relative axes
(II) Logitech Optical USB Mouse: Found scroll wheel(s)
(II) Logitech Optical USB Mouse: Configuring as mouse
(**) Logitech Optical USB Mouse: YAxisMapping: buttons 4 and 5
(**) Logitech Optical USB Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Logitech Optical USB Mouse" (type: MOUSE)
(**) Logitech Optical USB Mouse: (accel) keeping acceleration scheme 1
(**) Logitech Optical USB Mouse: (accel) filter chain progression: 2.00
(**) Logitech Optical USB Mouse: (accel) filter stage 0: 20.00 ms
(**) Logitech Optical USB Mouse: (accel) set acceleration profile 0
(II) Logitech Optical USB Mouse: initialized for relative axes.
(II) intel(0): EDID for output VGA1
(II) intel(0): Manufacturer: SAM  Model: 584  Serial#: 1297691187
(II) intel(0): Year: 2009  Week: 51
(II) intel(0): EDID Version: 1.3
(II) intel(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) intel(0): Sync:  Separate  Composite  SyncOnGreen
(II) intel(0): Max Image Size [cm]: horiz.: 51  vert.: 29
(II) intel(0): Gamma: 2.20
(II) intel(0): DPMS capabilities: Off; RGB/Color Display
(II) intel(0): First detailed timing is preferred mode
(II) intel(0): redX: 0.640 redY: 0.330   greenX: 0.300 greenY: 0.600
(II) intel(0): blueX: 0.150 blueY: 0.060   whiteX: 0.312 whiteY: 0.329
(II) intel(0): Supported established timings:
(II) intel(0): 640x480@60Hz
(II) intel(0): 800x600@56Hz
(II) intel(0): 800x600@60Hz
(II) intel(0): 1024x768@60Hz
(II) intel(0): Manufacturer's mask: 0
(II) intel(0): Supported standard timings:
(II) intel(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) intel(0): #1: hsize: 1280  vsize 960  refresh: 60  vid: 16513
(II) intel(0): #2: hsize: 1280  vsize 800  refresh: 60  vid: 129
(II) intel(0): #3: hsize: 1440  vsize 900  refresh: 60  vid: 149
(II) intel(0): #4: hsize: 1680  vsize 1050  refresh: 60  vid: 179
(II) intel(0): Supported detailed timing:
(II) intel(0): clock: 156.8 MHz   Image Size:  510 x 287 mm
(II) intel(0): h_active: 2048  h_sync: 2096  h_sync_end 2128 h_blank_end 2208 h_border: 0
(II) intel(0): v_active: 1152  v_sync: 1155  v_sync_end 1160 v_blanking: 1185 v_border: 0
(II) intel(0): Ranges: V min: 56 V max: 60 Hz, H min: 30 H max: 81 kHz, PixClock max 160 MHz
(II) intel(0): Monitor name: SyncMaster
(II) intel(0): Serial No: HVMSC01920
(II) intel(0): EDID (in hex):
(II) intel(0):     00ffffffffffff004c2d84053332594d
(II) intel(0):     331301030e331d782aee91a3544c9926
(II) intel(0):     0f50542308008180814081009500b300
(II) intel(0):     0101010101013b3d00a0808021403020
(II) intel(0):     3500fe1f1100001a000000fd00383c1e
(II) intel(0):     5110000a202020202020000000fc0053
(II) intel(0):     796e634d61737465720a2020000000ff
(II) intel(0):     0048564d534330313932300a202000aa
(II) intel(0): EDID vendor "SAM", prod id 1412
(II) intel(0): Using hsync ranges from config file
(II) intel(0): Using vrefresh ranges from config file
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "2048x1152"x0.0  156.75  2048 2096 2128 2208  1152 1155 1160 1185 +hsync -vsync (71.0 kHz)
(II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) intel(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
(II) intel(0): Modeline "1280x800"x0.0   83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync (49.7 kHz)
(II) intel(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
(II) intel(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
(II) intel(0): Not using mode "2048x1152_60.00" (hsync out of range)
(II) intel(0): Not using mode "2048x1152" (hsync out of range)
(II) intel(0): Printing probed modes for output VGA1
(II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): EDID for output VGA1
(II) intel(0): Manufacturer: SAM  Model: 584  Serial#: 1297691187
(II) intel(0): Year: 2009  Week: 51
(II) intel(0): EDID Version: 1.3
(II) intel(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) intel(0): Sync:  Separate  Composite  SyncOnGreen
(II) intel(0): Max Image Size [cm]: horiz.: 51  vert.: 29
(II) intel(0): Gamma: 2.20
(II) intel(0): DPMS capabilities: Off; RGB/Color Display
(II) intel(0): First detailed timing is preferred mode
(II) intel(0): redX: 0.640 redY: 0.330   greenX: 0.300 greenY: 0.600
(II) intel(0): blueX: 0.150 blueY: 0.060   whiteX: 0.312 whiteY: 0.329
(II) intel(0): Supported established timings:
(II) intel(0): 640x480@60Hz
(II) intel(0): 800x600@56Hz
(II) intel(0): 800x600@60Hz
(II) intel(0): 1024x768@60Hz
(II) intel(0): Manufacturer's mask: 0
(II) intel(0): Supported standard timings:
(II) intel(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) intel(0): #1: hsize: 1280  vsize 960  refresh: 60  vid: 16513
(II) intel(0): #2: hsize: 1280  vsize 800  refresh: 60  vid: 129
(II) intel(0): #3: hsize: 1440  vsize 900  refresh: 60  vid: 149
(II) intel(0): #4: hsize: 1680  vsize 1050  refresh: 60  vid: 179
(II) intel(0): Supported detailed timing:
(II) intel(0): clock: 156.8 MHz   Image Size:  510 x 287 mm
(II) intel(0): h_active: 2048  h_sync: 2096  h_sync_end 2128 h_blank_end 2208 h_border: 0
(II) intel(0): v_active: 1152  v_sync: 1155  v_sync_end 1160 v_blanking: 1185 v_border: 0
(II) intel(0): Ranges: V min: 56 V max: 60 Hz, H min: 30 H max: 81 kHz, PixClock max 160 MHz
(II) intel(0): Monitor name: SyncMaster
(II) intel(0): Serial No: HVMSC01920
(II) intel(0): EDID (in hex):
(II) intel(0):     00ffffffffffff004c2d84053332594d
(II) intel(0):     331301030e331d782aee91a3544c9926
(II) intel(0):     0f50542308008180814081009500b300
(II) intel(0):     0101010101013b3d00a0808021403020
(II) intel(0):     3500fe1f1100001a000000fd00383c1e
(II) intel(0):     5110000a202020202020000000fc0053
(II) intel(0):     796e634d61737465720a2020000000ff
(II) intel(0):     0048564d534330313932300a202000aa
(II) intel(0): EDID vendor "SAM", prod id 1412
(II) intel(0): Using hsync ranges from config file
(II) intel(0): Using vrefresh ranges from config file
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "2048x1152"x0.0  156.75  2048 2096 2128 2208  1152 1155 1160 1185 +hsync -vsync (71.0 kHz)
(II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) intel(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
(II) intel(0): Modeline "1280x800"x0.0   83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync (49.7 kHz)
(II) intel(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
(II) intel(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
(II) intel(0): Not using mode "2048x1152_60.00" (hsync out of range)
(II) intel(0): Not using mode "2048x1152" (hsync out of range)
(II) intel(0): Printing probed modes for output VGA1
(II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): EDID for output VGA1
(II) intel(0): Manufacturer: SAM  Model: 584  Serial#: 1297691187
(II) intel(0): Year: 2009  Week: 51
(II) intel(0): EDID Version: 1.3
(II) intel(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) intel(0): Sync:  Separate  Composite  SyncOnGreen
(II) intel(0): Max Image Size [cm]: horiz.: 51  vert.: 29
(II) intel(0): Gamma: 2.20
(II) intel(0): DPMS capabilities: Off; RGB/Color Display
(II) intel(0): First detailed timing is preferred mode
(II) intel(0): redX: 0.640 redY: 0.330   greenX: 0.300 greenY: 0.600
(II) intel(0): blueX: 0.150 blueY: 0.060   whiteX: 0.312 whiteY: 0.329
(II) intel(0): Supported established timings:
(II) intel(0): 640x480@60Hz
(II) intel(0): 800x600@56Hz
(II) intel(0): 800x600@60Hz
(II) intel(0): 1024x768@60Hz
(II) intel(0): Manufacturer's mask: 0
(II) intel(0): Supported standard timings:
(II) intel(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) intel(0): #1: hsize: 1280  vsize 960  refresh: 60  vid: 16513
(II) intel(0): #2: hsize: 1280  vsize 800  refresh: 60  vid: 129
(II) intel(0): #3: hsize: 1440  vsize 900  refresh: 60  vid: 149
(II) intel(0): #4: hsize: 1680  vsize 1050  refresh: 60  vid: 179
(II) intel(0): Supported detailed timing:
(II) intel(0): clock: 156.8 MHz   Image Size:  510 x 287 mm
(II) intel(0): h_active: 2048  h_sync: 2096  h_sync_end 2128 h_blank_end 2208 h_border: 0
(II) intel(0): v_active: 1152  v_sync: 1155  v_sync_end 1160 v_blanking: 1185 v_border: 0
(II) intel(0): Ranges: V min: 56 V max: 60 Hz, H min: 30 H max: 81 kHz, PixClock max 160 MHz
(II) intel(0): Monitor name: SyncMaster
(II) intel(0): Serial No: HVMSC01920
(II) intel(0): EDID (in hex):
(II) intel(0):     00ffffffffffff004c2d84053332594d
(II) intel(0):     331301030e331d782aee91a3544c9926
(II) intel(0):     0f50542308008180814081009500b300
(II) intel(0):     0101010101013b3d00a0808021403020
(II) intel(0):     3500fe1f1100001a000000fd00383c1e
(II) intel(0):     5110000a202020202020000000fc0053
(II) intel(0):     796e634d61737465720a2020000000ff
(II) intel(0):     0048564d534330313932300a202000aa
(II) intel(0): EDID vendor "SAM", prod id 1412
(II) intel(0): Using hsync ranges from config file
(II) intel(0): Using vrefresh ranges from config file
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "2048x1152"x0.0  156.75  2048 2096 2128 2208  1152 1155 1160 1185 +hsync -vsync (71.0 kHz)
(II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) intel(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
(II) intel(0): Modeline "1280x800"x0.0   83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync (49.7 kHz)
(II) intel(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
(II) intel(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
(II) intel(0): Not using mode "2048x1152_60.00" (hsync out of range)
(II) intel(0): Not using mode "2048x1152" (hsync out of range)
(II) intel(0): Printing probed modes for output VGA1
(II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): EDID for output VGA1
(II) intel(0): Manufacturer: SAM  Model: 584  Serial#: 1297691187
(II) intel(0): Year: 2009  Week: 51
(II) intel(0): EDID Version: 1.3
(II) intel(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) intel(0): Sync:  Separate  Composite  SyncOnGreen
(II) intel(0): Max Image Size [cm]: horiz.: 51  vert.: 29
(II) intel(0): Gamma: 2.20
(II) intel(0): DPMS capabilities: Off; RGB/Color Display
(II) intel(0): First detailed timing is preferred mode
(II) intel(0): redX: 0.640 redY: 0.330   greenX: 0.300 greenY: 0.600
(II) intel(0): blueX: 0.150 blueY: 0.060   whiteX: 0.312 whiteY: 0.329
(II) intel(0): Supported established timings:
(II) intel(0): 640x480@60Hz
(II) intel(0): 800x600@56Hz
(II) intel(0): 800x600@60Hz
(II) intel(0): 1024x768@60Hz
(II) intel(0): Manufacturer's mask: 0
(II) intel(0): Supported standard timings:
(II) intel(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) intel(0): #1: hsize: 1280  vsize 960  refresh: 60  vid: 16513
(II) intel(0): #2: hsize: 1280  vsize 800  refresh: 60  vid: 129
(II) intel(0): #3: hsize: 1440  vsize 900  refresh: 60  vid: 149
(II) intel(0): #4: hsize: 1680  vsize 1050  refresh: 60  vid: 179
(II) intel(0): Supported detailed timing:
(II) intel(0): clock: 156.8 MHz   Image Size:  510 x 287 mm
(II) intel(0): h_active: 2048  h_sync: 2096  h_sync_end 2128 h_blank_end 2208 h_border: 0
(II) intel(0): v_active: 1152  v_sync: 1155  v_sync_end 1160 v_blanking: 1185 v_border: 0
(II) intel(0): Ranges: V min: 56 V max: 60 Hz, H min: 30 H max: 81 kHz, PixClock max 160 MHz
(II) intel(0): Monitor name: SyncMaster
(II) intel(0): Serial No: HVMSC01920
(II) intel(0): EDID (in hex):
(II) intel(0):     00ffffffffffff004c2d84053332594d
(II) intel(0):     331301030e331d782aee91a3544c9926
(II) intel(0):     0f50542308008180814081009500b300
(II) intel(0):     0101010101013b3d00a0808021403020
(II) intel(0):     3500fe1f1100001a000000fd00383c1e
(II) intel(0):     5110000a202020202020000000fc0053
(II) intel(0):     796e634d61737465720a2020000000ff
(II) intel(0):     0048564d534330313932300a202000aa
(II) intel(0): EDID vendor "SAM", prod id 1412
(II) intel(0): Using hsync ranges from config file
(II) intel(0): Using vrefresh ranges from config file
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "2048x1152"x0.0  156.75  2048 2096 2128 2208  1152 1155 1160 1185 +hsync -vsync (71.0 kHz)
(II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) intel(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
(II) intel(0): Modeline "1280x800"x0.0   83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync (49.7 kHz)
(II) intel(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
(II) intel(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
(II) intel(0): Not using mode "2048x1152_60.00" (hsync out of range)
(II) intel(0): Not using mode "2048x1152" (hsync out of range)
(II) intel(0): Printing probed modes for output VGA1
(II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)thanks again

---

### Post by patchwork on 2010-03-11
Add to the "Monitor" Section
```
 HorizSync 28-72
```
And restart x

You should be all set with this

---

### Post by mystik_spiral on 2010-03-11
> **shazbut said:**
> Have you tried the cvt/xrandr method described [here]("https://wiki.ubuntu.com/X/Config/Resolution") and [here]("http://www.ubuntugeek.com/how-change-display-resolution-settings-using-xrandr.html")?

I was of the understanding the whole xorg.conf setup was soon to go the way of the dodo.  Speaking of which, it's about time analogue VGA died a horrible death too, and most of these problems would disappear with it.
haven't tried. going to see what magic patchwork can do for me.

---

### Post by mystik_spiral on 2010-03-11
> **patchwork said:**
> Add to the "Monitor" Section
```
 HorizSync 28-72
```And restart x

You should be all set with this
Monitor "Monitor0" HorizSync 28-72

like that?

oh, change HorizSync 30 - 60 into HorizSync 28-72?

---

### Post by patchwork on 2010-03-11
> I was of the understanding the whole xorg.conf setup was soon to go the way of the dodo

Unfortunately, some systems still require this, at least in parts.  It is true that most computers can load a default configuration thanks to the vesa standard modes.

---

### Post by patchwork on 2010-03-11
Yes, edit the current horizsync
Also make sure that the name in the modeline matches a mode name in the screen section, i.e.     

modeline "2048x1152"  ..............


modes "2048x1152"


Edit:  your mode is being reject for horizontal sync out of range, so we are adding a manual value for the range to include your desired settings

---

### Post by mystik_spiral on 2010-03-11
> **patchwork said:**
> Yes, edit the current horizsync
Also make sure that the name in the modeline matches a mode name in the screen section, i.e.     

modeline "2048x1152"  ..............


modes "2048x1152"


Edit:  your mode is being reject for horizontal sync out of range, so we are adding a manual value for the range to include your desired settings
right now for modes I have:

modes "2048x1152" "1600x1200" "1024x768"

eliminate the last two?

---

### Post by patchwork on 2010-03-11
You can keep them there, but make sure the "2048x1152" exactly matches "2048x1152" in the modeline 

"2048x1152@0" is trying to reference a different mode

---

### Post by mystik_spiral on 2010-03-11
> **patchwork said:**
> You can keep them there, but make sure the "2048x1152" exactly matches "2048x1152" in the modeline 

"2048x1152@0" is trying to reference a different mode
yes, they both say "2048x1152". rebooting now.

---

### Post by mystik_spiral on 2010-03-11
We have a problem.

When I rebooted this error came up.:

> Ubuntu is running in low-graphics mode. The following error was encountered. You may need to update your configuration to solve this. (EE) Problem parsing the config file. (EE) Error parsing the config file.I clicked OK and then:

> What would you like to do?
- run with low graphics for one session?
- reconfigure graphics?
- troubleshoot error?
- exit to console login?Obviously, I clicked the first option.

On the bright side, it looks like the monitor is now 1280x1024 (5:4). Getting there!

---

### Post by patchwork on 2010-03-11
Can I see another copy of your xorg.conf and the /var/log/Xorg.0.log?

---

### Post by mystik_spiral on 2010-03-11
> Section "Monitor"
Identifier "Monitor0"
VendorName "SAMSUNG"
ModelName "SyncMaster 2343BWX"
HorizSync 28 - 72
VertRefresh 55 - 75
Modeline "2048x1152_60.00"  197.00  2048 2184 2400 2752  1152 1155 1160 1195 -hsync +vsync
EndSection

Section "Device"
Identifier "Device0"
Driver "intel"
VendorName "Intel 82865G"
EndSection

Section "Screen"
Identifier "Screen0"
Device "Device0"
Monitor "Monitor0" HorizSync 28-72
DefaultDepth 24
SubSection "Display"
Depth 24
Modes "2048x1152" "1600x1200" "1024x768"
EndSubSection
EndSection

> 
X.Org X Server 1.6.4
Release Date: 2009-9-27
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux beckie-desktop 2.6.31-20-generic #57-Ubuntu SMP Mon Feb 8 09:05:19 UTC 2010 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-20-generic root=UUID=aa199442-43f3-44ba-b70a-3bc870b1a4e3 ro quiet splash
Build Date: 14 November 2009  05:48:26PM
xorg-server 2:1.6.4-2ubuntu4.1 (buildd@) 
    Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Thu Mar 11 19:43:59 2010
(==) Using config file: "/etc/X11/xorg.conf"
Parse error on line 19 of section Screen in file /etc/X11/xorg.conf
    "HorizSync" is not a valid keyword in this section.
(EE) Problem parsing the config file
(EE) Error parsing the config file

Fatal server error:
no screens found

Please consult the The X.Org Foundation support 
     at [http://wiki.x.org](http://wiki.x.org)
 for help. 
Please also check the log file at "/var/log/Xorg.0.log" for additional information.

(WW) xf86CloseConsole: KDSETMODE failed: Bad file descriptor
(WW) xf86CloseConsole: VT_GETMODE failed: Bad file descriptor
(WW) xf86OpenConsole: VT_GETSTATE failed: Bad file descriptor
 ddxSigGiveUp: Closing log

What the heck happened here?

---

### Post by patchwork on 2010-03-11
> Section "Screen"
Identifier "Screen0"
Device "Device0"
Monitor "Monitor0" **HorizSync 28-72**
DefaultDepth 24
SubSection "Display"
Depth 24
Modes "2048x1152" "1600x1200" "1024x768"
EndSubSection
EndSection                                      Remove the bolded portion.....it only goes in the "Monitor" Section (not the "Screen" Section)

Also, you don't need to reboot, only restart x:

```
sudo service gdm restart
```

---

### Post by mystik_spiral on 2010-03-11
[QUOTE=patchwork;8952857]Remove the bolded portion.....it only goes in the "Monitor" Section (not the "Screen" Section

Also, you don't need to reboot, only restart x:

```
sudo service gdm restart
```[/QUOTE
whoops, didn't realize that I left that there still. my bad...one second.

---

### Post by mystik_spiral on 2010-03-11
[SIZE="5"]WOW.[/SIZE]
After erasing the extra HorizSync 28-72 and going to sudo service gdm restart, my computer went to black so I thought "that was odd". Had to reboot my computer and now the desktop...is entirely black aside from an orange line going down the left side of the screen. I am back to my original problem from [http://ubuntuforums.org/showthread.php?t=1426013](http://ubuntuforums.org/showthread.php?t=1426013) !

So I am running Windows right now.

---

### Post by patchwork on 2010-03-11
Can you drop to console and copy your /vr/log/Xorg.0.log to another file?  I'd like to see it, but only after we get you back to a working resolution.

Change the HorizSync back to 28-60 and restart x, this should bring us back to where you were.


EDIT: Drop to console is CTRL ALT F1

sudo cp /var/log/Xorg.0.log ~/Desktop/xlog.txt

sudo nano /etc/X11/xorg.conf

---

### Post by mystik_spiral on 2010-03-11
I don't know. that's going to get tricky. i'll probably be able to access vr/log/Xorg.0.log in drop to console mode but i'm sure if I'm going to be able to copy it into another file. just save it as under a different name? i wont be able to do it any other way.

---

### Post by patchwork on 2010-03-11
the cp command saves it as another name in another location.

sudo cp /var/log/Xorg.0.log /home/<username>/Desktop/xlog.txt will copy the log to a text file in your Desktop directory


Edit:   see the updated file path.....~/Desktop as root will create a new directory /Desktop (as opposed to /home/<username>/Desktop)

---

### Post by mystik_spiral on 2010-03-11
Ubuntu opened up "normally" this time so I can just provide you with the log:

> X.Org X Server 1.6.4
Release Date: 2009-9-27
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux beckie-desktop 2.6.31-20-generic #57-Ubuntu SMP Mon Feb 8 09:05:19 UTC 2010 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-20-generic root=UUID=aa199442-43f3-44ba-b70a-3bc870b1a4e3 ro quiet splash
Build Date: 14 November 2009  05:48:26PM
xorg-server 2:1.6.4-2ubuntu4.1 (buildd@) 
    Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Thu Mar 11 20:33:44 2010
(==) Using config file: "/etc/X11/xorg.conf"
(==) No Layout section.  Using the first Screen section.
(**) |-->Screen "Screen0" (0)
(**) |   |-->Monitor "Monitor0"
(**) |   |-->Device "Device0"
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

(--) PCI:*(0:0:2:0) 8086:2572:1028:019d Intel Corporation 82865G Integrated Graphics Controller rev 2, Mem @ 0xe8000000/134217728, 0xfeb80000/524288, I/O @ 0x0000ed98/8
(II) Open ACPI successful (/var/run/acpid.socket)
(II) System resource ranges:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [4] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [5] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
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
(II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
    i810-dc100, i810e, i815, i830M, 845G, 852GM/855GM, 865G, 915G,
    E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
    965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
    4 Series, G45/G43, Q45/Q43, G41, B43, Clarkdale, Arrandale
(II) Primary Device is: PCI 00@00:02:0
(II) resource ranges after probing:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [4] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [5] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: Searching for BusID pci:0000:00:02.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: drmOpenMinor returns 8
drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
(**) intel(0): Depth 24, (--) framebuffer bpp 32
(==) intel(0): RGB weight 888
(==) intel(0): Default visual is TrueColor
(II) intel(0): Integrated Graphics Chipset: Intel(R) 865G
(--) intel(0): Chipset: "865G"
(II) intel(0): Output VGA1 using monitor section Monitor0
(II) intel(0): EDID for output VGA1
(II) intel(0): Manufacturer: SAM  Model: 584  Serial#: 1297691187
(II) intel(0): Year: 2009  Week: 51
(II) intel(0): EDID Version: 1.3
(II) intel(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) intel(0): Sync:  Separate  Composite  SyncOnGreen
(II) intel(0): Max Image Size [cm]: horiz.: 51  vert.: 29
(II) intel(0): Gamma: 2.20
(II) intel(0): DPMS capabilities: Off; RGB/Color Display
(II) intel(0): First detailed timing is preferred mode
(II) intel(0): redX: 0.640 redY: 0.330   greenX: 0.300 greenY: 0.600
(II) intel(0): blueX: 0.150 blueY: 0.060   whiteX: 0.312 whiteY: 0.329
(II) intel(0): Supported established timings:
(II) intel(0): 640x480@60Hz
(II) intel(0): 800x600@56Hz
(II) intel(0): 800x600@60Hz
(II) intel(0): 1024x768@60Hz
(II) intel(0): Manufacturer's mask: 0
(II) intel(0): Supported standard timings:
(II) intel(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) intel(0): #1: hsize: 1280  vsize 960  refresh: 60  vid: 16513
(II) intel(0): #2: hsize: 1280  vsize 800  refresh: 60  vid: 129
(II) intel(0): #3: hsize: 1440  vsize 900  refresh: 60  vid: 149
(II) intel(0): #4: hsize: 1680  vsize 1050  refresh: 60  vid: 179
(II) intel(0): Supported detailed timing:
(II) intel(0): clock: 156.8 MHz   Image Size:  510 x 287 mm
(II) intel(0): h_active: 2048  h_sync: 2096  h_sync_end 2128 h_blank_end 2208 h_border: 0
(II) intel(0): v_active: 1152  v_sync: 1155  v_sync_end 1160 v_blanking: 1185 v_border: 0
(II) intel(0): Ranges: V min: 56 V max: 60 Hz, H min: 30 H max: 81 kHz, PixClock max 160 MHz
(II) intel(0): Monitor name: SyncMaster
(II) intel(0): Serial No: HVMSC01920
(II) intel(0): EDID (in hex):
(II) intel(0):     00ffffffffffff004c2d84053332594d
(II) intel(0):     331301030e331d782aee91a3544c9926
(II) intel(0):     0f50542308008180814081009500b300
(II) intel(0):     0101010101013b3d00a0808021403020
(II) intel(0):     3500fe1f1100001a000000fd00383c1e
(II) intel(0):     5110000a202020202020000000fc0053
(II) intel(0):     796e634d61737465720a2020000000ff
(II) intel(0):     0048564d534330313932300a202000aa
(II) intel(0): EDID vendor "SAM", prod id 1412
(II) intel(0): Using hsync ranges from config file
(II) intel(0): Using vrefresh ranges from config file
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "2048x1152"x0.0  156.75  2048 2096 2128 2208  1152 1155 1160 1185 +hsync -vsync (71.0 kHz)
(II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) intel(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
(II) intel(0): Modeline "1280x800"x0.0   83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync (49.7 kHz)
(II) intel(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
(II) intel(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
(II) intel(0): Printing probed modes for output VGA1
(II) intel(0): Modeline "2048x1152"x59.9  156.75  2048 2096 2128 2208  1152 1155 1160 1185 +hsync -vsync (71.0 kHz)
(II) intel(0): Modeline "2048x1152_60.00"x59.9  197.00  2048 2184 2400 2752  1152 1155 1160 1195 -hsync +vsync (71.6 kHz)
(II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Output VGA1 connected
(II) intel(0): Using user preference for initial modes
(II) intel(0): Output VGA1 using initial mode 2048x1152
(==) intel(0): video overlay key set to 0x101fe
(==) intel(0): Using gamma correction (1.0, 1.0, 1.0)
(**) intel(0): Display dimensions: (510, 290) mm
(**) intel(0): DPI set to (101, 100)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.4
(==) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [4] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [5] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
(II) intel(0): [DRI2] Setup complete
(**) intel(0): Framebuffer compression disabled
(**) intel(0): Tiling enabled
(**) intel(0): SwapBuffers wait enabled
(==) intel(0): VideoRam: 131072 KB
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
(WW) intel(0): Disabling Xv because no adaptors could be initialized.
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
(II) intel(0): Setting screen physical size to 510 x 287
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
(II) config/hal: Adding input device Logitech Optical USB Mouse
(**) Logitech Optical USB Mouse: always reports core events
(**) Logitech Optical USB Mouse: Device: "/dev/input/event4"
(II) Logitech Optical USB Mouse: Found 3 mouse buttons
(II) Logitech Optical USB Mouse: Found x and y relative axes
(II) Logitech Optical USB Mouse: Found scroll wheel(s)
(II) Logitech Optical USB Mouse: Configuring as mouse
(**) Logitech Optical USB Mouse: YAxisMapping: buttons 4 and 5
(**) Logitech Optical USB Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Logitech Optical USB Mouse" (type: MOUSE)
(**) Logitech Optical USB Mouse: (accel) keeping acceleration scheme 1
(**) Logitech Optical USB Mouse: (accel) filter chain progression: 2.00
(**) Logitech Optical USB Mouse: (accel) filter stage 0: 20.00 ms
(**) Logitech Optical USB Mouse: (accel) set acceleration profile 0
(II) Logitech Optical USB Mouse: initialized for relative axes.
(II) intel(0): EDID for output VGA1
(II) intel(0): Manufacturer: SAM  Model: 584  Serial#: 1297691187
(II) intel(0): Year: 2009  Week: 51
(II) intel(0): EDID Version: 1.3
(II) intel(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) intel(0): Sync:  Separate  Composite  SyncOnGreen
(II) intel(0): Max Image Size [cm]: horiz.: 51  vert.: 29
(II) intel(0): Gamma: 2.20
(II) intel(0): DPMS capabilities: Off; RGB/Color Display
(II) intel(0): First detailed timing is preferred mode
(II) intel(0): redX: 0.640 redY: 0.330   greenX: 0.300 greenY: 0.600
(II) intel(0): blueX: 0.150 blueY: 0.060   whiteX: 0.312 whiteY: 0.329
(II) intel(0): Supported established timings:
(II) intel(0): 640x480@60Hz
(II) intel(0): 800x600@56Hz
(II) intel(0): 800x600@60Hz
(II) intel(0): 1024x768@60Hz
(II) intel(0): Manufacturer's mask: 0
(II) intel(0): Supported standard timings:
(II) intel(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) intel(0): #1: hsize: 1280  vsize 960  refresh: 60  vid: 16513
(II) intel(0): #2: hsize: 1280  vsize 800  refresh: 60  vid: 129
(II) intel(0): #3: hsize: 1440  vsize 900  refresh: 60  vid: 149
(II) intel(0): #4: hsize: 1680  vsize 1050  refresh: 60  vid: 179
(II) intel(0): Supported detailed timing:
(II) intel(0): clock: 156.8 MHz   Image Size:  510 x 287 mm
(II) intel(0): h_active: 2048  h_sync: 2096  h_sync_end 2128 h_blank_end 2208 h_border: 0
(II) intel(0): v_active: 1152  v_sync: 1155  v_sync_end 1160 v_blanking: 1185 v_border: 0
(II) intel(0): Ranges: V min: 56 V max: 60 Hz, H min: 30 H max: 81 kHz, PixClock max 160 MHz
(II) intel(0): Monitor name: SyncMaster
(II) intel(0): Serial No: HVMSC01920
(II) intel(0): EDID (in hex):
(II) intel(0):     00ffffffffffff004c2d84053332594d
(II) intel(0):     331301030e331d782aee91a3544c9926
(II) intel(0):     0f50542308008180814081009500b300
(II) intel(0):     0101010101013b3d00a0808021403020
(II) intel(0):     3500fe1f1100001a000000fd00383c1e
(II) intel(0):     5110000a202020202020000000fc0053
(II) intel(0):     796e634d61737465720a2020000000ff
(II) intel(0):     0048564d534330313932300a202000aa
(II) intel(0): EDID vendor "SAM", prod id 1412
(II) intel(0): Using hsync ranges from config file
(II) intel(0): Using vrefresh ranges from config file
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "2048x1152"x0.0  156.75  2048 2096 2128 2208  1152 1155 1160 1185 +hsync -vsync (71.0 kHz)
(II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) intel(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
(II) intel(0): Modeline "1280x800"x0.0   83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync (49.7 kHz)
(II) intel(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
(II) intel(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
(II) intel(0): Printing probed modes for output VGA1
(II) intel(0): Modeline "2048x1152"x59.9  156.75  2048 2096 2128 2208  1152 1155 1160 1185 +hsync -vsync (71.0 kHz)
(II) intel(0): Modeline "2048x1152_60.00"x59.9  197.00  2048 2184 2400 2752  1152 1155 1160 1195 -hsync +vsync (71.6 kHz)
(II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): EDID for output VGA1
(II) intel(0): Manufacturer: SAM  Model: 584  Serial#: 1297691187
(II) intel(0): Year: 2009  Week: 51
(II) intel(0): EDID Version: 1.3
(II) intel(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) intel(0): Sync:  Separate  Composite  SyncOnGreen
(II) intel(0): Max Image Size [cm]: horiz.: 51  vert.: 29
(II) intel(0): Gamma: 2.20
(II) intel(0): DPMS capabilities: Off; RGB/Color Display
(II) intel(0): First detailed timing is preferred mode
(II) intel(0): redX: 0.640 redY: 0.330   greenX: 0.300 greenY: 0.600
(II) intel(0): blueX: 0.150 blueY: 0.060   whiteX: 0.312 whiteY: 0.329
(II) intel(0): Supported established timings:
(II) intel(0): 640x480@60Hz
(II) intel(0): 800x600@56Hz
(II) intel(0): 800x600@60Hz
(II) intel(0): 1024x768@60Hz
(II) intel(0): Manufacturer's mask: 0
(II) intel(0): Supported standard timings:
(II) intel(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) intel(0): #1: hsize: 1280  vsize 960  refresh: 60  vid: 16513
(II) intel(0): #2: hsize: 1280  vsize 800  refresh: 60  vid: 129
(II) intel(0): #3: hsize: 1440  vsize 900  refresh: 60  vid: 149
(II) intel(0): #4: hsize: 1680  vsize 1050  refresh: 60  vid: 179
(II) intel(0): Supported detailed timing:
(II) intel(0): clock: 156.8 MHz   Image Size:  510 x 287 mm
(II) intel(0): h_active: 2048  h_sync: 2096  h_sync_end 2128 h_blank_end 2208 h_border: 0
(II) intel(0): v_active: 1152  v_sync: 1155  v_sync_end 1160 v_blanking: 1185 v_border: 0
(II) intel(0): Ranges: V min: 56 V max: 60 Hz, H min: 30 H max: 81 kHz, PixClock max 160 MHz
(II) intel(0): Monitor name: SyncMaster
(II) intel(0): Serial No: HVMSC01920
(II) intel(0): EDID (in hex):
(II) intel(0):     00ffffffffffff004c2d84053332594d
(II) intel(0):     331301030e331d782aee91a3544c9926
(II) intel(0):     0f50542308008180814081009500b300
(II) intel(0):     0101010101013b3d00a0808021403020
(II) intel(0):     3500fe1f1100001a000000fd00383c1e
(II) intel(0):     5110000a202020202020000000fc0053
(II) intel(0):     796e634d61737465720a2020000000ff
(II) intel(0):     0048564d534330313932300a202000aa
(II) intel(0): EDID vendor "SAM", prod id 1412
(II) intel(0): Using hsync ranges from config file
(II) intel(0): Using vrefresh ranges from config file
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "2048x1152"x0.0  156.75  2048 2096 2128 2208  1152 1155 1160 1185 +hsync -vsync (71.0 kHz)
(II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) intel(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
(II) intel(0): Modeline "1280x800"x0.0   83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync (49.7 kHz)
(II) intel(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
(II) intel(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
(II) intel(0): Printing probed modes for output VGA1
(II) intel(0): Modeline "2048x1152"x59.9  156.75  2048 2096 2128 2208  1152 1155 1160 1185 +hsync -vsync (71.0 kHz)
(II) intel(0): Modeline "2048x1152_60.00"x59.9  197.00  2048 2184 2400 2752  1152 1155 1160 1195 -hsync +vsync (71.6 kHz)
(II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): EDID for output VGA1
(II) intel(0): Manufacturer: SAM  Model: 584  Serial#: 1297691187
(II) intel(0): Year: 2009  Week: 51
(II) intel(0): EDID Version: 1.3
(II) intel(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) intel(0): Sync:  Separate  Composite  SyncOnGreen
(II) intel(0): Max Image Size [cm]: horiz.: 51  vert.: 29
(II) intel(0): Gamma: 2.20
(II) intel(0): DPMS capabilities: Off; RGB/Color Display
(II) intel(0): First detailed timing is preferred mode
(II) intel(0): redX: 0.640 redY: 0.330   greenX: 0.300 greenY: 0.600
(II) intel(0): blueX: 0.150 blueY: 0.060   whiteX: 0.312 whiteY: 0.329
(II) intel(0): Supported established timings:
(II) intel(0): 640x480@60Hz
(II) intel(0): 800x600@56Hz
(II) intel(0): 800x600@60Hz
(II) intel(0): 1024x768@60Hz
(II) intel(0): Manufacturer's mask: 0
(II) intel(0): Supported standard timings:
(II) intel(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) intel(0): #1: hsize: 1280  vsize 960  refresh: 60  vid: 16513
(II) intel(0): #2: hsize: 1280  vsize 800  refresh: 60  vid: 129
(II) intel(0): #3: hsize: 1440  vsize 900  refresh: 60  vid: 149
(II) intel(0): #4: hsize: 1680  vsize 1050  refresh: 60  vid: 179
(II) intel(0): Supported detailed timing:
(II) intel(0): clock: 156.8 MHz   Image Size:  510 x 287 mm
(II) intel(0): h_active: 2048  h_sync: 2096  h_sync_end 2128 h_blank_end 2208 h_border: 0
(II) intel(0): v_active: 1152  v_sync: 1155  v_sync_end 1160 v_blanking: 1185 v_border: 0
(II) intel(0): Ranges: V min: 56 V max: 60 Hz, H min: 30 H max: 81 kHz, PixClock max 160 MHz
(II) intel(0): Monitor name: SyncMaster
(II) intel(0): Serial No: HVMSC01920
(II) intel(0): EDID (in hex):
(II) intel(0):     00ffffffffffff004c2d84053332594d
(II) intel(0):     331301030e331d782aee91a3544c9926
(II) intel(0):     0f50542308008180814081009500b300
(II) intel(0):     0101010101013b3d00a0808021403020
(II) intel(0):     3500fe1f1100001a000000fd00383c1e
(II) intel(0):     5110000a202020202020000000fc0053
(II) intel(0):     796e634d61737465720a2020000000ff
(II) intel(0):     0048564d534330313932300a202000aa
(II) intel(0): EDID vendor "SAM", prod id 1412
(II) intel(0): Using hsync ranges from config file
(II) intel(0): Using vrefresh ranges from config file
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "2048x1152"x0.0  156.75  2048 2096 2128 2208  1152 1155 1160 1185 +hsync -vsync (71.0 kHz)
(II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) intel(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
(II) intel(0): Modeline "1280x800"x0.0   83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync (49.7 kHz)
(II) intel(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
(II) intel(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
(II) intel(0): Printing probed modes for output VGA1
(II) intel(0): Modeline "2048x1152"x59.9  156.75  2048 2096 2128 2208  1152 1155 1160 1185 +hsync -vsync (71.0 kHz)
(II) intel(0): Modeline "2048x1152_60.00"x59.9  197.00  2048 2184 2400 2752  1152 1155 1160 1195 -hsync +vsync (71.6 kHz)
(II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Allocate new frame buffer 1024x768 stride 1024
(II) intel(0): EDID for output VGA1
(II) intel(0): Manufacturer: SAM  Model: 584  Serial#: 1297691187
(II) intel(0): Year: 2009  Week: 51
(II) intel(0): EDID Version: 1.3
(II) intel(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) intel(0): Sync:  Separate  Composite  SyncOnGreen
(II) intel(0): Max Image Size [cm]: horiz.: 51  vert.: 29
(II) intel(0): Gamma: 2.20
(II) intel(0): DPMS capabilities: Off; RGB/Color Display
(II) intel(0): First detailed timing is preferred mode
(II) intel(0): redX: 0.640 redY: 0.330   greenX: 0.300 greenY: 0.600
(II) intel(0): blueX: 0.150 blueY: 0.060   whiteX: 0.312 whiteY: 0.329
(II) intel(0): Supported established timings:
(II) intel(0): 640x480@60Hz
(II) intel(0): 800x600@56Hz
(II) intel(0): 800x600@60Hz
(II) intel(0): 1024x768@60Hz
(II) intel(0): Manufacturer's mask: 0
(II) intel(0): Supported standard timings:
(II) intel(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) intel(0): #1: hsize: 1280  vsize 960  refresh: 60  vid: 16513
(II) intel(0): #2: hsize: 1280  vsize 800  refresh: 60  vid: 129
(II) intel(0): #3: hsize: 1440  vsize 900  refresh: 60  vid: 149
(II) intel(0): #4: hsize: 1680  vsize 1050  refresh: 60  vid: 179
(II) intel(0): Supported detailed timing:
(II) intel(0): clock: 156.8 MHz   Image Size:  510 x 287 mm
(II) intel(0): h_active: 2048  h_sync: 2096  h_sync_end 2128 h_blank_end 2208 h_border: 0
(II) intel(0): v_active: 1152  v_sync: 1155  v_sync_end 1160 v_blanking: 1185 v_border: 0
(II) intel(0): Ranges: V min: 56 V max: 60 Hz, H min: 30 H max: 81 kHz, PixClock max 160 MHz
(II) intel(0): Monitor name: SyncMaster
(II) intel(0): Serial No: HVMSC01920
(II) intel(0): EDID (in hex):
(II) intel(0):     00ffffffffffff004c2d84053332594d
(II) intel(0):     331301030e331d782aee91a3544c9926
(II) intel(0):     0f50542308008180814081009500b300
(II) intel(0):     0101010101013b3d00a0808021403020
(II) intel(0):     3500fe1f1100001a000000fd00383c1e
(II) intel(0):     5110000a202020202020000000fc0053
(II) intel(0):     796e634d61737465720a2020000000ff
(II) intel(0):     0048564d534330313932300a202000aa
(II) intel(0): EDID vendor "SAM", prod id 1412
(II) intel(0): Using hsync ranges from config file
(II) intel(0): Using vrefresh ranges from config file
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "2048x1152"x0.0  156.75  2048 2096 2128 2208  1152 1155 1160 1185 +hsync -vsync (71.0 kHz)
(II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) intel(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
(II) intel(0): Modeline "1280x800"x0.0   83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync (49.7 kHz)
(II) intel(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
(II) intel(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
(II) intel(0): Printing probed modes for output VGA1
(II) intel(0): Modeline "2048x1152"x59.9  156.75  2048 2096 2128 2208  1152 1155 1160 1185 +hsync -vsync (71.0 kHz)
(II) intel(0): Modeline "2048x1152_60.00"x59.9  197.00  2048 2184 2400 2752  1152 1155 1160 1195 -hsync +vsync (71.6 kHz)
(II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): EDID for output VGA1
(II) intel(0): Manufacturer: SAM  Model: 584  Serial#: 1297691187
(II) intel(0): Year: 2009  Week: 51
(II) intel(0): EDID Version: 1.3
(II) intel(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) intel(0): Sync:  Separate  Composite  SyncOnGreen
(II) intel(0): Max Image Size [cm]: horiz.: 51  vert.: 29
(II) intel(0): Gamma: 2.20
(II) intel(0): DPMS capabilities: Off; RGB/Color Display
(II) intel(0): First detailed timing is preferred mode
(II) intel(0): redX: 0.640 redY: 0.330   greenX: 0.300 greenY: 0.600
(II) intel(0): blueX: 0.150 blueY: 0.060   whiteX: 0.312 whiteY: 0.329
(II) intel(0): Supported established timings:
(II) intel(0): 640x480@60Hz
(II) intel(0): 800x600@56Hz
(II) intel(0): 800x600@60Hz
(II) intel(0): 1024x768@60Hz
(II) intel(0): Manufacturer's mask: 0
(II) intel(0): Supported standard timings:
(II) intel(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) intel(0): #1: hsize: 1280  vsize 960  refresh: 60  vid: 16513
(II) intel(0): #2: hsize: 1280  vsize 800  refresh: 60  vid: 129
(II) intel(0): #3: hsize: 1440  vsize 900  refresh: 60  vid: 149
(II) intel(0): #4: hsize: 1680  vsize 1050  refresh: 60  vid: 179
(II) intel(0): Supported detailed timing:
(II) intel(0): clock: 156.8 MHz   Image Size:  510 x 287 mm
(II) intel(0): h_active: 2048  h_sync: 2096  h_sync_end 2128 h_blank_end 2208 h_border: 0
(II) intel(0): v_active: 1152  v_sync: 1155  v_sync_end 1160 v_blanking: 1185 v_border: 0
(II) intel(0): Ranges: V min: 56 V max: 60 Hz, H min: 30 H max: 81 kHz, PixClock max 160 MHz
(II) intel(0): Monitor name: SyncMaster
(II) intel(0): Serial No: HVMSC01920
(II) intel(0): EDID (in hex):
(II) intel(0):     00ffffffffffff004c2d84053332594d
(II) intel(0):     331301030e331d782aee91a3544c9926
(II) intel(0):     0f50542308008180814081009500b300
(II) intel(0):     0101010101013b3d00a0808021403020
(II) intel(0):     3500fe1f1100001a000000fd00383c1e
(II) intel(0):     5110000a202020202020000000fc0053
(II) intel(0):     796e634d61737465720a2020000000ff
(II) intel(0):     0048564d534330313932300a202000aa
(II) intel(0): EDID vendor "SAM", prod id 1412
(II) intel(0): Using hsync ranges from config file
(II) intel(0): Using vrefresh ranges from config file
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "2048x1152"x0.0  156.75  2048 2096 2128 2208  1152 1155 1160 1185 +hsync -vsync (71.0 kHz)
(II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) intel(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
(II) intel(0): Modeline "1280x800"x0.0   83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync (49.7 kHz)
(II) intel(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
(II) intel(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
(II) intel(0): Printing probed modes for output VGA1
(II) intel(0): Modeline "2048x1152"x59.9  156.75  2048 2096 2128 2208  1152 1155 1160 1185 +hsync -vsync (71.0 kHz)
(II) intel(0): Modeline "2048x1152_60.00"x59.9  197.00  2048 2184 2400 2752  1152 1155 1160 1195 -hsync +vsync (71.6 kHz)
(II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): EDID for output VGA1
(II) intel(0): Manufacturer: SAM  Model: 584  Serial#: 1297691187
(II) intel(0): Year: 2009  Week: 51
(II) intel(0): EDID Version: 1.3
(II) intel(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) intel(0): Sync:  Separate  Composite  SyncOnGreen
(II) intel(0): Max Image Size [cm]: horiz.: 51  vert.: 29
(II) intel(0): Gamma: 2.20
(II) intel(0): DPMS capabilities: Off; RGB/Color Display
(II) intel(0): First detailed timing is preferred mode
(II) intel(0): redX: 0.640 redY: 0.330   greenX: 0.300 greenY: 0.600
(II) intel(0): blueX: 0.150 blueY: 0.060   whiteX: 0.312 whiteY: 0.329
(II) intel(0): Supported established timings:
(II) intel(0): 640x480@60Hz
(II) intel(0): 800x600@56Hz
(II) intel(0): 800x600@60Hz
(II) intel(0): 1024x768@60Hz
(II) intel(0): Manufacturer's mask: 0
(II) intel(0): Supported standard timings:
(II) intel(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) intel(0): #1: hsize: 1280  vsize 960  refresh: 60  vid: 16513
(II) intel(0): #2: hsize: 1280  vsize 800  refresh: 60  vid: 129
(II) intel(0): #3: hsize: 1440  vsize 900  refresh: 60  vid: 149
(II) intel(0): #4: hsize: 1680  vsize 1050  refresh: 60  vid: 179
(II) intel(0): Supported detailed timing:
(II) intel(0): clock: 156.8 MHz   Image Size:  510 x 287 mm
(II) intel(0): h_active: 2048  h_sync: 2096  h_sync_end 2128 h_blank_end 2208 h_border: 0
(II) intel(0): v_active: 1152  v_sync: 1155  v_sync_end 1160 v_blanking: 1185 v_border: 0
(II) intel(0): Ranges: V min: 56 V max: 60 Hz, H min: 30 H max: 81 kHz, PixClock max 160 MHz
(II) intel(0): Monitor name: SyncMaster
(II) intel(0): Serial No: HVMSC01920
(II) intel(0): EDID (in hex):
(II) intel(0):     00ffffffffffff004c2d84053332594d
(II) intel(0):     331301030e331d782aee91a3544c9926
(II) intel(0):     0f50542308008180814081009500b300
(II) intel(0):     0101010101013b3d00a0808021403020
(II) intel(0):     3500fe1f1100001a000000fd00383c1e
(II) intel(0):     5110000a202020202020000000fc0053
(II) intel(0):     796e634d61737465720a2020000000ff
(II) intel(0):     0048564d534330313932300a202000aa
(II) intel(0): EDID vendor "SAM", prod id 1412
(II) intel(0): Using hsync ranges from config file
(II) intel(0): Using vrefresh ranges from config file
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "2048x1152"x0.0  156.75  2048 2096 2128 2208  1152 1155 1160 1185 +hsync -vsync (71.0 kHz)
(II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) intel(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
(II) intel(0): Modeline "1280x800"x0.0   83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync (49.7 kHz)
(II) intel(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
(II) intel(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
(II) intel(0): Printing probed modes for output VGA1
(II) intel(0): Modeline "2048x1152"x59.9  156.75  2048 2096 2128 2208  1152 1155 1160 1185 +hsync -vsync (71.0 kHz)
(II) intel(0): Modeline "2048x1152_60.00"x59.9  197.00  2048 2184 2400 2752  1152 1155 1160 1195 -hsync +vsync (71.6 kHz)
(II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)Last time, after I removed the extra information I had, I went into System > Preferences > Display and saw that 2048x 1152 was actually available to select. Clicked it and that's when my screen turned back and walla, back to vertical orange line of death on left side.

I am currently running in 1024x768.

---

### Post by qyot27 on 2010-03-11
I recently had to deal with the '2 inches of black on the right side' issue with my grandfather's SyncMaster 2494 monitor when using 1920x1080 (and the black was there for 1080, a 16:9 resolution, even when it *wasn't* there for 1360x768, another 16:9 resolution).

The solution was mind-numbingly simple, and I actually think I found it by accident.  I knew the monitor had an Auto-adjust function, but I didn't think about using it with Ubuntu.  Put the screen on the desired resolution, and then told it to auto-adjust.  The black excess on the right side disappeared and 1920x1080 took up the full proper amount of screen space.  And it remembers, too, so I don't have to continually tell it to adjust whenever I muck around with the resolution.

Don't know if this would help, though.  Just thought I'd mention it.

---

### Post by patchwork on 2010-03-11
```
(II) intel(0): Using user preference for initial modes
(II) intel(0): Output VGA1 using initial mode 2048x1152
```

This is where I'm getting confused....


Let's try something slightly different.  Place a # in front of your modeline.  This will prevent the line from being read.   It's possible that the timings are not working for your card...

That being said, there are validated vesa modes for the 2048x1152 resolution, but each requires the horizsync to be set back to 28-72.

So, to recap, let's try this.
put a # in front of the modeline
# Modeline .....

Change HorizSync to 
HorizSync 28-72

restart x

If you go back to the orange bar again, the problem is likely that your card can't handle the high horizsync value....

---

### Post by mystik_spiral on 2010-03-11
> **patchwork said:**
> ```
(II) intel(0): Using user preference for initial modes
(II) intel(0): Output VGA1 using initial mode 2048x1152
```This is where I'm getting confused....


Let's try something slightly different.  Place a # in front of your modeline.  This will prevent the line from being read.   It's possible that the timings are not working for your card...

That being said, there are validated vesa modes for the 2048x1152 resolution, but each requires the horizsync to be set back to 28-72.

So, to recap, let's try this.
put a # in front of the modeline
# Modeline .....

Change HorizSync to 
HorizSync 28-72

restart x

If you go back to the orange bar again, the problem is likely that your card can't handle the high horizsync value....
I'm trying to open my /etc/x11/Xorg.conf and it keeps opening up with a blank document.

---

### Post by patchwork on 2010-03-11
it's xorg, not Xorg

---

### Post by mystik_spiral on 2010-03-11
orange line of death.

but then why does it work for windows when I set the resolution as 2048x1152?

---

### Post by patchwork on 2010-03-11
I don't know the answer to that...

Sorry I can't be of more help.

---

### Post by mystik_spiral on 2010-03-11
thanks for the effort. 

so you think I need a new video card? how much do those cost? haha

---

### Post by patchwork on 2010-03-11
Is there any way you can get a copy of the /var/log/Xorg.0.log immediately after the orange screen (i.e.from console)  

This will give us a better idea about what is actually happening at the critical time.  The last log you posted was from the 1024x768 resolution.

Can you drop to console and save a copy of the log, then change the xorg.conf so that you can restart x in 1024x768 and repost the log?

---

### Post by mystik_spiral on 2010-03-11
> **qyot27 said:**
> I recently had to deal with the '2 inches of black on the right side' issue with my grandfather's SyncMaster 2494 monitor when using 1920x1080 (and the black was there for 1080, a 16:9 resolution, even when it *wasn't* there for 1360x768, another 16:9 resolution).

The solution was mind-numbingly simple, and I actually think I found it by accident.  I knew the monitor had an Auto-adjust function, but I didn't think about using it with Ubuntu.  **Put the screen on the desired resolution**, and then told it to auto-adjust.  The black excess on the right side disappeared and 1920x1080 took up the full proper amount of screen space.  And it remembers, too, so I don't have to continually tell it to adjust whenever I muck around with the resolution.

Don't know if this would help, though.  Just thought I'd mention it.
That's the problem right now. I cannot do that or it goes into a fully black screen with a orange vertical line coming down the left side of monitor.

---

### Post by patchwork on 2010-03-11
I don't know if you need a new video card....there may be options out there (i.e. updated drivers), but I have no experience personally with intel video drivers.

---

### Post by mystik_spiral on 2010-03-11
> **patchwork said:**
> Is there any way you can get a copy of the /var/log/Xorg.0.log immediately after the orange screen (i.e.from console)  

This will give us a better idea about what is actually happening at the critical time.  The last log you posted was from the 1024x768 resolution.

Can you drop to console and save a copy of the log, then change the xorg.conf so that you can restart x in 1024x768 and repost the log?
so you wont me to purposely get the orange line back so we can try this?

---

### Post by patchwork on 2010-03-11
Yeah, now that we know what causes (and fixes-ish) this condition.  The log from the orange screen boot might help us further.

---

### Post by mystik_spiral on 2010-03-11
Regrettably, I am running out of time and need to get going to work for an overnight shift. I will either be back early in morning or sometime tomorrow evening.

thanks. I'll post the log in critical status once I have more time.

---

### Post by patchwork on 2010-03-11
OK, good luck

---

### Post by pj_kare on 2010-03-12
I noticed from your first post in this newer thread that when you used the Modeline generator that you may not have entered a refresh rate.
[FONT=Courier New][FONT=Verdana]As seen in bold below.[/FONT] [/FONT]
 
> Modeline "2048x1152@**0**" 0.00 2048 2080 2080 2112 1152 1181 1181 1210
 
However if you add 60 as the refresh rate in the Modeline generator it produces this: 
 
Modeline "2048x1152@[COLOR=red]60[/COLOR]" [COLOR=red]211.75[/COLOR] 2048 2080 [COLOR=red]2880[/COLOR] [COLOR=red]2912[/COLOR] 1152 [COLOR=red]1175[/COLOR] [COLOR=red]1186[/COLOR] 1210
(I marked the difference in red)
 
I have no idea if it makes any difference or not.
 
(I found the refresh rate (60) for your monitor on a Review page for it.)

---

### Post by mystik_spiral on 2010-03-12
> **pj_kare said:**
> I noticed from your first post in this newer thread that when you used the Modeline generator that you may not have entered a refresh rate.
[FONT=Courier New][FONT=Verdana]As seen in bold below.[/FONT] [/FONT]
 

 
However if you add 60 as the refresh rate in the Modeline generator it produces this: 
 
Modeline "2048x1152@[COLOR=red]60[/COLOR]" [COLOR=red]211.75[/COLOR] 2048 2080 [COLOR=red]2880[/COLOR] [COLOR=red]2912[/COLOR] 1152 [COLOR=red]1175[/COLOR] [COLOR=red]1186[/COLOR] 1210
(I marked the difference in red)
 
I have no idea if it makes any difference or not.
 
(I found the refresh rate (60) for your monitor on a Review page for it.)
okay...i'm going to make those corrections and now try patchwork's idea.

---

### Post by patchwork on 2010-03-12
That modeline was one of the first things to go.  As of right now there is no modeline (commented out), 2048x1152 is being validated as a Vesa Mode, but the hsync value (72khz) needed to drive the mode is causing the orange screen.

---

### Post by mystik_spiral on 2010-03-12
> **patchwork said:**
> That modeline was one of the first things to go.  As of right now there is no modeline (commented out), 2048x1152 is being validated as a Vesa Mode, but the hsync value (72khz) needed to drive the mode is causing the orange screen.
i have no comment for the above (basically because i'm tired) but I tried to copy the log into another name after the orange line of death appeared and this is what came up in the console:

> cp: missing destination file operand after /var/log/Xorg.0.log.home/beckie/desktop/xlog.txtplease advise.

oh, so my username should be in "< >"?

---

### Post by patchwork on 2010-03-12
there should not be a . between the /var/log/Xorg.0.log and the destination file

---

### Post by mystik_spiral on 2010-03-12
> **patchwork said:**
> there should not be a . between the /var/log/Xorg.0.log and the destination file
now this came up:

> -bash: beckie: no such file or directoryI think that is my username though I'm not even sure. Looking at System >Preferences > About Me, it looks to be the case. 

this is what I wrote down:

```
sudo cp /var/log/Xorg.0.log/ home/<beckie>/Desktop/xlog.txt
```

---

### Post by mystik_spiral on 2010-03-12
> **patchwork said:**
> That modeline was one of the first things to go.  As of right now there is no modeline (commented out), 2048x1152 is being validated as a Vesa Mode, but the hsync value (72khz) needed to drive the mode is causing the orange screen.
k, this makes perfect sense re-reading it. I re-inserted the values that we've used prior including the "#" before the modeline.

---

### Post by mystik_spiral on 2010-03-12
hi patchwork (or someone else),

sorry, this is taking longer than it should (my apologies) but I can't seem to get the correct code going here. can you help me out? see two posts above.

i'm planning on going to bed in a bit and i would love for you to be able to get the log with the "bad" resolution information (during the messed up screen) and take a glance over it.

thanks!

---

### Post by JKyleOKC on 2010-03-12
Try this to copy that log file:
```
cp /var/log/Xorg.0.log $HOME/desktop/xlog.txt
```
The "$HOME" will automagically be replaced by the path to your home directory. Be sure to have the blank spaces after "cp" and "log" since the command processor uses them to help determine what you want it to do.

---

### Post by patchwork on 2010-03-12
Like Jkyle said, but make sure Desktop has a capital D

---

### Post by orky7 on 2010-03-12
u know what i always afraid this thing will happen to me also, so when i go to buy a extra monitor for my old lappy i just take my lappy to the shop and check it by myself each and every monitor to ensure it work for me

anyways there is a greater chance that the zoom effect will be there as your motherboard does not support such high resolution and also the aspect resolution conflicts so just try to upgrade the driver of the graphic and try to make your panning area large to reduce the black/blank space, in new motherboards panning is in advance settings at least on my one..

---

### Post by mystik_spiral on 2010-03-12
here we go:

```

X.Org X Server 1.6.4
Release Date: 2009-9-27
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux beckie-desktop 2.6.31-20-generic #57-Ubuntu SMP Mon Feb 8 09:05:19 UTC 2010 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-20-generic root=UUID=aa199442-43f3-44ba-b70a-3bc870b1a4e3 ro quiet splash
Build Date: 14 November 2009  05:48:26PM
xorg-server 2:1.6.4-2ubuntu4.1 (buildd@) 
    Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Fri Mar 12 16:26:40 2010
(==) Using config file: "/etc/X11/xorg.conf"
(==) No Layout section.  Using the first Screen section.
(**) |-->Screen "Screen0" (0)
(**) |   |-->Monitor "Monitor0"
(**) |   |-->Device "Device0"
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

(--) PCI:*(0:0:2:0) 8086:2572:1028:019d Intel Corporation 82865G Integrated Graphics Controller rev 2, Mem @ 0xe8000000/134217728, 0xfeb80000/524288, I/O @ 0x0000ed98/8
(II) Open ACPI successful (/var/run/acpid.socket)
(II) System resource ranges:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [4] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [5] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
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
(II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
    i810-dc100, i810e, i815, i830M, 845G, 852GM/855GM, 865G, 915G,
    E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
    965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
    4 Series, G45/G43, Q45/Q43, G41, B43, Clarkdale, Arrandale
(II) Primary Device is: PCI 00@00:02:0
(II) resource ranges after probing:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [4] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [5] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: Searching for BusID pci:0000:00:02.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: drmOpenMinor returns 8
drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
(**) intel(0): Depth 24, (--) framebuffer bpp 32
(==) intel(0): RGB weight 888
(==) intel(0): Default visual is TrueColor
(II) intel(0): Integrated Graphics Chipset: Intel(R) 865G
(--) intel(0): Chipset: "865G"
(II) intel(0): Output VGA1 using monitor section Monitor0
(II) intel(0): EDID for output VGA1
(II) intel(0): Manufacturer: SAM  Model: 584  Serial#: 1297691187
(II) intel(0): Year: 2009  Week: 51
(II) intel(0): EDID Version: 1.3
(II) intel(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) intel(0): Sync:  Separate  Composite  SyncOnGreen
(II) intel(0): Max Image Size [cm]: horiz.: 51  vert.: 29
(II) intel(0): Gamma: 2.20
(II) intel(0): DPMS capabilities: Off; RGB/Color Display
(II) intel(0): First detailed timing is preferred mode
(II) intel(0): redX: 0.640 redY: 0.330   greenX: 0.300 greenY: 0.600
(II) intel(0): blueX: 0.150 blueY: 0.060   whiteX: 0.312 whiteY: 0.329
(II) intel(0): Supported established timings:
(II) intel(0): 640x480@60Hz
(II) intel(0): 800x600@56Hz
(II) intel(0): 800x600@60Hz
(II) intel(0): 1024x768@60Hz
(II) intel(0): Manufacturer's mask: 0
(II) intel(0): Supported standard timings:
(II) intel(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) intel(0): #1: hsize: 1280  vsize 960  refresh: 60  vid: 16513
(II) intel(0): #2: hsize: 1280  vsize 800  refresh: 60  vid: 129
(II) intel(0): #3: hsize: 1440  vsize 900  refresh: 60  vid: 149
(II) intel(0): #4: hsize: 1680  vsize 1050  refresh: 60  vid: 179
(II) intel(0): Supported detailed timing:
(II) intel(0): clock: 156.8 MHz   Image Size:  510 x 287 mm
(II) intel(0): h_active: 2048  h_sync: 2096  h_sync_end 2128 h_blank_end 2208 h_border: 0
(II) intel(0): v_active: 1152  v_sync: 1155  v_sync_end 1160 v_blanking: 1185 v_border: 0
(II) intel(0): Ranges: V min: 56 V max: 60 Hz, H min: 30 H max: 81 kHz, PixClock max 160 MHz
(II) intel(0): Monitor name: SyncMaster
(II) intel(0): Serial No: HVMSC01920
(II) intel(0): EDID (in hex):
(II) intel(0):     00ffffffffffff004c2d84053332594d
(II) intel(0):     331301030e331d782aee91a3544c9926
(II) intel(0):     0f50542308008180814081009500b300
(II) intel(0):     0101010101013b3d00a0808021403020
(II) intel(0):     3500fe1f1100001a000000fd00383c1e
(II) intel(0):     5110000a202020202020000000fc0053
(II) intel(0):     796e634d61737465720a2020000000ff
(II) intel(0):     0048564d534330313932300a202000aa
(II) intel(0): EDID vendor "SAM", prod id 1412
(II) intel(0): Using hsync ranges from config file
(II) intel(0): Using vrefresh ranges from config file
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "2048x1152"x0.0  156.75  2048 2096 2128 2208  1152 1155 1160 1185 +hsync -vsync (71.0 kHz)
(II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) intel(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
(II) intel(0): Modeline "1280x800"x0.0   83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync (49.7 kHz)
(II) intel(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
(II) intel(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
(II) intel(0): Printing probed modes for output VGA1
(II) intel(0): Modeline "2048x1152"x59.9  156.75  2048 2096 2128 2208  1152 1155 1160 1185 +hsync -vsync (71.0 kHz)
(II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Output VGA1 connected
(II) intel(0): Using user preference for initial modes
(II) intel(0): Output VGA1 using initial mode 2048x1152
(==) intel(0): video overlay key set to 0x101fe
(==) intel(0): Using gamma correction (1.0, 1.0, 1.0)
(**) intel(0): Display dimensions: (510, 290) mm
(**) intel(0): DPI set to (101, 100)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.4
(==) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [4] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [5] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
(II) intel(0): [DRI2] Setup complete
(**) intel(0): Framebuffer compression disabled
(**) intel(0): Tiling enabled
(**) intel(0): SwapBuffers wait enabled
(==) intel(0): VideoRam: 131072 KB
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
(WW) intel(0): Disabling Xv because no adaptors could be initialized.
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
(II) intel(0): Setting screen physical size to 510 x 287
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
(II) config/hal: Adding input device Logitech Optical USB Mouse
(**) Logitech Optical USB Mouse: always reports core events
(**) Logitech Optical USB Mouse: Device: "/dev/input/event4"
(II) Logitech Optical USB Mouse: Found 3 mouse buttons
(II) Logitech Optical USB Mouse: Found x and y relative axes
(II) Logitech Optical USB Mouse: Found scroll wheel(s)
(II) Logitech Optical USB Mouse: Configuring as mouse
(**) Logitech Optical USB Mouse: YAxisMapping: buttons 4 and 5
(**) Logitech Optical USB Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Logitech Optical USB Mouse" (type: MOUSE)
(**) Logitech Optical USB Mouse: (accel) keeping acceleration scheme 1
(**) Logitech Optical USB Mouse: (accel) filter chain progression: 2.00
(**) Logitech Optical USB Mouse: (accel) filter stage 0: 20.00 ms
(**) Logitech Optical USB Mouse: (accel) set acceleration profile 0
(II) Logitech Optical USB Mouse: initialized for relative axes.
(II) intel(0): EDID for output VGA1
(II) intel(0): Manufacturer: SAM  Model: 584  Serial#: 1297691187
(II) intel(0): Year: 2009  Week: 51
(II) intel(0): EDID Version: 1.3
(II) intel(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) intel(0): Sync:  Separate  Composite  SyncOnGreen
(II) intel(0): Max Image Size [cm]: horiz.: 51  vert.: 29
(II) intel(0): Gamma: 2.20
(II) intel(0): DPMS capabilities: Off; RGB/Color Display
(II) intel(0): First detailed timing is preferred mode
(II) intel(0): redX: 0.640 redY: 0.330   greenX: 0.300 greenY: 0.600
(II) intel(0): blueX: 0.150 blueY: 0.060   whiteX: 0.312 whiteY: 0.329
(II) intel(0): Supported established timings:
(II) intel(0): 640x480@60Hz
(II) intel(0): 800x600@56Hz
(II) intel(0): 800x600@60Hz
(II) intel(0): 1024x768@60Hz
(II) intel(0): Manufacturer's mask: 0
(II) intel(0): Supported standard timings:
(II) intel(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) intel(0): #1: hsize: 1280  vsize 960  refresh: 60  vid: 16513
(II) intel(0): #2: hsize: 1280  vsize 800  refresh: 60  vid: 129
(II) intel(0): #3: hsize: 1440  vsize 900  refresh: 60  vid: 149
(II) intel(0): #4: hsize: 1680  vsize 1050  refresh: 60  vid: 179
(II) intel(0): Supported detailed timing:
(II) intel(0): clock: 156.8 MHz   Image Size:  510 x 287 mm
(II) intel(0): h_active: 2048  h_sync: 2096  h_sync_end 2128 h_blank_end 2208 h_border: 0
(II) intel(0): v_active: 1152  v_sync: 1155  v_sync_end 1160 v_blanking: 1185 v_border: 0
(II) intel(0): Ranges: V min: 56 V max: 60 Hz, H min: 30 H max: 81 kHz, PixClock max 160 MHz
(II) intel(0): Monitor name: SyncMaster
(II) intel(0): Serial No: HVMSC01920
(II) intel(0): EDID (in hex):
(II) intel(0):     00ffffffffffff004c2d84053332594d
(II) intel(0):     331301030e331d782aee91a3544c9926
(II) intel(0):     0f50542308008180814081009500b300
(II) intel(0):     0101010101013b3d00a0808021403020
(II) intel(0):     3500fe1f1100001a000000fd00383c1e
(II) intel(0):     5110000a202020202020000000fc0053
(II) intel(0):     796e634d61737465720a2020000000ff
(II) intel(0):     0048564d534330313932300a202000aa
(II) intel(0): EDID vendor "SAM", prod id 1412
(II) intel(0): Using hsync ranges from config file
(II) intel(0): Using vrefresh ranges from config file
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "2048x1152"x0.0  156.75  2048 2096 2128 2208  1152 1155 1160 1185 +hsync -vsync (71.0 kHz)
(II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) intel(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
(II) intel(0): Modeline "1280x800"x0.0   83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync (49.7 kHz)
(II) intel(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
(II) intel(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
(II) intel(0): Printing probed modes for output VGA1
(II) intel(0): Modeline "2048x1152"x59.9  156.75  2048 2096 2128 2208  1152 1155 1160 1185 +hsync -vsync (71.0 kHz)
(II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): EDID for output VGA1
(II) intel(0): Manufacturer: SAM  Model: 584  Serial#: 1297691187
(II) intel(0): Year: 2009  Week: 51
(II) intel(0): EDID Version: 1.3
(II) intel(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) intel(0): Sync:  Separate  Composite  SyncOnGreen
(II) intel(0): Max Image Size [cm]: horiz.: 51  vert.: 29
(II) intel(0): Gamma: 2.20
(II) intel(0): DPMS capabilities: Off; RGB/Color Display
(II) intel(0): First detailed timing is preferred mode
(II) intel(0): redX: 0.640 redY: 0.330   greenX: 0.300 greenY: 0.600
(II) intel(0): blueX: 0.150 blueY: 0.060   whiteX: 0.312 whiteY: 0.329
(II) intel(0): Supported established timings:
(II) intel(0): 640x480@60Hz
(II) intel(0): 800x600@56Hz
(II) intel(0): 800x600@60Hz
(II) intel(0): 1024x768@60Hz
(II) intel(0): Manufacturer's mask: 0
(II) intel(0): Supported standard timings:
(II) intel(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) intel(0): #1: hsize: 1280  vsize 960  refresh: 60  vid: 16513
(II) intel(0): #2: hsize: 1280  vsize 800  refresh: 60  vid: 129
(II) intel(0): #3: hsize: 1440  vsize 900  refresh: 60  vid: 149
(II) intel(0): #4: hsize: 1680  vsize 1050  refresh: 60  vid: 179
(II) intel(0): Supported detailed timing:
(II) intel(0): clock: 156.8 MHz   Image Size:  510 x 287 mm
(II) intel(0): h_active: 2048  h_sync: 2096  h_sync_end 2128 h_blank_end 2208 h_border: 0
(II) intel(0): v_active: 1152  v_sync: 1155  v_sync_end 1160 v_blanking: 1185 v_border: 0
(II) intel(0): Ranges: V min: 56 V max: 60 Hz, H min: 30 H max: 81 kHz, PixClock max 160 MHz
(II) intel(0): Monitor name: SyncMaster
(II) intel(0): Serial No: HVMSC01920
(II) intel(0): EDID (in hex):
(II) intel(0):     00ffffffffffff004c2d84053332594d
(II) intel(0):     331301030e331d782aee91a3544c9926
(II) intel(0):     0f50542308008180814081009500b300
(II) intel(0):     0101010101013b3d00a0808021403020
(II) intel(0):     3500fe1f1100001a000000fd00383c1e
(II) intel(0):     5110000a202020202020000000fc0053
(II) intel(0):     796e634d61737465720a2020000000ff
(II) intel(0):     0048564d534330313932300a202000aa
(II) intel(0): EDID vendor "SAM", prod id 1412
(II) intel(0): Using hsync ranges from config file
(II) intel(0): Using vrefresh ranges from config file
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "2048x1152"x0.0  156.75  2048 2096 2128 2208  1152 1155 1160 1185 +hsync -vsync (71.0 kHz)
(II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) intel(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
(II) intel(0): Modeline "1280x800"x0.0   83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync (49.7 kHz)
(II) intel(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
(II) intel(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
(II) intel(0): Printing probed modes for output VGA1
(II) intel(0): Modeline "2048x1152"x59.9  156.75  2048 2096 2128 2208  1152 1155 1160 1185 +hsync -vsync (71.0 kHz)
(II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): EDID for output VGA1
(II) intel(0): Manufacturer: SAM  Model: 584  Serial#: 1297691187
(II) intel(0): Year: 2009  Week: 51
(II) intel(0): EDID Version: 1.3
(II) intel(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) intel(0): Sync:  Separate  Composite  SyncOnGreen
(II) intel(0): Max Image Size [cm]: horiz.: 51  vert.: 29
(II) intel(0): Gamma: 2.20
(II) intel(0): DPMS capabilities: Off; RGB/Color Display
(II) intel(0): First detailed timing is preferred mode
(II) intel(0): redX: 0.640 redY: 0.330   greenX: 0.300 greenY: 0.600
(II) intel(0): blueX: 0.150 blueY: 0.060   whiteX: 0.312 whiteY: 0.329
(II) intel(0): Supported established timings:
(II) intel(0): 640x480@60Hz
(II) intel(0): 800x600@56Hz
(II) intel(0): 800x600@60Hz
(II) intel(0): 1024x768@60Hz
(II) intel(0): Manufacturer's mask: 0
(II) intel(0): Supported standard timings:
(II) intel(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) intel(0): #1: hsize: 1280  vsize 960  refresh: 60  vid: 16513
(II) intel(0): #2: hsize: 1280  vsize 800  refresh: 60  vid: 129
(II) intel(0): #3: hsize: 1440  vsize 900  refresh: 60  vid: 149
(II) intel(0): #4: hsize: 1680  vsize 1050  refresh: 60  vid: 179
(II) intel(0): Supported detailed timing:
(II) intel(0): clock: 156.8 MHz   Image Size:  510 x 287 mm
(II) intel(0): h_active: 2048  h_sync: 2096  h_sync_end 2128 h_blank_end 2208 h_border: 0
(II) intel(0): v_active: 1152  v_sync: 1155  v_sync_end 1160 v_blanking: 1185 v_border: 0
(II) intel(0): Ranges: V min: 56 V max: 60 Hz, H min: 30 H max: 81 kHz, PixClock max 160 MHz
(II) intel(0): Monitor name: SyncMaster
(II) intel(0): Serial No: HVMSC01920
(II) intel(0): EDID (in hex):
(II) intel(0):     00ffffffffffff004c2d84053332594d
(II) intel(0):     331301030e331d782aee91a3544c9926
(II) intel(0):     0f50542308008180814081009500b300
(II) intel(0):     0101010101013b3d00a0808021403020
(II) intel(0):     3500fe1f1100001a000000fd00383c1e
(II) intel(0):     5110000a202020202020000000fc0053
(II) intel(0):     796e634d61737465720a2020000000ff
(II) intel(0):     0048564d534330313932300a202000aa
(II) intel(0): EDID vendor "SAM", prod id 1412
(II) intel(0): Using hsync ranges from config file
(II) intel(0): Using vrefresh ranges from config file
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "2048x1152"x0.0  156.75  2048 2096 2128 2208  1152 1155 1160 1185 +hsync -vsync (71.0 kHz)
(II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) intel(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
(II) intel(0): Modeline "1280x800"x0.0   83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync (49.7 kHz)
(II) intel(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
(II) intel(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
(II) intel(0): Printing probed modes for output VGA1
(II) intel(0): Modeline "2048x1152"x59.9  156.75  2048 2096 2128 2208  1152 1155 1160 1185 +hsync -vsync (71.0 kHz)
(II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Allocate new frame buffer 1024x768 stride 1024
(II) intel(0): EDID for output VGA1
(II) intel(0): Manufacturer: SAM  Model: 584  Serial#: 1297691187
(II) intel(0): Year: 2009  Week: 51
(II) intel(0): EDID Version: 1.3
(II) intel(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) intel(0): Sync:  Separate  Composite  SyncOnGreen
(II) intel(0): Max Image Size [cm]: horiz.: 51  vert.: 29
(II) intel(0): Gamma: 2.20
(II) intel(0): DPMS capabilities: Off; RGB/Color Display
(II) intel(0): First detailed timing is preferred mode
(II) intel(0): redX: 0.640 redY: 0.330   greenX: 0.300 greenY: 0.600
(II) intel(0): blueX: 0.150 blueY: 0.060   whiteX: 0.312 whiteY: 0.329
(II) intel(0): Supported established timings:
(II) intel(0): 640x480@60Hz
(II) intel(0): 800x600@56Hz
(II) intel(0): 800x600@60Hz
(II) intel(0): 1024x768@60Hz
(II) intel(0): Manufacturer's mask: 0
(II) intel(0): Supported standard timings:
(II) intel(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) intel(0): #1: hsize: 1280  vsize 960  refresh: 60  vid: 16513
(II) intel(0): #2: hsize: 1280  vsize 800  refresh: 60  vid: 129
(II) intel(0): #3: hsize: 1440  vsize 900  refresh: 60  vid: 149
(II) intel(0): #4: hsize: 1680  vsize 1050  refresh: 60  vid: 179
(II) intel(0): Supported detailed timing:
(II) intel(0): clock: 156.8 MHz   Image Size:  510 x 287 mm
(II) intel(0): h_active: 2048  h_sync: 2096  h_sync_end 2128 h_blank_end 2208 h_border: 0
(II) intel(0): v_active: 1152  v_sync: 1155  v_sync_end 1160 v_blanking: 1185 v_border: 0
(II) intel(0): Ranges: V min: 56 V max: 60 Hz, H min: 30 H max: 81 kHz, PixClock max 160 MHz
(II) intel(0): Monitor name: SyncMaster
(II) intel(0): Serial No: HVMSC01920
(II) intel(0): EDID (in hex):
(II) intel(0):     00ffffffffffff004c2d84053332594d
(II) intel(0):     331301030e331d782aee91a3544c9926
(II) intel(0):     0f50542308008180814081009500b300
(II) intel(0):     0101010101013b3d00a0808021403020
(II) intel(0):     3500fe1f1100001a000000fd00383c1e
(II) intel(0):     5110000a202020202020000000fc0053
(II) intel(0):     796e634d61737465720a2020000000ff
(II) intel(0):     0048564d534330313932300a202000aa
(II) intel(0): EDID vendor "SAM", prod id 1412
(II) intel(0): Using hsync ranges from config file
(II) intel(0): Using vrefresh ranges from config file
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "2048x1152"x0.0  156.75  2048 2096 2128 2208  1152 1155 1160 1185 +hsync -vsync (71.0 kHz)
(II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) intel(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
(II) intel(0): Modeline "1280x800"x0.0   83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync (49.7 kHz)
(II) intel(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
(II) intel(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
(II) intel(0): Printing probed modes for output VGA1
(II) intel(0): Modeline "2048x1152"x59.9  156.75  2048 2096 2128 2208  1152 1155 1160 1185 +hsync -vsync (71.0 kHz)
(II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): EDID for output VGA1
(II) intel(0): Manufacturer: SAM  Model: 584  Serial#: 1297691187
(II) intel(0): Year: 2009  Week: 51
(II) intel(0): EDID Version: 1.3
(II) intel(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) intel(0): Sync:  Separate  Composite  SyncOnGreen
(II) intel(0): Max Image Size [cm]: horiz.: 51  vert.: 29
(II) intel(0): Gamma: 2.20
(II) intel(0): DPMS capabilities: Off; RGB/Color Display
(II) intel(0): First detailed timing is preferred mode
(II) intel(0): redX: 0.640 redY: 0.330   greenX: 0.300 greenY: 0.600
(II) intel(0): blueX: 0.150 blueY: 0.060   whiteX: 0.312 whiteY: 0.329
(II) intel(0): Supported established timings:
(II) intel(0): 640x480@60Hz
(II) intel(0): 800x600@56Hz
(II) intel(0): 800x600@60Hz
(II) intel(0): 1024x768@60Hz
(II) intel(0): Manufacturer's mask: 0
(II) intel(0): Supported standard timings:
(II) intel(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) intel(0): #1: hsize: 1280  vsize 960  refresh: 60  vid: 16513
(II) intel(0): #2: hsize: 1280  vsize 800  refresh: 60  vid: 129
(II) intel(0): #3: hsize: 1440  vsize 900  refresh: 60  vid: 149
(II) intel(0): #4: hsize: 1680  vsize 1050  refresh: 60  vid: 179
(II) intel(0): Supported detailed timing:
(II) intel(0): clock: 156.8 MHz   Image Size:  510 x 287 mm
(II) intel(0): h_active: 2048  h_sync: 2096  h_sync_end 2128 h_blank_end 2208 h_border: 0
(II) intel(0): v_active: 1152  v_sync: 1155  v_sync_end 1160 v_blanking: 1185 v_border: 0
(II) intel(0): Ranges: V min: 56 V max: 60 Hz, H min: 30 H max: 81 kHz, PixClock max 160 MHz
(II) intel(0): Monitor name: SyncMaster
(II) intel(0): Serial No: HVMSC01920
(II) intel(0): EDID (in hex):
(II) intel(0):     00ffffffffffff004c2d84053332594d
(II) intel(0):     331301030e331d782aee91a3544c9926
(II) intel(0):     0f50542308008180814081009500b300
(II) intel(0):     0101010101013b3d00a0808021403020
(II) intel(0):     3500fe1f1100001a000000fd00383c1e
(II) intel(0):     5110000a202020202020000000fc0053
(II) intel(0):     796e634d61737465720a2020000000ff
(II) intel(0):     0048564d534330313932300a202000aa
(II) intel(0): EDID vendor "SAM", prod id 1412
(II) intel(0): Using hsync ranges from config file
(II) intel(0): Using vrefresh ranges from config file
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "2048x1152"x0.0  156.75  2048 2096 2128 2208  1152 1155 1160 1185 +hsync -vsync (71.0 kHz)
(II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) intel(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
(II) intel(0): Modeline "1280x800"x0.0   83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync (49.7 kHz)
(II) intel(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
(II) intel(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
(II) intel(0): Printing probed modes for output VGA1
(II) intel(0): Modeline "2048x1152"x59.9  156.75  2048 2096 2128 2208  1152 1155 1160 1185 +hsync -vsync (71.0 kHz)
(II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): EDID for output VGA1
(II) intel(0): Manufacturer: SAM  Model: 584  Serial#: 1297691187
(II) intel(0): Year: 2009  Week: 51
(II) intel(0): EDID Version: 1.3
(II) intel(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) intel(0): Sync:  Separate  Composite  SyncOnGreen
(II) intel(0): Max Image Size [cm]: horiz.: 51  vert.: 29
(II) intel(0): Gamma: 2.20
(II) intel(0): DPMS capabilities: Off; RGB/Color Display
(II) intel(0): First detailed timing is preferred mode
(II) intel(0): redX: 0.640 redY: 0.330   greenX: 0.300 greenY: 0.600
(II) intel(0): blueX: 0.150 blueY: 0.060   whiteX: 0.312 whiteY: 0.329
(II) intel(0): Supported established timings:
(II) intel(0): 640x480@60Hz
(II) intel(0): 800x600@56Hz
(II) intel(0): 800x600@60Hz
(II) intel(0): 1024x768@60Hz
(II) intel(0): Manufacturer's mask: 0
(II) intel(0): Supported standard timings:
(II) intel(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) intel(0): #1: hsize: 1280  vsize 960  refresh: 60  vid: 16513
(II) intel(0): #2: hsize: 1280  vsize 800  refresh: 60  vid: 129
(II) intel(0): #3: hsize: 1440  vsize 900  refresh: 60  vid: 149
(II) intel(0): #4: hsize: 1680  vsize 1050  refresh: 60  vid: 179
(II) intel(0): Supported detailed timing:
(II) intel(0): clock: 156.8 MHz   Image Size:  510 x 287 mm
(II) intel(0): h_active: 2048  h_sync: 2096  h_sync_end 2128 h_blank_end 2208 h_border: 0
(II) intel(0): v_active: 1152  v_sync: 1155  v_sync_end 1160 v_blanking: 1185 v_border: 0
(II) intel(0): Ranges: V min: 56 V max: 60 Hz, H min: 30 H max: 81 kHz, PixClock max 160 MHz
(II) intel(0): Monitor name: SyncMaster
(II) intel(0): Serial No: HVMSC01920
(II) intel(0): EDID (in hex):
(II) intel(0):     00ffffffffffff004c2d84053332594d
(II) intel(0):     331301030e331d782aee91a3544c9926
(II) intel(0):     0f50542308008180814081009500b300
(II) intel(0):     0101010101013b3d00a0808021403020
(II) intel(0):     3500fe1f1100001a000000fd00383c1e
(II) intel(0):     5110000a202020202020000000fc0053
(II) intel(0):     796e634d61737465720a2020000000ff
(II) intel(0):     0048564d534330313932300a202000aa
(II) intel(0): EDID vendor "SAM", prod id 1412
(II) intel(0): Using hsync ranges from config file
(II) intel(0): Using vrefresh ranges from config file
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "2048x1152"x0.0  156.75  2048 2096 2128 2208  1152 1155 1160 1185 +hsync -vsync (71.0 kHz)
(II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) intel(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
(II) intel(0): Modeline "1280x800"x0.0   83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync (49.7 kHz)
(II) intel(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
(II) intel(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
(II) intel(0): Printing probed modes for output VGA1
(II) intel(0): Modeline "2048x1152"x59.9  156.75  2048 2096 2128 2208  1152 1155 1160 1185 +hsync -vsync (71.0 kHz)
(II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): EDID for output VGA1
(II) intel(0): Manufacturer: SAM  Model: 584  Serial#: 1297691187
(II) intel(0): Year: 2009  Week: 51
(II) intel(0): EDID Version: 1.3
(II) intel(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) intel(0): Sync:  Separate  Composite  SyncOnGreen
(II) intel(0): Max Image Size [cm]: horiz.: 51  vert.: 29
(II) intel(0): Gamma: 2.20
(II) intel(0): DPMS capabilities: Off; RGB/Color Display
(II) intel(0): First detailed timing is preferred mode
(II) intel(0): redX: 0.640 redY: 0.330   greenX: 0.300 greenY: 0.600
(II) intel(0): blueX: 0.150 blueY: 0.060   whiteX: 0.312 whiteY: 0.329
(II) intel(0): Supported established timings:
(II) intel(0): 640x480@60Hz
(II) intel(0): 800x600@56Hz
(II) intel(0): 800x600@60Hz
(II) intel(0): 1024x768@60Hz
(II) intel(0): Manufacturer's mask: 0
(II) intel(0): Supported standard timings:
(II) intel(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) intel(0): #1: hsize: 1280  vsize 960  refresh: 60  vid: 16513
(II) intel(0): #2: hsize: 1280  vsize 800  refresh: 60  vid: 129
(II) intel(0): #3: hsize: 1440  vsize 900  refresh: 60  vid: 149
(II) intel(0): #4: hsize: 1680  vsize 1050  refresh: 60  vid: 179
(II) intel(0): Supported detailed timing:
(II) intel(0): clock: 156.8 MHz   Image Size:  510 x 287 mm
(II) intel(0): h_active: 2048  h_sync: 2096  h_sync_end 2128 h_blank_end 2208 h_border: 0
(II) intel(0): v_active: 1152  v_sync: 1155  v_sync_end 1160 v_blanking: 1185 v_border: 0
(II) intel(0): Ranges: V min: 56 V max: 60 Hz, H min: 30 H max: 81 kHz, PixClock max 160 MHz
(II) intel(0): Monitor name: SyncMaster
(II) intel(0): Serial No: HVMSC01920
(II) intel(0): EDID (in hex):
(II) intel(0):     00ffffffffffff004c2d84053332594d
(II) intel(0):     331301030e331d782aee91a3544c9926
(II) intel(0):     0f50542308008180814081009500b300
(II) intel(0):     0101010101013b3d00a0808021403020
(II) intel(0):     3500fe1f1100001a000000fd00383c1e
(II) intel(0):     5110000a202020202020000000fc0053
(II) intel(0):     796e634d61737465720a2020000000ff
(II) intel(0):     0048564d534330313932300a202000aa
(II) intel(0): EDID vendor "SAM", prod id 1412
(II) intel(0): Using hsync ranges from config file
(II) intel(0): Using vrefresh ranges from config file
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "2048x1152"x0.0  156.75  2048 2096 2128 2208  1152 1155 1160 1185 +hsync -vsync (71.0 kHz)
(II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) intel(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
(II) intel(0): Modeline "1280x800"x0.0   83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync (49.7 kHz)
(II) intel(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
(II) intel(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
(II) intel(0): Printing probed modes for output VGA1
(II) intel(0): Modeline "2048x1152"x59.9  156.75  2048 2096 2128 2208  1152 1155 1160 1185 +hsync -vsync (71.0 kHz)
(II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Allocate new frame buffer 2048x1152 stride 2048
(II) AIGLX: Suspending AIGLX clients for VT switch
```

---

### Post by patchwork on 2010-03-12
```
 Supported detailed timing:
(II) intel(0): clock: 156.8 MHz   Image Size:  510 x 287 mm
(II) intel(0): h_active: 2048  h_sync: 2096  h_sync_end 2128 h_blank_end 2208 h_border: 0
(II) intel(0): v_active: 1152  v_sync: 1155  v_sync_end 1160 v_blanking: 1185 v_border: 0
(II) intel(0): Ranges: V min: 56 **V max: 60 Hz**, **H min: 30 H max: 81 kHz**, PixClock max 160 MHz
(II) intel(0): Monitor name: SyncMaster
(II) intel(0): Serial No: HVMSC01920
```I don't see anything that blatantly jumps out besides this.

Since your monitor is sending it's edid information just fine, try commenting out the VertRefresh line and the HorizSync line like this:

```
# VertRefresh ....
# HorizSync ......
```The only thing I see is maybe the vert refresh range you have specified (up to 75hz) is too high?

I don't think this is the case, however, since the range specifies 55 -75

If all else fails, you can try this modeline from the above information:
```
Modeline "2048x1152" 156.8 2048 2096 2128 2208 1152 1155 1160 1185 +hysnc -vsync
```But I would try commenting out the two refresh ranges first.

---

### Post by mystik_spiral on 2010-03-12
First idea didn't work.

For the next idea, want me to lose the '#" before the VertRefresh, HorizSync and Modeline or leave them there?

---

### Post by patchwork on 2010-03-12
Just add the new modeline, leave the other lines as they are.

Also, it seems from [here]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/352760") that your video card is extremely buggy.   You may want to try the "NoAccel" "True" line in the "Device" Section...

EDIT:  Clarification...
The last line of your log indicates the the AIGLX (acceleration enabling) is trying to switch modes, and this may be the cause of the hangup.  Not sure about this though.

---

### Post by mystik_spiral on 2010-03-12
to confirm, "NoAccel" "True" beside the existing Device "Device0"?

---

### Post by patchwork on 2010-03-12
```
Option "NoAccel" "True"
``` on a new line in the Section "Device"

---

### Post by mystik_spiral on 2010-03-12
so where it says Section "Device" in the 2nd batch of variables, you want me to add a new line below it with this new information?

also to further confirm, after I am making changes, you want me to restart x, right? (keeping in mind that when I am restarting x, I am in an incorrect but working resolution)

---

### Post by patchwork on 2010-03-12
EDIT: Rather inside of the Device Section (i.e. before the EndSection line)

And yes, restart X (it's the only way to test the x configuration after changing it, that I know of)

---

### Post by mystik_spiral on 2010-03-12
so in between 

VendorName "Intel 82865G"
and
EndSection
?

---

### Post by patchwork on 2010-03-12
Yes, that's fine.  It doesn't matter where, so long as it's between 

Section "Device"

and 

EndSection

---

### Post by mystik_spiral on 2010-03-12
I am now in "low graphics mode". 1280 x 1024 (highest I can go to).

---

### Post by patchwork on 2010-03-12
Hate to ask for this again, but can you post your log?


Only other option I can think of is to turn off the edid information gathering and use ONLY the modeline you put in the file....but this shouldn't be necessary.  But then again, nothing else has worked...

---

### Post by mystik_spiral on 2010-03-12
I am getting a brain fart here. How do I open the logs again? I remember how to do the longer version when i'm in console but not the normal way.

/var/log/Xorg.0.log

am I adding a sudo before this?

sudo cp /var/log/Xorg.0.log ?

---

### Post by patchwork on 2010-03-12
you can just use 
```
gedit /var/log/Xorg.0.log
```

Or open gedit, and open /var/log/Xorg.0.log

---

### Post by mystik_spiral on 2010-03-12
thanks

---

### Post by mystik_spiral on 2010-03-12
short one:

```
X.Org X Server 1.6.4
Release Date: 2009-9-27
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux beckie-desktop 2.6.31-20-generic #57-Ubuntu SMP Mon Feb 8 09:05:19 UTC 2010 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-20-generic root=UUID=aa199442-43f3-44ba-b70a-3bc870b1a4e3 ro quiet splash
Build Date: 14 November 2009  05:48:26PM
xorg-server 2:1.6.4-2ubuntu4.1 (buildd@) 
    Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Fri Mar 12 17:50:53 2010
(==) Using config file: "/etc/X11/xorg.conf"
Parse error on line 7 of section Monitor in file /etc/X11/xorg.conf
    "+hysnc" is not a valid keyword in this section.
(EE) Problem parsing the config file
(EE) Error parsing the config file

Fatal server error:
no screens found

Please consult the The X.Org Foundation support 
     at http://wiki.x.org
 for help. 
Please also check the log file at "/var/log/Xorg.0.log" for additional information.

(WW) xf86CloseConsole: KDSETMODE failed: Bad file descriptor
(WW) xf86CloseConsole: VT_GETMODE failed: Bad file descriptor
(WW) xf86OpenConsole: VT_GETSTATE failed: Bad file descriptor
 ddxSigGiveUp: Closing log
```

---

### Post by mystik_spiral on 2010-03-12
```
Section "Monitor"
Identifier "Monitor0"
VendorName "SAMSUNG"
ModelName "SyncMaster 2343BWX"
# HorizSync 28 - 72
# VertRefresh 55 - 75
Modeline "2048x1152" 156.8 2048 2096 2128 2208 1152 1155 1160 1185 +hysnc -vsync
EndSection

Section "Device"
Identifier "Device0"
Driver "intel"
VendorName "Intel 82865G"
Option "NoAccel" "True"
EndSection

Section "Screen"
Identifier "Screen0"
Device "Device0"
Monitor "Monitor0"
DefaultDepth 24
SubSection "Display"
Depth 24
Modes "2048x1152" "1600x1200" "1024x768"
EndSubSection
EndSection

```

---

### Post by patchwork on 2010-03-12
EDIT: sorry, it's +hsync


it's spelled wrong

Same with vsync

---

### Post by mystik_spiral on 2010-03-12
restarted x.

It went to a black screen. the CTRL ALT F2 keys did nothing. Had to power off machine.
CTRL ALT F1 I tried first actually.

however, in the display preferences, i notice that 2048 x 1152 is an option again (it comes and goes after we make changes).

---

### Post by patchwork on 2010-03-12
On reboot were you able to get into low graphic mode or drop to console?

---

### Post by mystik_spiral on 2010-03-12
neither.

i could try going into 2048x1152 messed up mode, then go into drop to console and try to fetch another bad log over to desktop.

---

### Post by patchwork on 2010-03-12
Hmmm.....if you can't log in, you're going to need to boot from livecd and change the xorg.conf from there to get your gui back (comment out the latest modeline).

If you're daring, you can keep the modeline as is, remove the comment from in front of the horizsync line, and try again.  Otherwise, I'm afraid I can't get your resolution any higher than we have already.


EDIT:  If you can login and access the logs, that'd be great.  I was under the impression you were getting black screen on both x and console?

---

### Post by mystik_spiral on 2010-03-12
when you told me to erase the sync typing error and restart x, that's when it went to a frozen black screen with no way out. however, when I change the settings manual to 2048x1152 in the preferences > display, I am able to go to console, if that makes sense.

so when the all black plus orange line appears, I can go to console; when an entire black screen comes up (sometimes when I restart x), that's when I can't do anything.

but I can always fetch the "bad log" when in black screen + crazy orange line view

log while in 2048x1152:

```
X.Org X Server 1.6.4
Release Date: 2009-9-27
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux beckie-desktop 2.6.31-20-generic #57-Ubuntu SMP Mon Feb 8 09:05:19 UTC 2010 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-20-generic root=UUID=aa199442-43f3-44ba-b70a-3bc870b1a4e3 ro quiet splash
Build Date: 14 November 2009  05:48:26PM
xorg-server 2:1.6.4-2ubuntu4.1 (buildd@) 
    Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Fri Mar 12 18:14:37 2010
(==) Using config file: "/etc/X11/xorg.conf"
(==) No Layout section.  Using the first Screen section.
(**) |-->Screen "Screen0" (0)
(**) |   |-->Monitor "Monitor0"
(**) |   |-->Device "Device0"
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

(--) PCI:*(0:0:2:0) 8086:2572:1028:019d Intel Corporation 82865G Integrated Graphics Controller rev 2, Mem @ 0xe8000000/134217728, 0xfeb80000/524288, I/O @ 0x0000ed98/8
(II) Open ACPI successful (/var/run/acpid.socket)
(II) System resource ranges:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [4] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [5] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
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
(II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
    i810-dc100, i810e, i815, i830M, 845G, 852GM/855GM, 865G, 915G,
    E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
    965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
    4 Series, G45/G43, Q45/Q43, G41, B43, Clarkdale, Arrandale
(II) Primary Device is: PCI 00@00:02:0
(II) resource ranges after probing:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [4] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [5] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: Searching for BusID pci:0000:00:02.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: drmOpenMinor returns 8
drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
(**) intel(0): Depth 24, (--) framebuffer bpp 32
(==) intel(0): RGB weight 888
(==) intel(0): Default visual is TrueColor
(II) intel(0): Integrated Graphics Chipset: Intel(R) 865G
(--) intel(0): Chipset: "865G"
(II) intel(0): Output VGA1 using monitor section Monitor0
(II) intel(0): EDID for output VGA1
(II) intel(0): Manufacturer: SAM  Model: 584  Serial#: 1297691187
(II) intel(0): Year: 2009  Week: 51
(II) intel(0): EDID Version: 1.3
(II) intel(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) intel(0): Sync:  Separate  Composite  SyncOnGreen
(II) intel(0): Max Image Size [cm]: horiz.: 51  vert.: 29
(II) intel(0): Gamma: 2.20
(II) intel(0): DPMS capabilities: Off; RGB/Color Display
(II) intel(0): First detailed timing is preferred mode
(II) intel(0): redX: 0.640 redY: 0.330   greenX: 0.300 greenY: 0.600
(II) intel(0): blueX: 0.150 blueY: 0.060   whiteX: 0.312 whiteY: 0.329
(II) intel(0): Supported established timings:
(II) intel(0): 640x480@60Hz
(II) intel(0): 800x600@56Hz
(II) intel(0): 800x600@60Hz
(II) intel(0): 1024x768@60Hz
(II) intel(0): Manufacturer's mask: 0
(II) intel(0): Supported standard timings:
(II) intel(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) intel(0): #1: hsize: 1280  vsize 960  refresh: 60  vid: 16513
(II) intel(0): #2: hsize: 1280  vsize 800  refresh: 60  vid: 129
(II) intel(0): #3: hsize: 1440  vsize 900  refresh: 60  vid: 149
(II) intel(0): #4: hsize: 1680  vsize 1050  refresh: 60  vid: 179
(II) intel(0): Supported detailed timing:
(II) intel(0): clock: 156.8 MHz   Image Size:  510 x 287 mm
(II) intel(0): h_active: 2048  h_sync: 2096  h_sync_end 2128 h_blank_end 2208 h_border: 0
(II) intel(0): v_active: 1152  v_sync: 1155  v_sync_end 1160 v_blanking: 1185 v_border: 0
(II) intel(0): Ranges: V min: 56 V max: 60 Hz, H min: 30 H max: 81 kHz, PixClock max 160 MHz
(II) intel(0): Monitor name: SyncMaster
(II) intel(0): Serial No: HVMSC01920
(II) intel(0): EDID (in hex):
(II) intel(0):     00ffffffffffff004c2d84053332594d
(II) intel(0):     331301030e331d782aee91a3544c9926
(II) intel(0):     0f50542308008180814081009500b300
(II) intel(0):     0101010101013b3d00a0808021403020
(II) intel(0):     3500fe1f1100001a000000fd00383c1e
(II) intel(0):     5110000a202020202020000000fc0053
(II) intel(0):     796e634d61737465720a2020000000ff
(II) intel(0):     0048564d534330313932300a202000aa
(II) intel(0): EDID vendor "SAM", prod id 1412
(II) intel(0): Using EDID range info for horizontal sync
(II) intel(0): Using EDID range info for vertical refresh
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "2048x1152"x0.0  156.75  2048 2096 2128 2208  1152 1155 1160 1185 +hsync -vsync (71.0 kHz)
(II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) intel(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
(II) intel(0): Modeline "1280x800"x0.0   83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync (49.7 kHz)
(II) intel(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
(II) intel(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
(II) intel(0): Printing probed modes for output VGA1
(II) intel(0): Modeline "2048x1152"x59.9  156.75  2048 2096 2128 2208  1152 1155 1160 1185 +hsync -vsync (71.0 kHz)
(II) intel(0): Modeline "2048x1152"x59.9  156.80  2048 2096 2128 2208  1152 1155 1160 1185 +hsync -vsync (71.0 kHz)
(II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Output VGA1 connected
(II) intel(0): Using user preference for initial modes
(II) intel(0): Output VGA1 using initial mode 2048x1152
(==) intel(0): video overlay key set to 0x101fe
(==) intel(0): Using gamma correction (1.0, 1.0, 1.0)
(**) intel(0): Display dimensions: (510, 290) mm
(**) intel(0): DPI set to (101, 100)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.4
(==) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [4] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [5] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
(II) intel(0): [DRI2] Setup complete
(**) intel(0): Framebuffer compression disabled
(**) intel(0): Tiling enabled
(**) intel(0): SwapBuffers wait enabled
(==) intel(0): VideoRam: 131072 KB
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
(WW) intel(0): Disabling Xv because no adaptors could be initialized.
(II) intel(0): direct rendering: DRI2 Enabled
(WW) intel(0): Option "NoAccel" is not used
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
(II) intel(0): Setting screen physical size to 510 x 287
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
(II) config/hal: Adding input device Logitech Optical USB Mouse
(**) Logitech Optical USB Mouse: always reports core events
(**) Logitech Optical USB Mouse: Device: "/dev/input/event4"
(II) Logitech Optical USB Mouse: Found 3 mouse buttons
(II) Logitech Optical USB Mouse: Found x and y relative axes
(II) Logitech Optical USB Mouse: Found scroll wheel(s)
(II) Logitech Optical USB Mouse: Configuring as mouse
(**) Logitech Optical USB Mouse: YAxisMapping: buttons 4 and 5
(**) Logitech Optical USB Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Logitech Optical USB Mouse" (type: MOUSE)
(**) Logitech Optical USB Mouse: (accel) keeping acceleration scheme 1
(**) Logitech Optical USB Mouse: (accel) filter chain progression: 2.00
(**) Logitech Optical USB Mouse: (accel) filter stage 0: 20.00 ms
(**) Logitech Optical USB Mouse: (accel) set acceleration profile 0
(II) Logitech Optical USB Mouse: initialized for relative axes.
(II) intel(0): EDID for output VGA1
(II) intel(0): Manufacturer: SAM  Model: 584  Serial#: 1297691187
(II) intel(0): Year: 2009  Week: 51
(II) intel(0): EDID Version: 1.3
(II) intel(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) intel(0): Sync:  Separate  Composite  SyncOnGreen
(II) intel(0): Max Image Size [cm]: horiz.: 51  vert.: 29
(II) intel(0): Gamma: 2.20
(II) intel(0): DPMS capabilities: Off; RGB/Color Display
(II) intel(0): First detailed timing is preferred mode
(II) intel(0): redX: 0.640 redY: 0.330   greenX: 0.300 greenY: 0.600
(II) intel(0): blueX: 0.150 blueY: 0.060   whiteX: 0.312 whiteY: 0.329
(II) intel(0): Supported established timings:
(II) intel(0): 640x480@60Hz
(II) intel(0): 800x600@56Hz
(II) intel(0): 800x600@60Hz
(II) intel(0): 1024x768@60Hz
(II) intel(0): Manufacturer's mask: 0
(II) intel(0): Supported standard timings:
(II) intel(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) intel(0): #1: hsize: 1280  vsize 960  refresh: 60  vid: 16513
(II) intel(0): #2: hsize: 1280  vsize 800  refresh: 60  vid: 129
(II) intel(0): #3: hsize: 1440  vsize 900  refresh: 60  vid: 149
(II) intel(0): #4: hsize: 1680  vsize 1050  refresh: 60  vid: 179
(II) intel(0): Supported detailed timing:
(II) intel(0): clock: 156.8 MHz   Image Size:  510 x 287 mm
(II) intel(0): h_active: 2048  h_sync: 2096  h_sync_end 2128 h_blank_end 2208 h_border: 0
(II) intel(0): v_active: 1152  v_sync: 1155  v_sync_end 1160 v_blanking: 1185 v_border: 0
(II) intel(0): Ranges: V min: 56 V max: 60 Hz, H min: 30 H max: 81 kHz, PixClock max 160 MHz
(II) intel(0): Monitor name: SyncMaster
(II) intel(0): Serial No: HVMSC01920
(II) intel(0): EDID (in hex):
(II) intel(0):     00ffffffffffff004c2d84053332594d
(II) intel(0):     331301030e331d782aee91a3544c9926
(II) intel(0):     0f50542308008180814081009500b300
(II) intel(0):     0101010101013b3d00a0808021403020
(II) intel(0):     3500fe1f1100001a000000fd00383c1e
(II) intel(0):     5110000a202020202020000000fc0053
(II) intel(0):     796e634d61737465720a2020000000ff
(II) intel(0):     0048564d534330313932300a202000aa
(II) intel(0): EDID vendor "SAM", prod id 1412
(II) intel(0): Using hsync ranges from config file
(II) intel(0): Using vrefresh ranges from config file
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "2048x1152"x0.0  156.75  2048 2096 2128 2208  1152 1155 1160 1185 +hsync -vsync (71.0 kHz)
(II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) intel(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
(II) intel(0): Modeline "1280x800"x0.0   83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync (49.7 kHz)
(II) intel(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
(II) intel(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
(II) intel(0): Printing probed modes for output VGA1
(II) intel(0): Modeline "2048x1152"x59.9  156.75  2048 2096 2128 2208  1152 1155 1160 1185 +hsync -vsync (71.0 kHz)
(II) intel(0): Modeline "2048x1152"x59.9  156.80  2048 2096 2128 2208  1152 1155 1160 1185 +hsync -vsync (71.0 kHz)
(II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): EDID for output VGA1
(II) intel(0): Manufacturer: SAM  Model: 584  Serial#: 1297691187
(II) intel(0): Year: 2009  Week: 51
(II) intel(0): EDID Version: 1.3
(II) intel(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) intel(0): Sync:  Separate  Composite  SyncOnGreen
(II) intel(0): Max Image Size [cm]: horiz.: 51  vert.: 29
(II) intel(0): Gamma: 2.20
(II) intel(0): DPMS capabilities: Off; RGB/Color Display
(II) intel(0): First detailed timing is preferred mode
(II) intel(0): redX: 0.640 redY: 0.330   greenX: 0.300 greenY: 0.600
(II) intel(0): blueX: 0.150 blueY: 0.060   whiteX: 0.312 whiteY: 0.329
(II) intel(0): Supported established timings:
(II) intel(0): 640x480@60Hz
(II) intel(0): 800x600@56Hz
(II) intel(0): 800x600@60Hz
(II) intel(0): 1024x768@60Hz
(II) intel(0): Manufacturer's mask: 0
(II) intel(0): Supported standard timings:
(II) intel(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) intel(0): #1: hsize: 1280  vsize 960  refresh: 60  vid: 16513
(II) intel(0): #2: hsize: 1280  vsize 800  refresh: 60  vid: 129
(II) intel(0): #3: hsize: 1440  vsize 900  refresh: 60  vid: 149
(II) intel(0): #4: hsize: 1680  vsize 1050  refresh: 60  vid: 179
(II) intel(0): Supported detailed timing:
(II) intel(0): clock: 156.8 MHz   Image Size:  510 x 287 mm
(II) intel(0): h_active: 2048  h_sync: 2096  h_sync_end 2128 h_blank_end 2208 h_border: 0
(II) intel(0): v_active: 1152  v_sync: 1155  v_sync_end 1160 v_blanking: 1185 v_border: 0
(II) intel(0): Ranges: V min: 56 V max: 60 Hz, H min: 30 H max: 81 kHz, PixClock max 160 MHz
(II) intel(0): Monitor name: SyncMaster
(II) intel(0): Serial No: HVMSC01920
(II) intel(0): EDID (in hex):
(II) intel(0):     00ffffffffffff004c2d84053332594d
(II) intel(0):     331301030e331d782aee91a3544c9926
(II) intel(0):     0f50542308008180814081009500b300
(II) intel(0):     0101010101013b3d00a0808021403020
(II) intel(0):     3500fe1f1100001a000000fd00383c1e
(II) intel(0):     5110000a202020202020000000fc0053
(II) intel(0):     796e634d61737465720a2020000000ff
(II) intel(0):     0048564d534330313932300a202000aa
(II) intel(0): EDID vendor "SAM", prod id 1412
(II) intel(0): Using hsync ranges from config file
(II) intel(0): Using vrefresh ranges from config file
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "2048x1152"x0.0  156.75  2048 2096 2128 2208  1152 1155 1160 1185 +hsync -vsync (71.0 kHz)
(II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) intel(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
(II) intel(0): Modeline "1280x800"x0.0   83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync (49.7 kHz)
(II) intel(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
(II) intel(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
(II) intel(0): Printing probed modes for output VGA1
(II) intel(0): Modeline "2048x1152"x59.9  156.75  2048 2096 2128 2208  1152 1155 1160 1185 +hsync -vsync (71.0 kHz)
(II) intel(0): Modeline "2048x1152"x59.9  156.80  2048 2096 2128 2208  1152 1155 1160 1185 +hsync -vsync (71.0 kHz)
(II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): EDID for output VGA1
(II) intel(0): Manufacturer: SAM  Model: 584  Serial#: 1297691187
(II) intel(0): Year: 2009  Week: 51
(II) intel(0): EDID Version: 1.3
(II) intel(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) intel(0): Sync:  Separate  Composite  SyncOnGreen
(II) intel(0): Max Image Size [cm]: horiz.: 51  vert.: 29
(II) intel(0): Gamma: 2.20
(II) intel(0): DPMS capabilities: Off; RGB/Color Display
(II) intel(0): First detailed timing is preferred mode
(II) intel(0): redX: 0.640 redY: 0.330   greenX: 0.300 greenY: 0.600
(II) intel(0): blueX: 0.150 blueY: 0.060   whiteX: 0.312 whiteY: 0.329
(II) intel(0): Supported established timings:
(II) intel(0): 640x480@60Hz
(II) intel(0): 800x600@56Hz
(II) intel(0): 800x600@60Hz
(II) intel(0): 1024x768@60Hz
(II) intel(0): Manufacturer's mask: 0
(II) intel(0): Supported standard timings:
(II) intel(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) intel(0): #1: hsize: 1280  vsize 960  refresh: 60  vid: 16513
(II) intel(0): #2: hsize: 1280  vsize 800  refresh: 60  vid: 129
(II) intel(0): #3: hsize: 1440  vsize 900  refresh: 60  vid: 149
(II) intel(0): #4: hsize: 1680  vsize 1050  refresh: 60  vid: 179
(II) intel(0): Supported detailed timing:
(II) intel(0): clock: 156.8 MHz   Image Size:  510 x 287 mm
(II) intel(0): h_active: 2048  h_sync: 2096  h_sync_end 2128 h_blank_end 2208 h_border: 0
(II) intel(0): v_active: 1152  v_sync: 1155  v_sync_end 1160 v_blanking: 1185 v_border: 0
(II) intel(0): Ranges: V min: 56 V max: 60 Hz, H min: 30 H max: 81 kHz, PixClock max 160 MHz
(II) intel(0): Monitor name: SyncMaster
(II) intel(0): Serial No: HVMSC01920
(II) intel(0): EDID (in hex):
(II) intel(0):     00ffffffffffff004c2d84053332594d
(II) intel(0):     331301030e331d782aee91a3544c9926
(II) intel(0):     0f50542308008180814081009500b300
(II) intel(0):     0101010101013b3d00a0808021403020
(II) intel(0):     3500fe1f1100001a000000fd00383c1e
(II) intel(0):     5110000a202020202020000000fc0053
(II) intel(0):     796e634d61737465720a2020000000ff
(II) intel(0):     0048564d534330313932300a202000aa
(II) intel(0): EDID vendor "SAM", prod id 1412
(II) intel(0): Using hsync ranges from config file
(II) intel(0): Using vrefresh ranges from config file
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "2048x1152"x0.0  156.75  2048 2096 2128 2208  1152 1155 1160 1185 +hsync -vsync (71.0 kHz)
(II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) intel(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
(II) intel(0): Modeline "1280x800"x0.0   83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync (49.7 kHz)
(II) intel(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
(II) intel(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
(II) intel(0): Printing probed modes for output VGA1
(II) intel(0): Modeline "2048x1152"x59.9  156.75  2048 2096 2128 2208  1152 1155 1160 1185 +hsync -vsync (71.0 kHz)
(II) intel(0): Modeline "2048x1152"x59.9  156.80  2048 2096 2128 2208  1152 1155 1160 1185 +hsync -vsync (71.0 kHz)
(II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Allocate new frame buffer 1024x768 stride 1024
(II) intel(0): EDID for output VGA1
(II) intel(0): Manufacturer: SAM  Model: 584  Serial#: 1297691187
(II) intel(0): Year: 2009  Week: 51
(II) intel(0): EDID Version: 1.3
(II) intel(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) intel(0): Sync:  Separate  Composite  SyncOnGreen
(II) intel(0): Max Image Size [cm]: horiz.: 51  vert.: 29
(II) intel(0): Gamma: 2.20
(II) intel(0): DPMS capabilities: Off; RGB/Color Display
(II) intel(0): First detailed timing is preferred mode
(II) intel(0): redX: 0.640 redY: 0.330   greenX: 0.300 greenY: 0.600
(II) intel(0): blueX: 0.150 blueY: 0.060   whiteX: 0.312 whiteY: 0.329
(II) intel(0): Supported established timings:
(II) intel(0): 640x480@60Hz
(II) intel(0): 800x600@56Hz
(II) intel(0): 800x600@60Hz
(II) intel(0): 1024x768@60Hz
(II) intel(0): Manufacturer's mask: 0
(II) intel(0): Supported standard timings:
(II) intel(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) intel(0): #1: hsize: 1280  vsize 960  refresh: 60  vid: 16513
(II) intel(0): #2: hsize: 1280  vsize 800  refresh: 60  vid: 129
(II) intel(0): #3: hsize: 1440  vsize 900  refresh: 60  vid: 149
(II) intel(0): #4: hsize: 1680  vsize 1050  refresh: 60  vid: 179
(II) intel(0): Supported detailed timing:
(II) intel(0): clock: 156.8 MHz   Image Size:  510 x 287 mm
(II) intel(0): h_active: 2048  h_sync: 2096  h_sync_end 2128 h_blank_end 2208 h_border: 0
(II) intel(0): v_active: 1152  v_sync: 1155  v_sync_end 1160 v_blanking: 1185 v_border: 0
(II) intel(0): Ranges: V min: 56 V max: 60 Hz, H min: 30 H max: 81 kHz, PixClock max 160 MHz
(II) intel(0): Monitor name: SyncMaster
(II) intel(0): Serial No: HVMSC01920
(II) intel(0): EDID (in hex):
(II) intel(0):     00ffffffffffff004c2d84053332594d
(II) intel(0):     331301030e331d782aee91a3544c9926
(II) intel(0):     0f50542308008180814081009500b300
(II) intel(0):     0101010101013b3d00a0808021403020
(II) intel(0):     3500fe1f1100001a000000fd00383c1e
(II) intel(0):     5110000a202020202020000000fc0053
(II) intel(0):     796e634d61737465720a2020000000ff
(II) intel(0):     0048564d534330313932300a202000aa
(II) intel(0): EDID vendor "SAM", prod id 1412
(II) intel(0): Using hsync ranges from config file
(II) intel(0): Using vrefresh ranges from config file
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "2048x1152"x0.0  156.75  2048 2096 2128 2208  1152 1155 1160 1185 +hsync -vsync (71.0 kHz)
(II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) intel(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
(II) intel(0): Modeline "1280x800"x0.0   83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync (49.7 kHz)
(II) intel(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
(II) intel(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
(II) intel(0): Printing probed modes for output VGA1
(II) intel(0): Modeline "2048x1152"x59.9  156.75  2048 2096 2128 2208  1152 1155 1160 1185 +hsync -vsync (71.0 kHz)
(II) intel(0): Modeline "2048x1152"x59.9  156.80  2048 2096 2128 2208  1152 1155 1160 1185 +hsync -vsync (71.0 kHz)
(II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): EDID for output VGA1
(II) intel(0): Manufacturer: SAM  Model: 584  Serial#: 1297691187
(II) intel(0): Year: 2009  Week: 51
(II) intel(0): EDID Version: 1.3
(II) intel(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) intel(0): Sync:  Separate  Composite  SyncOnGreen
(II) intel(0): Max Image Size [cm]: horiz.: 51  vert.: 29
(II) intel(0): Gamma: 2.20
(II) intel(0): DPMS capabilities: Off; RGB/Color Display
(II) intel(0): First detailed timing is preferred mode
(II) intel(0): redX: 0.640 redY: 0.330   greenX: 0.300 greenY: 0.600
(II) intel(0): blueX: 0.150 blueY: 0.060   whiteX: 0.312 whiteY: 0.329
(II) intel(0): Supported established timings:
(II) intel(0): 640x480@60Hz
(II) intel(0): 800x600@56Hz
(II) intel(0): 800x600@60Hz
(II) intel(0): 1024x768@60Hz
(II) intel(0): Manufacturer's mask: 0
(II) intel(0): Supported standard timings:
(II) intel(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) intel(0): #1: hsize: 1280  vsize 960  refresh: 60  vid: 16513
(II) intel(0): #2: hsize: 1280  vsize 800  refresh: 60  vid: 129
(II) intel(0): #3: hsize: 1440  vsize 900  refresh: 60  vid: 149
(II) intel(0): #4: hsize: 1680  vsize 1050  refresh: 60  vid: 179
(II) intel(0): Supported detailed timing:
(II) intel(0): clock: 156.8 MHz   Image Size:  510 x 287 mm
(II) intel(0): h_active: 2048  h_sync: 2096  h_sync_end 2128 h_blank_end 2208 h_border: 0
(II) intel(0): v_active: 1152  v_sync: 1155  v_sync_end 1160 v_blanking: 1185 v_border: 0
(II) intel(0): Ranges: V min: 56 V max: 60 Hz, H min: 30 H max: 81 kHz, PixClock max 160 MHz
(II) intel(0): Monitor name: SyncMaster
(II) intel(0): Serial No: HVMSC01920
(II) intel(0): EDID (in hex):
(II) intel(0):     00ffffffffffff004c2d84053332594d
(II) intel(0):     331301030e331d782aee91a3544c9926
(II) intel(0):     0f50542308008180814081009500b300
(II) intel(0):     0101010101013b3d00a0808021403020
(II) intel(0):     3500fe1f1100001a000000fd00383c1e
(II) intel(0):     5110000a202020202020000000fc0053
(II) intel(0):     796e634d61737465720a2020000000ff
(II) intel(0):     0048564d534330313932300a202000aa
(II) intel(0): EDID vendor "SAM", prod id 1412
(II) intel(0): Using hsync ranges from config file
(II) intel(0): Using vrefresh ranges from config file
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "2048x1152"x0.0  156.75  2048 2096 2128 2208  1152 1155 1160 1185 +hsync -vsync (71.0 kHz)
(II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) intel(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
(II) intel(0): Modeline "1280x800"x0.0   83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync (49.7 kHz)
(II) intel(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
(II) intel(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
(II) intel(0): Printing probed modes for output VGA1
(II) intel(0): Modeline "2048x1152"x59.9  156.75  2048 2096 2128 2208  1152 1155 1160 1185 +hsync -vsync (71.0 kHz)
(II) intel(0): Modeline "2048x1152"x59.9  156.80  2048 2096 2128 2208  1152 1155 1160 1185 +hsync -vsync (71.0 kHz)
(II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): EDID for output VGA1
(II) intel(0): Manufacturer: SAM  Model: 584  Serial#: 1297691187
(II) intel(0): Year: 2009  Week: 51
(II) intel(0): EDID Version: 1.3
(II) intel(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) intel(0): Sync:  Separate  Composite  SyncOnGreen
(II) intel(0): Max Image Size [cm]: horiz.: 51  vert.: 29
(II) intel(0): Gamma: 2.20
(II) intel(0): DPMS capabilities: Off; RGB/Color Display
(II) intel(0): First detailed timing is preferred mode
(II) intel(0): redX: 0.640 redY: 0.330   greenX: 0.300 greenY: 0.600
(II) intel(0): blueX: 0.150 blueY: 0.060   whiteX: 0.312 whiteY: 0.329
(II) intel(0): Supported established timings:
(II) intel(0): 640x480@60Hz
(II) intel(0): 800x600@56Hz
(II) intel(0): 800x600@60Hz
(II) intel(0): 1024x768@60Hz
(II) intel(0): Manufacturer's mask: 0
(II) intel(0): Supported standard timings:
(II) intel(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) intel(0): #1: hsize: 1280  vsize 960  refresh: 60  vid: 16513
(II) intel(0): #2: hsize: 1280  vsize 800  refresh: 60  vid: 129
(II) intel(0): #3: hsize: 1440  vsize 900  refresh: 60  vid: 149
(II) intel(0): #4: hsize: 1680  vsize 1050  refresh: 60  vid: 179
(II) intel(0): Supported detailed timing:
(II) intel(0): clock: 156.8 MHz   Image Size:  510 x 287 mm
(II) intel(0): h_active: 2048  h_sync: 2096  h_sync_end 2128 h_blank_end 2208 h_border: 0
(II) intel(0): v_active: 1152  v_sync: 1155  v_sync_end 1160 v_blanking: 1185 v_border: 0
(II) intel(0): Ranges: V min: 56 V max: 60 Hz, H min: 30 H max: 81 kHz, PixClock max 160 MHz
(II) intel(0): Monitor name: SyncMaster
(II) intel(0): Serial No: HVMSC01920
(II) intel(0): EDID (in hex):
(II) intel(0):     00ffffffffffff004c2d84053332594d
(II) intel(0):     331301030e331d782aee91a3544c9926
(II) intel(0):     0f50542308008180814081009500b300
(II) intel(0):     0101010101013b3d00a0808021403020
(II) intel(0):     3500fe1f1100001a000000fd00383c1e
(II) intel(0):     5110000a202020202020000000fc0053
(II) intel(0):     796e634d61737465720a2020000000ff
(II) intel(0):     0048564d534330313932300a202000aa
(II) intel(0): EDID vendor "SAM", prod id 1412
(II) intel(0): Using hsync ranges from config file
(II) intel(0): Using vrefresh ranges from config file
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "2048x1152"x0.0  156.75  2048 2096 2128 2208  1152 1155 1160 1185 +hsync -vsync (71.0 kHz)
(II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) intel(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
(II) intel(0): Modeline "1280x800"x0.0   83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync (49.7 kHz)
(II) intel(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
(II) intel(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
(II) intel(0): Printing probed modes for output VGA1
(II) intel(0): Modeline "2048x1152"x59.9  156.75  2048 2096 2128 2208  1152 1155 1160 1185 +hsync -vsync (71.0 kHz)
(II) intel(0): Modeline "2048x1152"x59.9  156.80  2048 2096 2128 2208  1152 1155 1160 1185 +hsync -vsync (71.0 kHz)
(II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): EDID for output VGA1
(II) intel(0): Manufacturer: SAM  Model: 584  Serial#: 1297691187
(II) intel(0): Year: 2009  Week: 51
(II) intel(0): EDID Version: 1.3
(II) intel(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) intel(0): Sync:  Separate  Composite  SyncOnGreen
(II) intel(0): Max Image Size [cm]: horiz.: 51  vert.: 29
(II) intel(0): Gamma: 2.20
(II) intel(0): DPMS capabilities: Off; RGB/Color Display
(II) intel(0): First detailed timing is preferred mode
(II) intel(0): redX: 0.640 redY: 0.330   greenX: 0.300 greenY: 0.600
(II) intel(0): blueX: 0.150 blueY: 0.060   whiteX: 0.312 whiteY: 0.329
(II) intel(0): Supported established timings:
(II) intel(0): 640x480@60Hz
(II) intel(0): 800x600@56Hz
(II) intel(0): 800x600@60Hz
(II) intel(0): 1024x768@60Hz
(II) intel(0): Manufacturer's mask: 0
(II) intel(0): Supported standard timings:
(II) intel(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) intel(0): #1: hsize: 1280  vsize 960  refresh: 60  vid: 16513
(II) intel(0): #2: hsize: 1280  vsize 800  refresh: 60  vid: 129
(II) intel(0): #3: hsize: 1440  vsize 900  refresh: 60  vid: 149
(II) intel(0): #4: hsize: 1680  vsize 1050  refresh: 60  vid: 179
(II) intel(0): Supported detailed timing:
(II) intel(0): clock: 156.8 MHz   Image Size:  510 x 287 mm
(II) intel(0): h_active: 2048  h_sync: 2096  h_sync_end 2128 h_blank_end 2208 h_border: 0
(II) intel(0): v_active: 1152  v_sync: 1155  v_sync_end 1160 v_blanking: 1185 v_border: 0
(II) intel(0): Ranges: V min: 56 V max: 60 Hz, H min: 30 H max: 81 kHz, PixClock max 160 MHz
(II) intel(0): Monitor name: SyncMaster
(II) intel(0): Serial No: HVMSC01920
(II) intel(0): EDID (in hex):
(II) intel(0):     00ffffffffffff004c2d84053332594d
(II) intel(0):     331301030e331d782aee91a3544c9926
(II) intel(0):     0f50542308008180814081009500b300
(II) intel(0):     0101010101013b3d00a0808021403020
(II) intel(0):     3500fe1f1100001a000000fd00383c1e
(II) intel(0):     5110000a202020202020000000fc0053
(II) intel(0):     796e634d61737465720a2020000000ff
(II) intel(0):     0048564d534330313932300a202000aa
(II) intel(0): EDID vendor "SAM", prod id 1412
(II) intel(0): Using hsync ranges from config file
(II) intel(0): Using vrefresh ranges from config file
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "2048x1152"x0.0  156.75  2048 2096 2128 2208  1152 1155 1160 1185 +hsync -vsync (71.0 kHz)
(II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) intel(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
(II) intel(0): Modeline "1280x800"x0.0   83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync (49.7 kHz)
(II) intel(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
(II) intel(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
(II) intel(0): Printing probed modes for output VGA1
(II) intel(0): Modeline "2048x1152"x59.9  156.75  2048 2096 2128 2208  1152 1155 1160 1185 +hsync -vsync (71.0 kHz)
(II) intel(0): Modeline "2048x1152"x59.9  156.80  2048 2096 2128 2208  1152 1155 1160 1185 +hsync -vsync (71.0 kHz)
(II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): EDID for output VGA1
(II) intel(0): Manufacturer: SAM  Model: 584  Serial#: 1297691187
(II) intel(0): Year: 2009  Week: 51
(II) intel(0): EDID Version: 1.3
(II) intel(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) intel(0): Sync:  Separate  Composite  SyncOnGreen
(II) intel(0): Max Image Size [cm]: horiz.: 51  vert.: 29
(II) intel(0): Gamma: 2.20
(II) intel(0): DPMS capabilities: Off; RGB/Color Display
(II) intel(0): First detailed timing is preferred mode
(II) intel(0): redX: 0.640 redY: 0.330   greenX: 0.300 greenY: 0.600
(II) intel(0): blueX: 0.150 blueY: 0.060   whiteX: 0.312 whiteY: 0.329
(II) intel(0): Supported established timings:
(II) intel(0): 640x480@60Hz
(II) intel(0): 800x600@56Hz
(II) intel(0): 800x600@60Hz
(II) intel(0): 1024x768@60Hz
(II) intel(0): Manufacturer's mask: 0
(II) intel(0): Supported standard timings:
(II) intel(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) intel(0): #1: hsize: 1280  vsize 960  refresh: 60  vid: 16513
(II) intel(0): #2: hsize: 1280  vsize 800  refresh: 60  vid: 129
(II) intel(0): #3: hsize: 1440  vsize 900  refresh: 60  vid: 149
(II) intel(0): #4: hsize: 1680  vsize 1050  refresh: 60  vid: 179
(II) intel(0): Supported detailed timing:
(II) intel(0): clock: 156.8 MHz   Image Size:  510 x 287 mm
(II) intel(0): h_active: 2048  h_sync: 2096  h_sync_end 2128 h_blank_end 2208 h_border: 0
(II) intel(0): v_active: 1152  v_sync: 1155  v_sync_end 1160 v_blanking: 1185 v_border: 0
(II) intel(0): Ranges: V min: 56 V max: 60 Hz, H min: 30 H max: 81 kHz, PixClock max 160 MHz
(II) intel(0): Monitor name: SyncMaster
(II) intel(0): Serial No: HVMSC01920
(II) intel(0): EDID (in hex):
(II) intel(0):     00ffffffffffff004c2d84053332594d
(II) intel(0):     331301030e331d782aee91a3544c9926
(II) intel(0):     0f50542308008180814081009500b300
(II) intel(0):     0101010101013b3d00a0808021403020
(II) intel(0):     3500fe1f1100001a000000fd00383c1e
(II) intel(0):     5110000a202020202020000000fc0053
(II) intel(0):     796e634d61737465720a2020000000ff
(II) intel(0):     0048564d534330313932300a202000aa
(II) intel(0): EDID vendor "SAM", prod id 1412
(II) intel(0): Using hsync ranges from config file
(II) intel(0): Using vrefresh ranges from config file
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "2048x1152"x0.0  156.75  2048 2096 2128 2208  1152 1155 1160 1185 +hsync -vsync (71.0 kHz)
(II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) intel(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
(II) intel(0): Modeline "1280x800"x0.0   83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync (49.7 kHz)
(II) intel(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
(II) intel(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
(II) intel(0): Printing probed modes for output VGA1
(II) intel(0): Modeline "2048x1152"x59.9  156.75  2048 2096 2128 2208  1152 1155 1160 1185 +hsync -vsync (71.0 kHz)
(II) intel(0): Modeline "2048x1152"x59.9  156.80  2048 2096 2128 2208  1152 1155 1160 1185 +hsync -vsync (71.0 kHz)
(II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Allocate new frame buffer 2048x1152 stride 2048
(II) AIGLX: Suspending AIGLX clients for VT switch
```

---

### Post by patchwork on 2010-03-12
So just to be clear, what is happening when you boot right now?   You are getting the orange bar?  Any graphics at all?  Or only dropping to console?

Also, was the log from starting x while the horizsync and vertrefresh settings were still commented out?

If so, have you removed the comments from in front of those lines and restarted X?

(THIS MAY CAUSE THE ORANGE BAR TO COME BACK ON STARTUP)


EDIT:  Also, it appears that the NoAccel Option isn't doing anything.

I'm running out of ideas if the horizsync thing doesn't work....

---

### Post by mystik_spiral on 2010-03-12
> So just to be clear, what is happening when you boot right now?   You are getting the orange bar?  Any graphics at all?  Or only dropping to console? The computer always restarts and sets itself as 1024x768 mode after I reboot it when it screws up in 2048x1152 mode. So...I don't get an orange bar problem. The graphics problems pop on on occasion when I make changes to the gedit thing. 

> Also, was the log from starting x while the horizsync and vertrefresh settings were still commented out?yes, pretty sure

> If so, have you removed the comments from in front of those lines and restarted X?haven't. should I?

> (THIS MAY CAUSE THE ORANGE BAR TO COME BACK ON STARTUP)


EDIT:  Also, it appears that the NoAccel Option isn't doing anything.I'm running out of ideas if the horizsync thing doesn't work....nooo!

---

### Post by patchwork on 2010-03-12
Yeah, try to remove the # from in front of the HorizSync and VertRefresh lines

If it causes you more trouble on rebooting, you can add the comments back in again.

---

### Post by mystik_spiral on 2010-03-12
Removed the number signs and it didn't make a difference.

Ubuntu, why do you have to be such a tease?

---

### Post by twisterpooh on 2010-03-12
can i ask you a question?

---

### Post by mystik_spiral on 2010-03-12
you have my permission.

---

### Post by patchwork on 2010-03-12
I'm plum out of ideas, btw

---

### Post by mystik_spiral on 2010-03-12
> **patchwork said:**
> I'm plum out of ideas, btw
hmmm...anyone have any ideas regarding driver updates or graphics card upgrades?

...OR I can permanently just use Windows forever!

---

### Post by patchwork on 2010-03-12
Have you tried turning Desktop Effects off?

Right click on Desktop > Change Desktop Background > Visual Effects > None

Ran across this[URL="https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/426380"]:
https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/426380[/URL]

---

### Post by mystik_spiral on 2010-03-12
[SIZE=7][U][B]WORKS!

[/B][/U][SIZE=2]All those codes for nothing! haha.

thanks a million.
[/SIZE][/SIZE]

---

### Post by patchwork on 2010-03-12
No problem....glad you got it working (and hopefully picked up a few things along the way!)

---

### Post by mystik_spiral on 2010-03-12
yeah I can problem solve now and remember codes like the back of my hand.

thanks again.

---

