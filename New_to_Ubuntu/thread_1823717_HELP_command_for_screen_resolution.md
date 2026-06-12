---
title: "HELP command for screen resolution"
date: 2011-08-12
forum: New to Ubuntu
---

### Post by david476 on 2011-08-12
is there a command for screen resolutions? Ubuntu only gives me three 4:3 possible screen resolutions, I need a what I think is a 16:9 aspect ratio, the recommended screen resolution is 1600x900

---

### Post by cmcanulty on 2011-08-12
Go to system-preferences-monitor
a drop down box gives several choices, very easy. It won't appear to stick until you log out and back in.

---

### Post by david476 on 2011-08-12
that menu does not give me enough options.

the recommended resolution is 1600x900 (16:9) the menu only gives me three options, all 4:3

---

### Post by JC Cheloven on 2011-08-12
This can be controlled by the xrandr command at terminal. 
You can get an idea (well, quite more than that) [here]("http://lubuntu.net/blog/lubuntu-screencast-lxpanel-2-panel-layout"). 
You can learn how it works typing "man xrandr" at terminal". The command "xrandr --help" also gives information. 
If you need some more guidance, please start by posting here the output of "xrandr" at terminal (with no arguments). Thank you.

---

### Post by david476 on 2011-08-12
It gives me the same options:



Screen 0: minimum 640 x 480, current 1024 x 768, maximum 1024 x 768
default connected 1024x768+0+0 0mm x 0mm
   1024x768        0.0* 
   800x600         0.0  
   640x480         0.0

---

### Post by realzippy on 2011-08-13
Which video driver do you use?
Post your 
/var/log/Xorg.0.log  file.

```
gedit /var/log/Xorg.0.log
```

Post output from:
```
lspci |grep VGA
```

---

### Post by cmcanulty on 2011-08-13
Mine also gives 16:9 and 16:10

---

### Post by realzippy on 2011-08-13
@cmcanulty
that doesn 't help OP.
Btw,his monitor gui will show the same options as
*xrandr -q* shows...:

**maximum 1024 x 768**
..it is a driver issue.
Xorg.0.log will show.

---

### Post by david476 on 2011-08-13
realzippy:

code 1:
```

X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-28-server x86_64 Ubuntu
Current Operating System: Linux Colossus 2.6.32-33-generic #72-Ubuntu SMP Fri Jul 29 21:07:13 UTC 2011 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-33-generic root=UUID=a626e385-5e8a-4416-b923-ea8cb08b206d ro quiet splash
Build Date: 08 March 2011  08:22:34AM
xorg-server 2:1.7.6-2ubuntu7.6 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
Current version of pixman: 0.16.4
    Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sat Aug 13 07:38:45 2011
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"
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
(==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
(II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
(II) Loader magic: 0x7cb840
(II) Module ABI versions:
    X.Org ANSI C Emulation: 0.4
    X.Org Video Driver: 6.0
    X.Org XInput driver : 7.0
    X.Org Server Extension : 2.0
(++) using VT number 7

(--) PCI:*(0:0:2:0) 8086:0112:1462:7678 Intel Corporation rev 9, Mem @ 0xfe000000/4194304, 0xc0000000/268435456, I/O @ 0x0000f000/64
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
(II) Loading /usr/lib/xorg/modules/extensions/libglx.so
(II) Module glx: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    ABI class: X.Org Server Extension, version 2.0
(==) AIGLX enabled
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
(==) Matched intel as autoconfigured driver 0
(==) Matched vesa as autoconfigured driver 1
(==) Matched fbdev as autoconfigured driver 2
(==) Assigned the driver to the xf86ConfigLayout
(II) LoadModule: "intel"
(II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
(II) Module intel: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 2.9.1
    Module class: X.Org Video Driver
    ABI class: X.Org Video Driver, version 6.0
(II) LoadModule: "vesa"
(II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
(II) Module vesa: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 2.3.0
    Module class: X.Org Video Driver
    ABI class: X.Org Video Driver, version 6.0
(II) LoadModule: "fbdev"
(II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
(II) Module fbdev: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 0.4.1
    ABI class: X.Org Video Driver, version 6.0
(II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
    i810-dc100, i810e, i815, i830M, 845G, 852GM/855GM, 865G, 915G,
    E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
    965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
    4 Series, G45/G43, Q45/Q43, G41, B43, Clarkdale, Arrandale
(II) VESA: driver for VESA chipsets: vesa
(II) FBDEV: driver for framebuffer: fbdev
(II) Primary Device is: PCI 00@00:02:0
(WW) Falling back to old probe method for fbdev
(II) Loading sub module "fbdevhw"
(II) LoadModule: "fbdevhw"
(II) Loading /usr/lib/xorg/modules/linux/libfbdevhw.so
(II) Module fbdevhw: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 0.0.2
    ABI class: X.Org Video Driver, version 6.0
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules/libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.1.0
    ABI class: X.Org Video Driver, version 6.0
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules/libint10.so
(II) Module int10: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    ABI class: X.Org Video Driver, version 6.0
(II) VESA(0): initializing int10
(II) VESA(0): Primary V_BIOS segment is: 0xc000
(II) VESA(0): VESA BIOS detected
(II) VESA(0): VESA VBE Version 3.0
(II) VESA(0): VESA VBE Total Mem: 65472 kB
(II) VESA(0): VESA VBE OEM: Intel(R)Sandybridge Desktop Graphics Chipset Accelerated VGA BIOS
(II) VESA(0): VESA VBE OEM Software Rev: 1.0
(II) VESA(0): VESA VBE OEM Vendor: Intel Corporation
(II) VESA(0): VESA VBE OEM Product: Intel(R)Sandybridge Desktop Graphics Controller
(II) VESA(0): VESA VBE OEM Product Rev: Hardware Version 0.0
(II) VESA(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
(==) VESA(0): Depth 24, (--) framebuffer bpp 32
(==) VESA(0): RGB weight 888
(==) VESA(0): Default visual is TrueColor
(==) VESA(0): Using gamma correction (1.0, 1.0, 1.0)
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(II) VESA(0): VESA VBE DDC supported
(II) VESA(0): VESA VBE DDC Level 2
(II) VESA(0): VESA VBE DDC transfer in appr. 1 sec.
(II) VESA(0): VESA VBE DDC read successfully
(II) VESA(0): Manufacturer: SAM  Model: 78b  Serial#: 1514292021
(II) VESA(0): Year: 2011  Week: 17
(II) VESA(0): EDID Version: 1.3
(II) VESA(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) VESA(0): Sync:  Separate  Composite  SyncOnGreen
(II) VESA(0): Max Image Size [cm]: horiz.: 44  vert.: 25
(II) VESA(0): Gamma: 2.20
(II) VESA(0): DPMS capabilities: Off; RGB/Color Display
(II) VESA(0): First detailed timing is preferred mode
(II) VESA(0): redX: 0.639 redY: 0.340   greenX: 0.324 greenY: 0.622
(II) VESA(0): blueX: 0.155 blueY: 0.042   whiteX: 0.312 whiteY: 0.329
(II) VESA(0): Supported established timings:
(II) VESA(0): 720x400@70Hz
(II) VESA(0): 640x480@60Hz
(II) VESA(0): 640x480@67Hz
(II) VESA(0): 640x480@72Hz
(II) VESA(0): 640x480@75Hz
(II) VESA(0): 800x600@56Hz
(II) VESA(0): 800x600@60Hz
(II) VESA(0): 800x600@72Hz
(II) VESA(0): 800x600@75Hz
(II) VESA(0): 832x624@75Hz
(II) VESA(0): 1024x768@60Hz
(II) VESA(0): 1024x768@70Hz
(II) VESA(0): 1024x768@75Hz
(II) VESA(0): 1152x864@75Hz
(II) VESA(0): Manufacturer's mask: 0
(II) VESA(0): Supported standard timings:
(II) VESA(0): #0: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) VESA(0): #1: hsize: 1280  vsize 800  refresh: 60  vid: 129
(II) VESA(0): #2: hsize: 1280  vsize 800  refresh: 75  vid: 3969
(II) VESA(0): #3: hsize: 1440  vsize 900  refresh: 60  vid: 149
(II) VESA(0): #4: hsize: 1440  vsize 900  refresh: 75  vid: 3989
(II) VESA(0): Supported detailed timing:
(II) VESA(0): clock: 108.0 MHz   Image Size:  443 x 249 mm
(II) VESA(0): h_active: 1600  h_sync: 1624  h_sync_end 1704 h_blank_end 1800 h_border: 0
(II) VESA(0): v_active: 900  v_sync: 901  v_sync_end 904 v_blanking: 1000 v_border: 0
(II) VESA(0): Ranges: V min: 56 V max: 75 Hz, H min: 30 H max: 81 kHz, PixClock max 150 MHz
(II) VESA(0): Monitor name: SA300/SA350
(II) VESA(0): Serial No: H9NB401854
(II) VESA(0): EDID (in hex):
(II) VESA(0):     00ffffffffffff004c2d8b073543425a
(II) VESA(0):     111501030e2c19782a81f1a357539f27
(II) VESA(0):     0a5054bfee80714f8100810f9500950f
(II) VESA(0):     010101010101302a40c8608464301850
(II) VESA(0):     1300bbf91000001e000000fd00384b1e
(II) VESA(0):     510f000a202020202020000000fc0053
(II) VESA(0):     413330302f53413335300a20000000ff
(II) VESA(0):     0048394e423430313835340a20200021
(II) VESA(0): EDID vendor "SAM", prod id 1931
(II) VESA(0): Using EDID range info for horizontal sync
(II) VESA(0): Using EDID range info for vertical refresh
(II) VESA(0): Printing DDC gathered Modelines:
(II) VESA(0): Modeline "1600x900"x0.0  108.00  1600 1624 1704 1800  900 901 904 1000 +hsync +vsync (60.0 kHz)
(II) VESA(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) VESA(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) VESA(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) VESA(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) VESA(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) VESA(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) VESA(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) VESA(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) VESA(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) VESA(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) VESA(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) VESA(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) VESA(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) VESA(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) VESA(0): Modeline "1280x800"x0.0   83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync (49.7 kHz)
(II) VESA(0): Modeline "1280x800"x0.0  106.50  1280 1360 1488 1696  800 803 809 838 -hsync +vsync (62.8 kHz)
(II) VESA(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
(II) VESA(0): Modeline "1440x900"x0.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz)
(II) VESA(0): Searching for matching VESA mode(s):
Mode: 160 (0x0)
    ModeAttributes: 0x0
    WinAAttributes: 0x0
    WinBAttributes: 0x0
    WinGranularity: 0
    WinSize: 0
    WinASegment: 0x0
    WinBSegment: 0x0
    WinFuncPtr: 0x0
    BytesPerScanline: 0
    XResolution: 0
    YResolution: 0
    XCharSize: 0
    YCharSize: 0
    NumberOfPlanes: 0
    BitsPerPixel: 0
    NumberOfBanks: 0
    MemoryModel: 0
    BankSize: 0
    NumberOfImages: 0
    RedMaskSize: 0
    RedFieldPosition: 0
    GreenMaskSize: 0
    GreenFieldPosition: 0
    BlueMaskSize: 0
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0x0
    LinBytesPerScanLine: 0
    BnkNumberOfImagePages: 0
    LinNumberOfImagePages: 0
    LinRedMaskSize: 0
    LinRedFieldPosition: 0
    LinGreenMaskSize: 0
    LinGreenFieldPosition: 0
    LinBlueMaskSize: 0
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 0
Mode: 161 (0x0)
    ModeAttributes: 0x0
    WinAAttributes: 0x0
    WinBAttributes: 0x0
    WinGranularity: 0
    WinSize: 0
    WinASegment: 0x0
    WinBSegment: 0x0
    WinFuncPtr: 0x0
    BytesPerScanline: 0
    XResolution: 0
    YResolution: 0
    XCharSize: 0
    YCharSize: 0
    NumberOfPlanes: 0
    BitsPerPixel: 0
    NumberOfBanks: 0
    MemoryModel: 0
    BankSize: 0
    NumberOfImages: 0
    RedMaskSize: 0
    RedFieldPosition: 0
    GreenMaskSize: 0
    GreenFieldPosition: 0
    BlueMaskSize: 0
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0x0
    LinBytesPerScanLine: 0
    BnkNumberOfImagePages: 0
    LinNumberOfImagePages: 0
    LinRedMaskSize: 0
    LinRedFieldPosition: 0
    LinGreenMaskSize: 0
    LinGreenFieldPosition: 0
    LinBlueMaskSize: 0
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 0
Mode: 162 (0x0)
    ModeAttributes: 0x0
    WinAAttributes: 0x0
    WinBAttributes: 0x0
    WinGranularity: 0
    WinSize: 0
    WinASegment: 0x0
    WinBSegment: 0x0
    WinFuncPtr: 0x0
    BytesPerScanline: 0
    XResolution: 0
    YResolution: 0
    XCharSize: 0
    YCharSize: 0
    NumberOfPlanes: 0
    BitsPerPixel: 0
    NumberOfBanks: 0
    MemoryModel: 0
    BankSize: 0
    NumberOfImages: 0
    RedMaskSize: 0
    RedFieldPosition: 0
    GreenMaskSize: 0
    GreenFieldPosition: 0
    BlueMaskSize: 0
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0x0
    LinBytesPerScanLine: 0
    BnkNumberOfImagePages: 0
    LinNumberOfImagePages: 0
    LinRedMaskSize: 0
    LinRedFieldPosition: 0
    LinGreenMaskSize: 0
    LinGreenFieldPosition: 0
    LinBlueMaskSize: 0
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 0
Mode: 163 (0x0)
    ModeAttributes: 0x0
    WinAAttributes: 0x0
    WinBAttributes: 0x0
    WinGranularity: 0
    WinSize: 0
    WinASegment: 0x0
    WinBSegment: 0x0
    WinFuncPtr: 0x0
    BytesPerScanline: 0
    XResolution: 0
    YResolution: 0
    XCharSize: 0
    YCharSize: 0
    NumberOfPlanes: 0
    BitsPerPixel: 0
    NumberOfBanks: 0
    MemoryModel: 0
    BankSize: 0
    NumberOfImages: 0
    RedMaskSize: 0
    RedFieldPosition: 0
    GreenMaskSize: 0
    GreenFieldPosition: 0
    BlueMaskSize: 0
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0x0
    LinBytesPerScanLine: 0
    BnkNumberOfImagePages: 0
    LinNumberOfImagePages: 0
    LinRedMaskSize: 0
    LinRedFieldPosition: 0
    LinGreenMaskSize: 0
    LinGreenFieldPosition: 0
    LinBlueMaskSize: 0
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 0
Mode: 164 (0x0)
    ModeAttributes: 0x0
    WinAAttributes: 0x0
    WinBAttributes: 0x0
    WinGranularity: 0
    WinSize: 0
    WinASegment: 0x0
    WinBSegment: 0x0
    WinFuncPtr: 0x0
    BytesPerScanline: 0
    XResolution: 0
    YResolution: 0
    XCharSize: 0
    YCharSize: 0
    NumberOfPlanes: 0
    BitsPerPixel: 0
    NumberOfBanks: 0
    MemoryModel: 0
    BankSize: 0
    NumberOfImages: 0
    RedMaskSize: 0
    RedFieldPosition: 0
    GreenMaskSize: 0
    GreenFieldPosition: 0
    BlueMaskSize: 0
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0x0
    LinBytesPerScanLine: 0
    BnkNumberOfImagePages: 0
    LinNumberOfImagePages: 0
    LinRedMaskSize: 0
    LinRedFieldPosition: 0
    LinGreenMaskSize: 0
    LinGreenFieldPosition: 0
    LinBlueMaskSize: 0
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 0
Mode: 165 (0x0)
    ModeAttributes: 0x0
    WinAAttributes: 0x0
    WinBAttributes: 0x0
    WinGranularity: 0
    WinSize: 0
    WinASegment: 0x0
    WinBSegment: 0x0
    WinFuncPtr: 0x0
    BytesPerScanline: 0
    XResolution: 0
    YResolution: 0
    XCharSize: 0
    YCharSize: 0
    NumberOfPlanes: 0
    BitsPerPixel: 0
    NumberOfBanks: 0
    MemoryModel: 0
    BankSize: 0
    NumberOfImages: 0
    RedMaskSize: 0
    RedFieldPosition: 0
    GreenMaskSize: 0
    GreenFieldPosition: 0
    BlueMaskSize: 0
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0x0
    LinBytesPerScanLine: 0
    BnkNumberOfImagePages: 0
    LinNumberOfImagePages: 0
    LinRedMaskSize: 0
    LinRedFieldPosition: 0
    LinGreenMaskSize: 0
    LinGreenFieldPosition: 0
    LinBlueMaskSize: 0
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 0
Mode: 166 (0x0)
    ModeAttributes: 0x0
    WinAAttributes: 0x0
    WinBAttributes: 0x0
    WinGranularity: 0
    WinSize: 0
    WinASegment: 0x0
    WinBSegment: 0x0
    WinFuncPtr: 0x0
    BytesPerScanline: 0
    XResolution: 0
    YResolution: 0
    XCharSize: 0
    YCharSize: 0
    NumberOfPlanes: 0
    BitsPerPixel: 0
    NumberOfBanks: 0
    MemoryModel: 0
    BankSize: 0
    NumberOfImages: 0
    RedMaskSize: 0
    RedFieldPosition: 0
    GreenMaskSize: 0
    GreenFieldPosition: 0
    BlueMaskSize: 0
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0x0
    LinBytesPerScanLine: 0
    BnkNumberOfImagePages: 0
    LinNumberOfImagePages: 0
    LinRedMaskSize: 0
    LinRedFieldPosition: 0
    LinGreenMaskSize: 0
    LinGreenFieldPosition: 0
    LinBlueMaskSize: 0
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 0
Mode: 167 (0x0)
    ModeAttributes: 0x0
    WinAAttributes: 0x0
    WinBAttributes: 0x0
    WinGranularity: 0
    WinSize: 0
    WinASegment: 0x0
    WinBSegment: 0x0
    WinFuncPtr: 0x0
    BytesPerScanline: 0
    XResolution: 0
    YResolution: 0
    XCharSize: 0
    YCharSize: 0
    NumberOfPlanes: 0
    BitsPerPixel: 0
    NumberOfBanks: 0
    MemoryModel: 0
    BankSize: 0
    NumberOfImages: 0
    RedMaskSize: 0
    RedFieldPosition: 0
    GreenMaskSize: 0
    GreenFieldPosition: 0
    BlueMaskSize: 0
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0x0
    LinBytesPerScanLine: 0
    BnkNumberOfImagePages: 0
    LinNumberOfImagePages: 0
    LinRedMaskSize: 0
    LinRedFieldPosition: 0
    LinGreenMaskSize: 0
    LinGreenFieldPosition: 0
    LinBlueMaskSize: 0
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 0
Mode: 168 (0x0)
    ModeAttributes: 0x0
    WinAAttributes: 0x0
    WinBAttributes: 0x0
    WinGranularity: 0
    WinSize: 0
    WinASegment: 0x0
    WinBSegment: 0x0
    WinFuncPtr: 0x0
    BytesPerScanline: 0
    XResolution: 0
    YResolution: 0
    XCharSize: 0
    YCharSize: 0
    NumberOfPlanes: 0
    BitsPerPixel: 0
    NumberOfBanks: 0
    MemoryModel: 0
    BankSize: 0
    NumberOfImages: 0
    RedMaskSize: 0
    RedFieldPosition: 0
    GreenMaskSize: 0
    GreenFieldPosition: 0
    BlueMaskSize: 0
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0x0
    LinBytesPerScanLine: 0
    BnkNumberOfImagePages: 0
    LinNumberOfImagePages: 0
    LinRedMaskSize: 0
    LinRedFieldPosition: 0
    LinGreenMaskSize: 0
    LinGreenFieldPosition: 0
    LinBlueMaskSize: 0
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 0
Mode: 13c (1920x1440)
    ModeAttributes: 0x9b
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc00079bc
    BytesPerScanline: 1920
    XResolution: 1920
    YResolution: 1440
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 8
    NumberOfBanks: 1
    MemoryModel: 4
    BankSize: 0
    NumberOfImages: 22
    RedMaskSize: 0
    RedFieldPosition: 0
    GreenMaskSize: 0
    GreenFieldPosition: 0
    BlueMaskSize: 0
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0xc0000000
    LinBytesPerScanLine: 1920
    BnkNumberOfImagePages: 22
    LinNumberOfImagePages: 22
    LinRedMaskSize: 0
    LinRedFieldPosition: 0
    LinGreenMaskSize: 0
    LinGreenFieldPosition: 0
    LinBlueMaskSize: 0
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 230000000
Mode: 14d (1920x1440)
    ModeAttributes: 0x9b
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc00079bc
    BytesPerScanline: 3840
    XResolution: 1920
    YResolution: 1440
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 16
    NumberOfBanks: 1
    MemoryModel: 6
    BankSize: 0
    NumberOfImages: 11
    RedMaskSize: 5
    RedFieldPosition: 11
    GreenMaskSize: 6
    GreenFieldPosition: 5
    BlueMaskSize: 5
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0xc0000000
    LinBytesPerScanLine: 3840
    BnkNumberOfImagePages: 11
    LinNumberOfImagePages: 11
    LinRedMaskSize: 5
    LinRedFieldPosition: 11
    LinGreenMaskSize: 6
    LinGreenFieldPosition: 5
    LinBlueMaskSize: 5
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 230000000
*Mode: 15c (1920x1440)
    ModeAttributes: 0x9b
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc00079bc
    BytesPerScanline: 7680
    XResolution: 1920
    YResolution: 1440
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 32
    NumberOfBanks: 1
    MemoryModel: 6
    BankSize: 0
    NumberOfImages: 5
    RedMaskSize: 8
    RedFieldPosition: 16
    GreenMaskSize: 8
    GreenFieldPosition: 8
    BlueMaskSize: 8
    BlueFieldPosition: 0
    RsvdMaskSize: 8
    RsvdFieldPosition: 24
    DirectColorModeInfo: 0
    PhysBasePtr: 0xc0000000
    LinBytesPerScanLine: 7680
    BnkNumberOfImagePages: 5
    LinNumberOfImagePages: 5
    LinRedMaskSize: 8
    LinRedFieldPosition: 16
    LinGreenMaskSize: 8
    LinGreenFieldPosition: 8
    LinBlueMaskSize: 8
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 8
    LinRsvdFieldPosition: 24
    MaxPixelClock: 230000000
Mode: 13a (1600x1200)
    ModeAttributes: 0x9b
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc00079bc
    BytesPerScanline: 1600
    XResolution: 1600
    YResolution: 1200
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 8
    NumberOfBanks: 1
    MemoryModel: 4
    BankSize: 0
    NumberOfImages: 33
    RedMaskSize: 0
    RedFieldPosition: 0
    GreenMaskSize: 0
    GreenFieldPosition: 0
    BlueMaskSize: 0
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0xc0000000
    LinBytesPerScanLine: 1600
    BnkNumberOfImagePages: 33
    LinNumberOfImagePages: 33
    LinRedMaskSize: 0
    LinRedFieldPosition: 0
    LinGreenMaskSize: 0
    LinGreenFieldPosition: 0
    LinBlueMaskSize: 0
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 230000000
Mode: 14b (1600x1200)
    ModeAttributes: 0x9b
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc00079bc
    BytesPerScanline: 3200
    XResolution: 1600
    YResolution: 1200
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 16
    NumberOfBanks: 1
    MemoryModel: 6
    BankSize: 0
    NumberOfImages: 16
    RedMaskSize: 5
    RedFieldPosition: 11
    GreenMaskSize: 6
    GreenFieldPosition: 5
    BlueMaskSize: 5
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0xc0000000
    LinBytesPerScanLine: 3200
    BnkNumberOfImagePages: 16
    LinNumberOfImagePages: 16
    LinRedMaskSize: 5
    LinRedFieldPosition: 11
    LinGreenMaskSize: 6
    LinGreenFieldPosition: 5
    LinBlueMaskSize: 5
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 230000000
*Mode: 15a (1600x1200)
    ModeAttributes: 0x9b
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc00079bc
    BytesPerScanline: 6400
    XResolution: 1600
    YResolution: 1200
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 32
    NumberOfBanks: 1
    MemoryModel: 6
    BankSize: 0
    NumberOfImages: 7
    RedMaskSize: 8
    RedFieldPosition: 16
    GreenMaskSize: 8
    GreenFieldPosition: 8
    BlueMaskSize: 8
    BlueFieldPosition: 0
    RsvdMaskSize: 8
    RsvdFieldPosition: 24
    DirectColorModeInfo: 0
    PhysBasePtr: 0xc0000000
    LinBytesPerScanLine: 6400
    BnkNumberOfImagePages: 7
    LinNumberOfImagePages: 7
    LinRedMaskSize: 8
    LinRedFieldPosition: 16
    LinGreenMaskSize: 8
    LinGreenFieldPosition: 8
    LinBlueMaskSize: 8
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 8
    LinRsvdFieldPosition: 24
    MaxPixelClock: 230000000
Mode: 107 (1280x1024)
    ModeAttributes: 0x9b
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc00079bc
    BytesPerScanline: 1280
    XResolution: 1280
    YResolution: 1024
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 8
    NumberOfBanks: 1
    MemoryModel: 4
    BankSize: 0
    NumberOfImages: 50
    RedMaskSize: 0
    RedFieldPosition: 0
    GreenMaskSize: 0
    GreenFieldPosition: 0
    BlueMaskSize: 0
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0xc0000000
    LinBytesPerScanLine: 1280
    BnkNumberOfImagePages: 50
    LinNumberOfImagePages: 50
    LinRedMaskSize: 0
    LinRedFieldPosition: 0
    LinGreenMaskSize: 0
    LinGreenFieldPosition: 0
    LinBlueMaskSize: 0
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 230000000
Mode: 11a (1280x1024)
    ModeAttributes: 0x9b
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc00079bc
    BytesPerScanline: 2560
    XResolution: 1280
    YResolution: 1024
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 16
    NumberOfBanks: 1
    MemoryModel: 6
    BankSize: 0
    NumberOfImages: 24
    RedMaskSize: 5
    RedFieldPosition: 11
    GreenMaskSize: 6
    GreenFieldPosition: 5
    BlueMaskSize: 5
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0xc0000000
    LinBytesPerScanLine: 2560
    BnkNumberOfImagePages: 24
    LinNumberOfImagePages: 24
    LinRedMaskSize: 5
    LinRedFieldPosition: 11
    LinGreenMaskSize: 6
    LinGreenFieldPosition: 5
    LinBlueMaskSize: 5
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 230000000
*Mode: 11b (1280x1024)
    ModeAttributes: 0x9b
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc00079bc
    BytesPerScanline: 5120
    XResolution: 1280
    YResolution: 1024
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 32
    NumberOfBanks: 1
    MemoryModel: 6
    BankSize: 0
    NumberOfImages: 11
    RedMaskSize: 8
    RedFieldPosition: 16
    GreenMaskSize: 8
    GreenFieldPosition: 8
    BlueMaskSize: 8
    BlueFieldPosition: 0
    RsvdMaskSize: 8
    RsvdFieldPosition: 24
    DirectColorModeInfo: 0
    PhysBasePtr: 0xc0000000
    LinBytesPerScanLine: 5120
    BnkNumberOfImagePages: 11
    LinNumberOfImagePages: 11
    LinRedMaskSize: 8
    LinRedFieldPosition: 16
    LinGreenMaskSize: 8
    LinGreenFieldPosition: 8
    LinBlueMaskSize: 8
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 8
    LinRsvdFieldPosition: 24
    MaxPixelClock: 230000000
Mode: 105 (1024x768)
    ModeAttributes: 0x9b
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc00079bc
    BytesPerScanline: 1024
    XResolution: 1024
    YResolution: 768
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 8
    NumberOfBanks: 1
    MemoryModel: 4
    BankSize: 0
    NumberOfImages: 84
    RedMaskSize: 0
    RedFieldPosition: 0
    GreenMaskSize: 0
    GreenFieldPosition: 0
    BlueMaskSize: 0
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0xc0000000
    LinBytesPerScanLine: 1024
    BnkNumberOfImagePages: 84
    LinNumberOfImagePages: 84
    LinRedMaskSize: 0
    LinRedFieldPosition: 0
    LinGreenMaskSize: 0
    LinGreenFieldPosition: 0
    LinBlueMaskSize: 0
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 230000000
Mode: 117 (1024x768)
    ModeAttributes: 0x9b
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc00079bc
    BytesPerScanline: 2048
    XResolution: 1024
    YResolution: 768
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 16
    NumberOfBanks: 1
    MemoryModel: 6
    BankSize: 0
    NumberOfImages: 41
    RedMaskSize: 5
    RedFieldPosition: 11
    GreenMaskSize: 6
    GreenFieldPosition: 5
    BlueMaskSize: 5
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0xc0000000
    LinBytesPerScanLine: 2048
    BnkNumberOfImagePages: 41
    LinNumberOfImagePages: 41
    LinRedMaskSize: 5
    LinRedFieldPosition: 11
    LinGreenMaskSize: 6
    LinGreenFieldPosition: 5
    LinBlueMaskSize: 5
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 230000000
*Mode: 118 (1024x768)
    ModeAttributes: 0x9b
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc00079bc
    BytesPerScanline: 4096
    XResolution: 1024
    YResolution: 768
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 32
    NumberOfBanks: 1
    MemoryModel: 6
    BankSize: 0
    NumberOfImages: 20
    RedMaskSize: 8
    RedFieldPosition: 16
    GreenMaskSize: 8
    GreenFieldPosition: 8
    BlueMaskSize: 8
    BlueFieldPosition: 0
    RsvdMaskSize: 8
    RsvdFieldPosition: 24
    DirectColorModeInfo: 0
    PhysBasePtr: 0xc0000000
    LinBytesPerScanLine: 4096
    BnkNumberOfImagePages: 20
    LinNumberOfImagePages: 20
    LinRedMaskSize: 8
    LinRedFieldPosition: 16
    LinGreenMaskSize: 8
    LinGreenFieldPosition: 8
    LinBlueMaskSize: 8
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 8
    LinRsvdFieldPosition: 24
    MaxPixelClock: 230000000
*Mode: 112 (640x480)
    ModeAttributes: 0x9b
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc00079bc
    BytesPerScanline: 2560
    XResolution: 640
    YResolution: 480
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 32
    NumberOfBanks: 1
    MemoryModel: 6
    BankSize: 0
    NumberOfImages: 52
    RedMaskSize: 8
    RedFieldPosition: 16
    GreenMaskSize: 8
    GreenFieldPosition: 8
    BlueMaskSize: 8
    BlueFieldPosition: 0
    RsvdMaskSize: 8
    RsvdFieldPosition: 24
    DirectColorModeInfo: 0
    PhysBasePtr: 0xc0000000
    LinBytesPerScanLine: 2560
    BnkNumberOfImagePages: 52
    LinNumberOfImagePages: 52
    LinRedMaskSize: 8
    LinRedFieldPosition: 16
    LinGreenMaskSize: 8
    LinGreenFieldPosition: 8
    LinBlueMaskSize: 8
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 8
    LinRsvdFieldPosition: 24
    MaxPixelClock: 230000000
Mode: 114 (800x600)
    ModeAttributes: 0x9b
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc00079bc
    BytesPerScanline: 1600
    XResolution: 800
    YResolution: 600
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 16
    NumberOfBanks: 1
    MemoryModel: 6
    BankSize: 0
    NumberOfImages: 67
    RedMaskSize: 5
    RedFieldPosition: 11
    GreenMaskSize: 6
    GreenFieldPosition: 5
    BlueMaskSize: 5
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0xc0000000
    LinBytesPerScanLine: 1600
    BnkNumberOfImagePages: 67
    LinNumberOfImagePages: 67
    LinRedMaskSize: 5
    LinRedFieldPosition: 11
    LinGreenMaskSize: 6
    LinGreenFieldPosition: 5
    LinBlueMaskSize: 5
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 230000000
*Mode: 115 (800x600)
    ModeAttributes: 0x9b
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc00079bc
    BytesPerScanline: 3200
    XResolution: 800
    YResolution: 600
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 32
    NumberOfBanks: 1
    MemoryModel: 6
    BankSize: 0
    NumberOfImages: 33
    RedMaskSize: 8
    RedFieldPosition: 16
    GreenMaskSize: 8
    GreenFieldPosition: 8
    BlueMaskSize: 8
    BlueFieldPosition: 0
    RsvdMaskSize: 8
    RsvdFieldPosition: 24
    DirectColorModeInfo: 0
    PhysBasePtr: 0xc0000000
    LinBytesPerScanLine: 3200
    BnkNumberOfImagePages: 33
    LinNumberOfImagePages: 33
    LinRedMaskSize: 8
    LinRedFieldPosition: 16
    LinGreenMaskSize: 8
    LinGreenFieldPosition: 8
    LinBlueMaskSize: 8
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 8
    LinRsvdFieldPosition: 24
    MaxPixelClock: 230000000
Mode: 101 (640x480)
    ModeAttributes: 0x9b
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc00079bc
    BytesPerScanline: 640
    XResolution: 640
    YResolution: 480
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 8
    NumberOfBanks: 1
    MemoryModel: 4
    BankSize: 0
    NumberOfImages: 203
    RedMaskSize: 0
    RedFieldPosition: 0
    GreenMaskSize: 0
    GreenFieldPosition: 0
    BlueMaskSize: 0
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0xc0000000
    LinBytesPerScanLine: 640
    BnkNumberOfImagePages: 203
    LinNumberOfImagePages: 203
    LinRedMaskSize: 0
    LinRedFieldPosition: 0
    LinGreenMaskSize: 0
    LinGreenFieldPosition: 0
    LinBlueMaskSize: 0
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 230000000
Mode: 103 (800x600)
    ModeAttributes: 0x9b
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc00079bc
    BytesPerScanline: 832
    XResolution: 800
    YResolution: 600
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 8
    NumberOfBanks: 1
    MemoryModel: 4
    BankSize: 0
    NumberOfImages: 126
    RedMaskSize: 0
    RedFieldPosition: 0
    GreenMaskSize: 0
    GreenFieldPosition: 0
    BlueMaskSize: 0
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0xc0000000
    LinBytesPerScanLine: 832
    BnkNumberOfImagePages: 126
    LinNumberOfImagePages: 126
    LinRedMaskSize: 0
    LinRedFieldPosition: 0
    LinGreenMaskSize: 0
    LinGreenFieldPosition: 0
    LinBlueMaskSize: 0
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 230000000
Mode: 111 (640x480)
    ModeAttributes: 0x9b
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc00079bc
    BytesPerScanline: 1280
    XResolution: 640
    YResolution: 480
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 16
    NumberOfBanks: 1
    MemoryModel: 6
    BankSize: 0
    NumberOfImages: 101
    RedMaskSize: 5
    RedFieldPosition: 11
    GreenMaskSize: 6
    GreenFieldPosition: 5
    BlueMaskSize: 5
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0xc0000000
    LinBytesPerScanLine: 1280
    BnkNumberOfImagePages: 101
    LinNumberOfImagePages: 101
    LinRedMaskSize: 5
    LinRedFieldPosition: 11
    LinGreenMaskSize: 6
    LinGreenFieldPosition: 5
    LinBlueMaskSize: 5
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 230000000

(II) VESA(0): Total Memory: 1023 64KB banks (65472kB)
(II) VESA(0): <default monitor>: Using hsync range of 30.00-81.00 kHz
(II) VESA(0): <default monitor>: Using vrefresh range of 56.00-75.00 Hz
(II) VESA(0): <default monitor>: Using maximum pixel clock of 150.00 MHz
(WW) VESA(0): Unable to estimate virtual size
(II) VESA(0): Not using built-in mode "1920x1440" (no mode of this name)
(II) VESA(0): Not using built-in mode "1600x1200" (no mode of this name)
(II) VESA(0): Not using built-in mode "1280x1024" (no mode of this name)
(--) VESA(0): Virtual size is 1024x768 (pitch 1024)
(**) VESA(0): *Built-in mode "1024x768"
(**) VESA(0): *Built-in mode "800x600"
(**) VESA(0): *Built-in mode "640x480"
(**) VESA(0): Display dimensions: (440, 250) mm
(**) VESA(0): DPI set to (59, 78)
(**) VESA(0): Using "Shadow Framebuffer"
(II) Loading sub module "shadow"
(II) LoadModule: "shadow"
(II) Loading /usr/lib/xorg/modules/libshadow.so
(II) Module shadow: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.1.0
    ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.4
(II) UnloadModule: "intel"
(II) Unloading /usr/lib/xorg/modules/drivers/intel_drv.so
(II) UnloadModule: "fbdev"
(II) Unloading /usr/lib/xorg/modules/drivers/fbdev_drv.so
(II) UnloadModule: "fbdevhw"
(II) Unloading /usr/lib/xorg/modules/linux/libfbdevhw.so
(==) Depth 24 pixmap format is 32 bpp
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules/libint10.so
(II) VESA(0): initializing int10
(II) VESA(0): Primary V_BIOS segment is: 0xc000
(II) VESA(0): VESA BIOS detected
(II) VESA(0): VESA VBE Version 3.0
(II) VESA(0): VESA VBE Total Mem: 65472 kB
(II) VESA(0): VESA VBE OEM: Intel(R)Sandybridge Desktop Graphics Chipset Accelerated VGA BIOS
(II) VESA(0): VESA VBE OEM Software Rev: 1.0
(II) VESA(0): VESA VBE OEM Vendor: Intel Corporation
(II) VESA(0): VESA VBE OEM Product: Intel(R)Sandybridge Desktop Graphics Controller
(II) VESA(0): VESA VBE OEM Product Rev: Hardware Version 0.0
(II) VESA(0): virtual address = 0x7f5b5dc52000,
    physical address = 0xc0000000, size = 67043328
(II) VESA(0): Setting up VESA Mode 0x118 (1024x768)
(==) VESA(0): Default visual is TrueColor
(==) VESA(0): Backing store disabled
(==) VESA(0): DPMS enabled
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
(II) config/udev: Adding input device Power Button (/dev/input/event1)
(**) Power Button: Applying InputClass "evdev keyboard catchall"
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 2.3.2
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 7.0
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event1"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/udev: Adding input device Power Button (/dev/input/event0)
(**) Power Button: Applying InputClass "evdev keyboard catchall"
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event0"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/udev: Adding input device Logitech USB Receiver (/dev/input/event3)
(**) Logitech USB Receiver: Applying InputClass "evdev keyboard catchall"
(**) Logitech USB Receiver: always reports core events
(**) Logitech USB Receiver: Device: "/dev/input/event3"
(II) Logitech USB Receiver: Found keys
(II) Logitech USB Receiver: Configuring as keyboard
(II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/udev: Adding input device Logitech USB Receiver (/dev/input/event4)
(**) Logitech USB Receiver: Applying InputClass "evdev pointer catchall"
(**) Logitech USB Receiver: Applying InputClass "evdev keyboard catchall"
(**) Logitech USB Receiver: always reports core events
(**) Logitech USB Receiver: Device: "/dev/input/event4"
(II) Logitech USB Receiver: Found 20 mouse buttons
(II) Logitech USB Receiver: Found scroll wheel(s)
(II) Logitech USB Receiver: Found relative axes
(II) Logitech USB Receiver: Found x and y relative axes
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
(II) Logitech USB Receiver: initialized for relative axes.
(WW) Logitech USB Receiver: ignoring absolute axes.
(II) config/udev: Adding input device Logitech USB Receiver (/dev/input/mouse1)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device Macintosh mouse button emulation (/dev/input/event2)
(**) Macintosh mouse button emulation: Applying InputClass "evdev pointer catchall"
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event2"
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



code 2:
```

00:02.0 VGA compatible controller: Intel Corporation Device 0112 (rev 09)

```

---

### Post by amjjawad on 2011-08-13
PLEASE, Do not post the output of any command without "CODE" tags.

I'll do it for others so they can read it but please, do it yourself next time.
Thanks.

```

X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-28-server x86_64 Ubuntu
Current Operating System: Linux Colossus 2.6.32-33-generic #72-Ubuntu SMP Fri Jul 29 21:07:13 UTC 2011 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-33-generic root=UUID=a626e385-5e8a-4416-b923-ea8cb08b206d ro quiet splash
Build Date: 08 March 2011  08:22:34AM
xorg-server 2:1.7.6-2ubuntu7.6 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
Current version of pixman: 0.16.4
    Before reporting problems, check [http://wiki.x.org]("http://wiki.x.org/")
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sat Aug 13 07:38:45 2011
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"
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
(==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
(II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
(II) Loader magic: 0x7cb840
(II) Module ABI versions:
    X.Org ANSI C Emulation: 0.4
    X.Org Video Driver: 6.0
    X.Org XInput driver : 7.0
    X.Org Server Extension : 2.0
(++) using VT number 7

(--) PCI:*(0:0:2:0) 8086:0112:1462:7678 Intel Corporation rev 9, Mem @  0xfe000000/4194304, 0xc0000000/268435456, I/O @ 0x0000f000/64
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
(II) Loading /usr/lib/xorg/modules/extensions/libglx.so
(II) Module glx: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    ABI class: X.Org Server Extension, version 2.0
(==) AIGLX enabled
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
(==) Matched intel as autoconfigured driver 0
(==) Matched vesa as autoconfigured driver 1
(==) Matched fbdev as autoconfigured driver 2
(==) Assigned the driver to the xf86ConfigLayout
(II) LoadModule: "intel"
(II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
(II) Module intel: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 2.9.1
    Module class: X.Org Video Driver
    ABI class: X.Org Video Driver, version 6.0
(II) LoadModule: "vesa"
(II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
(II) Module vesa: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 2.3.0
    Module class: X.Org Video Driver
    ABI class: X.Org Video Driver, version 6.0
(II) LoadModule: "fbdev"
(II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
(II) Module fbdev: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 0.4.1
    ABI class: X.Org Video Driver, version 6.0
(II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
    i810-dc100, i810e, i815, i830M, 845G, 852GM/855GM, 865G, 915G,
    E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
    965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
    4 Series, G45/G43, Q45/Q43, G41, B43, Clarkdale, Arrandale
(II) VESA: driver for VESA chipsets: vesa
(II) FBDEV: driver for framebuffer: fbdev
(II) Primary Device is: PCI 00@00:02:0
(WW) Falling back to old probe method for fbdev
(II) Loading sub module "fbdevhw"
(II) LoadModule: "fbdevhw"
(II) Loading /usr/lib/xorg/modules/linux/libfbdevhw.so
(II) Module fbdevhw: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 0.0.2
    ABI class: X.Org Video Driver, version 6.0
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules/libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.1.0
    ABI class: X.Org Video Driver, version 6.0
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules/libint10.so
(II) Module int10: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    ABI class: X.Org Video Driver, version 6.0
(II) VESA(0): initializing int10
(II) VESA(0): Primary V_BIOS segment is: 0xc000
(II) VESA(0): VESA BIOS detected
(II) VESA(0): VESA VBE Version 3.0
(II) VESA(0): VESA VBE Total Mem: 65472 kB
(II) VESA(0): VESA VBE OEM: Intel(R)Sandybridge Desktop Graphics Chipset Accelerated VGA BIOS
(II) VESA(0): VESA VBE OEM Software Rev: 1.0
(II) VESA(0): VESA VBE OEM Vendor: Intel Corporation
(II) VESA(0): VESA VBE OEM Product: Intel(R)Sandybridge Desktop Graphics Controller
(II) VESA(0): VESA VBE OEM Product Rev: Hardware Version 0.0
(II) VESA(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
(==) VESA(0): Depth 24, (--) framebuffer bpp 32
(==) VESA(0): RGB weight 888
(==) VESA(0): Default visual is TrueColor
(==) VESA(0): Using gamma correction (1.0, 1.0, 1.0)
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(II) VESA(0): VESA VBE DDC supported
(II) VESA(0): VESA VBE DDC Level 2
(II) VESA(0): VESA VBE DDC transfer in appr. 1 sec.
(II) VESA(0): VESA VBE DDC read successfully
(II) VESA(0): Manufacturer: SAM  Model: 78b  Serial#: 1514292021
(II) VESA(0): Year: 2011  Week: 17
(II) VESA(0): EDID Version: 1.3
(II) VESA(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) VESA(0): Sync:  Separate  Composite  SyncOnGreen
(II) VESA(0): Max Image Size [cm]: horiz.: 44  vert.: 25
(II) VESA(0): Gamma: 2.20
(II) VESA(0): DPMS capabilities: Off; RGB/Color Display
(II) VESA(0): First detailed timing is preferred mode
(II) VESA(0): redX: 0.639 redY: 0.340   greenX: 0.324 greenY: 0.622
(II) VESA(0): blueX: 0.155 blueY: 0.042   whiteX: 0.312 whiteY: 0.329
(II) VESA(0): Supported established timings:
(II) VESA(0): 720x400@70Hz
(II) VESA(0): 640x480@60Hz
(II) VESA(0): 640x480@67Hz
(II) VESA(0): 640x480@72Hz
(II) VESA(0): 640x480@75Hz
(II) VESA(0): 800x600@56Hz
(II) VESA(0): 800x600@60Hz
(II) VESA(0): 800x600@72Hz
(II) VESA(0): 800x600@75Hz
(II) VESA(0): 832x624@75Hz
(II) VESA(0): 1024x768@60Hz
(II) VESA(0): 1024x768@70Hz
(II) VESA(0): 1024x768@75Hz
(II) VESA(0): 1152x864@75Hz
(II) VESA(0): Manufacturer's mask: 0
(II) VESA(0): Supported standard timings:
(II) VESA(0): #0: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) VESA(0): #1: hsize: 1280  vsize 800  refresh: 60  vid: 129
(II) VESA(0): #2: hsize: 1280  vsize 800  refresh: 75  vid: 3969
(II) VESA(0): #3: hsize: 1440  vsize 900  refresh: 60  vid: 149
(II) VESA(0): #4: hsize: 1440  vsize 900  refresh: 75  vid: 3989
(II) VESA(0): Supported detailed timing:
(II) VESA(0): clock: 108.0 MHz   Image Size:  443 x 249 mm
(II) VESA(0): h_active: 1600  h_sync: 1624  h_sync_end 1704 h_blank_end 1800 h_border: 0
(II) VESA(0): v_active: 900  v_sync: 901  v_sync_end 904 v_blanking: 1000 v_border: 0
(II) VESA(0): Ranges: V min: 56 V max: 75 Hz, H min: 30 H max: 81 kHz, PixClock max 150 MHz
(II) VESA(0): Monitor name: SA300/SA350
(II) VESA(0): Serial No: H9NB401854
(II) VESA(0): EDID (in hex):
(II) VESA(0):     00ffffffffffff004c2d8b073543425a
(II) VESA(0):     111501030e2c19782a81f1a357539f27
(II) VESA(0):     0a5054bfee80714f8100810f9500950f
(II) VESA(0):     010101010101302a40c8608464301850
(II) VESA(0):     1300bbf91000001e000000fd00384b1e
(II) VESA(0):     510f000a202020202020000000fc0053
(II) VESA(0):     413330302f53413335300a20000000ff
(II) VESA(0):     0048394e423430313835340a20200021
(II) VESA(0): EDID vendor "SAM", prod id 1931
(II) VESA(0): Using EDID range info for horizontal sync
(II) VESA(0): Using EDID range info for vertical refresh
(II) VESA(0): Printing DDC gathered Modelines:
(II) VESA(0): Modeline "1600x900"x0.0  108.00  1600 1624 1704 1800  900 901 904 1000 +hsync +vsync (60.0 kHz)
(II) VESA(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) VESA(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) VESA(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) VESA(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) VESA(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) VESA(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) VESA(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) VESA(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) VESA(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) VESA(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) VESA(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) VESA(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) VESA(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) VESA(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) VESA(0): Modeline "1280x800"x0.0   83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync (49.7 kHz)
(II) VESA(0): Modeline "1280x800"x0.0  106.50  1280 1360 1488 1696  800 803 809 838 -hsync +vsync (62.8 kHz)
(II) VESA(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
(II) VESA(0): Modeline "1440x900"x0.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz)
(II) VESA(0): Searching for matching VESA mode(s):
Mode: 160 (0x0)
    ModeAttributes: 0x0
    WinAAttributes: 0x0
    WinBAttributes: 0x0
    WinGranularity: 0
    WinSize: 0
    WinASegment: 0x0
    WinBSegment: 0x0
    WinFuncPtr: 0x0
    BytesPerScanline: 0
    XResolution: 0
    YResolution: 0
    XCharSize: 0
    YCharSize: 0
    NumberOfPlanes: 0
    BitsPerPixel: 0
    NumberOfBanks: 0
    MemoryModel: 0
    BankSize: 0
    NumberOfImages: 0
    RedMaskSize: 0
    RedFieldPosition: 0
    GreenMaskSize: 0
    GreenFieldPosition: 0
    BlueMaskSize: 0
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0x0
    LinBytesPerScanLine: 0
    BnkNumberOfImagePages: 0
    LinNumberOfImagePages: 0
    LinRedMaskSize: 0
    LinRedFieldPosition: 0
    LinGreenMaskSize: 0
    LinGreenFieldPosition: 0
    LinBlueMaskSize: 0
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 0
Mode: 161 (0x0)
    ModeAttributes: 0x0
    WinAAttributes: 0x0
    WinBAttributes: 0x0
    WinGranularity: 0
    WinSize: 0
    WinASegment: 0x0
    WinBSegment: 0x0
    WinFuncPtr: 0x0
    BytesPerScanline: 0
    XResolution: 0
    YResolution: 0
    XCharSize: 0
    YCharSize: 0
    NumberOfPlanes: 0
    BitsPerPixel: 0
    NumberOfBanks: 0
    MemoryModel: 0
    BankSize: 0
    NumberOfImages: 0
    RedMaskSize: 0
    RedFieldPosition: 0
    GreenMaskSize: 0
    GreenFieldPosition: 0
    BlueMaskSize: 0
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0x0
    LinBytesPerScanLine: 0
    BnkNumberOfImagePages: 0
    LinNumberOfImagePages: 0
    LinRedMaskSize: 0
    LinRedFieldPosition: 0
    LinGreenMaskSize: 0
    LinGreenFieldPosition: 0
    LinBlueMaskSize: 0
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 0
Mode: 162 (0x0)
    ModeAttributes: 0x0
    WinAAttributes: 0x0
    WinBAttributes: 0x0
    WinGranularity: 0
    WinSize: 0
    WinASegment: 0x0
    WinBSegment: 0x0
    WinFuncPtr: 0x0
    BytesPerScanline: 0
    XResolution: 0
    YResolution: 0
    XCharSize: 0
    YCharSize: 0
    NumberOfPlanes: 0
    BitsPerPixel: 0
    NumberOfBanks: 0
    MemoryModel: 0
    BankSize: 0
    NumberOfImages: 0
    RedMaskSize: 0
    RedFieldPosition: 0
    GreenMaskSize: 0
    GreenFieldPosition: 0
    BlueMaskSize: 0
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0x0
    LinBytesPerScanLine: 0
    BnkNumberOfImagePages: 0
    LinNumberOfImagePages: 0
    LinRedMaskSize: 0
    LinRedFieldPosition: 0
    LinGreenMaskSize: 0
    LinGreenFieldPosition: 0
    LinBlueMaskSize: 0
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 0
Mode: 163 (0x0)
    ModeAttributes: 0x0
    WinAAttributes: 0x0
    WinBAttributes: 0x0
    WinGranularity: 0
    WinSize: 0
    WinASegment: 0x0
    WinBSegment: 0x0
    WinFuncPtr: 0x0
    BytesPerScanline: 0
    XResolution: 0
    YResolution: 0
    XCharSize: 0
    YCharSize: 0
    NumberOfPlanes: 0
    BitsPerPixel: 0
    NumberOfBanks: 0
    MemoryModel: 0
    BankSize: 0
    NumberOfImages: 0
    RedMaskSize: 0
    RedFieldPosition: 0
    GreenMaskSize: 0
    GreenFieldPosition: 0
    BlueMaskSize: 0
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0x0
    LinBytesPerScanLine: 0
    BnkNumberOfImagePages: 0
    LinNumberOfImagePages: 0
    LinRedMaskSize: 0
    LinRedFieldPosition: 0
    LinGreenMaskSize: 0
    LinGreenFieldPosition: 0
    LinBlueMaskSize: 0
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 0
Mode: 164 (0x0)
    ModeAttributes: 0x0
    WinAAttributes: 0x0
    WinBAttributes: 0x0
    WinGranularity: 0
    WinSize: 0
    WinASegment: 0x0
    WinBSegment: 0x0
    WinFuncPtr: 0x0
    BytesPerScanline: 0
    XResolution: 0
    YResolution: 0
    XCharSize: 0
    YCharSize: 0
    NumberOfPlanes: 0
    BitsPerPixel: 0
    NumberOfBanks: 0
    MemoryModel: 0
    BankSize: 0
    NumberOfImages: 0
    RedMaskSize: 0
    RedFieldPosition: 0
    GreenMaskSize: 0
    GreenFieldPosition: 0
    BlueMaskSize: 0
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0x0
    LinBytesPerScanLine: 0
    BnkNumberOfImagePages: 0
    LinNumberOfImagePages: 0
    LinRedMaskSize: 0
    LinRedFieldPosition: 0
    LinGreenMaskSize: 0
    LinGreenFieldPosition: 0
    LinBlueMaskSize: 0
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 0
Mode: 165 (0x0)
    ModeAttributes: 0x0
    WinAAttributes: 0x0
    WinBAttributes: 0x0
    WinGranularity: 0
    WinSize: 0
    WinASegment: 0x0
    WinBSegment: 0x0
    WinFuncPtr: 0x0
    BytesPerScanline: 0
    XResolution: 0
    YResolution: 0
    XCharSize: 0
    YCharSize: 0
    NumberOfPlanes: 0
    BitsPerPixel: 0
    NumberOfBanks: 0
    MemoryModel: 0
    BankSize: 0
    NumberOfImages: 0
    RedMaskSize: 0
    RedFieldPosition: 0
    GreenMaskSize: 0
    GreenFieldPosition: 0
    BlueMaskSize: 0
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0x0
    LinBytesPerScanLine: 0
    BnkNumberOfImagePages: 0
    LinNumberOfImagePages: 0
    LinRedMaskSize: 0
    LinRedFieldPosition: 0
    LinGreenMaskSize: 0
    LinGreenFieldPosition: 0
    LinBlueMaskSize: 0
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 0
Mode: 166 (0x0)
    ModeAttributes: 0x0
    WinAAttributes: 0x0
    WinBAttributes: 0x0
    WinGranularity: 0
    WinSize: 0
    WinASegment: 0x0
    WinBSegment: 0x0
    WinFuncPtr: 0x0
    BytesPerScanline: 0
    XResolution: 0
    YResolution: 0
    XCharSize: 0
    YCharSize: 0
    NumberOfPlanes: 0
    BitsPerPixel: 0
    NumberOfBanks: 0
    MemoryModel: 0
    BankSize: 0
    NumberOfImages: 0
    RedMaskSize: 0
    RedFieldPosition: 0
    GreenMaskSize: 0
    GreenFieldPosition: 0
    BlueMaskSize: 0
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0x0
    LinBytesPerScanLine: 0
    BnkNumberOfImagePages: 0
    LinNumberOfImagePages: 0
    LinRedMaskSize: 0
    LinRedFieldPosition: 0
    LinGreenMaskSize: 0
    LinGreenFieldPosition: 0
    LinBlueMaskSize: 0
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 0
Mode: 167 (0x0)
    ModeAttributes: 0x0
    WinAAttributes: 0x0
    WinBAttributes: 0x0
    WinGranularity: 0
    WinSize: 0
    WinASegment: 0x0
    WinBSegment: 0x0
    WinFuncPtr: 0x0
    BytesPerScanline: 0
    XResolution: 0
    YResolution: 0
    XCharSize: 0
    YCharSize: 0
    NumberOfPlanes: 0
    BitsPerPixel: 0
    NumberOfBanks: 0
    MemoryModel: 0
    BankSize: 0
    NumberOfImages: 0
    RedMaskSize: 0
    RedFieldPosition: 0
    GreenMaskSize: 0
    GreenFieldPosition: 0
    BlueMaskSize: 0
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0x0
    LinBytesPerScanLine: 0
    BnkNumberOfImagePages: 0
    LinNumberOfImagePages: 0
    LinRedMaskSize: 0
    LinRedFieldPosition: 0
    LinGreenMaskSize: 0
    LinGreenFieldPosition: 0
    LinBlueMaskSize: 0
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 0
Mode: 168 (0x0)
    ModeAttributes: 0x0
    WinAAttributes: 0x0
    WinBAttributes: 0x0
    WinGranularity: 0
    WinSize: 0
    WinASegment: 0x0
    WinBSegment: 0x0
    WinFuncPtr: 0x0
    BytesPerScanline: 0
    XResolution: 0
    YResolution: 0
    XCharSize: 0
    YCharSize: 0
    NumberOfPlanes: 0
    BitsPerPixel: 0
    NumberOfBanks: 0
    MemoryModel: 0
    BankSize: 0
    NumberOfImages: 0
    RedMaskSize: 0
    RedFieldPosition: 0
    GreenMaskSize: 0
    GreenFieldPosition: 0
    BlueMaskSize: 0
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0x0
    LinBytesPerScanLine: 0
    BnkNumberOfImagePages: 0
    LinNumberOfImagePages: 0
    LinRedMaskSize: 0
    LinRedFieldPosition: 0
    LinGreenMaskSize: 0
    LinGreenFieldPosition: 0
    LinBlueMaskSize: 0
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 0
Mode: 13c (1920x1440)
    ModeAttributes: 0x9b
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc00079bc
    BytesPerScanline: 1920
    XResolution: 1920
    YResolution: 1440
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 8
    NumberOfBanks: 1
    MemoryModel: 4
    BankSize: 0
    NumberOfImages: 22
    RedMaskSize: 0
    RedFieldPosition: 0
    GreenMaskSize: 0
    GreenFieldPosition: 0
    BlueMaskSize: 0
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0xc0000000
    LinBytesPerScanLine: 1920
    BnkNumberOfImagePages: 22
    LinNumberOfImagePages: 22
    LinRedMaskSize: 0
    LinRedFieldPosition: 0
    LinGreenMaskSize: 0
    LinGreenFieldPosition: 0
    LinBlueMaskSize: 0
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 230000000
Mode: 14d (1920x1440)
    ModeAttributes: 0x9b
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc00079bc
    BytesPerScanline: 3840
    XResolution: 1920
    YResolution: 1440
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 16
    NumberOfBanks: 1
    MemoryModel: 6
    BankSize: 0
    NumberOfImages: 11
    RedMaskSize: 5
    RedFieldPosition: 11
    GreenMaskSize: 6
    GreenFieldPosition: 5
    BlueMaskSize: 5
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0xc0000000
    LinBytesPerScanLine: 3840
    BnkNumberOfImagePages: 11
    LinNumberOfImagePages: 11
    LinRedMaskSize: 5
    LinRedFieldPosition: 11
    LinGreenMaskSize: 6
    LinGreenFieldPosition: 5
    LinBlueMaskSize: 5
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 230000000
*Mode: 15c (1920x1440)
    ModeAttributes: 0x9b
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc00079bc
    BytesPerScanline: 7680
    XResolution: 1920
    YResolution: 1440
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 32
    NumberOfBanks: 1
    MemoryModel: 6
    BankSize: 0
    NumberOfImages: 5
    RedMaskSize: 8
    RedFieldPosition: 16
    GreenMaskSize: 8
    GreenFieldPosition: 8
    BlueMaskSize: 8
    BlueFieldPosition: 0
    RsvdMaskSize: 8
    RsvdFieldPosition: 24
    DirectColorModeInfo: 0
    PhysBasePtr: 0xc0000000
    LinBytesPerScanLine: 7680
    BnkNumberOfImagePages: 5
    LinNumberOfImagePages: 5
    LinRedMaskSize: 8
    LinRedFieldPosition: 16
    LinGreenMaskSize: 8
    LinGreenFieldPosition: 8
    LinBlueMaskSize: 8
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 8
    LinRsvdFieldPosition: 24
    MaxPixelClock: 230000000
Mode: 13a (1600x1200)
    ModeAttributes: 0x9b
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc00079bc
    BytesPerScanline: 1600
    XResolution: 1600
    YResolution: 1200
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 8
    NumberOfBanks: 1
    MemoryModel: 4
    BankSize: 0
    NumberOfImages: 33
    RedMaskSize: 0
    RedFieldPosition: 0
    GreenMaskSize: 0
    GreenFieldPosition: 0
    BlueMaskSize: 0
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0xc0000000
    LinBytesPerScanLine: 1600
    BnkNumberOfImagePages: 33
    LinNumberOfImagePages: 33
    LinRedMaskSize: 0
    LinRedFieldPosition: 0
    LinGreenMaskSize: 0
    LinGreenFieldPosition: 0
    LinBlueMaskSize: 0
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 230000000
Mode: 14b (1600x1200)
    ModeAttributes: 0x9b
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc00079bc
    BytesPerScanline: 3200
    XResolution: 1600
    YResolution: 1200
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 16
    NumberOfBanks: 1
    MemoryModel: 6
    BankSize: 0
    NumberOfImages: 16
    RedMaskSize: 5
    RedFieldPosition: 11
    GreenMaskSize: 6
    GreenFieldPosition: 5
    BlueMaskSize: 5
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0xc0000000
    LinBytesPerScanLine: 3200
    BnkNumberOfImagePages: 16
    LinNumberOfImagePages: 16
    LinRedMaskSize: 5
    LinRedFieldPosition: 11
    LinGreenMaskSize: 6
    LinGreenFieldPosition: 5
    LinBlueMaskSize: 5
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 230000000
*Mode: 15a (1600x1200)
    ModeAttributes: 0x9b
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc00079bc
    BytesPerScanline: 6400
    XResolution: 1600
    YResolution: 1200
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 32
    NumberOfBanks: 1
    MemoryModel: 6
    BankSize: 0
    NumberOfImages: 7
    RedMaskSize: 8
    RedFieldPosition: 16
    GreenMaskSize: 8
    GreenFieldPosition: 8
    BlueMaskSize: 8
    BlueFieldPosition: 0
    RsvdMaskSize: 8
    RsvdFieldPosition: 24
    DirectColorModeInfo: 0
    PhysBasePtr: 0xc0000000
    LinBytesPerScanLine: 6400
    BnkNumberOfImagePages: 7
    LinNumberOfImagePages: 7
    LinRedMaskSize: 8
    LinRedFieldPosition: 16
    LinGreenMaskSize: 8
    LinGreenFieldPosition: 8
    LinBlueMaskSize: 8
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 8
    LinRsvdFieldPosition: 24
    MaxPixelClock: 230000000
Mode: 107 (1280x1024)
    ModeAttributes: 0x9b
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc00079bc
    BytesPerScanline: 1280
    XResolution: 1280
    YResolution: 1024
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 8
    NumberOfBanks: 1
    MemoryModel: 4
    BankSize: 0
    NumberOfImages: 50
    RedMaskSize: 0
    RedFieldPosition: 0
    GreenMaskSize: 0
    GreenFieldPosition: 0
    BlueMaskSize: 0
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0xc0000000
    LinBytesPerScanLine: 1280
    BnkNumberOfImagePages: 50
    LinNumberOfImagePages: 50
    LinRedMaskSize: 0
    LinRedFieldPosition: 0
    LinGreenMaskSize: 0
    LinGreenFieldPosition: 0
    LinBlueMaskSize: 0
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 230000000
Mode: 11a (1280x1024)
    ModeAttributes: 0x9b
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc00079bc
    BytesPerScanline: 2560
    XResolution: 1280
    YResolution: 1024
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 16
    NumberOfBanks: 1
    MemoryModel: 6
    BankSize: 0
    NumberOfImages: 24
    RedMaskSize: 5
    RedFieldPosition: 11
    GreenMaskSize: 6
    GreenFieldPosition: 5
    BlueMaskSize: 5
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0xc0000000
    LinBytesPerScanLine: 2560
    BnkNumberOfImagePages: 24
    LinNumberOfImagePages: 24
    LinRedMaskSize: 5
    LinRedFieldPosition: 11
    LinGreenMaskSize: 6
    LinGreenFieldPosition: 5
    LinBlueMaskSize: 5
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 230000000
*Mode: 11b (1280x1024)
    ModeAttributes: 0x9b
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc00079bc
    BytesPerScanline: 5120
    XResolution: 1280
    YResolution: 1024
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 32
    NumberOfBanks: 1
    MemoryModel: 6
    BankSize: 0
    NumberOfImages: 11
    RedMaskSize: 8
    RedFieldPosition: 16
    GreenMaskSize: 8
    GreenFieldPosition: 8
    BlueMaskSize: 8
    BlueFieldPosition: 0
    RsvdMaskSize: 8
    RsvdFieldPosition: 24
    DirectColorModeInfo: 0
    PhysBasePtr: 0xc0000000
    LinBytesPerScanLine: 5120
    BnkNumberOfImagePages: 11
    LinNumberOfImagePages: 11
    LinRedMaskSize: 8
    LinRedFieldPosition: 16
    LinGreenMaskSize: 8
    LinGreenFieldPosition: 8
    LinBlueMaskSize: 8
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 8
    LinRsvdFieldPosition: 24
    MaxPixelClock: 230000000
Mode: 105 (1024x76:cool:
    ModeAttributes: 0x9b
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc00079bc
    BytesPerScanline: 1024
    XResolution: 1024
    YResolution: 768
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 8
    NumberOfBanks: 1
    MemoryModel: 4
    BankSize: 0
    NumberOfImages: 84
    RedMaskSize: 0
    RedFieldPosition: 0
    GreenMaskSize: 0
    GreenFieldPosition: 0
    BlueMaskSize: 0
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0xc0000000
    LinBytesPerScanLine: 1024
    BnkNumberOfImagePages: 84
    LinNumberOfImagePages: 84
    LinRedMaskSize: 0
    LinRedFieldPosition: 0
    LinGreenMaskSize: 0
    LinGreenFieldPosition: 0
    LinBlueMaskSize: 0
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 230000000
Mode: 117 (1024x76:cool:
    ModeAttributes: 0x9b
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc00079bc
    BytesPerScanline: 2048
    XResolution: 1024
    YResolution: 768
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 16
    NumberOfBanks: 1
    MemoryModel: 6
    BankSize: 0
    NumberOfImages: 41
    RedMaskSize: 5
    RedFieldPosition: 11
    GreenMaskSize: 6
    GreenFieldPosition: 5
    BlueMaskSize: 5
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0xc0000000
    LinBytesPerScanLine: 2048
    BnkNumberOfImagePages: 41
    LinNumberOfImagePages: 41
    LinRedMaskSize: 5
    LinRedFieldPosition: 11
    LinGreenMaskSize: 6
    LinGreenFieldPosition: 5
    LinBlueMaskSize: 5
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 230000000
*Mode: 118 (1024x76:cool:
    ModeAttributes: 0x9b
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc00079bc
    BytesPerScanline: 4096
    XResolution: 1024
    YResolution: 768
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 32
    NumberOfBanks: 1
    MemoryModel: 6
    BankSize: 0
    NumberOfImages: 20
    RedMaskSize: 8
    RedFieldPosition: 16
    GreenMaskSize: 8
    GreenFieldPosition: 8
    BlueMaskSize: 8
    BlueFieldPosition: 0
    RsvdMaskSize: 8
    RsvdFieldPosition: 24
    DirectColorModeInfo: 0
    PhysBasePtr: 0xc0000000
    LinBytesPerScanLine: 4096
    BnkNumberOfImagePages: 20
    LinNumberOfImagePages: 20
    LinRedMaskSize: 8
    LinRedFieldPosition: 16
    LinGreenMaskSize: 8
    LinGreenFieldPosition: 8
    LinBlueMaskSize: 8
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 8
    LinRsvdFieldPosition: 24
    MaxPixelClock: 230000000
*Mode: 112 (640x480)
    ModeAttributes: 0x9b
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc00079bc
    BytesPerScanline: 2560
    XResolution: 640
    YResolution: 480
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 32
    NumberOfBanks: 1
    MemoryModel: 6
    BankSize: 0
    NumberOfImages: 52
    RedMaskSize: 8
    RedFieldPosition: 16
    GreenMaskSize: 8
    GreenFieldPosition: 8
    BlueMaskSize: 8
    BlueFieldPosition: 0
    RsvdMaskSize: 8
    RsvdFieldPosition: 24
    DirectColorModeInfo: 0
    PhysBasePtr: 0xc0000000
    LinBytesPerScanLine: 2560
    BnkNumberOfImagePages: 52
    LinNumberOfImagePages: 52
    LinRedMaskSize: 8
    LinRedFieldPosition: 16
    LinGreenMaskSize: 8
    LinGreenFieldPosition: 8
    LinBlueMaskSize: 8
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 8
    LinRsvdFieldPosition: 24
    MaxPixelClock: 230000000
Mode: 114 (800x600)
    ModeAttributes: 0x9b
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc00079bc
    BytesPerScanline: 1600
    XResolution: 800
    YResolution: 600
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 16
    NumberOfBanks: 1
    MemoryModel: 6
    BankSize: 0
    NumberOfImages: 67
    RedMaskSize: 5
    RedFieldPosition: 11
    GreenMaskSize: 6
    GreenFieldPosition: 5
    BlueMaskSize: 5
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0xc0000000
    LinBytesPerScanLine: 1600
    BnkNumberOfImagePages: 67
    LinNumberOfImagePages: 67
    LinRedMaskSize: 5
    LinRedFieldPosition: 11
    LinGreenMaskSize: 6
    LinGreenFieldPosition: 5
    LinBlueMaskSize: 5
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 230000000
*Mode: 115 (800x600)
    ModeAttributes: 0x9b
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc00079bc
    BytesPerScanline: 3200
    XResolution: 800
    YResolution: 600
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 32
    NumberOfBanks: 1
    MemoryModel: 6
    BankSize: 0
    NumberOfImages: 33
    RedMaskSize: 8
    RedFieldPosition: 16
    GreenMaskSize: 8
    GreenFieldPosition: 8
    BlueMaskSize: 8
    BlueFieldPosition: 0
    RsvdMaskSize: 8
    RsvdFieldPosition: 24
    DirectColorModeInfo: 0
    PhysBasePtr: 0xc0000000
    LinBytesPerScanLine: 3200
    BnkNumberOfImagePages: 33
    LinNumberOfImagePages: 33
    LinRedMaskSize: 8
    LinRedFieldPosition: 16
    LinGreenMaskSize: 8
    LinGreenFieldPosition: 8
    LinBlueMaskSize: 8
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 8
    LinRsvdFieldPosition: 24
    MaxPixelClock: 230000000
Mode: 101 (640x480)
    ModeAttributes: 0x9b
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc00079bc
    BytesPerScanline: 640
    XResolution: 640
    YResolution: 480
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 8
    NumberOfBanks: 1
    MemoryModel: 4
    BankSize: 0
    NumberOfImages: 203
    RedMaskSize: 0
    RedFieldPosition: 0
    GreenMaskSize: 0
    GreenFieldPosition: 0
    BlueMaskSize: 0
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0xc0000000
    LinBytesPerScanLine: 640
    BnkNumberOfImagePages: 203
    LinNumberOfImagePages: 203
    LinRedMaskSize: 0
    LinRedFieldPosition: 0
    LinGreenMaskSize: 0
    LinGreenFieldPosition: 0
    LinBlueMaskSize: 0
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 230000000
Mode: 103 (800x600)
    ModeAttributes: 0x9b
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc00079bc
    BytesPerScanline: 832
    XResolution: 800
    YResolution: 600
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 8
    NumberOfBanks: 1
    MemoryModel: 4
    BankSize: 0
    NumberOfImages: 126
    RedMaskSize: 0
    RedFieldPosition: 0
    GreenMaskSize: 0
    GreenFieldPosition: 0
    BlueMaskSize: 0
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0xc0000000
    LinBytesPerScanLine: 832
    BnkNumberOfImagePages: 126
    LinNumberOfImagePages: 126
    LinRedMaskSize: 0
    LinRedFieldPosition: 0
    LinGreenMaskSize: 0
    LinGreenFieldPosition: 0
    LinBlueMaskSize: 0
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 230000000
Mode: 111 (640x480)
    ModeAttributes: 0x9b
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc00079bc
    BytesPerScanline: 1280
    XResolution: 640
    YResolution: 480
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 16
    NumberOfBanks: 1
    MemoryModel: 6
    BankSize: 0
    NumberOfImages: 101
    RedMaskSize: 5
    RedFieldPosition: 11
    GreenMaskSize: 6
    GreenFieldPosition: 5
    BlueMaskSize: 5
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0xc0000000
    LinBytesPerScanLine: 1280
    BnkNumberOfImagePages: 101
    LinNumberOfImagePages: 101
    LinRedMaskSize: 5
    LinRedFieldPosition: 11
    LinGreenMaskSize: 6
    LinGreenFieldPosition: 5
    LinBlueMaskSize: 5
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 230000000

(II) VESA(0): Total Memory: 1023 64KB banks (65472kB)
(II) VESA(0): <default monitor>: Using hsync range of 30.00-81.00 kHz
(II) VESA(0): <default monitor>: Using vrefresh range of 56.00-75.00 Hz
(II) VESA(0): <default monitor>: Using maximum pixel clock of 150.00 MHz
(WW) VESA(0): Unable to estimate virtual size
(II) VESA(0): Not using built-in mode "1920x1440" (no mode of this name)
(II) VESA(0): Not using built-in mode "1600x1200" (no mode of this name)
(II) VESA(0): Not using built-in mode "1280x1024" (no mode of this name)
(--) VESA(0): Virtual size is 1024x768 (pitch 1024)
(**) VESA(0): *Built-in mode "1024x768"
(**) VESA(0): *Built-in mode "800x600"
(**) VESA(0): *Built-in mode "640x480"
(**) VESA(0): Display dimensions: (440, 250) mm
(**) VESA(0): DPI set to (59, 7:cool:
(**) VESA(0): Using "Shadow Framebuffer"
(II) Loading sub module "shadow"
(II) LoadModule: "shadow"
(II) Loading /usr/lib/xorg/modules/libshadow.so
(II) Module shadow: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.1.0
    ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.4
(II) UnloadModule: "intel"
(II) Unloading /usr/lib/xorg/modules/drivers/intel_drv.so
(II) UnloadModule: "fbdev"
(II) Unloading /usr/lib/xorg/modules/drivers/fbdev_drv.so
(II) UnloadModule: "fbdevhw"
(II) Unloading /usr/lib/xorg/modules/linux/libfbdevhw.so
(==) Depth 24 pixmap format is 32 bpp
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules/libint10.so
(II) VESA(0): initializing int10
(II) VESA(0): Primary V_BIOS segment is: 0xc000
(II) VESA(0): VESA BIOS detected
(II) VESA(0): VESA VBE Version 3.0
(II) VESA(0): VESA VBE Total Mem: 65472 kB
(II) VESA(0): VESA VBE OEM: Intel(R)Sandybridge Desktop Graphics Chipset Accelerated VGA BIOS
(II) VESA(0): VESA VBE OEM Software Rev: 1.0
(II) VESA(0): VESA VBE OEM Vendor: Intel Corporation
(II) VESA(0): VESA VBE OEM Product: Intel(R)Sandybridge Desktop Graphics Controller
(II) VESA(0): VESA VBE OEM Product Rev: Hardware Version 0.0
(II) VESA(0): virtual address = 0x7f5b5dc52000,
    physical address = 0xc0000000, size = 67043328
(II) VESA(0): Setting up VESA Mode 0x118 (1024x76:cool:
(==) VESA(0): Default visual is TrueColor
(==) VESA(0): Backing store disabled
(==) VESA(0): DPMS enabled
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
(II) config/udev: Adding input device Power Button (/dev/input/event1)
(**) Power Button: Applying InputClass "evdev keyboard catchall"
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 2.3.2
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 7.0
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event1"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/udev: Adding input device Power Button (/dev/input/event0)
(**) Power Button: Applying InputClass "evdev keyboard catchall"
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event0"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/udev: Adding input device Logitech USB Receiver (/dev/input/event3)
(**) Logitech USB Receiver: Applying InputClass "evdev keyboard catchall"
(**) Logitech USB Receiver: always reports core events
(**) Logitech USB Receiver: Device: "/dev/input/event3"
(II) Logitech USB Receiver: Found keys
(II) Logitech USB Receiver: Configuring as keyboard
(II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/udev: Adding input device Logitech USB Receiver (/dev/input/event4)
(**) Logitech USB Receiver: Applying InputClass "evdev pointer catchall"
(**) Logitech USB Receiver: Applying InputClass "evdev keyboard catchall"
(**) Logitech USB Receiver: always reports core events
(**) Logitech USB Receiver: Device: "/dev/input/event4"
(II) Logitech USB Receiver: Found 20 mouse buttons
(II) Logitech USB Receiver: Found scroll wheel(s)
(II) Logitech USB Receiver: Found relative axes
(II) Logitech USB Receiver: Found x and y relative axes
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
(II) Logitech USB Receiver: initialized for relative axes.
(WW) Logitech USB Receiver: ignoring absolute axes.
(II) config/udev: Adding input device Logitech USB Receiver (/dev/input/mouse1)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device Macintosh mouse button emulation (/dev/input/event2)
(**) Macintosh mouse button emulation: Applying InputClass "evdev pointer catchall"
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event2"
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

### Post by realzippy on 2011-08-13
For some reason the intel driver is not loaded (vesa instead).
Which ubuntu version?
Did you blacklist anything?
Edited boot options?
(something with modeset or nomodeset ?)

Post output from:

```
gedit /etc/default/grub
```

```
gedit /etc/modprobe.d/blacklist.conf
```

---

### Post by david476 on 2011-08-13
I am using Ubuntu 11.04.

code 1:
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_LINUX_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"







code 2:

# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac

---

### Post by realzippy on 2011-08-13
edit:
something messed up the order here.

---

### Post by david476 on 2011-08-13
I'm not sure what you mean

---

### Post by david476 on 2011-08-13
realzippy: The "I'm not sure what you mean" was responding to amjjawad's, last post. I'm still trying to completely figure out the Ubuntu forums. Sorry for the lack in clarity.


I posted the results in post 12

---

### Post by realzippy on 2011-08-13
I am not sure what is going on here.
For some reason the intel kernel module seems not to work.
..have you done any attempt formerly to make your graphics work?
If so,which?
Please show output from
```
lshw -C display
```

Which machine do you use?

---

### Post by amjjawad on 2011-08-13
> **david476 said:**
> I'm not sure what you mean

[IMG]http://ubuntuforums.org/picture.php?albumid=2161&pictureid=8148[/IMG]


You can either use the icons on the message box bar OR use "Quote" and/or "Code" tags - type them.

;)

---

### Post by realzippy on 2011-08-13
Please also show output from:
```
lspci -k -nn
```

---

### Post by david476 on 2011-08-13
amjjawad: thanks for the clarification.
realzippy:

latest code:
```
00:00.0 Host bridge [0600]: Intel Corporation Device [8086:0100] (rev 09)
00:02.0 VGA compatible controller [0300]: Intel Corporation Device [8086:0112] (rev 09)
00:16.0 Communication controller [0780]: Intel Corporation Cougar Point HECI Controller #1 [8086:1c3a] (rev 04)
00:1a.0 USB Controller [0c03]: Intel Corporation Cougar Point USB Enhanced Host Controller #2 [8086:1c2d] (rev 05)
    Kernel driver in use: ehci_hcd
00:1b.0 Audio device [0403]: Intel Corporation Cougar Point High Definition Audio Controller [8086:1c20] (rev 05)
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel
00:1c.0 PCI bridge [0604]: Intel Corporation Cougar Point PCI Express Root Port 1 [8086:1c10] (rev b5)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1c.4 PCI bridge [0604]: Intel Corporation Cougar Point PCI Express Root Port 5 [8086:1c18] (rev b5)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1c.5 PCI bridge [0604]: Intel Corporation Cougar Point PCI Express Root Port 6 [8086:1c1a] (rev b5)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1c.6 PCI bridge [0604]: Intel Corporation Cougar Point PCI Express Root Port 7 [8086:1c1c] (rev b5)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1d.0 USB Controller [0c03]: Intel Corporation Cougar Point USB Enhanced Host Controller #1 [8086:1c26] (rev 05)
    Kernel driver in use: ehci_hcd
00:1f.0 ISA bridge [0601]: Intel Corporation Device [8086:1c4a] (rev 05)
    Kernel modules: iTCO_wdt
00:1f.2 IDE interface [0101]: Intel Corporation Cougar Point 4 port SATA IDE Controller [8086:1c00] (rev 05)
    Kernel driver in use: ata_piix
00:1f.3 SMBus [0c05]: Intel Corporation Cougar Point SMBus Controller [8086:1c22] (rev 05)
    Kernel modules: i2c-i801
00:1f.5 IDE interface [0101]: Intel Corporation Cougar Point 2 port SATA IDE Controller [8086:1c08] (rev 05)
    Kernel driver in use: ata_piix
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 06)
    Kernel driver in use: r8169
    Kernel modules: r8169
03:00.0 FireWire (IEEE 1394) [0c00]: VIA Technologies, Inc. Device [1106:3403] (rev 01)
    Kernel driver in use: ohci1394
    Kernel modules: firewire-ohci, ohci1394
04:00.0 USB Controller [0c03]: NEC Corporation Device [1033:0194] (rev 04)
    Kernel driver in use: xhci_hcd
    Kernel modules: xhci
```


Other code:

WARNING: you should run this program as super-user.
  *-display UNCLAIMED     
       description: VGA compatible controller
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       ```
capabilities: bus_master cap_list
       configuration: latency=0
       resources: memory:fe000000-fe3fffff memory:c0000000-cfffffff(prefetchable) ioport:f000(size=64)

```

---

### Post by realzippy on 2011-08-13
Xorg.0.log says :
8086:0112:1462:7678
=
Intel integrated graphics 2nd generation 
=
Sandy Bridge ?

...but doesn 't load i915 kernel module
...which should work for this device ##(afaik,may someone correct me please !?)


So I suggest to run:
```
gksudo gedit /etc/default/grub
```

change

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
to
GRUB_CMDLINE_LINUX_DEFAULT=&#8221;quiet splash i915.modeset=1&#8243;

```
sudo update-grub
```
Reboot.
If it does not work,post Xorg.0.log again.

Since we are in beginners talk:
If something should go wrong (not booting),press "shift" during boot,choose
1rst recovery mode,choose failsafe graphics and undo above.(may write above down/print)
If worser ;-) start the live CD and post.

---

### Post by realzippy on 2011-08-13
sorry.doubled.

---

### Post by david476 on 2011-08-13
I did it and double checked it. As far as I can tell nothing changed.
		Xorg.0.log:

		```
X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-28-server x86_64 Ubuntu
Current Operating System: Linux Colossus 2.6.32-33-generic #72-Ubuntu SMP Fri Jul 29 21:07:13 UTC 2011 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-33-generic root=UUID=a626e385-5e8a-4416-b923-ea8cb08b206d ro quiet splash i915.modeset+1
Build Date: 08 March 2011  08:22:34AM
xorg-server 2:1.7.6-2ubuntu7.6 (For technical support please see http://www.ubuntu.com/support) 
Current version of pixman: 0.16.4
    Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sat Aug 13 20:52:48 2011
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"
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
(==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
(II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
(II) Loader magic: 0x7cb840
(II) Module ABI versions:
    X.Org ANSI C Emulation: 0.4
    X.Org Video Driver: 6.0
    X.Org XInput driver : 7.0
    X.Org Server Extension : 2.0
(++) using VT number 7

(--) PCI:*(0:0:2:0) 8086:0112:1462:7678 Intel Corporation rev 9, Mem @ 0xfe000000/4194304, 0xc0000000/268435456, I/O @ 0x0000f000/64
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
(II) Loading /usr/lib/xorg/modules/extensions/libglx.so
(II) Module glx: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    ABI class: X.Org Server Extension, version 2.0
(==) AIGLX enabled
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
(==) Matched intel as autoconfigured driver 0
(==) Matched vesa as autoconfigured driver 1
(==) Matched fbdev as autoconfigured driver 2
(==) Assigned the driver to the xf86ConfigLayout
(II) LoadModule: "intel"
(II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
(II) Module intel: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 2.9.1
    Module class: X.Org Video Driver
    ABI class: X.Org Video Driver, version 6.0
(II) LoadModule: "vesa"
(II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
(II) Module vesa: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 2.3.0
    Module class: X.Org Video Driver
    ABI class: X.Org Video Driver, version 6.0
(II) LoadModule: "fbdev"
(II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
(II) Module fbdev: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 0.4.1
    ABI class: X.Org Video Driver, version 6.0
(II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
    i810-dc100, i810e, i815, i830M, 845G, 852GM/855GM, 865G, 915G,
    E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
    965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
    4 Series, G45/G43, Q45/Q43, G41, B43, Clarkdale, Arrandale
(II) VESA: driver for VESA chipsets: vesa
(II) FBDEV: driver for framebuffer: fbdev
(II) Primary Device is: PCI 00@00:02:0
(WW) Falling back to old probe method for fbdev
(II) Loading sub module "fbdevhw"
(II) LoadModule: "fbdevhw"
(II) Loading /usr/lib/xorg/modules/linux/libfbdevhw.so
(II) Module fbdevhw: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 0.0.2
    ABI class: X.Org Video Driver, version 6.0
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules/libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.1.0
    ABI class: X.Org Video Driver, version 6.0
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules/libint10.so
(II) Module int10: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    ABI class: X.Org Video Driver, version 6.0
(II) VESA(0): initializing int10
(II) VESA(0): Primary V_BIOS segment is: 0xc000
(II) VESA(0): VESA BIOS detected
(II) VESA(0): VESA VBE Version 3.0
(II) VESA(0): VESA VBE Total Mem: 65472 kB
(II) VESA(0): VESA VBE OEM: Intel(R)Sandybridge Desktop Graphics Chipset Accelerated VGA BIOS
(II) VESA(0): VESA VBE OEM Software Rev: 1.0
(II) VESA(0): VESA VBE OEM Vendor: Intel Corporation
(II) VESA(0): VESA VBE OEM Product: Intel(R)Sandybridge Desktop Graphics Controller
(II) VESA(0): VESA VBE OEM Product Rev: Hardware Version 0.0
(II) VESA(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
(==) VESA(0): Depth 24, (--) framebuffer bpp 32
(==) VESA(0): RGB weight 888
(==) VESA(0): Default visual is TrueColor
(==) VESA(0): Using gamma correction (1.0, 1.0, 1.0)
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(II) VESA(0): VESA VBE DDC supported
(II) VESA(0): VESA VBE DDC Level 2
(II) VESA(0): VESA VBE DDC transfer in appr. 1 sec.
(II) VESA(0): VESA VBE DDC read successfully
(II) VESA(0): Manufacturer: SAM  Model: 78b  Serial#: 1514292021
(II) VESA(0): Year: 2011  Week: 17
(II) VESA(0): EDID Version: 1.3
(II) VESA(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) VESA(0): Sync:  Separate  Composite  SyncOnGreen
(II) VESA(0): Max Image Size [cm]: horiz.: 44  vert.: 25
(II) VESA(0): Gamma: 2.20
(II) VESA(0): DPMS capabilities: Off; RGB/Color Display
(II) VESA(0): First detailed timing is preferred mode
(II) VESA(0): redX: 0.639 redY: 0.340   greenX: 0.324 greenY: 0.622
(II) VESA(0): blueX: 0.155 blueY: 0.042   whiteX: 0.312 whiteY: 0.329
(II) VESA(0): Supported established timings:
(II) VESA(0): 720x400@70Hz
(II) VESA(0): 640x480@60Hz
(II) VESA(0): 640x480@67Hz
(II) VESA(0): 640x480@72Hz
(II) VESA(0): 640x480@75Hz
(II) VESA(0): 800x600@56Hz
(II) VESA(0): 800x600@60Hz
(II) VESA(0): 800x600@72Hz
(II) VESA(0): 800x600@75Hz
(II) VESA(0): 832x624@75Hz
(II) VESA(0): 1024x768@60Hz
(II) VESA(0): 1024x768@70Hz
(II) VESA(0): 1024x768@75Hz
(II) VESA(0): 1152x864@75Hz
(II) VESA(0): Manufacturer's mask: 0
(II) VESA(0): Supported standard timings:
(II) VESA(0): #0: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) VESA(0): #1: hsize: 1280  vsize 800  refresh: 60  vid: 129
(II) VESA(0): #2: hsize: 1280  vsize 800  refresh: 75  vid: 3969
(II) VESA(0): #3: hsize: 1440  vsize 900  refresh: 60  vid: 149
(II) VESA(0): #4: hsize: 1440  vsize 900  refresh: 75  vid: 3989
(II) VESA(0): Supported detailed timing:
(II) VESA(0): clock: 108.0 MHz   Image Size:  443 x 249 mm
(II) VESA(0): h_active: 1600  h_sync: 1624  h_sync_end 1704 h_blank_end 1800 h_border: 0
(II) VESA(0): v_active: 900  v_sync: 901  v_sync_end 904 v_blanking: 1000 v_border: 0
(II) VESA(0): Ranges: V min: 56 V max: 75 Hz, H min: 30 H max: 81 kHz, PixClock max 150 MHz
(II) VESA(0): Monitor name: SA300/SA350
(II) VESA(0): Serial No: H9NB401854
(II) VESA(0): EDID (in hex):
(II) VESA(0):     00ffffffffffff004c2d8b073543425a
(II) VESA(0):     111501030e2c19782a81f1a357539f27
(II) VESA(0):     0a5054bfee80714f8100810f9500950f
(II) VESA(0):     010101010101302a40c8608464301850
(II) VESA(0):     1300bbf91000001e000000fd00384b1e
(II) VESA(0):     510f000a202020202020000000fc0053
(II) VESA(0):     413330302f53413335300a20000000ff
(II) VESA(0):     0048394e423430313835340a20200021
(II) VESA(0): EDID vendor "SAM", prod id 1931
(II) VESA(0): Using EDID range info for horizontal sync
(II) VESA(0): Using EDID range info for vertical refresh
(II) VESA(0): Printing DDC gathered Modelines:
(II) VESA(0): Modeline "1600x900"x0.0  108.00  1600 1624 1704 1800  900 901 904 1000 +hsync +vsync (60.0 kHz)
(II) VESA(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) VESA(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) VESA(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) VESA(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) VESA(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) VESA(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) VESA(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) VESA(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) VESA(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) VESA(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) VESA(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) VESA(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) VESA(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) VESA(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) VESA(0): Modeline "1280x800"x0.0   83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync (49.7 kHz)
(II) VESA(0): Modeline "1280x800"x0.0  106.50  1280 1360 1488 1696  800 803 809 838 -hsync +vsync (62.8 kHz)
(II) VESA(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
(II) VESA(0): Modeline "1440x900"x0.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz)
(II) VESA(0): Searching for matching VESA mode(s):
Mode: 160 (0x0)
    ModeAttributes: 0x0
    WinAAttributes: 0x0
    WinBAttributes: 0x0
    WinGranularity: 0
    WinSize: 0
    WinASegment: 0x0
    WinBSegment: 0x0
    WinFuncPtr: 0x0
    BytesPerScanline: 0
    XResolution: 0
    YResolution: 0
    XCharSize: 0
    YCharSize: 0
    NumberOfPlanes: 0
    BitsPerPixel: 0
    NumberOfBanks: 0
    MemoryModel: 0
    BankSize: 0
    NumberOfImages: 0
    RedMaskSize: 0
    RedFieldPosition: 0
    GreenMaskSize: 0
    GreenFieldPosition: 0
    BlueMaskSize: 0
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0x0
    LinBytesPerScanLine: 0
    BnkNumberOfImagePages: 0
    LinNumberOfImagePages: 0
    LinRedMaskSize: 0
    LinRedFieldPosition: 0
    LinGreenMaskSize: 0
    LinGreenFieldPosition: 0
    LinBlueMaskSize: 0
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 0
Mode: 161 (0x0)
    ModeAttributes: 0x0
    WinAAttributes: 0x0
    WinBAttributes: 0x0
    WinGranularity: 0
    WinSize: 0
    WinASegment: 0x0
    WinBSegment: 0x0
    WinFuncPtr: 0x0
    BytesPerScanline: 0
    XResolution: 0
    YResolution: 0
    XCharSize: 0
    YCharSize: 0
    NumberOfPlanes: 0
    BitsPerPixel: 0
    NumberOfBanks: 0
    MemoryModel: 0
    BankSize: 0
    NumberOfImages: 0
    RedMaskSize: 0
    RedFieldPosition: 0
    GreenMaskSize: 0
    GreenFieldPosition: 0
    BlueMaskSize: 0
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0x0
    LinBytesPerScanLine: 0
    BnkNumberOfImagePages: 0
    LinNumberOfImagePages: 0
    LinRedMaskSize: 0
    LinRedFieldPosition: 0
    LinGreenMaskSize: 0
    LinGreenFieldPosition: 0
    LinBlueMaskSize: 0
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 0
Mode: 162 (0x0)
    ModeAttributes: 0x0
    WinAAttributes: 0x0
    WinBAttributes: 0x0
    WinGranularity: 0
    WinSize: 0
    WinASegment: 0x0
    WinBSegment: 0x0
    WinFuncPtr: 0x0
    BytesPerScanline: 0
    XResolution: 0
    YResolution: 0
    XCharSize: 0
    YCharSize: 0
    NumberOfPlanes: 0
    BitsPerPixel: 0
    NumberOfBanks: 0
    MemoryModel: 0
    BankSize: 0
    NumberOfImages: 0
    RedMaskSize: 0
    RedFieldPosition: 0
    GreenMaskSize: 0
    GreenFieldPosition: 0
    BlueMaskSize: 0
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0x0
    LinBytesPerScanLine: 0
    BnkNumberOfImagePages: 0
    LinNumberOfImagePages: 0
    LinRedMaskSize: 0
    LinRedFieldPosition: 0
    LinGreenMaskSize: 0
    LinGreenFieldPosition: 0
    LinBlueMaskSize: 0
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 0
Mode: 163 (0x0)
    ModeAttributes: 0x0
    WinAAttributes: 0x0
    WinBAttributes: 0x0
    WinGranularity: 0
    WinSize: 0
    WinASegment: 0x0
    WinBSegment: 0x0
    WinFuncPtr: 0x0
    BytesPerScanline: 0
    XResolution: 0
    YResolution: 0
    XCharSize: 0
    YCharSize: 0
    NumberOfPlanes: 0
    BitsPerPixel: 0
    NumberOfBanks: 0
    MemoryModel: 0
    BankSize: 0
    NumberOfImages: 0
    RedMaskSize: 0
    RedFieldPosition: 0
    GreenMaskSize: 0
    GreenFieldPosition: 0
    BlueMaskSize: 0
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0x0
    LinBytesPerScanLine: 0
    BnkNumberOfImagePages: 0
    LinNumberOfImagePages: 0
    LinRedMaskSize: 0
    LinRedFieldPosition: 0
    LinGreenMaskSize: 0
    LinGreenFieldPosition: 0
    LinBlueMaskSize: 0
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 0
Mode: 164 (0x0)
    ModeAttributes: 0x0
    WinAAttributes: 0x0
    WinBAttributes: 0x0
    WinGranularity: 0
    WinSize: 0
    WinASegment: 0x0
    WinBSegment: 0x0
    WinFuncPtr: 0x0
    BytesPerScanline: 0
    XResolution: 0
    YResolution: 0
    XCharSize: 0
    YCharSize: 0
    NumberOfPlanes: 0
    BitsPerPixel: 0
    NumberOfBanks: 0
    MemoryModel: 0
    BankSize: 0
    NumberOfImages: 0
    RedMaskSize: 0
    RedFieldPosition: 0
    GreenMaskSize: 0
    GreenFieldPosition: 0
    BlueMaskSize: 0
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0x0
    LinBytesPerScanLine: 0
    BnkNumberOfImagePages: 0
    LinNumberOfImagePages: 0
    LinRedMaskSize: 0
    LinRedFieldPosition: 0
    LinGreenMaskSize: 0
    LinGreenFieldPosition: 0
    LinBlueMaskSize: 0
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 0
Mode: 165 (0x0)
    ModeAttributes: 0x0
    WinAAttributes: 0x0
    WinBAttributes: 0x0
    WinGranularity: 0
    WinSize: 0
    WinASegment: 0x0
    WinBSegment: 0x0
    WinFuncPtr: 0x0
    BytesPerScanline: 0
    XResolution: 0
    YResolution: 0
    XCharSize: 0
    YCharSize: 0
    NumberOfPlanes: 0
    BitsPerPixel: 0
    NumberOfBanks: 0
    MemoryModel: 0
    BankSize: 0
    NumberOfImages: 0
    RedMaskSize: 0
    RedFieldPosition: 0
    GreenMaskSize: 0
    GreenFieldPosition: 0
    BlueMaskSize: 0
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0x0
    LinBytesPerScanLine: 0
    BnkNumberOfImagePages: 0
    LinNumberOfImagePages: 0
    LinRedMaskSize: 0
    LinRedFieldPosition: 0
    LinGreenMaskSize: 0
    LinGreenFieldPosition: 0
    LinBlueMaskSize: 0
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 0
Mode: 166 (0x0)
    ModeAttributes: 0x0
    WinAAttributes: 0x0
    WinBAttributes: 0x0
    WinGranularity: 0
    WinSize: 0
    WinASegment: 0x0
    WinBSegment: 0x0
    WinFuncPtr: 0x0
    BytesPerScanline: 0
    XResolution: 0
    YResolution: 0
    XCharSize: 0
    YCharSize: 0
    NumberOfPlanes: 0
    BitsPerPixel: 0
    NumberOfBanks: 0
    MemoryModel: 0
    BankSize: 0
    NumberOfImages: 0
    RedMaskSize: 0
    RedFieldPosition: 0
    GreenMaskSize: 0
    GreenFieldPosition: 0
    BlueMaskSize: 0
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0x0
    LinBytesPerScanLine: 0
    BnkNumberOfImagePages: 0
    LinNumberOfImagePages: 0
    LinRedMaskSize: 0
    LinRedFieldPosition: 0
    LinGreenMaskSize: 0
    LinGreenFieldPosition: 0
    LinBlueMaskSize: 0
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 0
Mode: 167 (0x0)
    ModeAttributes: 0x0
    WinAAttributes: 0x0
    WinBAttributes: 0x0
    WinGranularity: 0
    WinSize: 0
    WinASegment: 0x0
    WinBSegment: 0x0
    WinFuncPtr: 0x0
    BytesPerScanline: 0
    XResolution: 0
    YResolution: 0
    XCharSize: 0
    YCharSize: 0
    NumberOfPlanes: 0
    BitsPerPixel: 0
    NumberOfBanks: 0
    MemoryModel: 0
    BankSize: 0
    NumberOfImages: 0
    RedMaskSize: 0
    RedFieldPosition: 0
    GreenMaskSize: 0
    GreenFieldPosition: 0
    BlueMaskSize: 0
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0x0
    LinBytesPerScanLine: 0
    BnkNumberOfImagePages: 0
    LinNumberOfImagePages: 0
    LinRedMaskSize: 0
    LinRedFieldPosition: 0
    LinGreenMaskSize: 0
    LinGreenFieldPosition: 0
    LinBlueMaskSize: 0
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 0
Mode: 168 (0x0)
    ModeAttributes: 0x0
    WinAAttributes: 0x0
    WinBAttributes: 0x0
    WinGranularity: 0
    WinSize: 0
    WinASegment: 0x0
    WinBSegment: 0x0
    WinFuncPtr: 0x0
    BytesPerScanline: 0
    XResolution: 0
    YResolution: 0
    XCharSize: 0
    YCharSize: 0
    NumberOfPlanes: 0
    BitsPerPixel: 0
    NumberOfBanks: 0
    MemoryModel: 0
    BankSize: 0
    NumberOfImages: 0
    RedMaskSize: 0
    RedFieldPosition: 0
    GreenMaskSize: 0
    GreenFieldPosition: 0
    BlueMaskSize: 0
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0x0
    LinBytesPerScanLine: 0
    BnkNumberOfImagePages: 0
    LinNumberOfImagePages: 0
    LinRedMaskSize: 0
    LinRedFieldPosition: 0
    LinGreenMaskSize: 0
    LinGreenFieldPosition: 0
    LinBlueMaskSize: 0
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 0
Mode: 13c (1920x1440)
    ModeAttributes: 0x9b
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc00079bc
    BytesPerScanline: 1920
    XResolution: 1920
    YResolution: 1440
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 8
    NumberOfBanks: 1
    MemoryModel: 4
    BankSize: 0
    NumberOfImages: 22
    RedMaskSize: 0
    RedFieldPosition: 0
    GreenMaskSize: 0
    GreenFieldPosition: 0
    BlueMaskSize: 0
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0xc0000000
    LinBytesPerScanLine: 1920
    BnkNumberOfImagePages: 22
    LinNumberOfImagePages: 22
    LinRedMaskSize: 0
    LinRedFieldPosition: 0
    LinGreenMaskSize: 0
    LinGreenFieldPosition: 0
    LinBlueMaskSize: 0
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 230000000
Mode: 14d (1920x1440)
    ModeAttributes: 0x9b
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc00079bc
    BytesPerScanline: 3840
    XResolution: 1920
    YResolution: 1440
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 16
    NumberOfBanks: 1
    MemoryModel: 6
    BankSize: 0
    NumberOfImages: 11
    RedMaskSize: 5
    RedFieldPosition: 11
    GreenMaskSize: 6
    GreenFieldPosition: 5
    BlueMaskSize: 5
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0xc0000000
    LinBytesPerScanLine: 3840
    BnkNumberOfImagePages: 11
    LinNumberOfImagePages: 11
    LinRedMaskSize: 5
    LinRedFieldPosition: 11
    LinGreenMaskSize: 6
    LinGreenFieldPosition: 5
    LinBlueMaskSize: 5
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 230000000
*Mode: 15c (1920x1440)
    ModeAttributes: 0x9b
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc00079bc
    BytesPerScanline: 7680
    XResolution: 1920
    YResolution: 1440
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 32
    NumberOfBanks: 1
    MemoryModel: 6
    BankSize: 0
    NumberOfImages: 5
    RedMaskSize: 8
    RedFieldPosition: 16
    GreenMaskSize: 8
    GreenFieldPosition: 8
    BlueMaskSize: 8
    BlueFieldPosition: 0
    RsvdMaskSize: 8
    RsvdFieldPosition: 24
    DirectColorModeInfo: 0
    PhysBasePtr: 0xc0000000
    LinBytesPerScanLine: 7680
    BnkNumberOfImagePages: 5
    LinNumberOfImagePages: 5
    LinRedMaskSize: 8
    LinRedFieldPosition: 16
    LinGreenMaskSize: 8
    LinGreenFieldPosition: 8
    LinBlueMaskSize: 8
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 8
    LinRsvdFieldPosition: 24
    MaxPixelClock: 230000000
Mode: 13a (1600x1200)
    ModeAttributes: 0x9b
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc00079bc
    BytesPerScanline: 1600
    XResolution: 1600
    YResolution: 1200
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 8
    NumberOfBanks: 1
    MemoryModel: 4
    BankSize: 0
    NumberOfImages: 33
    RedMaskSize: 0
    RedFieldPosition: 0
    GreenMaskSize: 0
    GreenFieldPosition: 0
    BlueMaskSize: 0
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0xc0000000
    LinBytesPerScanLine: 1600
    BnkNumberOfImagePages: 33
    LinNumberOfImagePages: 33
    LinRedMaskSize: 0
    LinRedFieldPosition: 0
    LinGreenMaskSize: 0
    LinGreenFieldPosition: 0
    LinBlueMaskSize: 0
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 230000000
Mode: 14b (1600x1200)
    ModeAttributes: 0x9b
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc00079bc
    BytesPerScanline: 3200
    XResolution: 1600
    YResolution: 1200
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 16
    NumberOfBanks: 1
    MemoryModel: 6
    BankSize: 0
    NumberOfImages: 16
    RedMaskSize: 5
    RedFieldPosition: 11
    GreenMaskSize: 6
    GreenFieldPosition: 5
    BlueMaskSize: 5
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0xc0000000
    LinBytesPerScanLine: 3200
    BnkNumberOfImagePages: 16
    LinNumberOfImagePages: 16
    LinRedMaskSize: 5
    LinRedFieldPosition: 11
    LinGreenMaskSize: 6
    LinGreenFieldPosition: 5
    LinBlueMaskSize: 5
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 230000000
*Mode: 15a (1600x1200)
    ModeAttributes: 0x9b
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc00079bc
    BytesPerScanline: 6400
    XResolution: 1600
    YResolution: 1200
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 32
    NumberOfBanks: 1
    MemoryModel: 6
    BankSize: 0
    NumberOfImages: 7
    RedMaskSize: 8
    RedFieldPosition: 16
    GreenMaskSize: 8
    GreenFieldPosition: 8
    BlueMaskSize: 8
    BlueFieldPosition: 0
    RsvdMaskSize: 8
    RsvdFieldPosition: 24
    DirectColorModeInfo: 0
    PhysBasePtr: 0xc0000000
    LinBytesPerScanLine: 6400
    BnkNumberOfImagePages: 7
    LinNumberOfImagePages: 7
    LinRedMaskSize: 8
    LinRedFieldPosition: 16
    LinGreenMaskSize: 8
    LinGreenFieldPosition: 8
    LinBlueMaskSize: 8
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 8
    LinRsvdFieldPosition: 24
    MaxPixelClock: 230000000
Mode: 107 (1280x1024)
    ModeAttributes: 0x9b
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc00079bc
    BytesPerScanline: 1280
    XResolution: 1280
    YResolution: 1024
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 8
    NumberOfBanks: 1
    MemoryModel: 4
    BankSize: 0
    NumberOfImages: 50
    RedMaskSize: 0
    RedFieldPosition: 0
    GreenMaskSize: 0
    GreenFieldPosition: 0
    BlueMaskSize: 0
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0xc0000000
    LinBytesPerScanLine: 1280
    BnkNumberOfImagePages: 50
    LinNumberOfImagePages: 50
    LinRedMaskSize: 0
    LinRedFieldPosition: 0
    LinGreenMaskSize: 0
    LinGreenFieldPosition: 0
    LinBlueMaskSize: 0
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 230000000
Mode: 11a (1280x1024)
    ModeAttributes: 0x9b
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc00079bc
    BytesPerScanline: 2560
    XResolution: 1280
    YResolution: 1024
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 16
    NumberOfBanks: 1
    MemoryModel: 6
    BankSize: 0
    NumberOfImages: 24
    RedMaskSize: 5
    RedFieldPosition: 11
    GreenMaskSize: 6
    GreenFieldPosition: 5
    BlueMaskSize: 5
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0xc0000000
    LinBytesPerScanLine: 2560
    BnkNumberOfImagePages: 24
    LinNumberOfImagePages: 24
    LinRedMaskSize: 5
    LinRedFieldPosition: 11
    LinGreenMaskSize: 6
    LinGreenFieldPosition: 5
    LinBlueMaskSize: 5
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 230000000
*Mode: 11b (1280x1024)
    ModeAttributes: 0x9b
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc00079bc
    BytesPerScanline: 5120
    XResolution: 1280
    YResolution: 1024
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 32
    NumberOfBanks: 1
    MemoryModel: 6
    BankSize: 0
    NumberOfImages: 11
    RedMaskSize: 8
    RedFieldPosition: 16
    GreenMaskSize: 8
    GreenFieldPosition: 8
    BlueMaskSize: 8
    BlueFieldPosition: 0
    RsvdMaskSize: 8
    RsvdFieldPosition: 24
    DirectColorModeInfo: 0
    PhysBasePtr: 0xc0000000
    LinBytesPerScanLine: 5120
    BnkNumberOfImagePages: 11
    LinNumberOfImagePages: 11
    LinRedMaskSize: 8
    LinRedFieldPosition: 16
    LinGreenMaskSize: 8
    LinGreenFieldPosition: 8
    LinBlueMaskSize: 8
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 8
    LinRsvdFieldPosition: 24
    MaxPixelClock: 230000000
Mode: 105 (1024x768)
    ModeAttributes: 0x9b
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc00079bc
    BytesPerScanline: 1024
    XResolution: 1024
    YResolution: 768
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 8
    NumberOfBanks: 1
    MemoryModel: 4
    BankSize: 0
    NumberOfImages: 84
    RedMaskSize: 0
    RedFieldPosition: 0
    GreenMaskSize: 0
    GreenFieldPosition: 0
    BlueMaskSize: 0
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0xc0000000
    LinBytesPerScanLine: 1024
    BnkNumberOfImagePages: 84
    LinNumberOfImagePages: 84
    LinRedMaskSize: 0
    LinRedFieldPosition: 0
    LinGreenMaskSize: 0
    LinGreenFieldPosition: 0
    LinBlueMaskSize: 0
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 230000000
Mode: 117 (1024x768)
    ModeAttributes: 0x9b
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc00079bc
    BytesPerScanline: 2048
    XResolution: 1024
    YResolution: 768
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 16
    NumberOfBanks: 1
    MemoryModel: 6
    BankSize: 0
    NumberOfImages: 41
    RedMaskSize: 5
    RedFieldPosition: 11
    GreenMaskSize: 6
    GreenFieldPosition: 5
    BlueMaskSize: 5
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0xc0000000
    LinBytesPerScanLine: 2048
    BnkNumberOfImagePages: 41
    LinNumberOfImagePages: 41
    LinRedMaskSize: 5
    LinRedFieldPosition: 11
    LinGreenMaskSize: 6
    LinGreenFieldPosition: 5
    LinBlueMaskSize: 5
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 230000000
*Mode: 118 (1024x768)
    ModeAttributes: 0x9b
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc00079bc
    BytesPerScanline: 4096
    XResolution: 1024
    YResolution: 768
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 32
    NumberOfBanks: 1
    MemoryModel: 6
    BankSize: 0
    NumberOfImages: 20
    RedMaskSize: 8
    RedFieldPosition: 16
    GreenMaskSize: 8
    GreenFieldPosition: 8
    BlueMaskSize: 8
    BlueFieldPosition: 0
    RsvdMaskSize: 8
    RsvdFieldPosition: 24
    DirectColorModeInfo: 0
    PhysBasePtr: 0xc0000000
    LinBytesPerScanLine: 4096
    BnkNumberOfImagePages: 20
    LinNumberOfImagePages: 20
    LinRedMaskSize: 8
    LinRedFieldPosition: 16
    LinGreenMaskSize: 8
    LinGreenFieldPosition: 8
    LinBlueMaskSize: 8
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 8
    LinRsvdFieldPosition: 24
    MaxPixelClock: 230000000
*Mode: 112 (640x480)
    ModeAttributes: 0x9b
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc00079bc
    BytesPerScanline: 2560
    XResolution: 640
    YResolution: 480
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 32
    NumberOfBanks: 1
    MemoryModel: 6
    BankSize: 0
    NumberOfImages: 52
    RedMaskSize: 8
    RedFieldPosition: 16
    GreenMaskSize: 8
    GreenFieldPosition: 8
    BlueMaskSize: 8
    BlueFieldPosition: 0
    RsvdMaskSize: 8
    RsvdFieldPosition: 24
    DirectColorModeInfo: 0
    PhysBasePtr: 0xc0000000
    LinBytesPerScanLine: 2560
    BnkNumberOfImagePages: 52
    LinNumberOfImagePages: 52
    LinRedMaskSize: 8
    LinRedFieldPosition: 16
    LinGreenMaskSize: 8
    LinGreenFieldPosition: 8
    LinBlueMaskSize: 8
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 8
    LinRsvdFieldPosition: 24
    MaxPixelClock: 230000000
Mode: 114 (800x600)
    ModeAttributes: 0x9b
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc00079bc
    BytesPerScanline: 1600
    XResolution: 800
    YResolution: 600
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 16
    NumberOfBanks: 1
    MemoryModel: 6
    BankSize: 0
    NumberOfImages: 67
    RedMaskSize: 5
    RedFieldPosition: 11
    GreenMaskSize: 6
    GreenFieldPosition: 5
    BlueMaskSize: 5
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0xc0000000
    LinBytesPerScanLine: 1600
    BnkNumberOfImagePages: 67
    LinNumberOfImagePages: 67
    LinRedMaskSize: 5
    LinRedFieldPosition: 11
    LinGreenMaskSize: 6
    LinGreenFieldPosition: 5
    LinBlueMaskSize: 5
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 230000000
*Mode: 115 (800x600)
    ModeAttributes: 0x9b
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc00079bc
    BytesPerScanline: 3200
    XResolution: 800
    YResolution: 600
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 32
    NumberOfBanks: 1
    MemoryModel: 6
    BankSize: 0
    NumberOfImages: 33
    RedMaskSize: 8
    RedFieldPosition: 16
    GreenMaskSize: 8
    GreenFieldPosition: 8
    BlueMaskSize: 8
    BlueFieldPosition: 0
    RsvdMaskSize: 8
    RsvdFieldPosition: 24
    DirectColorModeInfo: 0
    PhysBasePtr: 0xc0000000
    LinBytesPerScanLine: 3200
    BnkNumberOfImagePages: 33
    LinNumberOfImagePages: 33
    LinRedMaskSize: 8
    LinRedFieldPosition: 16
    LinGreenMaskSize: 8
    LinGreenFieldPosition: 8
    LinBlueMaskSize: 8
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 8
    LinRsvdFieldPosition: 24
    MaxPixelClock: 230000000
Mode: 101 (640x480)
    ModeAttributes: 0x9b
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc00079bc
    BytesPerScanline: 640
    XResolution: 640
    YResolution: 480
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 8
    NumberOfBanks: 1
    MemoryModel: 4
    BankSize: 0
    NumberOfImages: 203
    RedMaskSize: 0
    RedFieldPosition: 0
    GreenMaskSize: 0
    GreenFieldPosition: 0
    BlueMaskSize: 0
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0xc0000000
    LinBytesPerScanLine: 640
    BnkNumberOfImagePages: 203
    LinNumberOfImagePages: 203
    LinRedMaskSize: 0
    LinRedFieldPosition: 0
    LinGreenMaskSize: 0
    LinGreenFieldPosition: 0
    LinBlueMaskSize: 0
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 230000000
Mode: 103 (800x600)
    ModeAttributes: 0x9b
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc00079bc
    BytesPerScanline: 832
    XResolution: 800
    YResolution: 600
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 8
    NumberOfBanks: 1
    MemoryModel: 4
    BankSize: 0
    NumberOfImages: 126
    RedMaskSize: 0
    RedFieldPosition: 0
    GreenMaskSize: 0
    GreenFieldPosition: 0
    BlueMaskSize: 0
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0xc0000000
    LinBytesPerScanLine: 832
    BnkNumberOfImagePages: 126
    LinNumberOfImagePages: 126
    LinRedMaskSize: 0
    LinRedFieldPosition: 0
    LinGreenMaskSize: 0
    LinGreenFieldPosition: 0
    LinBlueMaskSize: 0
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 230000000
Mode: 111 (640x480)
    ModeAttributes: 0x9b
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc00079bc
    BytesPerScanline: 1280
    XResolution: 640
    YResolution: 480
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 16
    NumberOfBanks: 1
    MemoryModel: 6
    BankSize: 0
    NumberOfImages: 101
    RedMaskSize: 5
    RedFieldPosition: 11
    GreenMaskSize: 6
    GreenFieldPosition: 5
    BlueMaskSize: 5
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0xc0000000
    LinBytesPerScanLine: 1280
    BnkNumberOfImagePages: 101
    LinNumberOfImagePages: 101
    LinRedMaskSize: 5
    LinRedFieldPosition: 11
    LinGreenMaskSize: 6
    LinGreenFieldPosition: 5
    LinBlueMaskSize: 5
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 230000000

(II) VESA(0): Total Memory: 1023 64KB banks (65472kB)
(II) VESA(0): <default monitor>: Using hsync range of 30.00-81.00 kHz
(II) VESA(0): <default monitor>: Using vrefresh range of 56.00-75.00 Hz
(II) VESA(0): <default monitor>: Using maximum pixel clock of 150.00 MHz
(WW) VESA(0): Unable to estimate virtual size
(II) VESA(0): Not using built-in mode "1920x1440" (no mode of this name)
(II) VESA(0): Not using built-in mode "1600x1200" (no mode of this name)
(II) VESA(0): Not using built-in mode "1280x1024" (no mode of this name)
(--) VESA(0): Virtual size is 1024x768 (pitch 1024)
(**) VESA(0): *Built-in mode "1024x768"
(**) VESA(0): *Built-in mode "800x600"
(**) VESA(0): *Built-in mode "640x480"
(**) VESA(0): Display dimensions: (440, 250) mm
(**) VESA(0): DPI set to (59, 78)
(**) VESA(0): Using "Shadow Framebuffer"
(II) Loading sub module "shadow"
(II) LoadModule: "shadow"
(II) Loading /usr/lib/xorg/modules/libshadow.so
(II) Module shadow: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.1.0
    ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.4
(II) UnloadModule: "intel"
(II) Unloading /usr/lib/xorg/modules/drivers/intel_drv.so
(II) UnloadModule: "fbdev"
(II) Unloading /usr/lib/xorg/modules/drivers/fbdev_drv.so
(II) UnloadModule: "fbdevhw"
(II) Unloading /usr/lib/xorg/modules/linux/libfbdevhw.so
(==) Depth 24 pixmap format is 32 bpp
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules/libint10.so
(II) VESA(0): initializing int10
(II) VESA(0): Primary V_BIOS segment is: 0xc000
(II) VESA(0): VESA BIOS detected
(II) VESA(0): VESA VBE Version 3.0
(II) VESA(0): VESA VBE Total Mem: 65472 kB
(II) VESA(0): VESA VBE OEM: Intel(R)Sandybridge Desktop Graphics Chipset Accelerated VGA BIOS
(II) VESA(0): VESA VBE OEM Software Rev: 1.0
(II) VESA(0): VESA VBE OEM Vendor: Intel Corporation
(II) VESA(0): VESA VBE OEM Product: Intel(R)Sandybridge Desktop Graphics Controller
(II) VESA(0): VESA VBE OEM Product Rev: Hardware Version 0.0
(II) VESA(0): virtual address = 0x7f07bd041000,
    physical address = 0xc0000000, size = 67043328
(II) VESA(0): Setting up VESA Mode 0x118 (1024x768)
(==) VESA(0): Default visual is TrueColor
(==) VESA(0): Backing store disabled
(==) VESA(0): DPMS enabled
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
(II) config/udev: Adding input device Power Button (/dev/input/event1)
(**) Power Button: Applying InputClass "evdev keyboard catchall"
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 2.3.2
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 7.0
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event1"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/udev: Adding input device Power Button (/dev/input/event0)
(**) Power Button: Applying InputClass "evdev keyboard catchall"
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event0"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/udev: Adding input device Logitech USB Receiver (/dev/input/event3)
(**) Logitech USB Receiver: Applying InputClass "evdev keyboard catchall"
(**) Logitech USB Receiver: always reports core events
(**) Logitech USB Receiver: Device: "/dev/input/event3"
(II) Logitech USB Receiver: Found keys
(II) Logitech USB Receiver: Configuring as keyboard
(II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/udev: Adding input device Logitech USB Receiver (/dev/input/event4)
(**) Logitech USB Receiver: Applying InputClass "evdev pointer catchall"
(**) Logitech USB Receiver: Applying InputClass "evdev keyboard catchall"
(**) Logitech USB Receiver: always reports core events
(**) Logitech USB Receiver: Device: "/dev/input/event4"
(II) Logitech USB Receiver: Found 20 mouse buttons
(II) Logitech USB Receiver: Found scroll wheel(s)
(II) Logitech USB Receiver: Found relative axes
(II) Logitech USB Receiver: Found x and y relative axes
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
(II) Logitech USB Receiver: initialized for relative axes.
(WW) Logitech USB Receiver: ignoring absolute axes.
(II) config/udev: Adding input device Logitech USB Receiver (/dev/input/mouse1)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device Macintosh mouse button emulation (/dev/input/event2)
(**) Macintosh mouse button emulation: Applying InputClass "evdev pointer catchall"
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event2"
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

### Post by realzippy on 2011-08-14
```
 Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-33-generic root=UUID=a626e385-5e8a-4416-b923-ea8cb08b206d ro quiet splash i915.modeset+1
```

1.
It seems you made a typo:
i915.modeset[COLOR="Red"]+[/COLOR]1
instead of
i915.modeset=1

Please correct this.

2.
You boot a pretty old kernel (2.6.32-33),maybe updating system helps:

```
sudo apt-get update
```

```
sudo apt-get upgrade
```

Please also run:
```
rm ~/.config/monitors.xml
```

Reboot.
Then post log file again..


Btw,
which machine do you use?

---

### Post by david476 on 2011-08-14
same thing. As far as I can tell there are no changes.
I built my own machine.

LOG:

```

X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-28-server x86_64 Ubuntu
Current Operating System: Linux Colossus 2.6.32-33-generic #72-Ubuntu SMP Fri Jul 29 21:07:13 UTC 2011 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-33-generic root=UUID=a626e385-5e8a-4416-b923-ea8cb08b206d ro quiet splash i915.modeset=1
Build Date: 08 March 2011  08:22:34AM
xorg-server 2:1.7.6-2ubuntu7.6 (For technical support please see http://www.ubuntu.com/support) 
Current version of pixman: 0.16.4
    Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sun Aug 14 10:47:50 2011
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"
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
(==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
(II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
(II) Loader magic: 0x7cb840
(II) Module ABI versions:
    X.Org ANSI C Emulation: 0.4
    X.Org Video Driver: 6.0
    X.Org XInput driver : 7.0
    X.Org Server Extension : 2.0
(++) using VT number 7

(--) PCI:*(0:0:2:0) 8086:0112:1462:7678 Intel Corporation rev 9, Mem @ 0xfe000000/4194304, 0xc0000000/268435456, I/O @ 0x0000f000/64
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
(II) Loading /usr/lib/xorg/modules/extensions/libglx.so
(II) Module glx: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    ABI class: X.Org Server Extension, version 2.0
(==) AIGLX enabled
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
(==) Matched intel as autoconfigured driver 0
(==) Matched vesa as autoconfigured driver 1
(==) Matched fbdev as autoconfigured driver 2
(==) Assigned the driver to the xf86ConfigLayout
(II) LoadModule: "intel"
(II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
(II) Module intel: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 2.9.1
    Module class: X.Org Video Driver
    ABI class: X.Org Video Driver, version 6.0
(II) LoadModule: "vesa"
(II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
(II) Module vesa: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 2.3.0
    Module class: X.Org Video Driver
    ABI class: X.Org Video Driver, version 6.0
(II) LoadModule: "fbdev"
(II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
(II) Module fbdev: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 0.4.1
    ABI class: X.Org Video Driver, version 6.0
(II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
    i810-dc100, i810e, i815, i830M, 845G, 852GM/855GM, 865G, 915G,
    E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
    965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
    4 Series, G45/G43, Q45/Q43, G41, B43, Clarkdale, Arrandale
(II) VESA: driver for VESA chipsets: vesa
(II) FBDEV: driver for framebuffer: fbdev
(II) Primary Device is: PCI 00@00:02:0
(WW) Falling back to old probe method for fbdev
(II) Loading sub module "fbdevhw"
(II) LoadModule: "fbdevhw"
(II) Loading /usr/lib/xorg/modules/linux/libfbdevhw.so
(II) Module fbdevhw: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 0.0.2
    ABI class: X.Org Video Driver, version 6.0
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules/libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.1.0
    ABI class: X.Org Video Driver, version 6.0
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules/libint10.so
(II) Module int10: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    ABI class: X.Org Video Driver, version 6.0
(II) VESA(0): initializing int10
(II) VESA(0): Primary V_BIOS segment is: 0xc000
(II) VESA(0): VESA BIOS detected
(II) VESA(0): VESA VBE Version 3.0
(II) VESA(0): VESA VBE Total Mem: 65472 kB
(II) VESA(0): VESA VBE OEM: Intel(R)Sandybridge Desktop Graphics Chipset Accelerated VGA BIOS
(II) VESA(0): VESA VBE OEM Software Rev: 1.0
(II) VESA(0): VESA VBE OEM Vendor: Intel Corporation
(II) VESA(0): VESA VBE OEM Product: Intel(R)Sandybridge Desktop Graphics Controller
(II) VESA(0): VESA VBE OEM Product Rev: Hardware Version 0.0
(II) VESA(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
(==) VESA(0): Depth 24, (--) framebuffer bpp 32
(==) VESA(0): RGB weight 888
(==) VESA(0): Default visual is TrueColor
(==) VESA(0): Using gamma correction (1.0, 1.0, 1.0)
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(II) VESA(0): VESA VBE DDC supported
(II) VESA(0): VESA VBE DDC Level 2
(II) VESA(0): VESA VBE DDC transfer in appr. 1 sec.
(II) VESA(0): VESA VBE DDC read successfully
(II) VESA(0): Manufacturer: SAM  Model: 78b  Serial#: 1514292021
(II) VESA(0): Year: 2011  Week: 17
(II) VESA(0): EDID Version: 1.3
(II) VESA(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) VESA(0): Sync:  Separate  Composite  SyncOnGreen
(II) VESA(0): Max Image Size [cm]: horiz.: 44  vert.: 25
(II) VESA(0): Gamma: 2.20
(II) VESA(0): DPMS capabilities: Off; RGB/Color Display
(II) VESA(0): First detailed timing is preferred mode
(II) VESA(0): redX: 0.639 redY: 0.340   greenX: 0.324 greenY: 0.622
(II) VESA(0): blueX: 0.155 blueY: 0.042   whiteX: 0.312 whiteY: 0.329
(II) VESA(0): Supported established timings:
(II) VESA(0): 720x400@70Hz
(II) VESA(0): 640x480@60Hz
(II) VESA(0): 640x480@67Hz
(II) VESA(0): 640x480@72Hz
(II) VESA(0): 640x480@75Hz
(II) VESA(0): 800x600@56Hz
(II) VESA(0): 800x600@60Hz
(II) VESA(0): 800x600@72Hz
(II) VESA(0): 800x600@75Hz
(II) VESA(0): 832x624@75Hz
(II) VESA(0): 1024x768@60Hz
(II) VESA(0): 1024x768@70Hz
(II) VESA(0): 1024x768@75Hz
(II) VESA(0): 1152x864@75Hz
(II) VESA(0): Manufacturer's mask: 0
(II) VESA(0): Supported standard timings:
(II) VESA(0): #0: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) VESA(0): #1: hsize: 1280  vsize 800  refresh: 60  vid: 129
(II) VESA(0): #2: hsize: 1280  vsize 800  refresh: 75  vid: 3969
(II) VESA(0): #3: hsize: 1440  vsize 900  refresh: 60  vid: 149
(II) VESA(0): #4: hsize: 1440  vsize 900  refresh: 75  vid: 3989
(II) VESA(0): Supported detailed timing:
(II) VESA(0): clock: 108.0 MHz   Image Size:  443 x 249 mm
(II) VESA(0): h_active: 1600  h_sync: 1624  h_sync_end 1704 h_blank_end 1800 h_border: 0
(II) VESA(0): v_active: 900  v_sync: 901  v_sync_end 904 v_blanking: 1000 v_border: 0
(II) VESA(0): Ranges: V min: 56 V max: 75 Hz, H min: 30 H max: 81 kHz, PixClock max 150 MHz
(II) VESA(0): Monitor name: SA300/SA350
(II) VESA(0): Serial No: H9NB401854
(II) VESA(0): EDID (in hex):
(II) VESA(0):     00ffffffffffff004c2d8b073543425a
(II) VESA(0):     111501030e2c19782a81f1a357539f27
(II) VESA(0):     0a5054bfee80714f8100810f9500950f
(II) VESA(0):     010101010101302a40c8608464301850
(II) VESA(0):     1300bbf91000001e000000fd00384b1e
(II) VESA(0):     510f000a202020202020000000fc0053
(II) VESA(0):     413330302f53413335300a20000000ff
(II) VESA(0):     0048394e423430313835340a20200021
(II) VESA(0): EDID vendor "SAM", prod id 1931
(II) VESA(0): Using EDID range info for horizontal sync
(II) VESA(0): Using EDID range info for vertical refresh
(II) VESA(0): Printing DDC gathered Modelines:
(II) VESA(0): Modeline "1600x900"x0.0  108.00  1600 1624 1704 1800  900 901 904 1000 +hsync +vsync (60.0 kHz)
(II) VESA(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) VESA(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) VESA(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) VESA(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) VESA(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) VESA(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) VESA(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) VESA(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) VESA(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) VESA(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) VESA(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) VESA(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) VESA(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) VESA(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) VESA(0): Modeline "1280x800"x0.0   83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync (49.7 kHz)
(II) VESA(0): Modeline "1280x800"x0.0  106.50  1280 1360 1488 1696  800 803 809 838 -hsync +vsync (62.8 kHz)
(II) VESA(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
(II) VESA(0): Modeline "1440x900"x0.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz)
(II) VESA(0): Searching for matching VESA mode(s):
Mode: 160 (0x0)
    ModeAttributes: 0x0
    WinAAttributes: 0x0
    WinBAttributes: 0x0
    WinGranularity: 0
    WinSize: 0
    WinASegment: 0x0
    WinBSegment: 0x0
    WinFuncPtr: 0x0
    BytesPerScanline: 0
    XResolution: 0
    YResolution: 0
    XCharSize: 0
    YCharSize: 0
    NumberOfPlanes: 0
    BitsPerPixel: 0
    NumberOfBanks: 0
    MemoryModel: 0
    BankSize: 0
    NumberOfImages: 0
    RedMaskSize: 0
    RedFieldPosition: 0
    GreenMaskSize: 0
    GreenFieldPosition: 0
    BlueMaskSize: 0
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0x0
    LinBytesPerScanLine: 0
    BnkNumberOfImagePages: 0
    LinNumberOfImagePages: 0
    LinRedMaskSize: 0
    LinRedFieldPosition: 0
    LinGreenMaskSize: 0
    LinGreenFieldPosition: 0
    LinBlueMaskSize: 0
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 0
Mode: 161 (0x0)
    ModeAttributes: 0x0
    WinAAttributes: 0x0
    WinBAttributes: 0x0
    WinGranularity: 0
    WinSize: 0
    WinASegment: 0x0
    WinBSegment: 0x0
    WinFuncPtr: 0x0
    BytesPerScanline: 0
    XResolution: 0
    YResolution: 0
    XCharSize: 0
    YCharSize: 0
    NumberOfPlanes: 0
    BitsPerPixel: 0
    NumberOfBanks: 0
    MemoryModel: 0
    BankSize: 0
    NumberOfImages: 0
    RedMaskSize: 0
    RedFieldPosition: 0
    GreenMaskSize: 0
    GreenFieldPosition: 0
    BlueMaskSize: 0
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0x0
    LinBytesPerScanLine: 0
    BnkNumberOfImagePages: 0
    LinNumberOfImagePages: 0
    LinRedMaskSize: 0
    LinRedFieldPosition: 0
    LinGreenMaskSize: 0
    LinGreenFieldPosition: 0
    LinBlueMaskSize: 0
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 0
Mode: 162 (0x0)
    ModeAttributes: 0x0
    WinAAttributes: 0x0
    WinBAttributes: 0x0
    WinGranularity: 0
    WinSize: 0
    WinASegment: 0x0
    WinBSegment: 0x0
    WinFuncPtr: 0x0
    BytesPerScanline: 0
    XResolution: 0
    YResolution: 0
    XCharSize: 0
    YCharSize: 0
    NumberOfPlanes: 0
    BitsPerPixel: 0
    NumberOfBanks: 0
    MemoryModel: 0
    BankSize: 0
    NumberOfImages: 0
    RedMaskSize: 0
    RedFieldPosition: 0
    GreenMaskSize: 0
    GreenFieldPosition: 0
    BlueMaskSize: 0
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0x0
    LinBytesPerScanLine: 0
    BnkNumberOfImagePages: 0
    LinNumberOfImagePages: 0
    LinRedMaskSize: 0
    LinRedFieldPosition: 0
    LinGreenMaskSize: 0
    LinGreenFieldPosition: 0
    LinBlueMaskSize: 0
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 0
Mode: 163 (0x0)
    ModeAttributes: 0x0
    WinAAttributes: 0x0
    WinBAttributes: 0x0
    WinGranularity: 0
    WinSize: 0
    WinASegment: 0x0
    WinBSegment: 0x0
    WinFuncPtr: 0x0
    BytesPerScanline: 0
    XResolution: 0
    YResolution: 0
    XCharSize: 0
    YCharSize: 0
    NumberOfPlanes: 0
    BitsPerPixel: 0
    NumberOfBanks: 0
    MemoryModel: 0
    BankSize: 0
    NumberOfImages: 0
    RedMaskSize: 0
    RedFieldPosition: 0
    GreenMaskSize: 0
    GreenFieldPosition: 0
    BlueMaskSize: 0
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0x0
    LinBytesPerScanLine: 0
    BnkNumberOfImagePages: 0
    LinNumberOfImagePages: 0
    LinRedMaskSize: 0
    LinRedFieldPosition: 0
    LinGreenMaskSize: 0
    LinGreenFieldPosition: 0
    LinBlueMaskSize: 0
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 0
Mode: 164 (0x0)
    ModeAttributes: 0x0
    WinAAttributes: 0x0
    WinBAttributes: 0x0
    WinGranularity: 0
    WinSize: 0
    WinASegment: 0x0
    WinBSegment: 0x0
    WinFuncPtr: 0x0
    BytesPerScanline: 0
    XResolution: 0
    YResolution: 0
    XCharSize: 0
    YCharSize: 0
    NumberOfPlanes: 0
    BitsPerPixel: 0
    NumberOfBanks: 0
    MemoryModel: 0
    BankSize: 0
    NumberOfImages: 0
    RedMaskSize: 0
    RedFieldPosition: 0
    GreenMaskSize: 0
    GreenFieldPosition: 0
    BlueMaskSize: 0
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0x0
    LinBytesPerScanLine: 0
    BnkNumberOfImagePages: 0
    LinNumberOfImagePages: 0
    LinRedMaskSize: 0
    LinRedFieldPosition: 0
    LinGreenMaskSize: 0
    LinGreenFieldPosition: 0
    LinBlueMaskSize: 0
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 0
Mode: 165 (0x0)
    ModeAttributes: 0x0
    WinAAttributes: 0x0
    WinBAttributes: 0x0
    WinGranularity: 0
    WinSize: 0
    WinASegment: 0x0
    WinBSegment: 0x0
    WinFuncPtr: 0x0
    BytesPerScanline: 0
    XResolution: 0
    YResolution: 0
    XCharSize: 0
    YCharSize: 0
    NumberOfPlanes: 0
    BitsPerPixel: 0
    NumberOfBanks: 0
    MemoryModel: 0
    BankSize: 0
    NumberOfImages: 0
    RedMaskSize: 0
    RedFieldPosition: 0
    GreenMaskSize: 0
    GreenFieldPosition: 0
    BlueMaskSize: 0
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0x0
    LinBytesPerScanLine: 0
    BnkNumberOfImagePages: 0
    LinNumberOfImagePages: 0
    LinRedMaskSize: 0
    LinRedFieldPosition: 0
    LinGreenMaskSize: 0
    LinGreenFieldPosition: 0
    LinBlueMaskSize: 0
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 0
Mode: 166 (0x0)
    ModeAttributes: 0x0
    WinAAttributes: 0x0
    WinBAttributes: 0x0
    WinGranularity: 0
    WinSize: 0
    WinASegment: 0x0
    WinBSegment: 0x0
    WinFuncPtr: 0x0
    BytesPerScanline: 0
    XResolution: 0
    YResolution: 0
    XCharSize: 0
    YCharSize: 0
    NumberOfPlanes: 0
    BitsPerPixel: 0
    NumberOfBanks: 0
    MemoryModel: 0
    BankSize: 0
    NumberOfImages: 0
    RedMaskSize: 0
    RedFieldPosition: 0
    GreenMaskSize: 0
    GreenFieldPosition: 0
    BlueMaskSize: 0
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0x0
    LinBytesPerScanLine: 0
    BnkNumberOfImagePages: 0
    LinNumberOfImagePages: 0
    LinRedMaskSize: 0
    LinRedFieldPosition: 0
    LinGreenMaskSize: 0
    LinGreenFieldPosition: 0
    LinBlueMaskSize: 0
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 0
Mode: 167 (0x0)
    ModeAttributes: 0x0
    WinAAttributes: 0x0
    WinBAttributes: 0x0
    WinGranularity: 0
    WinSize: 0
    WinASegment: 0x0
    WinBSegment: 0x0
    WinFuncPtr: 0x0
    BytesPerScanline: 0
    XResolution: 0
    YResolution: 0
    XCharSize: 0
    YCharSize: 0
    NumberOfPlanes: 0
    BitsPerPixel: 0
    NumberOfBanks: 0
    MemoryModel: 0
    BankSize: 0
    NumberOfImages: 0
    RedMaskSize: 0
    RedFieldPosition: 0
    GreenMaskSize: 0
    GreenFieldPosition: 0
    BlueMaskSize: 0
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0x0
    LinBytesPerScanLine: 0
    BnkNumberOfImagePages: 0
    LinNumberOfImagePages: 0
    LinRedMaskSize: 0
    LinRedFieldPosition: 0
    LinGreenMaskSize: 0
    LinGreenFieldPosition: 0
    LinBlueMaskSize: 0
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 0
Mode: 168 (0x0)
    ModeAttributes: 0x0
    WinAAttributes: 0x0
    WinBAttributes: 0x0
    WinGranularity: 0
    WinSize: 0
    WinASegment: 0x0
    WinBSegment: 0x0
    WinFuncPtr: 0x0
    BytesPerScanline: 0
    XResolution: 0
    YResolution: 0
    XCharSize: 0
    YCharSize: 0
    NumberOfPlanes: 0
    BitsPerPixel: 0
    NumberOfBanks: 0
    MemoryModel: 0
    BankSize: 0
    NumberOfImages: 0
    RedMaskSize: 0
    RedFieldPosition: 0
    GreenMaskSize: 0
    GreenFieldPosition: 0
    BlueMaskSize: 0
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0x0
    LinBytesPerScanLine: 0
    BnkNumberOfImagePages: 0
    LinNumberOfImagePages: 0
    LinRedMaskSize: 0
    LinRedFieldPosition: 0
    LinGreenMaskSize: 0
    LinGreenFieldPosition: 0
    LinBlueMaskSize: 0
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 0
Mode: 13c (1920x1440)
    ModeAttributes: 0x9b
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc00079bc
    BytesPerScanline: 1920
    XResolution: 1920
    YResolution: 1440
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 8
    NumberOfBanks: 1
    MemoryModel: 4
    BankSize: 0
    NumberOfImages: 22
    RedMaskSize: 0
    RedFieldPosition: 0
    GreenMaskSize: 0
    GreenFieldPosition: 0
    BlueMaskSize: 0
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0xc0000000
    LinBytesPerScanLine: 1920
    BnkNumberOfImagePages: 22
    LinNumberOfImagePages: 22
    LinRedMaskSize: 0
    LinRedFieldPosition: 0
    LinGreenMaskSize: 0
    LinGreenFieldPosition: 0
    LinBlueMaskSize: 0
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 230000000
Mode: 14d (1920x1440)
    ModeAttributes: 0x9b
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc00079bc
    BytesPerScanline: 3840
    XResolution: 1920
    YResolution: 1440
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 16
    NumberOfBanks: 1
    MemoryModel: 6
    BankSize: 0
    NumberOfImages: 11
    RedMaskSize: 5
    RedFieldPosition: 11
    GreenMaskSize: 6
    GreenFieldPosition: 5
    BlueMaskSize: 5
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0xc0000000
    LinBytesPerScanLine: 3840
    BnkNumberOfImagePages: 11
    LinNumberOfImagePages: 11
    LinRedMaskSize: 5
    LinRedFieldPosition: 11
    LinGreenMaskSize: 6
    LinGreenFieldPosition: 5
    LinBlueMaskSize: 5
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 230000000
*Mode: 15c (1920x1440)
    ModeAttributes: 0x9b
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc00079bc
    BytesPerScanline: 7680
    XResolution: 1920
    YResolution: 1440
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 32
    NumberOfBanks: 1
    MemoryModel: 6
    BankSize: 0
    NumberOfImages: 5
    RedMaskSize: 8
    RedFieldPosition: 16
    GreenMaskSize: 8
    GreenFieldPosition: 8
    BlueMaskSize: 8
    BlueFieldPosition: 0
    RsvdMaskSize: 8
    RsvdFieldPosition: 24
    DirectColorModeInfo: 0
    PhysBasePtr: 0xc0000000
    LinBytesPerScanLine: 7680
    BnkNumberOfImagePages: 5
    LinNumberOfImagePages: 5
    LinRedMaskSize: 8
    LinRedFieldPosition: 16
    LinGreenMaskSize: 8
    LinGreenFieldPosition: 8
    LinBlueMaskSize: 8
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 8
    LinRsvdFieldPosition: 24
    MaxPixelClock: 230000000
Mode: 13a (1600x1200)
    ModeAttributes: 0x9b
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc00079bc
    BytesPerScanline: 1600
    XResolution: 1600
    YResolution: 1200
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 8
    NumberOfBanks: 1
    MemoryModel: 4
    BankSize: 0
    NumberOfImages: 33
    RedMaskSize: 0
    RedFieldPosition: 0
    GreenMaskSize: 0
    GreenFieldPosition: 0
    BlueMaskSize: 0
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0xc0000000
    LinBytesPerScanLine: 1600
    BnkNumberOfImagePages: 33
    LinNumberOfImagePages: 33
    LinRedMaskSize: 0
    LinRedFieldPosition: 0
    LinGreenMaskSize: 0
    LinGreenFieldPosition: 0
    LinBlueMaskSize: 0
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 230000000
Mode: 14b (1600x1200)
    ModeAttributes: 0x9b
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc00079bc
    BytesPerScanline: 3200
    XResolution: 1600
    YResolution: 1200
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 16
    NumberOfBanks: 1
    MemoryModel: 6
    BankSize: 0
    NumberOfImages: 16
    RedMaskSize: 5
    RedFieldPosition: 11
    GreenMaskSize: 6
    GreenFieldPosition: 5
    BlueMaskSize: 5
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0xc0000000
    LinBytesPerScanLine: 3200
    BnkNumberOfImagePages: 16
    LinNumberOfImagePages: 16
    LinRedMaskSize: 5
    LinRedFieldPosition: 11
    LinGreenMaskSize: 6
    LinGreenFieldPosition: 5
    LinBlueMaskSize: 5
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 230000000
*Mode: 15a (1600x1200)
    ModeAttributes: 0x9b
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc00079bc
    BytesPerScanline: 6400
    XResolution: 1600
    YResolution: 1200
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 32
    NumberOfBanks: 1
    MemoryModel: 6
    BankSize: 0
    NumberOfImages: 7
    RedMaskSize: 8
    RedFieldPosition: 16
    GreenMaskSize: 8
    GreenFieldPosition: 8
    BlueMaskSize: 8
    BlueFieldPosition: 0
    RsvdMaskSize: 8
    RsvdFieldPosition: 24
    DirectColorModeInfo: 0
    PhysBasePtr: 0xc0000000
    LinBytesPerScanLine: 6400
    BnkNumberOfImagePages: 7
    LinNumberOfImagePages: 7
    LinRedMaskSize: 8
    LinRedFieldPosition: 16
    LinGreenMaskSize: 8
    LinGreenFieldPosition: 8
    LinBlueMaskSize: 8
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 8
    LinRsvdFieldPosition: 24
    MaxPixelClock: 230000000
Mode: 107 (1280x1024)
    ModeAttributes: 0x9b
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc00079bc
    BytesPerScanline: 1280
    XResolution: 1280
    YResolution: 1024
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 8
    NumberOfBanks: 1
    MemoryModel: 4
    BankSize: 0
    NumberOfImages: 50
    RedMaskSize: 0
    RedFieldPosition: 0
    GreenMaskSize: 0
    GreenFieldPosition: 0
    BlueMaskSize: 0
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0xc0000000
    LinBytesPerScanLine: 1280
    BnkNumberOfImagePages: 50
    LinNumberOfImagePages: 50
    LinRedMaskSize: 0
    LinRedFieldPosition: 0
    LinGreenMaskSize: 0
    LinGreenFieldPosition: 0
    LinBlueMaskSize: 0
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 230000000
Mode: 11a (1280x1024)
    ModeAttributes: 0x9b
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc00079bc
    BytesPerScanline: 2560
    XResolution: 1280
    YResolution: 1024
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 16
    NumberOfBanks: 1
    MemoryModel: 6
    BankSize: 0
    NumberOfImages: 24
    RedMaskSize: 5
    RedFieldPosition: 11
    GreenMaskSize: 6
    GreenFieldPosition: 5
    BlueMaskSize: 5
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0xc0000000
    LinBytesPerScanLine: 2560
    BnkNumberOfImagePages: 24
    LinNumberOfImagePages: 24
    LinRedMaskSize: 5
    LinRedFieldPosition: 11
    LinGreenMaskSize: 6
    LinGreenFieldPosition: 5
    LinBlueMaskSize: 5
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 230000000
*Mode: 11b (1280x1024)
    ModeAttributes: 0x9b
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc00079bc
    BytesPerScanline: 5120
    XResolution: 1280
    YResolution: 1024
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 32
    NumberOfBanks: 1
    MemoryModel: 6
    BankSize: 0
    NumberOfImages: 11
    RedMaskSize: 8
    RedFieldPosition: 16
    GreenMaskSize: 8
    GreenFieldPosition: 8
    BlueMaskSize: 8
    BlueFieldPosition: 0
    RsvdMaskSize: 8
    RsvdFieldPosition: 24
    DirectColorModeInfo: 0
    PhysBasePtr: 0xc0000000
    LinBytesPerScanLine: 5120
    BnkNumberOfImagePages: 11
    LinNumberOfImagePages: 11
    LinRedMaskSize: 8
    LinRedFieldPosition: 16
    LinGreenMaskSize: 8
    LinGreenFieldPosition: 8
    LinBlueMaskSize: 8
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 8
    LinRsvdFieldPosition: 24
    MaxPixelClock: 230000000
Mode: 105 (1024x768)
    ModeAttributes: 0x9b
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc00079bc
    BytesPerScanline: 1024
    XResolution: 1024
    YResolution: 768
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 8
    NumberOfBanks: 1
    MemoryModel: 4
    BankSize: 0
    NumberOfImages: 84
    RedMaskSize: 0
    RedFieldPosition: 0
    GreenMaskSize: 0
    GreenFieldPosition: 0
    BlueMaskSize: 0
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0xc0000000
    LinBytesPerScanLine: 1024
    BnkNumberOfImagePages: 84
    LinNumberOfImagePages: 84
    LinRedMaskSize: 0
    LinRedFieldPosition: 0
    LinGreenMaskSize: 0
    LinGreenFieldPosition: 0
    LinBlueMaskSize: 0
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 230000000
Mode: 117 (1024x768)
    ModeAttributes: 0x9b
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc00079bc
    BytesPerScanline: 2048
    XResolution: 1024
    YResolution: 768
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 16
    NumberOfBanks: 1
    MemoryModel: 6
    BankSize: 0
    NumberOfImages: 41
    RedMaskSize: 5
    RedFieldPosition: 11
    GreenMaskSize: 6
    GreenFieldPosition: 5
    BlueMaskSize: 5
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0xc0000000
    LinBytesPerScanLine: 2048
    BnkNumberOfImagePages: 41
    LinNumberOfImagePages: 41
    LinRedMaskSize: 5
    LinRedFieldPosition: 11
    LinGreenMaskSize: 6
    LinGreenFieldPosition: 5
    LinBlueMaskSize: 5
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 230000000
*Mode: 118 (1024x768)
    ModeAttributes: 0x9b
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc00079bc
    BytesPerScanline: 4096
    XResolution: 1024
    YResolution: 768
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 32
    NumberOfBanks: 1
    MemoryModel: 6
    BankSize: 0
    NumberOfImages: 20
    RedMaskSize: 8
    RedFieldPosition: 16
    GreenMaskSize: 8
    GreenFieldPosition: 8
    BlueMaskSize: 8
    BlueFieldPosition: 0
    RsvdMaskSize: 8
    RsvdFieldPosition: 24
    DirectColorModeInfo: 0
    PhysBasePtr: 0xc0000000
    LinBytesPerScanLine: 4096
    BnkNumberOfImagePages: 20
    LinNumberOfImagePages: 20
    LinRedMaskSize: 8
    LinRedFieldPosition: 16
    LinGreenMaskSize: 8
    LinGreenFieldPosition: 8
    LinBlueMaskSize: 8
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 8
    LinRsvdFieldPosition: 24
    MaxPixelClock: 230000000
*Mode: 112 (640x480)
    ModeAttributes: 0x9b
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc00079bc
    BytesPerScanline: 2560
    XResolution: 640
    YResolution: 480
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 32
    NumberOfBanks: 1
    MemoryModel: 6
    BankSize: 0
    NumberOfImages: 52
    RedMaskSize: 8
    RedFieldPosition: 16
    GreenMaskSize: 8
    GreenFieldPosition: 8
    BlueMaskSize: 8
    BlueFieldPosition: 0
    RsvdMaskSize: 8
    RsvdFieldPosition: 24
    DirectColorModeInfo: 0
    PhysBasePtr: 0xc0000000
    LinBytesPerScanLine: 2560
    BnkNumberOfImagePages: 52
    LinNumberOfImagePages: 52
    LinRedMaskSize: 8
    LinRedFieldPosition: 16
    LinGreenMaskSize: 8
    LinGreenFieldPosition: 8
    LinBlueMaskSize: 8
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 8
    LinRsvdFieldPosition: 24
    MaxPixelClock: 230000000
Mode: 114 (800x600)
    ModeAttributes: 0x9b
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc00079bc
    BytesPerScanline: 1600
    XResolution: 800
    YResolution: 600
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 16
    NumberOfBanks: 1
    MemoryModel: 6
    BankSize: 0
    NumberOfImages: 67
    RedMaskSize: 5
    RedFieldPosition: 11
    GreenMaskSize: 6
    GreenFieldPosition: 5
    BlueMaskSize: 5
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0xc0000000
    LinBytesPerScanLine: 1600
    BnkNumberOfImagePages: 67
    LinNumberOfImagePages: 67
    LinRedMaskSize: 5
    LinRedFieldPosition: 11
    LinGreenMaskSize: 6
    LinGreenFieldPosition: 5
    LinBlueMaskSize: 5
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 230000000
*Mode: 115 (800x600)
    ModeAttributes: 0x9b
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc00079bc
    BytesPerScanline: 3200
    XResolution: 800
    YResolution: 600
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 32
    NumberOfBanks: 1
    MemoryModel: 6
    BankSize: 0
    NumberOfImages: 33
    RedMaskSize: 8
    RedFieldPosition: 16
    GreenMaskSize: 8
    GreenFieldPosition: 8
    BlueMaskSize: 8
    BlueFieldPosition: 0
    RsvdMaskSize: 8
    RsvdFieldPosition: 24
    DirectColorModeInfo: 0
    PhysBasePtr: 0xc0000000
    LinBytesPerScanLine: 3200
    BnkNumberOfImagePages: 33
    LinNumberOfImagePages: 33
    LinRedMaskSize: 8
    LinRedFieldPosition: 16
    LinGreenMaskSize: 8
    LinGreenFieldPosition: 8
    LinBlueMaskSize: 8
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 8
    LinRsvdFieldPosition: 24
    MaxPixelClock: 230000000
Mode: 101 (640x480)
    ModeAttributes: 0x9b
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc00079bc
    BytesPerScanline: 640
    XResolution: 640
    YResolution: 480
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 8
    NumberOfBanks: 1
    MemoryModel: 4
    BankSize: 0
    NumberOfImages: 203
    RedMaskSize: 0
    RedFieldPosition: 0
    GreenMaskSize: 0
    GreenFieldPosition: 0
    BlueMaskSize: 0
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0xc0000000
    LinBytesPerScanLine: 640
    BnkNumberOfImagePages: 203
    LinNumberOfImagePages: 203
    LinRedMaskSize: 0
    LinRedFieldPosition: 0
    LinGreenMaskSize: 0
    LinGreenFieldPosition: 0
    LinBlueMaskSize: 0
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 230000000
Mode: 103 (800x600)
    ModeAttributes: 0x9b
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc00079bc
    BytesPerScanline: 832
    XResolution: 800
    YResolution: 600
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 8
    NumberOfBanks: 1
    MemoryModel: 4
    BankSize: 0
    NumberOfImages: 126
    RedMaskSize: 0
    RedFieldPosition: 0
    GreenMaskSize: 0
    GreenFieldPosition: 0
    BlueMaskSize: 0
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0xc0000000
    LinBytesPerScanLine: 832
    BnkNumberOfImagePages: 126
    LinNumberOfImagePages: 126
    LinRedMaskSize: 0
    LinRedFieldPosition: 0
    LinGreenMaskSize: 0
    LinGreenFieldPosition: 0
    LinBlueMaskSize: 0
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 230000000
Mode: 111 (640x480)
    ModeAttributes: 0x9b
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc00079bc
    BytesPerScanline: 1280
    XResolution: 640
    YResolution: 480
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 16
    NumberOfBanks: 1
    MemoryModel: 6
    BankSize: 0
    NumberOfImages: 101
    RedMaskSize: 5
    RedFieldPosition: 11
    GreenMaskSize: 6
    GreenFieldPosition: 5
    BlueMaskSize: 5
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0xc0000000
    LinBytesPerScanLine: 1280
    BnkNumberOfImagePages: 101
    LinNumberOfImagePages: 101
    LinRedMaskSize: 5
    LinRedFieldPosition: 11
    LinGreenMaskSize: 6
    LinGreenFieldPosition: 5
    LinBlueMaskSize: 5
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 230000000

(II) VESA(0): Total Memory: 1023 64KB banks (65472kB)
(II) VESA(0): <default monitor>: Using hsync range of 30.00-81.00 kHz
(II) VESA(0): <default monitor>: Using vrefresh range of 56.00-75.00 Hz
(II) VESA(0): <default monitor>: Using maximum pixel clock of 150.00 MHz
(WW) VESA(0): Unable to estimate virtual size
(II) VESA(0): Not using built-in mode "1920x1440" (no mode of this name)
(II) VESA(0): Not using built-in mode "1600x1200" (no mode of this name)
(II) VESA(0): Not using built-in mode "1280x1024" (no mode of this name)
(--) VESA(0): Virtual size is 1024x768 (pitch 1024)
(**) VESA(0): *Built-in mode "1024x768"
(**) VESA(0): *Built-in mode "800x600"
(**) VESA(0): *Built-in mode "640x480"
(**) VESA(0): Display dimensions: (440, 250) mm
(**) VESA(0): DPI set to (59, 78)
(**) VESA(0): Using "Shadow Framebuffer"
(II) Loading sub module "shadow"
(II) LoadModule: "shadow"
(II) Loading /usr/lib/xorg/modules/libshadow.so
(II) Module shadow: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.1.0
    ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.4
(II) UnloadModule: "intel"
(II) Unloading /usr/lib/xorg/modules/drivers/intel_drv.so
(II) UnloadModule: "fbdev"
(II) Unloading /usr/lib/xorg/modules/drivers/fbdev_drv.so
(II) UnloadModule: "fbdevhw"
(II) Unloading /usr/lib/xorg/modules/linux/libfbdevhw.so
(==) Depth 24 pixmap format is 32 bpp
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules/libint10.so
(II) VESA(0): initializing int10
(II) VESA(0): Primary V_BIOS segment is: 0xc000
(II) VESA(0): VESA BIOS detected
(II) VESA(0): VESA VBE Version 3.0
(II) VESA(0): VESA VBE Total Mem: 65472 kB
(II) VESA(0): VESA VBE OEM: Intel(R)Sandybridge Desktop Graphics Chipset Accelerated VGA BIOS
(II) VESA(0): VESA VBE OEM Software Rev: 1.0
(II) VESA(0): VESA VBE OEM Vendor: Intel Corporation
(II) VESA(0): VESA VBE OEM Product: Intel(R)Sandybridge Desktop Graphics Controller
(II) VESA(0): VESA VBE OEM Product Rev: Hardware Version 0.0
(II) VESA(0): virtual address = 0x7fc76b6d9000,
    physical address = 0xc0000000, size = 67043328
(II) VESA(0): Setting up VESA Mode 0x118 (1024x768)
(==) VESA(0): Default visual is TrueColor
(==) VESA(0): Backing store disabled
(==) VESA(0): DPMS enabled
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
(II) config/udev: Adding input device Power Button (/dev/input/event1)
(**) Power Button: Applying InputClass "evdev keyboard catchall"
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 2.3.2
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 7.0
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event1"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/udev: Adding input device Power Button (/dev/input/event0)
(**) Power Button: Applying InputClass "evdev keyboard catchall"
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event0"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/udev: Adding input device Logitech USB Receiver (/dev/input/event3)
(**) Logitech USB Receiver: Applying InputClass "evdev keyboard catchall"
(**) Logitech USB Receiver: always reports core events
(**) Logitech USB Receiver: Device: "/dev/input/event3"
(II) Logitech USB Receiver: Found keys
(II) Logitech USB Receiver: Configuring as keyboard
(II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/udev: Adding input device Logitech USB Receiver (/dev/input/event4)
(**) Logitech USB Receiver: Applying InputClass "evdev pointer catchall"
(**) Logitech USB Receiver: Applying InputClass "evdev keyboard catchall"
(**) Logitech USB Receiver: always reports core events
(**) Logitech USB Receiver: Device: "/dev/input/event4"
(II) Logitech USB Receiver: Found 20 mouse buttons
(II) Logitech USB Receiver: Found scroll wheel(s)
(II) Logitech USB Receiver: Found relative axes
(II) Logitech USB Receiver: Found x and y relative axes
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
(II) Logitech USB Receiver: initialized for relative axes.
(WW) Logitech USB Receiver: ignoring absolute axes.
(II) config/udev: Adding input device Logitech USB Receiver (/dev/input/mouse1)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device Macintosh mouse button emulation (/dev/input/event2)
(**) Macintosh mouse button emulation: Applying InputClass "evdev pointer catchall"
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event2"
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

### Post by realzippy on 2011-08-14
You still run the old kernel.
run
```
sudo update-grub
```

and reboot.

---

### Post by david476 on 2011-08-14
still nothing

---

### Post by realzippy on 2011-08-14
> **david476 said:**
> still nothing

This doesn't help.
So please post the logfile.  ;-)

I can understand that all this might not be to your pleasure,
but a little more vigor could help.
So please tell me at last which CPU and mainboard you use...
I also asked if you have upgraded to natty 11.04 or made a fresh install.

I was asking all this already to understand why the intel kernel module has a problem with your intel graphics.
And why you seem to use a 10.04 kernel...

---

### Post by david476 on 2011-08-15
Sorry for my lack of "vigor" and thank you for all the time you put into this. Also, I apologize for the lateness in this post, I did not have time last night.

When I finished my computer I made a fresh install of 11.04. I am using a intel core i5 2500K and a H67MA-E45 micro ATX MSI motherboard.

log file:

```

X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-28-server x86_64 Ubuntu
Current Operating System: Linux Colossus 2.6.32-33-generic #72-Ubuntu SMP Fri Jul 29 21:07:13 UTC 2011 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-33-generic root=UUID=a626e385-5e8a-4416-b923-ea8cb08b206d ro quiet splash i915.modeset=1
Build Date: 08 March 2011  08:22:34AM
xorg-server 2:1.7.6-2ubuntu7.6 (For technical support please see http://www.ubuntu.com/support) 
Current version of pixman: 0.16.4
    Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Mon Aug 15 07:14:03 2011
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"
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
(==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
(II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
(II) Loader magic: 0x7cb840
(II) Module ABI versions:
    X.Org ANSI C Emulation: 0.4
    X.Org Video Driver: 6.0
    X.Org XInput driver : 7.0
    X.Org Server Extension : 2.0
(++) using VT number 7

(--) PCI:*(0:0:2:0) 8086:0112:1462:7678 Intel Corporation rev 9, Mem @ 0xfe000000/4194304, 0xc0000000/268435456, I/O @ 0x0000f000/64
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
(II) Loading /usr/lib/xorg/modules/extensions/libglx.so
(II) Module glx: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    ABI class: X.Org Server Extension, version 2.0
(==) AIGLX enabled
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
(==) Matched intel as autoconfigured driver 0
(==) Matched vesa as autoconfigured driver 1
(==) Matched fbdev as autoconfigured driver 2
(==) Assigned the driver to the xf86ConfigLayout
(II) LoadModule: "intel"
(II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
(II) Module intel: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 2.9.1
    Module class: X.Org Video Driver
    ABI class: X.Org Video Driver, version 6.0
(II) LoadModule: "vesa"
(II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
(II) Module vesa: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 2.3.0
    Module class: X.Org Video Driver
    ABI class: X.Org Video Driver, version 6.0
(II) LoadModule: "fbdev"
(II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
(II) Module fbdev: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 0.4.1
    ABI class: X.Org Video Driver, version 6.0
(II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
    i810-dc100, i810e, i815, i830M, 845G, 852GM/855GM, 865G, 915G,
    E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
    965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
    4 Series, G45/G43, Q45/Q43, G41, B43, Clarkdale, Arrandale
(II) VESA: driver for VESA chipsets: vesa
(II) FBDEV: driver for framebuffer: fbdev
(II) Primary Device is: PCI 00@00:02:0
(WW) Falling back to old probe method for fbdev
(II) Loading sub module "fbdevhw"
(II) LoadModule: "fbdevhw"
(II) Loading /usr/lib/xorg/modules/linux/libfbdevhw.so
(II) Module fbdevhw: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 0.0.2
    ABI class: X.Org Video Driver, version 6.0
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules/libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.1.0
    ABI class: X.Org Video Driver, version 6.0
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules/libint10.so
(II) Module int10: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    ABI class: X.Org Video Driver, version 6.0
(II) VESA(0): initializing int10
(II) VESA(0): Primary V_BIOS segment is: 0xc000
(II) VESA(0): VESA BIOS detected
(II) VESA(0): VESA VBE Version 3.0
(II) VESA(0): VESA VBE Total Mem: 65472 kB
(II) VESA(0): VESA VBE OEM: Intel(R)Sandybridge Desktop Graphics Chipset Accelerated VGA BIOS
(II) VESA(0): VESA VBE OEM Software Rev: 1.0
(II) VESA(0): VESA VBE OEM Vendor: Intel Corporation
(II) VESA(0): VESA VBE OEM Product: Intel(R)Sandybridge Desktop Graphics Controller
(II) VESA(0): VESA VBE OEM Product Rev: Hardware Version 0.0
(II) VESA(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
(==) VESA(0): Depth 24, (--) framebuffer bpp 32
(==) VESA(0): RGB weight 888
(==) VESA(0): Default visual is TrueColor
(==) VESA(0): Using gamma correction (1.0, 1.0, 1.0)
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(II) VESA(0): VESA VBE DDC supported
(II) VESA(0): VESA VBE DDC Level 2
(II) VESA(0): VESA VBE DDC transfer in appr. 1 sec.
(II) VESA(0): VESA VBE DDC read successfully
(II) VESA(0): Manufacturer: SAM  Model: 78b  Serial#: 1514292021
(II) VESA(0): Year: 2011  Week: 17
(II) VESA(0): EDID Version: 1.3
(II) VESA(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) VESA(0): Sync:  Separate  Composite  SyncOnGreen
(II) VESA(0): Max Image Size [cm]: horiz.: 44  vert.: 25
(II) VESA(0): Gamma: 2.20
(II) VESA(0): DPMS capabilities: Off; RGB/Color Display
(II) VESA(0): First detailed timing is preferred mode
(II) VESA(0): redX: 0.639 redY: 0.340   greenX: 0.324 greenY: 0.622
(II) VESA(0): blueX: 0.155 blueY: 0.042   whiteX: 0.312 whiteY: 0.329
(II) VESA(0): Supported established timings:
(II) VESA(0): 720x400@70Hz
(II) VESA(0): 640x480@60Hz
(II) VESA(0): 640x480@67Hz
(II) VESA(0): 640x480@72Hz
(II) VESA(0): 640x480@75Hz
(II) VESA(0): 800x600@56Hz
(II) VESA(0): 800x600@60Hz
(II) VESA(0): 800x600@72Hz
(II) VESA(0): 800x600@75Hz
(II) VESA(0): 832x624@75Hz
(II) VESA(0): 1024x768@60Hz
(II) VESA(0): 1024x768@70Hz
(II) VESA(0): 1024x768@75Hz
(II) VESA(0): 1152x864@75Hz
(II) VESA(0): Manufacturer's mask: 0
(II) VESA(0): Supported standard timings:
(II) VESA(0): #0: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) VESA(0): #1: hsize: 1280  vsize 800  refresh: 60  vid: 129
(II) VESA(0): #2: hsize: 1280  vsize 800  refresh: 75  vid: 3969
(II) VESA(0): #3: hsize: 1440  vsize 900  refresh: 60  vid: 149
(II) VESA(0): #4: hsize: 1440  vsize 900  refresh: 75  vid: 3989
(II) VESA(0): Supported detailed timing:
(II) VESA(0): clock: 108.0 MHz   Image Size:  443 x 249 mm
(II) VESA(0): h_active: 1600  h_sync: 1624  h_sync_end 1704 h_blank_end 1800 h_border: 0
(II) VESA(0): v_active: 900  v_sync: 901  v_sync_end 904 v_blanking: 1000 v_border: 0
(II) VESA(0): Ranges: V min: 56 V max: 75 Hz, H min: 30 H max: 81 kHz, PixClock max 150 MHz
(II) VESA(0): Monitor name: SA300/SA350
(II) VESA(0): Serial No: H9NB401854
(II) VESA(0): EDID (in hex):
(II) VESA(0):     00ffffffffffff004c2d8b073543425a
(II) VESA(0):     111501030e2c19782a81f1a357539f27
(II) VESA(0):     0a5054bfee80714f8100810f9500950f
(II) VESA(0):     010101010101302a40c8608464301850
(II) VESA(0):     1300bbf91000001e000000fd00384b1e
(II) VESA(0):     510f000a202020202020000000fc0053
(II) VESA(0):     413330302f53413335300a20000000ff
(II) VESA(0):     0048394e423430313835340a20200021
(II) VESA(0): EDID vendor "SAM", prod id 1931
(II) VESA(0): Using EDID range info for horizontal sync
(II) VESA(0): Using EDID range info for vertical refresh
(II) VESA(0): Printing DDC gathered Modelines:
(II) VESA(0): Modeline "1600x900"x0.0  108.00  1600 1624 1704 1800  900 901 904 1000 +hsync +vsync (60.0 kHz)
(II) VESA(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) VESA(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) VESA(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) VESA(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) VESA(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) VESA(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) VESA(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) VESA(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) VESA(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) VESA(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) VESA(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) VESA(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) VESA(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) VESA(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) VESA(0): Modeline "1280x800"x0.0   83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync (49.7 kHz)
(II) VESA(0): Modeline "1280x800"x0.0  106.50  1280 1360 1488 1696  800 803 809 838 -hsync +vsync (62.8 kHz)
(II) VESA(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
(II) VESA(0): Modeline "1440x900"x0.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz)
(II) VESA(0): Searching for matching VESA mode(s):
Mode: 160 (0x0)
    ModeAttributes: 0x0
    WinAAttributes: 0x0
    WinBAttributes: 0x0
    WinGranularity: 0
    WinSize: 0
    WinASegment: 0x0
    WinBSegment: 0x0
    WinFuncPtr: 0x0
    BytesPerScanline: 0
    XResolution: 0
    YResolution: 0
    XCharSize: 0
    YCharSize: 0
    NumberOfPlanes: 0
    BitsPerPixel: 0
    NumberOfBanks: 0
    MemoryModel: 0
    BankSize: 0
    NumberOfImages: 0
    RedMaskSize: 0
    RedFieldPosition: 0
    GreenMaskSize: 0
    GreenFieldPosition: 0
    BlueMaskSize: 0
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0x0
    LinBytesPerScanLine: 0
    BnkNumberOfImagePages: 0
    LinNumberOfImagePages: 0
    LinRedMaskSize: 0
    LinRedFieldPosition: 0
    LinGreenMaskSize: 0
    LinGreenFieldPosition: 0
    LinBlueMaskSize: 0
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 0
Mode: 161 (0x0)
    ModeAttributes: 0x0
    WinAAttributes: 0x0
    WinBAttributes: 0x0
    WinGranularity: 0
    WinSize: 0
    WinASegment: 0x0
    WinBSegment: 0x0
    WinFuncPtr: 0x0
    BytesPerScanline: 0
    XResolution: 0
    YResolution: 0
    XCharSize: 0
    YCharSize: 0
    NumberOfPlanes: 0
    BitsPerPixel: 0
    NumberOfBanks: 0
    MemoryModel: 0
    BankSize: 0
    NumberOfImages: 0
    RedMaskSize: 0
    RedFieldPosition: 0
    GreenMaskSize: 0
    GreenFieldPosition: 0
    BlueMaskSize: 0
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0x0
    LinBytesPerScanLine: 0
    BnkNumberOfImagePages: 0
    LinNumberOfImagePages: 0
    LinRedMaskSize: 0
    LinRedFieldPosition: 0
    LinGreenMaskSize: 0
    LinGreenFieldPosition: 0
    LinBlueMaskSize: 0
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 0
Mode: 162 (0x0)
    ModeAttributes: 0x0
    WinAAttributes: 0x0
    WinBAttributes: 0x0
    WinGranularity: 0
    WinSize: 0
    WinASegment: 0x0
    WinBSegment: 0x0
    WinFuncPtr: 0x0
    BytesPerScanline: 0
    XResolution: 0
    YResolution: 0
    XCharSize: 0
    YCharSize: 0
    NumberOfPlanes: 0
    BitsPerPixel: 0
    NumberOfBanks: 0
    MemoryModel: 0
    BankSize: 0
    NumberOfImages: 0
    RedMaskSize: 0
    RedFieldPosition: 0
    GreenMaskSize: 0
    GreenFieldPosition: 0
    BlueMaskSize: 0
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0x0
    LinBytesPerScanLine: 0
    BnkNumberOfImagePages: 0
    LinNumberOfImagePages: 0
    LinRedMaskSize: 0
    LinRedFieldPosition: 0
    LinGreenMaskSize: 0
    LinGreenFieldPosition: 0
    LinBlueMaskSize: 0
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 0
Mode: 163 (0x0)
    ModeAttributes: 0x0
    WinAAttributes: 0x0
    WinBAttributes: 0x0
    WinGranularity: 0
    WinSize: 0
    WinASegment: 0x0
    WinBSegment: 0x0
    WinFuncPtr: 0x0
    BytesPerScanline: 0
    XResolution: 0
    YResolution: 0
    XCharSize: 0
    YCharSize: 0
    NumberOfPlanes: 0
    BitsPerPixel: 0
    NumberOfBanks: 0
    MemoryModel: 0
    BankSize: 0
    NumberOfImages: 0
    RedMaskSize: 0
    RedFieldPosition: 0
    GreenMaskSize: 0
    GreenFieldPosition: 0
    BlueMaskSize: 0
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0x0
    LinBytesPerScanLine: 0
    BnkNumberOfImagePages: 0
    LinNumberOfImagePages: 0
    LinRedMaskSize: 0
    LinRedFieldPosition: 0
    LinGreenMaskSize: 0
    LinGreenFieldPosition: 0
    LinBlueMaskSize: 0
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 0
Mode: 164 (0x0)
    ModeAttributes: 0x0
    WinAAttributes: 0x0
    WinBAttributes: 0x0
    WinGranularity: 0
    WinSize: 0
    WinASegment: 0x0
    WinBSegment: 0x0
    WinFuncPtr: 0x0
    BytesPerScanline: 0
    XResolution: 0
    YResolution: 0
    XCharSize: 0
    YCharSize: 0
    NumberOfPlanes: 0
    BitsPerPixel: 0
    NumberOfBanks: 0
    MemoryModel: 0
    BankSize: 0
    NumberOfImages: 0
    RedMaskSize: 0
    RedFieldPosition: 0
    GreenMaskSize: 0
    GreenFieldPosition: 0
    BlueMaskSize: 0
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0x0
    LinBytesPerScanLine: 0
    BnkNumberOfImagePages: 0
    LinNumberOfImagePages: 0
    LinRedMaskSize: 0
    LinRedFieldPosition: 0
    LinGreenMaskSize: 0
    LinGreenFieldPosition: 0
    LinBlueMaskSize: 0
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 0
Mode: 165 (0x0)
    ModeAttributes: 0x0
    WinAAttributes: 0x0
    WinBAttributes: 0x0
    WinGranularity: 0
    WinSize: 0
    WinASegment: 0x0
    WinBSegment: 0x0
    WinFuncPtr: 0x0
    BytesPerScanline: 0
    XResolution: 0
    YResolution: 0
    XCharSize: 0
    YCharSize: 0
    NumberOfPlanes: 0
    BitsPerPixel: 0
    NumberOfBanks: 0
    MemoryModel: 0
    BankSize: 0
    NumberOfImages: 0
    RedMaskSize: 0
    RedFieldPosition: 0
    GreenMaskSize: 0
    GreenFieldPosition: 0
    BlueMaskSize: 0
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0x0
    LinBytesPerScanLine: 0
    BnkNumberOfImagePages: 0
    LinNumberOfImagePages: 0
    LinRedMaskSize: 0
    LinRedFieldPosition: 0
    LinGreenMaskSize: 0
    LinGreenFieldPosition: 0
    LinBlueMaskSize: 0
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 0
Mode: 166 (0x0)
    ModeAttributes: 0x0
    WinAAttributes: 0x0
    WinBAttributes: 0x0
    WinGranularity: 0
    WinSize: 0
    WinASegment: 0x0
    WinBSegment: 0x0
    WinFuncPtr: 0x0
    BytesPerScanline: 0
    XResolution: 0
    YResolution: 0
    XCharSize: 0
    YCharSize: 0
    NumberOfPlanes: 0
    BitsPerPixel: 0
    NumberOfBanks: 0
    MemoryModel: 0
    BankSize: 0
    NumberOfImages: 0
    RedMaskSize: 0
    RedFieldPosition: 0
    GreenMaskSize: 0
    GreenFieldPosition: 0
    BlueMaskSize: 0
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0x0
    LinBytesPerScanLine: 0
    BnkNumberOfImagePages: 0
    LinNumberOfImagePages: 0
    LinRedMaskSize: 0
    LinRedFieldPosition: 0
    LinGreenMaskSize: 0
    LinGreenFieldPosition: 0
    LinBlueMaskSize: 0
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 0
Mode: 167 (0x0)
    ModeAttributes: 0x0
    WinAAttributes: 0x0
    WinBAttributes: 0x0
    WinGranularity: 0
    WinSize: 0
    WinASegment: 0x0
    WinBSegment: 0x0
    WinFuncPtr: 0x0
    BytesPerScanline: 0
    XResolution: 0
    YResolution: 0
    XCharSize: 0
    YCharSize: 0
    NumberOfPlanes: 0
    BitsPerPixel: 0
    NumberOfBanks: 0
    MemoryModel: 0
    BankSize: 0
    NumberOfImages: 0
    RedMaskSize: 0
    RedFieldPosition: 0
    GreenMaskSize: 0
    GreenFieldPosition: 0
    BlueMaskSize: 0
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0x0
    LinBytesPerScanLine: 0
    BnkNumberOfImagePages: 0
    LinNumberOfImagePages: 0
    LinRedMaskSize: 0
    LinRedFieldPosition: 0
    LinGreenMaskSize: 0
    LinGreenFieldPosition: 0
    LinBlueMaskSize: 0
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 0
Mode: 168 (0x0)
    ModeAttributes: 0x0
    WinAAttributes: 0x0
    WinBAttributes: 0x0
    WinGranularity: 0
    WinSize: 0
    WinASegment: 0x0
    WinBSegment: 0x0
    WinFuncPtr: 0x0
    BytesPerScanline: 0
    XResolution: 0
    YResolution: 0
    XCharSize: 0
    YCharSize: 0
    NumberOfPlanes: 0
    BitsPerPixel: 0
    NumberOfBanks: 0
    MemoryModel: 0
    BankSize: 0
    NumberOfImages: 0
    RedMaskSize: 0
    RedFieldPosition: 0
    GreenMaskSize: 0
    GreenFieldPosition: 0
    BlueMaskSize: 0
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0x0
    LinBytesPerScanLine: 0
    BnkNumberOfImagePages: 0
    LinNumberOfImagePages: 0
    LinRedMaskSize: 0
    LinRedFieldPosition: 0
    LinGreenMaskSize: 0
    LinGreenFieldPosition: 0
    LinBlueMaskSize: 0
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 0
Mode: 13c (1920x1440)
    ModeAttributes: 0x9b
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc00079bc
    BytesPerScanline: 1920
    XResolution: 1920
    YResolution: 1440
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 8
    NumberOfBanks: 1
    MemoryModel: 4
    BankSize: 0
    NumberOfImages: 22
    RedMaskSize: 0
    RedFieldPosition: 0
    GreenMaskSize: 0
    GreenFieldPosition: 0
    BlueMaskSize: 0
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0xc0000000
    LinBytesPerScanLine: 1920
    BnkNumberOfImagePages: 22
    LinNumberOfImagePages: 22
    LinRedMaskSize: 0
    LinRedFieldPosition: 0
    LinGreenMaskSize: 0
    LinGreenFieldPosition: 0
    LinBlueMaskSize: 0
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 230000000
Mode: 14d (1920x1440)
    ModeAttributes: 0x9b
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc00079bc
    BytesPerScanline: 3840
    XResolution: 1920
    YResolution: 1440
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 16
    NumberOfBanks: 1
    MemoryModel: 6
    BankSize: 0
    NumberOfImages: 11
    RedMaskSize: 5
    RedFieldPosition: 11
    GreenMaskSize: 6
    GreenFieldPosition: 5
    BlueMaskSize: 5
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0xc0000000
    LinBytesPerScanLine: 3840
    BnkNumberOfImagePages: 11
    LinNumberOfImagePages: 11
    LinRedMaskSize: 5
    LinRedFieldPosition: 11
    LinGreenMaskSize: 6
    LinGreenFieldPosition: 5
    LinBlueMaskSize: 5
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 230000000
*Mode: 15c (1920x1440)
    ModeAttributes: 0x9b
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc00079bc
    BytesPerScanline: 7680
    XResolution: 1920
    YResolution: 1440
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 32
    NumberOfBanks: 1
    MemoryModel: 6
    BankSize: 0
    NumberOfImages: 5
    RedMaskSize: 8
    RedFieldPosition: 16
    GreenMaskSize: 8
    GreenFieldPosition: 8
    BlueMaskSize: 8
    BlueFieldPosition: 0
    RsvdMaskSize: 8
    RsvdFieldPosition: 24
    DirectColorModeInfo: 0
    PhysBasePtr: 0xc0000000
    LinBytesPerScanLine: 7680
    BnkNumberOfImagePages: 5
    LinNumberOfImagePages: 5
    LinRedMaskSize: 8
    LinRedFieldPosition: 16
    LinGreenMaskSize: 8
    LinGreenFieldPosition: 8
    LinBlueMaskSize: 8
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 8
    LinRsvdFieldPosition: 24
    MaxPixelClock: 230000000
Mode: 13a (1600x1200)
    ModeAttributes: 0x9b
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc00079bc
    BytesPerScanline: 1600
    XResolution: 1600
    YResolution: 1200
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 8
    NumberOfBanks: 1
    MemoryModel: 4
    BankSize: 0
    NumberOfImages: 33
    RedMaskSize: 0
    RedFieldPosition: 0
    GreenMaskSize: 0
    GreenFieldPosition: 0
    BlueMaskSize: 0
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0xc0000000
    LinBytesPerScanLine: 1600
    BnkNumberOfImagePages: 33
    LinNumberOfImagePages: 33
    LinRedMaskSize: 0
    LinRedFieldPosition: 0
    LinGreenMaskSize: 0
    LinGreenFieldPosition: 0
    LinBlueMaskSize: 0
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 230000000
Mode: 14b (1600x1200)
    ModeAttributes: 0x9b
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc00079bc
    BytesPerScanline: 3200
    XResolution: 1600
    YResolution: 1200
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 16
    NumberOfBanks: 1
    MemoryModel: 6
    BankSize: 0
    NumberOfImages: 16
    RedMaskSize: 5
    RedFieldPosition: 11
    GreenMaskSize: 6
    GreenFieldPosition: 5
    BlueMaskSize: 5
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0xc0000000
    LinBytesPerScanLine: 3200
    BnkNumberOfImagePages: 16
    LinNumberOfImagePages: 16
    LinRedMaskSize: 5
    LinRedFieldPosition: 11
    LinGreenMaskSize: 6
    LinGreenFieldPosition: 5
    LinBlueMaskSize: 5
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 230000000
*Mode: 15a (1600x1200)
    ModeAttributes: 0x9b
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc00079bc
    BytesPerScanline: 6400
    XResolution: 1600
    YResolution: 1200
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 32
    NumberOfBanks: 1
    MemoryModel: 6
    BankSize: 0
    NumberOfImages: 7
    RedMaskSize: 8
    RedFieldPosition: 16
    GreenMaskSize: 8
    GreenFieldPosition: 8
    BlueMaskSize: 8
    BlueFieldPosition: 0
    RsvdMaskSize: 8
    RsvdFieldPosition: 24
    DirectColorModeInfo: 0
    PhysBasePtr: 0xc0000000
    LinBytesPerScanLine: 6400
    BnkNumberOfImagePages: 7
    LinNumberOfImagePages: 7
    LinRedMaskSize: 8
    LinRedFieldPosition: 16
    LinGreenMaskSize: 8
    LinGreenFieldPosition: 8
    LinBlueMaskSize: 8
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 8
    LinRsvdFieldPosition: 24
    MaxPixelClock: 230000000
Mode: 107 (1280x1024)
    ModeAttributes: 0x9b
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc00079bc
    BytesPerScanline: 1280
    XResolution: 1280
    YResolution: 1024
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 8
    NumberOfBanks: 1
    MemoryModel: 4
    BankSize: 0
    NumberOfImages: 50
    RedMaskSize: 0
    RedFieldPosition: 0
    GreenMaskSize: 0
    GreenFieldPosition: 0
    BlueMaskSize: 0
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0xc0000000
    LinBytesPerScanLine: 1280
    BnkNumberOfImagePages: 50
    LinNumberOfImagePages: 50
    LinRedMaskSize: 0
    LinRedFieldPosition: 0
    LinGreenMaskSize: 0
    LinGreenFieldPosition: 0
    LinBlueMaskSize: 0
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 230000000
Mode: 11a (1280x1024)
    ModeAttributes: 0x9b
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc00079bc
    BytesPerScanline: 2560
    XResolution: 1280
    YResolution: 1024
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 16
    NumberOfBanks: 1
    MemoryModel: 6
    BankSize: 0
    NumberOfImages: 24
    RedMaskSize: 5
    RedFieldPosition: 11
    GreenMaskSize: 6
    GreenFieldPosition: 5
    BlueMaskSize: 5
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0xc0000000
    LinBytesPerScanLine: 2560
    BnkNumberOfImagePages: 24
    LinNumberOfImagePages: 24
    LinRedMaskSize: 5
    LinRedFieldPosition: 11
    LinGreenMaskSize: 6
    LinGreenFieldPosition: 5
    LinBlueMaskSize: 5
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 230000000
*Mode: 11b (1280x1024)
    ModeAttributes: 0x9b
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc00079bc
    BytesPerScanline: 5120
    XResolution: 1280
    YResolution: 1024
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 32
    NumberOfBanks: 1
    MemoryModel: 6
    BankSize: 0
    NumberOfImages: 11
    RedMaskSize: 8
    RedFieldPosition: 16
    GreenMaskSize: 8
    GreenFieldPosition: 8
    BlueMaskSize: 8
    BlueFieldPosition: 0
    RsvdMaskSize: 8
    RsvdFieldPosition: 24
    DirectColorModeInfo: 0
    PhysBasePtr: 0xc0000000
    LinBytesPerScanLine: 5120
    BnkNumberOfImagePages: 11
    LinNumberOfImagePages: 11
    LinRedMaskSize: 8
    LinRedFieldPosition: 16
    LinGreenMaskSize: 8
    LinGreenFieldPosition: 8
    LinBlueMaskSize: 8
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 8
    LinRsvdFieldPosition: 24
    MaxPixelClock: 230000000
Mode: 105 (1024x768)
    ModeAttributes: 0x9b
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc00079bc
    BytesPerScanline: 1024
    XResolution: 1024
    YResolution: 768
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 8
    NumberOfBanks: 1
    MemoryModel: 4
    BankSize: 0
    NumberOfImages: 84
    RedMaskSize: 0
    RedFieldPosition: 0
    GreenMaskSize: 0
    GreenFieldPosition: 0
    BlueMaskSize: 0
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0xc0000000
    LinBytesPerScanLine: 1024
    BnkNumberOfImagePages: 84
    LinNumberOfImagePages: 84
    LinRedMaskSize: 0
    LinRedFieldPosition: 0
    LinGreenMaskSize: 0
    LinGreenFieldPosition: 0
    LinBlueMaskSize: 0
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 230000000
Mode: 117 (1024x768)
    ModeAttributes: 0x9b
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc00079bc
    BytesPerScanline: 2048
    XResolution: 1024
    YResolution: 768
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 16
    NumberOfBanks: 1
    MemoryModel: 6
    BankSize: 0
    NumberOfImages: 41
    RedMaskSize: 5
    RedFieldPosition: 11
    GreenMaskSize: 6
    GreenFieldPosition: 5
    BlueMaskSize: 5
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0xc0000000
    LinBytesPerScanLine: 2048
    BnkNumberOfImagePages: 41
    LinNumberOfImagePages: 41
    LinRedMaskSize: 5
    LinRedFieldPosition: 11
    LinGreenMaskSize: 6
    LinGreenFieldPosition: 5
    LinBlueMaskSize: 5
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 230000000
*Mode: 118 (1024x768)
    ModeAttributes: 0x9b
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc00079bc
    BytesPerScanline: 4096
    XResolution: 1024
    YResolution: 768
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 32
    NumberOfBanks: 1
    MemoryModel: 6
    BankSize: 0
    NumberOfImages: 20
    RedMaskSize: 8
    RedFieldPosition: 16
    GreenMaskSize: 8
    GreenFieldPosition: 8
    BlueMaskSize: 8
    BlueFieldPosition: 0
    RsvdMaskSize: 8
    RsvdFieldPosition: 24
    DirectColorModeInfo: 0
    PhysBasePtr: 0xc0000000
    LinBytesPerScanLine: 4096
    BnkNumberOfImagePages: 20
    LinNumberOfImagePages: 20
    LinRedMaskSize: 8
    LinRedFieldPosition: 16
    LinGreenMaskSize: 8
    LinGreenFieldPosition: 8
    LinBlueMaskSize: 8
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 8
    LinRsvdFieldPosition: 24
    MaxPixelClock: 230000000
*Mode: 112 (640x480)
    ModeAttributes: 0x9b
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc00079bc
    BytesPerScanline: 2560
    XResolution: 640
    YResolution: 480
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 32
    NumberOfBanks: 1
    MemoryModel: 6
    BankSize: 0
    NumberOfImages: 52
    RedMaskSize: 8
    RedFieldPosition: 16
    GreenMaskSize: 8
    GreenFieldPosition: 8
    BlueMaskSize: 8
    BlueFieldPosition: 0
    RsvdMaskSize: 8
    RsvdFieldPosition: 24
    DirectColorModeInfo: 0
    PhysBasePtr: 0xc0000000
    LinBytesPerScanLine: 2560
    BnkNumberOfImagePages: 52
    LinNumberOfImagePages: 52
    LinRedMaskSize: 8
    LinRedFieldPosition: 16
    LinGreenMaskSize: 8
    LinGreenFieldPosition: 8
    LinBlueMaskSize: 8
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 8
    LinRsvdFieldPosition: 24
    MaxPixelClock: 230000000
Mode: 114 (800x600)
    ModeAttributes: 0x9b
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc00079bc
    BytesPerScanline: 1600
    XResolution: 800
    YResolution: 600
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 16
    NumberOfBanks: 1
    MemoryModel: 6
    BankSize: 0
    NumberOfImages: 67
    RedMaskSize: 5
    RedFieldPosition: 11
    GreenMaskSize: 6
    GreenFieldPosition: 5
    BlueMaskSize: 5
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0xc0000000
    LinBytesPerScanLine: 1600
    BnkNumberOfImagePages: 67
    LinNumberOfImagePages: 67
    LinRedMaskSize: 5
    LinRedFieldPosition: 11
    LinGreenMaskSize: 6
    LinGreenFieldPosition: 5
    LinBlueMaskSize: 5
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 230000000
*Mode: 115 (800x600)
    ModeAttributes: 0x9b
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc00079bc
    BytesPerScanline: 3200
    XResolution: 800
    YResolution: 600
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 32
    NumberOfBanks: 1
    MemoryModel: 6
    BankSize: 0
    NumberOfImages: 33
    RedMaskSize: 8
    RedFieldPosition: 16
    GreenMaskSize: 8
    GreenFieldPosition: 8
    BlueMaskSize: 8
    BlueFieldPosition: 0
    RsvdMaskSize: 8
    RsvdFieldPosition: 24
    DirectColorModeInfo: 0
    PhysBasePtr: 0xc0000000
    LinBytesPerScanLine: 3200
    BnkNumberOfImagePages: 33
    LinNumberOfImagePages: 33
    LinRedMaskSize: 8
    LinRedFieldPosition: 16
    LinGreenMaskSize: 8
    LinGreenFieldPosition: 8
    LinBlueMaskSize: 8
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 8
    LinRsvdFieldPosition: 24
    MaxPixelClock: 230000000
Mode: 101 (640x480)
    ModeAttributes: 0x9b
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc00079bc
    BytesPerScanline: 640
    XResolution: 640
    YResolution: 480
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 8
    NumberOfBanks: 1
    MemoryModel: 4
    BankSize: 0
    NumberOfImages: 203
    RedMaskSize: 0
    RedFieldPosition: 0
    GreenMaskSize: 0
    GreenFieldPosition: 0
    BlueMaskSize: 0
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0xc0000000
    LinBytesPerScanLine: 640
    BnkNumberOfImagePages: 203
    LinNumberOfImagePages: 203
    LinRedMaskSize: 0
    LinRedFieldPosition: 0
    LinGreenMaskSize: 0
    LinGreenFieldPosition: 0
    LinBlueMaskSize: 0
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 230000000
Mode: 103 (800x600)
    ModeAttributes: 0x9b
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc00079bc
    BytesPerScanline: 832
    XResolution: 800
    YResolution: 600
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 8
    NumberOfBanks: 1
    MemoryModel: 4
    BankSize: 0
    NumberOfImages: 126
    RedMaskSize: 0
    RedFieldPosition: 0
    GreenMaskSize: 0
    GreenFieldPosition: 0
    BlueMaskSize: 0
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0xc0000000
    LinBytesPerScanLine: 832
    BnkNumberOfImagePages: 126
    LinNumberOfImagePages: 126
    LinRedMaskSize: 0
    LinRedFieldPosition: 0
    LinGreenMaskSize: 0
    LinGreenFieldPosition: 0
    LinBlueMaskSize: 0
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 230000000
Mode: 111 (640x480)
    ModeAttributes: 0x9b
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc00079bc
    BytesPerScanline: 1280
    XResolution: 640
    YResolution: 480
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 16
    NumberOfBanks: 1
    MemoryModel: 6
    BankSize: 0
    NumberOfImages: 101
    RedMaskSize: 5
    RedFieldPosition: 11
    GreenMaskSize: 6
    GreenFieldPosition: 5
    BlueMaskSize: 5
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0xc0000000
    LinBytesPerScanLine: 1280
    BnkNumberOfImagePages: 101
    LinNumberOfImagePages: 101
    LinRedMaskSize: 5
    LinRedFieldPosition: 11
    LinGreenMaskSize: 6
    LinGreenFieldPosition: 5
    LinBlueMaskSize: 5
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 230000000

(II) VESA(0): Total Memory: 1023 64KB banks (65472kB)
(II) VESA(0): <default monitor>: Using hsync range of 30.00-81.00 kHz
(II) VESA(0): <default monitor>: Using vrefresh range of 56.00-75.00 Hz
(II) VESA(0): <default monitor>: Using maximum pixel clock of 150.00 MHz
(WW) VESA(0): Unable to estimate virtual size
(II) VESA(0): Not using built-in mode "1920x1440" (no mode of this name)
(II) VESA(0): Not using built-in mode "1600x1200" (no mode of this name)
(II) VESA(0): Not using built-in mode "1280x1024" (no mode of this name)
(--) VESA(0): Virtual size is 1024x768 (pitch 1024)
(**) VESA(0): *Built-in mode "1024x768"
(**) VESA(0): *Built-in mode "800x600"
(**) VESA(0): *Built-in mode "640x480"
(**) VESA(0): Display dimensions: (440, 250) mm
(**) VESA(0): DPI set to (59, 78)
(**) VESA(0): Using "Shadow Framebuffer"
(II) Loading sub module "shadow"
(II) LoadModule: "shadow"
(II) Loading /usr/lib/xorg/modules/libshadow.so
(II) Module shadow: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.1.0
    ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.4
(II) UnloadModule: "intel"
(II) Unloading /usr/lib/xorg/modules/drivers/intel_drv.so
(II) UnloadModule: "fbdev"
(II) Unloading /usr/lib/xorg/modules/drivers/fbdev_drv.so
(II) UnloadModule: "fbdevhw"
(II) Unloading /usr/lib/xorg/modules/linux/libfbdevhw.so
(==) Depth 24 pixmap format is 32 bpp
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules/libint10.so
(II) VESA(0): initializing int10
(II) VESA(0): Primary V_BIOS segment is: 0xc000
(II) VESA(0): VESA BIOS detected
(II) VESA(0): VESA VBE Version 3.0
(II) VESA(0): VESA VBE Total Mem: 65472 kB
(II) VESA(0): VESA VBE OEM: Intel(R)Sandybridge Desktop Graphics Chipset Accelerated VGA BIOS
(II) VESA(0): VESA VBE OEM Software Rev: 1.0
(II) VESA(0): VESA VBE OEM Vendor: Intel Corporation
(II) VESA(0): VESA VBE OEM Product: Intel(R)Sandybridge Desktop Graphics Controller
(II) VESA(0): VESA VBE OEM Product Rev: Hardware Version 0.0
(II) VESA(0): virtual address = 0x7fcac75b5000,
    physical address = 0xc0000000, size = 67043328
(II) VESA(0): Setting up VESA Mode 0x118 (1024x768)
(==) VESA(0): Default visual is TrueColor
(==) VESA(0): Backing store disabled
(==) VESA(0): DPMS enabled
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
(II) config/udev: Adding input device Power Button (/dev/input/event1)
(**) Power Button: Applying InputClass "evdev keyboard catchall"
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 2.3.2
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 7.0
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event1"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/udev: Adding input device Power Button (/dev/input/event0)
(**) Power Button: Applying InputClass "evdev keyboard catchall"
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event0"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/udev: Adding input device Logitech USB Receiver (/dev/input/event3)
(**) Logitech USB Receiver: Applying InputClass "evdev keyboard catchall"
(**) Logitech USB Receiver: always reports core events
(**) Logitech USB Receiver: Device: "/dev/input/event3"
(II) Logitech USB Receiver: Found keys
(II) Logitech USB Receiver: Configuring as keyboard
(II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/udev: Adding input device Logitech USB Receiver (/dev/input/event4)
(**) Logitech USB Receiver: Applying InputClass "evdev pointer catchall"
(**) Logitech USB Receiver: Applying InputClass "evdev keyboard catchall"
(**) Logitech USB Receiver: always reports core events
(**) Logitech USB Receiver: Device: "/dev/input/event4"
(II) Logitech USB Receiver: Found 20 mouse buttons
(II) Logitech USB Receiver: Found scroll wheel(s)
(II) Logitech USB Receiver: Found relative axes
(II) Logitech USB Receiver: Found x and y relative axes
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
(II) Logitech USB Receiver: initialized for relative axes.
(WW) Logitech USB Receiver: ignoring absolute axes.
(II) config/udev: Adding input device Logitech USB Receiver (/dev/input/mouse1)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device Macintosh mouse button emulation (/dev/input/event2)
(**) Macintosh mouse button emulation: Applying InputClass "evdev pointer catchall"
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event2"
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

### Post by david476 on 2011-08-15
would using a DVI cable help?

---

### Post by realzippy on 2011-08-15
No,I guess not. 
Ubuntu can see your monitor data (EDID),this is not the problem
(it usually is ;-),but not here,edid is seen in log)
..problem is that the kernel cannot see the graphics core of your I5 CPU
and does not load the intel driver.
Idea is to install fresher kernel for natty and latest intel driver from xorgedgers.

Create a folder on your user's home named "kernel":
```
mkdir kernel
```

go there:
```
cd kernel
```
Kernel PPA is down at the moment,so we have to do it manually:
You have to install 3 so called ".deb files" in a special order:
To download part1:
```
wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.39-oneiric/linux-headers-2.6.39-020639_2.6.39-020639.201105190911_all.deb
```
Install :
```
sudo dpkg -i linux-headers-2.6.39-020639_2.6.39-020639.201105190911_all.deb
```
then:
For **32bit** Natty:
```
wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.39-oneiric/linux-headers-2.6.39-020639-generic_2.6.39-020639.201105190911_i386.deb
```

```
sudo dpkg -i linux-headers-2.6.39-020639-generic_2.6.39-020639.201105190911_i386.deb
```

```
wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.39-oneiric/linux-image-2.6.39-020639-generic_2.6.39-020639.201105190911_i386.deb
```

```
sudo dpkg -i linux-image-2.6.39-020639-generic_2.6.39-020639.201105190911_i386.deb
```


For **64bit** Natty:
```
wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.39-oneiric/linux-headers-2.6.39-020639-generic_2.6.39-020639.201105190911_amd64.deb

```
```
sudo dpkg -i linux-headers-2.6.39-020639-generic_2.6.39-020639.201105190911_amd64.deb
```

```
wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.39-oneiric/linux-image-2.6.39-020639-generic_2.6.39-020639.201105190911_amd64.deb
```

```
sudo dpkg -i linux-image-2.6.39-020639-generic_2.6.39-020639.201105190911_amd64.deb

```

For all:

```
sudo update-grub
```

Reboot.
run
```
uname -r
```
hopefully you see 2.6.39...

Next step is to update your video driver.
The xorgedgers ppa team has the "best" for your purpose .
I can't give you the instructions before you have read the stuff
(they wan't it this way ...) so visit:
[https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)
and read.
When done ,post,then we go on.  :P

---

### Post by david476 on 2011-08-15
I got:
2.6.32-33-generic

I think it had trouble installing things.

If you need the log:

```
X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-28-server x86_64 Ubuntu
Current Operating System: Linux Colossus 2.6.32-33-generic #72-Ubuntu SMP Fri Jul 29 21:07:13 UTC 2011 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-33-generic root=UUID=a626e385-5e8a-4416-b923-ea8cb08b206d ro quiet splash i915.modeset=1
Build Date: 08 March 2011  08:22:34AM
xorg-server 2:1.7.6-2ubuntu7.6 (For technical support please see http://www.ubuntu.com/support) 
Current version of pixman: 0.16.4
    Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Mon Aug 15 13:25:04 2011
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"
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
(==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
(II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
(II) Loader magic: 0x7cb840
(II) Module ABI versions:
    X.Org ANSI C Emulation: 0.4
    X.Org Video Driver: 6.0
    X.Org XInput driver : 7.0
    X.Org Server Extension : 2.0
(++) using VT number 7

(--) PCI:*(0:0:2:0) 8086:0112:1462:7678 Intel Corporation rev 9, Mem @ 0xfe000000/4194304, 0xc0000000/268435456, I/O @ 0x0000f000/64
(WW) Open ACPI failed (/var/run/acpid.socket) (No such file or directory)
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
(II) Loading /usr/lib/xorg/modules/extensions/libglx.so
(II) Module glx: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    ABI class: X.Org Server Extension, version 2.0
(==) AIGLX enabled
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
(==) Matched intel as autoconfigured driver 0
(==) Matched vesa as autoconfigured driver 1
(==) Matched fbdev as autoconfigured driver 2
(==) Assigned the driver to the xf86ConfigLayout
(II) LoadModule: "intel"
(II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
(II) Module intel: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 2.9.1
    Module class: X.Org Video Driver
    ABI class: X.Org Video Driver, version 6.0
(II) LoadModule: "vesa"
(II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
(II) Module vesa: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 2.3.0
    Module class: X.Org Video Driver
    ABI class: X.Org Video Driver, version 6.0
(II) LoadModule: "fbdev"
(II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
(II) Module fbdev: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 0.4.1
    ABI class: X.Org Video Driver, version 6.0
(II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
    i810-dc100, i810e, i815, i830M, 845G, 852GM/855GM, 865G, 915G,
    E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
    965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
    4 Series, G45/G43, Q45/Q43, G41, B43, Clarkdale, Arrandale
(II) VESA: driver for VESA chipsets: vesa
(II) FBDEV: driver for framebuffer: fbdev
(II) Primary Device is: PCI 00@00:02:0
(WW) Falling back to old probe method for fbdev
(II) Loading sub module "fbdevhw"
(II) LoadModule: "fbdevhw"
(II) Loading /usr/lib/xorg/modules/linux/libfbdevhw.so
(II) Module fbdevhw: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 0.0.2
    ABI class: X.Org Video Driver, version 6.0
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules/libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.1.0
    ABI class: X.Org Video Driver, version 6.0
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules/libint10.so
(II) Module int10: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    ABI class: X.Org Video Driver, version 6.0
(II) VESA(0): initializing int10
(II) VESA(0): Primary V_BIOS segment is: 0xc000
(II) VESA(0): VESA BIOS detected
(II) VESA(0): VESA VBE Version 3.0
(II) VESA(0): VESA VBE Total Mem: 65472 kB
(II) VESA(0): VESA VBE OEM: Intel(R)Sandybridge Desktop Graphics Chipset Accelerated VGA BIOS
(II) VESA(0): VESA VBE OEM Software Rev: 1.0
(II) VESA(0): VESA VBE OEM Vendor: Intel Corporation
(II) VESA(0): VESA VBE OEM Product: Intel(R)Sandybridge Desktop Graphics Controller
(II) VESA(0): VESA VBE OEM Product Rev: Hardware Version 0.0
(II) VESA(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
(==) VESA(0): Depth 24, (--) framebuffer bpp 32
(==) VESA(0): RGB weight 888
(==) VESA(0): Default visual is TrueColor
(==) VESA(0): Using gamma correction (1.0, 1.0, 1.0)
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(II) VESA(0): VESA VBE DDC supported
(II) VESA(0): VESA VBE DDC Level 2
(II) VESA(0): VESA VBE DDC transfer in appr. 1 sec.
(II) VESA(0): VESA VBE DDC read successfully
(II) VESA(0): Manufacturer: SAM  Model: 78b  Serial#: 1514292021
(II) VESA(0): Year: 2011  Week: 17
(II) VESA(0): EDID Version: 1.3
(II) VESA(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) VESA(0): Sync:  Separate  Composite  SyncOnGreen
(II) VESA(0): Max Image Size [cm]: horiz.: 44  vert.: 25
(II) VESA(0): Gamma: 2.20
(II) VESA(0): DPMS capabilities: Off; RGB/Color Display
(II) VESA(0): First detailed timing is preferred mode
(II) VESA(0): redX: 0.639 redY: 0.340   greenX: 0.324 greenY: 0.622
(II) VESA(0): blueX: 0.155 blueY: 0.042   whiteX: 0.312 whiteY: 0.329
(II) VESA(0): Supported established timings:
(II) VESA(0): 720x400@70Hz
(II) VESA(0): 640x480@60Hz
(II) VESA(0): 640x480@67Hz
(II) VESA(0): 640x480@72Hz
(II) VESA(0): 640x480@75Hz
(II) VESA(0): 800x600@56Hz
(II) VESA(0): 800x600@60Hz
(II) VESA(0): 800x600@72Hz
(II) VESA(0): 800x600@75Hz
(II) VESA(0): 832x624@75Hz
(II) VESA(0): 1024x768@60Hz
(II) VESA(0): 1024x768@70Hz
(II) VESA(0): 1024x768@75Hz
(II) VESA(0): 1152x864@75Hz
(II) VESA(0): Manufacturer's mask: 0
(II) VESA(0): Supported standard timings:
(II) VESA(0): #0: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) VESA(0): #1: hsize: 1280  vsize 800  refresh: 60  vid: 129
(II) VESA(0): #2: hsize: 1280  vsize 800  refresh: 75  vid: 3969
(II) VESA(0): #3: hsize: 1440  vsize 900  refresh: 60  vid: 149
(II) VESA(0): #4: hsize: 1440  vsize 900  refresh: 75  vid: 3989
(II) VESA(0): Supported detailed timing:
(II) VESA(0): clock: 108.0 MHz   Image Size:  443 x 249 mm
(II) VESA(0): h_active: 1600  h_sync: 1624  h_sync_end 1704 h_blank_end 1800 h_border: 0
(II) VESA(0): v_active: 900  v_sync: 901  v_sync_end 904 v_blanking: 1000 v_border: 0
(II) VESA(0): Ranges: V min: 56 V max: 75 Hz, H min: 30 H max: 81 kHz, PixClock max 150 MHz
(II) VESA(0): Monitor name: SA300/SA350
(II) VESA(0): Serial No: H9NB401854
(II) VESA(0): EDID (in hex):
(II) VESA(0):     00ffffffffffff004c2d8b073543425a
(II) VESA(0):     111501030e2c19782a81f1a357539f27
(II) VESA(0):     0a5054bfee80714f8100810f9500950f
(II) VESA(0):     010101010101302a40c8608464301850
(II) VESA(0):     1300bbf91000001e000000fd00384b1e
(II) VESA(0):     510f000a202020202020000000fc0053
(II) VESA(0):     413330302f53413335300a20000000ff
(II) VESA(0):     0048394e423430313835340a20200021
(II) VESA(0): EDID vendor "SAM", prod id 1931
(II) VESA(0): Using EDID range info for horizontal sync
(II) VESA(0): Using EDID range info for vertical refresh
(II) VESA(0): Printing DDC gathered Modelines:
(II) VESA(0): Modeline "1600x900"x0.0  108.00  1600 1624 1704 1800  900 901 904 1000 +hsync +vsync (60.0 kHz)
(II) VESA(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) VESA(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) VESA(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) VESA(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) VESA(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) VESA(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) VESA(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) VESA(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) VESA(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) VESA(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) VESA(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) VESA(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) VESA(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) VESA(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) VESA(0): Modeline "1280x800"x0.0   83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync (49.7 kHz)
(II) VESA(0): Modeline "1280x800"x0.0  106.50  1280 1360 1488 1696  800 803 809 838 -hsync +vsync (62.8 kHz)
(II) VESA(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
(II) VESA(0): Modeline "1440x900"x0.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz)
(II) VESA(0): Searching for matching VESA mode(s):
Mode: 160 (0x0)
    ModeAttributes: 0x0
    WinAAttributes: 0x0
    WinBAttributes: 0x0
    WinGranularity: 0
    WinSize: 0
    WinASegment: 0x0
    WinBSegment: 0x0
    WinFuncPtr: 0x0
    BytesPerScanline: 0
    XResolution: 0
    YResolution: 0
    XCharSize: 0
    YCharSize: 0
    NumberOfPlanes: 0
    BitsPerPixel: 0
    NumberOfBanks: 0
    MemoryModel: 0
    BankSize: 0
    NumberOfImages: 0
    RedMaskSize: 0
    RedFieldPosition: 0
    GreenMaskSize: 0
    GreenFieldPosition: 0
    BlueMaskSize: 0
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0x0
    LinBytesPerScanLine: 0
    BnkNumberOfImagePages: 0
    LinNumberOfImagePages: 0
    LinRedMaskSize: 0
    LinRedFieldPosition: 0
    LinGreenMaskSize: 0
    LinGreenFieldPosition: 0
    LinBlueMaskSize: 0
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 0
Mode: 161 (0x0)
    ModeAttributes: 0x0
    WinAAttributes: 0x0
    WinBAttributes: 0x0
    WinGranularity: 0
    WinSize: 0
    WinASegment: 0x0
    WinBSegment: 0x0
    WinFuncPtr: 0x0
    BytesPerScanline: 0
    XResolution: 0
    YResolution: 0
    XCharSize: 0
    YCharSize: 0
    NumberOfPlanes: 0
    BitsPerPixel: 0
    NumberOfBanks: 0
    MemoryModel: 0
    BankSize: 0
    NumberOfImages: 0
    RedMaskSize: 0
    RedFieldPosition: 0
    GreenMaskSize: 0
    GreenFieldPosition: 0
    BlueMaskSize: 0
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0x0
    LinBytesPerScanLine: 0
    BnkNumberOfImagePages: 0
    LinNumberOfImagePages: 0
    LinRedMaskSize: 0
    LinRedFieldPosition: 0
    LinGreenMaskSize: 0
    LinGreenFieldPosition: 0
    LinBlueMaskSize: 0
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 0
Mode: 162 (0x0)
    ModeAttributes: 0x0
    WinAAttributes: 0x0
    WinBAttributes: 0x0
    WinGranularity: 0
    WinSize: 0
    WinASegment: 0x0
    WinBSegment: 0x0
    WinFuncPtr: 0x0
    BytesPerScanline: 0
    XResolution: 0
    YResolution: 0
    XCharSize: 0
    YCharSize: 0
    NumberOfPlanes: 0
    BitsPerPixel: 0
    NumberOfBanks: 0
    MemoryModel: 0
    BankSize: 0
    NumberOfImages: 0
    RedMaskSize: 0
    RedFieldPosition: 0
    GreenMaskSize: 0
    GreenFieldPosition: 0
    BlueMaskSize: 0
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0x0
    LinBytesPerScanLine: 0
    BnkNumberOfImagePages: 0
    LinNumberOfImagePages: 0
    LinRedMaskSize: 0
    LinRedFieldPosition: 0
    LinGreenMaskSize: 0
    LinGreenFieldPosition: 0
    LinBlueMaskSize: 0
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 0
Mode: 163 (0x0)
    ModeAttributes: 0x0
    WinAAttributes: 0x0
    WinBAttributes: 0x0
    WinGranularity: 0
    WinSize: 0
    WinASegment: 0x0
    WinBSegment: 0x0
    WinFuncPtr: 0x0
    BytesPerScanline: 0
    XResolution: 0
    YResolution: 0
    XCharSize: 0
    YCharSize: 0
    NumberOfPlanes: 0
    BitsPerPixel: 0
    NumberOfBanks: 0
    MemoryModel: 0
    BankSize: 0
    NumberOfImages: 0
    RedMaskSize: 0
    RedFieldPosition: 0
    GreenMaskSize: 0
    GreenFieldPosition: 0
    BlueMaskSize: 0
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0x0
    LinBytesPerScanLine: 0
    BnkNumberOfImagePages: 0
    LinNumberOfImagePages: 0
    LinRedMaskSize: 0
    LinRedFieldPosition: 0
    LinGreenMaskSize: 0
    LinGreenFieldPosition: 0
    LinBlueMaskSize: 0
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 0
Mode: 164 (0x0)
    ModeAttributes: 0x0
    WinAAttributes: 0x0
    WinBAttributes: 0x0
    WinGranularity: 0
    WinSize: 0
    WinASegment: 0x0
    WinBSegment: 0x0
    WinFuncPtr: 0x0
    BytesPerScanline: 0
    XResolution: 0
    YResolution: 0
    XCharSize: 0
    YCharSize: 0
    NumberOfPlanes: 0
    BitsPerPixel: 0
    NumberOfBanks: 0
    MemoryModel: 0
    BankSize: 0
    NumberOfImages: 0
    RedMaskSize: 0
    RedFieldPosition: 0
    GreenMaskSize: 0
    GreenFieldPosition: 0
    BlueMaskSize: 0
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0x0
    LinBytesPerScanLine: 0
    BnkNumberOfImagePages: 0
    LinNumberOfImagePages: 0
    LinRedMaskSize: 0
    LinRedFieldPosition: 0
    LinGreenMaskSize: 0
    LinGreenFieldPosition: 0
    LinBlueMaskSize: 0
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 0
Mode: 165 (0x0)
    ModeAttributes: 0x0
    WinAAttributes: 0x0
    WinBAttributes: 0x0
    WinGranularity: 0
    WinSize: 0
    WinASegment: 0x0
    WinBSegment: 0x0
    WinFuncPtr: 0x0
    BytesPerScanline: 0
    XResolution: 0
    YResolution: 0
    XCharSize: 0
    YCharSize: 0
    NumberOfPlanes: 0
    BitsPerPixel: 0
    NumberOfBanks: 0
    MemoryModel: 0
    BankSize: 0
    NumberOfImages: 0
    RedMaskSize: 0
    RedFieldPosition: 0
    GreenMaskSize: 0
    GreenFieldPosition: 0
    BlueMaskSize: 0
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0x0
    LinBytesPerScanLine: 0
    BnkNumberOfImagePages: 0
    LinNumberOfImagePages: 0
    LinRedMaskSize: 0
    LinRedFieldPosition: 0
    LinGreenMaskSize: 0
    LinGreenFieldPosition: 0
    LinBlueMaskSize: 0
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 0
Mode: 166 (0x0)
    ModeAttributes: 0x0
    WinAAttributes: 0x0
    WinBAttributes: 0x0
    WinGranularity: 0
    WinSize: 0
    WinASegment: 0x0
    WinBSegment: 0x0
    WinFuncPtr: 0x0
    BytesPerScanline: 0
    XResolution: 0
    YResolution: 0
    XCharSize: 0
    YCharSize: 0
    NumberOfPlanes: 0
    BitsPerPixel: 0
    NumberOfBanks: 0
    MemoryModel: 0
    BankSize: 0
    NumberOfImages: 0
    RedMaskSize: 0
    RedFieldPosition: 0
    GreenMaskSize: 0
    GreenFieldPosition: 0
    BlueMaskSize: 0
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0x0
    LinBytesPerScanLine: 0
    BnkNumberOfImagePages: 0
    LinNumberOfImagePages: 0
    LinRedMaskSize: 0
    LinRedFieldPosition: 0
    LinGreenMaskSize: 0
    LinGreenFieldPosition: 0
    LinBlueMaskSize: 0
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 0
Mode: 167 (0x0)
    ModeAttributes: 0x0
    WinAAttributes: 0x0
    WinBAttributes: 0x0
    WinGranularity: 0
    WinSize: 0
    WinASegment: 0x0
    WinBSegment: 0x0
    WinFuncPtr: 0x0
    BytesPerScanline: 0
    XResolution: 0
    YResolution: 0
    XCharSize: 0
    YCharSize: 0
    NumberOfPlanes: 0
    BitsPerPixel: 0
    NumberOfBanks: 0
    MemoryModel: 0
    BankSize: 0
    NumberOfImages: 0
    RedMaskSize: 0
    RedFieldPosition: 0
    GreenMaskSize: 0
    GreenFieldPosition: 0
    BlueMaskSize: 0
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0x0
    LinBytesPerScanLine: 0
    BnkNumberOfImagePages: 0
    LinNumberOfImagePages: 0
    LinRedMaskSize: 0
    LinRedFieldPosition: 0
    LinGreenMaskSize: 0
    LinGreenFieldPosition: 0
    LinBlueMaskSize: 0
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 0
Mode: 168 (0x0)
    ModeAttributes: 0x0
    WinAAttributes: 0x0
    WinBAttributes: 0x0
    WinGranularity: 0
    WinSize: 0
    WinASegment: 0x0
    WinBSegment: 0x0
    WinFuncPtr: 0x0
    BytesPerScanline: 0
    XResolution: 0
    YResolution: 0
    XCharSize: 0
    YCharSize: 0
    NumberOfPlanes: 0
    BitsPerPixel: 0
    NumberOfBanks: 0
    MemoryModel: 0
    BankSize: 0
    NumberOfImages: 0
    RedMaskSize: 0
    RedFieldPosition: 0
    GreenMaskSize: 0
    GreenFieldPosition: 0
    BlueMaskSize: 0
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0x0
    LinBytesPerScanLine: 0
    BnkNumberOfImagePages: 0
    LinNumberOfImagePages: 0
    LinRedMaskSize: 0
    LinRedFieldPosition: 0
    LinGreenMaskSize: 0
    LinGreenFieldPosition: 0
    LinBlueMaskSize: 0
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 0
Mode: 13c (1920x1440)
    ModeAttributes: 0x9b
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc00079bc
    BytesPerScanline: 1920
    XResolution: 1920
    YResolution: 1440
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 8
    NumberOfBanks: 1
    MemoryModel: 4
    BankSize: 0
    NumberOfImages: 22
    RedMaskSize: 0
    RedFieldPosition: 0
    GreenMaskSize: 0
    GreenFieldPosition: 0
    BlueMaskSize: 0
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0xc0000000
    LinBytesPerScanLine: 1920
    BnkNumberOfImagePages: 22
    LinNumberOfImagePages: 22
    LinRedMaskSize: 0
    LinRedFieldPosition: 0
    LinGreenMaskSize: 0
    LinGreenFieldPosition: 0
    LinBlueMaskSize: 0
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 230000000
Mode: 14d (1920x1440)
    ModeAttributes: 0x9b
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc00079bc
    BytesPerScanline: 3840
    XResolution: 1920
    YResolution: 1440
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 16
    NumberOfBanks: 1
    MemoryModel: 6
    BankSize: 0
    NumberOfImages: 11
    RedMaskSize: 5
    RedFieldPosition: 11
    GreenMaskSize: 6
    GreenFieldPosition: 5
    BlueMaskSize: 5
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0xc0000000
    LinBytesPerScanLine: 3840
    BnkNumberOfImagePages: 11
    LinNumberOfImagePages: 11
    LinRedMaskSize: 5
    LinRedFieldPosition: 11
    LinGreenMaskSize: 6
    LinGreenFieldPosition: 5
    LinBlueMaskSize: 5
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 230000000
*Mode: 15c (1920x1440)
    ModeAttributes: 0x9b
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc00079bc
    BytesPerScanline: 7680
    XResolution: 1920
    YResolution: 1440
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 32
    NumberOfBanks: 1
    MemoryModel: 6
    BankSize: 0
    NumberOfImages: 5
    RedMaskSize: 8
    RedFieldPosition: 16
    GreenMaskSize: 8
    GreenFieldPosition: 8
    BlueMaskSize: 8
    BlueFieldPosition: 0
    RsvdMaskSize: 8
    RsvdFieldPosition: 24
    DirectColorModeInfo: 0
    PhysBasePtr: 0xc0000000
    LinBytesPerScanLine: 7680
    BnkNumberOfImagePages: 5
    LinNumberOfImagePages: 5
    LinRedMaskSize: 8
    LinRedFieldPosition: 16
    LinGreenMaskSize: 8
    LinGreenFieldPosition: 8
    LinBlueMaskSize: 8
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 8
    LinRsvdFieldPosition: 24
    MaxPixelClock: 230000000
Mode: 13a (1600x1200)
    ModeAttributes: 0x9b
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc00079bc
    BytesPerScanline: 1600
    XResolution: 1600
    YResolution: 1200
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 8
    NumberOfBanks: 1
    MemoryModel: 4
    BankSize: 0
    NumberOfImages: 33
    RedMaskSize: 0
    RedFieldPosition: 0
    GreenMaskSize: 0
    GreenFieldPosition: 0
    BlueMaskSize: 0
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0xc0000000
    LinBytesPerScanLine: 1600
    BnkNumberOfImagePages: 33
    LinNumberOfImagePages: 33
    LinRedMaskSize: 0
    LinRedFieldPosition: 0
    LinGreenMaskSize: 0
    LinGreenFieldPosition: 0
    LinBlueMaskSize: 0
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 230000000
Mode: 14b (1600x1200)
    ModeAttributes: 0x9b
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc00079bc
    BytesPerScanline: 3200
    XResolution: 1600
    YResolution: 1200
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 16
    NumberOfBanks: 1
    MemoryModel: 6
    BankSize: 0
    NumberOfImages: 16
    RedMaskSize: 5
    RedFieldPosition: 11
    GreenMaskSize: 6
    GreenFieldPosition: 5
    BlueMaskSize: 5
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0xc0000000
    LinBytesPerScanLine: 3200
    BnkNumberOfImagePages: 16
    LinNumberOfImagePages: 16
    LinRedMaskSize: 5
    LinRedFieldPosition: 11
    LinGreenMaskSize: 6
    LinGreenFieldPosition: 5
    LinBlueMaskSize: 5
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 230000000
*Mode: 15a (1600x1200)
    ModeAttributes: 0x9b
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc00079bc
    BytesPerScanline: 6400
    XResolution: 1600
    YResolution: 1200
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 32
    NumberOfBanks: 1
    MemoryModel: 6
    BankSize: 0
    NumberOfImages: 7
    RedMaskSize: 8
    RedFieldPosition: 16
    GreenMaskSize: 8
    GreenFieldPosition: 8
    BlueMaskSize: 8
    BlueFieldPosition: 0
    RsvdMaskSize: 8
    RsvdFieldPosition: 24
    DirectColorModeInfo: 0
    PhysBasePtr: 0xc0000000
    LinBytesPerScanLine: 6400
    BnkNumberOfImagePages: 7
    LinNumberOfImagePages: 7
    LinRedMaskSize: 8
    LinRedFieldPosition: 16
    LinGreenMaskSize: 8
    LinGreenFieldPosition: 8
    LinBlueMaskSize: 8
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 8
    LinRsvdFieldPosition: 24
    MaxPixelClock: 230000000
Mode: 107 (1280x1024)
    ModeAttributes: 0x9b
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc00079bc
    BytesPerScanline: 1280
    XResolution: 1280
    YResolution: 1024
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 8
    NumberOfBanks: 1
    MemoryModel: 4
    BankSize: 0
    NumberOfImages: 50
    RedMaskSize: 0
    RedFieldPosition: 0
    GreenMaskSize: 0
    GreenFieldPosition: 0
    BlueMaskSize: 0
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0xc0000000
    LinBytesPerScanLine: 1280
    BnkNumberOfImagePages: 50
    LinNumberOfImagePages: 50
    LinRedMaskSize: 0
    LinRedFieldPosition: 0
    LinGreenMaskSize: 0
    LinGreenFieldPosition: 0
    LinBlueMaskSize: 0
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 230000000
Mode: 11a (1280x1024)
    ModeAttributes: 0x9b
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc00079bc
    BytesPerScanline: 2560
    XResolution: 1280
    YResolution: 1024
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 16
    NumberOfBanks: 1
    MemoryModel: 6
    BankSize: 0
    NumberOfImages: 24
    RedMaskSize: 5
    RedFieldPosition: 11
    GreenMaskSize: 6
    GreenFieldPosition: 5
    BlueMaskSize: 5
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0xc0000000
    LinBytesPerScanLine: 2560
    BnkNumberOfImagePages: 24
    LinNumberOfImagePages: 24
    LinRedMaskSize: 5
    LinRedFieldPosition: 11
    LinGreenMaskSize: 6
    LinGreenFieldPosition: 5
    LinBlueMaskSize: 5
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 230000000
*Mode: 11b (1280x1024)
    ModeAttributes: 0x9b
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc00079bc
    BytesPerScanline: 5120
    XResolution: 1280
    YResolution: 1024
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 32
    NumberOfBanks: 1
    MemoryModel: 6
    BankSize: 0
    NumberOfImages: 11
    RedMaskSize: 8
    RedFieldPosition: 16
    GreenMaskSize: 8
    GreenFieldPosition: 8
    BlueMaskSize: 8
    BlueFieldPosition: 0
    RsvdMaskSize: 8
    RsvdFieldPosition: 24
    DirectColorModeInfo: 0
    PhysBasePtr: 0xc0000000
    LinBytesPerScanLine: 5120
    BnkNumberOfImagePages: 11
    LinNumberOfImagePages: 11
    LinRedMaskSize: 8
    LinRedFieldPosition: 16
    LinGreenMaskSize: 8
    LinGreenFieldPosition: 8
    LinBlueMaskSize: 8
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 8
    LinRsvdFieldPosition: 24
    MaxPixelClock: 230000000
Mode: 105 (1024x768)
    ModeAttributes: 0x9b
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc00079bc
    BytesPerScanline: 1024
    XResolution: 1024
    YResolution: 768
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 8
    NumberOfBanks: 1
    MemoryModel: 4
    BankSize: 0
    NumberOfImages: 84
    RedMaskSize: 0
    RedFieldPosition: 0
    GreenMaskSize: 0
    GreenFieldPosition: 0
    BlueMaskSize: 0
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0xc0000000
    LinBytesPerScanLine: 1024
    BnkNumberOfImagePages: 84
    LinNumberOfImagePages: 84
    LinRedMaskSize: 0
    LinRedFieldPosition: 0
    LinGreenMaskSize: 0
    LinGreenFieldPosition: 0
    LinBlueMaskSize: 0
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 230000000
Mode: 117 (1024x768)
    ModeAttributes: 0x9b
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc00079bc
    BytesPerScanline: 2048
    XResolution: 1024
    YResolution: 768
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 16
    NumberOfBanks: 1
    MemoryModel: 6
    BankSize: 0
    NumberOfImages: 41
    RedMaskSize: 5
    RedFieldPosition: 11
    GreenMaskSize: 6
    GreenFieldPosition: 5
    BlueMaskSize: 5
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0xc0000000
    LinBytesPerScanLine: 2048
    BnkNumberOfImagePages: 41
    LinNumberOfImagePages: 41
    LinRedMaskSize: 5
    LinRedFieldPosition: 11
    LinGreenMaskSize: 6
    LinGreenFieldPosition: 5
    LinBlueMaskSize: 5
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 230000000
*Mode: 118 (1024x768)
    ModeAttributes: 0x9b
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc00079bc
    BytesPerScanline: 4096
    XResolution: 1024
    YResolution: 768
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 32
    NumberOfBanks: 1
    MemoryModel: 6
    BankSize: 0
    NumberOfImages: 20
    RedMaskSize: 8
    RedFieldPosition: 16
    GreenMaskSize: 8
    GreenFieldPosition: 8
    BlueMaskSize: 8
    BlueFieldPosition: 0
    RsvdMaskSize: 8
    RsvdFieldPosition: 24
    DirectColorModeInfo: 0
    PhysBasePtr: 0xc0000000
    LinBytesPerScanLine: 4096
    BnkNumberOfImagePages: 20
    LinNumberOfImagePages: 20
    LinRedMaskSize: 8
    LinRedFieldPosition: 16
    LinGreenMaskSize: 8
    LinGreenFieldPosition: 8
    LinBlueMaskSize: 8
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 8
    LinRsvdFieldPosition: 24
    MaxPixelClock: 230000000
*Mode: 112 (640x480)
    ModeAttributes: 0x9b
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc00079bc
    BytesPerScanline: 2560
    XResolution: 640
    YResolution: 480
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 32
    NumberOfBanks: 1
    MemoryModel: 6
    BankSize: 0
    NumberOfImages: 52
    RedMaskSize: 8
    RedFieldPosition: 16
    GreenMaskSize: 8
    GreenFieldPosition: 8
    BlueMaskSize: 8
    BlueFieldPosition: 0
    RsvdMaskSize: 8
    RsvdFieldPosition: 24
    DirectColorModeInfo: 0
    PhysBasePtr: 0xc0000000
    LinBytesPerScanLine: 2560
    BnkNumberOfImagePages: 52
    LinNumberOfImagePages: 52
    LinRedMaskSize: 8
    LinRedFieldPosition: 16
    LinGreenMaskSize: 8
    LinGreenFieldPosition: 8
    LinBlueMaskSize: 8
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 8
    LinRsvdFieldPosition: 24
    MaxPixelClock: 230000000
Mode: 114 (800x600)
    ModeAttributes: 0x9b
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc00079bc
    BytesPerScanline: 1600
    XResolution: 800
    YResolution: 600
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 16
    NumberOfBanks: 1
    MemoryModel: 6
    BankSize: 0
    NumberOfImages: 67
    RedMaskSize: 5
    RedFieldPosition: 11
    GreenMaskSize: 6
    GreenFieldPosition: 5
    BlueMaskSize: 5
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0xc0000000
    LinBytesPerScanLine: 1600
    BnkNumberOfImagePages: 67
    LinNumberOfImagePages: 67
    LinRedMaskSize: 5
    LinRedFieldPosition: 11
    LinGreenMaskSize: 6
    LinGreenFieldPosition: 5
    LinBlueMaskSize: 5
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 230000000
*Mode: 115 (800x600)
    ModeAttributes: 0x9b
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc00079bc
    BytesPerScanline: 3200
    XResolution: 800
    YResolution: 600
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 32
    NumberOfBanks: 1
    MemoryModel: 6
    BankSize: 0
    NumberOfImages: 33
    RedMaskSize: 8
    RedFieldPosition: 16
    GreenMaskSize: 8
    GreenFieldPosition: 8
    BlueMaskSize: 8
    BlueFieldPosition: 0
    RsvdMaskSize: 8
    RsvdFieldPosition: 24
    DirectColorModeInfo: 0
    PhysBasePtr: 0xc0000000
    LinBytesPerScanLine: 3200
    BnkNumberOfImagePages: 33
    LinNumberOfImagePages: 33
    LinRedMaskSize: 8
    LinRedFieldPosition: 16
    LinGreenMaskSize: 8
    LinGreenFieldPosition: 8
    LinBlueMaskSize: 8
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 8
    LinRsvdFieldPosition: 24
    MaxPixelClock: 230000000
Mode: 101 (640x480)
    ModeAttributes: 0x9b
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc00079bc
    BytesPerScanline: 640
    XResolution: 640
    YResolution: 480
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 8
    NumberOfBanks: 1
    MemoryModel: 4
    BankSize: 0
    NumberOfImages: 203
    RedMaskSize: 0
    RedFieldPosition: 0
    GreenMaskSize: 0
    GreenFieldPosition: 0
    BlueMaskSize: 0
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0xc0000000
    LinBytesPerScanLine: 640
    BnkNumberOfImagePages: 203
    LinNumberOfImagePages: 203
    LinRedMaskSize: 0
    LinRedFieldPosition: 0
    LinGreenMaskSize: 0
    LinGreenFieldPosition: 0
    LinBlueMaskSize: 0
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 230000000
Mode: 103 (800x600)
    ModeAttributes: 0x9b
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc00079bc
    BytesPerScanline: 832
    XResolution: 800
    YResolution: 600
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 8
    NumberOfBanks: 1
    MemoryModel: 4
    BankSize: 0
    NumberOfImages: 126
    RedMaskSize: 0
    RedFieldPosition: 0
    GreenMaskSize: 0
    GreenFieldPosition: 0
    BlueMaskSize: 0
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0xc0000000
    LinBytesPerScanLine: 832
    BnkNumberOfImagePages: 126
    LinNumberOfImagePages: 126
    LinRedMaskSize: 0
    LinRedFieldPosition: 0
    LinGreenMaskSize: 0
    LinGreenFieldPosition: 0
    LinBlueMaskSize: 0
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 230000000
Mode: 111 (640x480)
    ModeAttributes: 0x9b
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc00079bc
    BytesPerScanline: 1280
    XResolution: 640
    YResolution: 480
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 16
    NumberOfBanks: 1
    MemoryModel: 6
    BankSize: 0
    NumberOfImages: 101
    RedMaskSize: 5
    RedFieldPosition: 11
    GreenMaskSize: 6
    GreenFieldPosition: 5
    BlueMaskSize: 5
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0xc0000000
    LinBytesPerScanLine: 1280
    BnkNumberOfImagePages: 101
    LinNumberOfImagePages: 101
    LinRedMaskSize: 5
    LinRedFieldPosition: 11
    LinGreenMaskSize: 6
    LinGreenFieldPosition: 5
    LinBlueMaskSize: 5
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 230000000

(II) VESA(0): Total Memory: 1023 64KB banks (65472kB)
(II) VESA(0): <default monitor>: Using hsync range of 30.00-81.00 kHz
(II) VESA(0): <default monitor>: Using vrefresh range of 56.00-75.00 Hz
(II) VESA(0): <default monitor>: Using maximum pixel clock of 150.00 MHz
(WW) VESA(0): Unable to estimate virtual size
(II) VESA(0): Not using built-in mode "1920x1440" (no mode of this name)
(II) VESA(0): Not using built-in mode "1600x1200" (no mode of this name)
(II) VESA(0): Not using built-in mode "1280x1024" (no mode of this name)
(--) VESA(0): Virtual size is 1024x768 (pitch 1024)
(**) VESA(0): *Built-in mode "1024x768"
(**) VESA(0): *Built-in mode "800x600"
(**) VESA(0): *Built-in mode "640x480"
(**) VESA(0): Display dimensions: (440, 250) mm
(**) VESA(0): DPI set to (59, 78)
(**) VESA(0): Using "Shadow Framebuffer"
(II) Loading sub module "shadow"
(II) LoadModule: "shadow"
(II) Loading /usr/lib/xorg/modules/libshadow.so
(II) Module shadow: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.1.0
    ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.4
(II) UnloadModule: "intel"
(II) Unloading /usr/lib/xorg/modules/drivers/intel_drv.so
(II) UnloadModule: "fbdev"
(II) Unloading /usr/lib/xorg/modules/drivers/fbdev_drv.so
(II) UnloadModule: "fbdevhw"
(II) Unloading /usr/lib/xorg/modules/linux/libfbdevhw.so
(==) Depth 24 pixmap format is 32 bpp
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules/libint10.so
(II) VESA(0): initializing int10
(II) VESA(0): Primary V_BIOS segment is: 0xc000
(II) VESA(0): VESA BIOS detected
(II) VESA(0): VESA VBE Version 3.0
(II) VESA(0): VESA VBE Total Mem: 65472 kB
(II) VESA(0): VESA VBE OEM: Intel(R)Sandybridge Desktop Graphics Chipset Accelerated VGA BIOS
(II) VESA(0): VESA VBE OEM Software Rev: 1.0
(II) VESA(0): VESA VBE OEM Vendor: Intel Corporation
(II) VESA(0): VESA VBE OEM Product: Intel(R)Sandybridge Desktop Graphics Controller
(II) VESA(0): VESA VBE OEM Product Rev: Hardware Version 0.0
(II) VESA(0): virtual address = 0x7f51d10b4000,
    physical address = 0xc0000000, size = 67043328
(II) VESA(0): Setting up VESA Mode 0x118 (1024x768)
(==) VESA(0): Default visual is TrueColor
(==) VESA(0): Backing store disabled
(==) VESA(0): DPMS enabled
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
(II) config/udev: Adding input device Power Button (/dev/input/event1)
(**) Power Button: Applying InputClass "evdev keyboard catchall"
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 2.3.2
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 7.0
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event1"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/udev: Adding input device Power Button (/dev/input/event0)
(**) Power Button: Applying InputClass "evdev keyboard catchall"
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event0"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/udev: Adding input device Logitech USB Receiver (/dev/input/event3)
(**) Logitech USB Receiver: Applying InputClass "evdev keyboard catchall"
(**) Logitech USB Receiver: always reports core events
(**) Logitech USB Receiver: Device: "/dev/input/event3"
(II) Logitech USB Receiver: Found keys
(II) Logitech USB Receiver: Configuring as keyboard
(II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/udev: Adding input device Logitech USB Receiver (/dev/input/event4)
(**) Logitech USB Receiver: Applying InputClass "evdev pointer catchall"
(**) Logitech USB Receiver: Applying InputClass "evdev keyboard catchall"
(**) Logitech USB Receiver: always reports core events
(**) Logitech USB Receiver: Device: "/dev/input/event4"
(II) Logitech USB Receiver: Found 20 mouse buttons
(II) Logitech USB Receiver: Found scroll wheel(s)
(II) Logitech USB Receiver: Found relative axes
(II) Logitech USB Receiver: Found x and y relative axes
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
(II) Logitech USB Receiver: initialized for relative axes.
(WW) Logitech USB Receiver: ignoring absolute axes.
(II) config/udev: Adding input device Logitech USB Receiver (/dev/input/mouse1)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device Macintosh mouse button emulation (/dev/input/event2)
(**) Macintosh mouse button emulation: Applying InputClass "evdev pointer catchall"
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event2"
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

### Post by realzippy on 2011-08-15
> **david476 said:**
> 
I think it had trouble installing things.

[COLOR="Black"]:confused:[/COLOR]
So run the commands again.Step by step.
And **post the command's output**
when you think "it has troubles"...

P.S.
..the Xorg log file isn't needed in the moment.

---

### Post by david476 on 2011-08-15
(I think I have 64bit) I think I have trouble when installing the second package:

```
david@Colossus:~/kernel$ sudo dpkg -i linux-headers-2.6.39-020639-generic_2.6.39-020639.201105190911_i386.deb
dpkg: error processing linux-headers-2.6.39-020639-generic_2.6.39-020639.201105190911_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 linux-headers-2.6.39-020639-generic_2.6.39-020639.201105190911_i386.deb
```and the third:

```
david@Colossus:~/kernel$ sudo dpkg -i linux-image-2.6.39-020639-generic_2.6.39-020639.201105190911_amd64.deb
dpkg: error processing linux-image-2.6.39-020639-generic_2.6.39-020639.201105190911_amd64.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 linux-image-2.6.39-020639-generic_2.6.39-020639.201105190911_amd64.deb
david@Colossus:~/kernel$
```

---

### Post by realzippy on 2011-08-16
> **david476 said:**
> (I think I have 64bit) I think I have trouble when installing the second package:

```
david@Colossus:~/kernel$ sudo dpkg -i linux-headers-2.6.39-020639-generic_2.6.39-020639.201105190911_[COLOR="Red"]i386[/COLOR].deb
dpkg: error processing linux-headers-2.6.39-020639-generic_2.6.39-020639.201105190911_[COLOR="Red"]i386[/COLOR].deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 linux-headers-2.6.39-020639-generic_2.6.39-020639.201105190911_i386.deb
```and the third:

```
david@Colossus:~/kernel$ sudo dpkg -i linux-image-2.6.39-020639-generic_2.6.39-020639.201105190911_amd64.deb
dpkg: error processing linux-image-2.6.39-020639-generic_2.6.39-020639.201105190911_amd64.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 linux-image-2.6.39-020639-generic_2.6.39-020639.201105190911_amd64.deb
david@Colossus:~/kernel$
```

For 1rst error:
When you have the 64 bit version downloaded,it won't find the 32bit of course (1rst error).
For 2nd error:.
.. this is not your fault,**I** posted the wrong version (mixed up 32 bit and 64 bit).I apologise,it was pretty late yesterday.Sorry.
Anyway,re-run:

```
cd kernel
```

```
wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.39-oneiric/linux-headers-2.6.39-020639-generic_2.6.39-020639.201105190911_amd64.deb

```
```
sudo dpkg -i linux-headers-2.6.39-020639-generic_2.6.39-020639.201105190911_amd64.deb
```

```
wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.39-oneiric/linux-image-2.6.39-020639-generic_2.6.39-020639.201105190911_amd64.deb

```

```
sudo dpkg -i linux-image-2.6.39-020639-generic_2.6.39-020639.201105190911_amd64.deb

```
Then run 
```
sudo update-grub

```
Reboot.
run
```
uname -r

```

---

### Post by david476 on 2011-08-16
It works!THANK YOU SO MUCH! I don't know if I should do more,
you were talking about updating video drivers?
 
uname -r:
```

2.6.39-020639-generic
```

---

### Post by realzippy on 2011-08-16
If it works,there is no need to update the intel(video)-driver.
I wasn't sure if it is the kernel module only which was too old to recognise the graphics core of your pretty new CPU or also the driver itself,which is started by the kernel.
Although it is only 2 commands to include those xorgedgers drivers,
it may corrupt your system (not very likely)...it is your choice.
But hey,if you have no video glitches/artefacts/lagging or issues like that,
don't wake up a sleeping dog.
Again sorry for my typo.

To help others,you might edit your first post with:
[B]Issue solved by installing kernel > 2.6.38 to recognise graphics core of I5
CPU correctly...[/B]
so they don't had to read through whole thread..
Please set thread as solved (ThreadTools)
& have fun !

PS.
One more thing,could you post now your Xorg.0.log ?
(for my private collection ;-) )

---

### Post by david476 on 2011-08-16
just one last thing, now when I boot up it gives me a bunch of errors until it starts working. Thanks again.

---

### Post by realzippy on 2011-08-17
You could have a look at your boot log and post the errors here.
Guess is about drivers already loaded,nothing serious?
boot log is : 
/var/log/boot.log

Btw,just installed the 3.0.1-030001-generic kernel here on natty.
Runs great without "booterrors"  (here).
If you want this kernel also (you can choose between the kernels at boot):

```
cd kernel
```

```
wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.0.1-oneiric/linux-headers-3.0.1-030001_3.0.1-030001.201108060905_all.deb
```

```
sudo dpkg -i linux-headers-3.0.1-030001_3.0.1-030001.201108060905_all.deb
```

```
wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.0.1-oneiric/linux-headers-3.0.1-030001-generic_3.0.1-030001.201108060905_amd64.deb
```

```
sudo dpkg -i linux-headers-3.0.1-030001-generic_3.0.1-030001.201108060905_amd64.deb
```

```
wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.0.1-oneiric/linux-image-3.0.1-030001-generic_3.0.1-030001.201108060905_amd64.deb
```

```
sudo dpkg -i linux-image-3.0.1-030001-generic_3.0.1-030001.201108060905_amd64.deb
```

```
sudo update-grub
```

---

### Post by david476 on 2011-08-17
Thanks. I think the errors are just it trying different things to detect the monitor

---

### Post by realzippy on 2011-08-21
Please set thread as solved (ThreadTools)
& have fun !

---

### Post by bapoumba on 2011-09-17
> **realzippy said:**
> Please set thread as solved (ThreadTools)
& have fun !
Done :)

---

