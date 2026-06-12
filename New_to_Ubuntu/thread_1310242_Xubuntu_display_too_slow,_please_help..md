---
title: "Xubuntu display too slow, please help."
date: 2009-11-01
forum: New to Ubuntu
---

### Post by gahute on 2009-11-01
Hi,

Here is what I did:
1) Installed ubuntu 9.04 (overwriting Win XP) on my old computer (Celeron 1000 MHz w/ 512Mb RAM). My system was slow.
2) Downgraded to xubuntu thinking it was going to speed up my system without success.
3) Installed edubuntu (just to see what it was).

I already posted this thread: [http://ubuntuforums.org/showthread.php?t=1308807](http://ubuntuforums.org/showthread.php?t=1308807)

What I'd like is to restart from "0" with only xubuntu and only the minimum installed (Firefox included to follow this thread).

In fact, if I could remove completely edubuntu and keep only xubuntu, it would be okay.

I started with linux yesterday evening and 24 hours later, I'm almost totally lost!

Thanks for your help!

---

### Post by Dullstar on 2009-11-01
Can you specify the exact hardware?

---

### Post by gahute on 2009-11-01
Here is what I know:

Motherboard:
 - pc133 systemboard Socket-370 M758 series w/Celeron 1000 MHz
 - Built-in AGP Graphics Accelerator (no video card)
 - Built-in Ethernet LAN (with 2 USB ports)

RAM:
 - 512Mb (2x256)

IDE Hard Drive:
 -  Maxtor 5T020H2 20Gb

Floppy drive, CD drive, DVD drive, sound card, etc.

If you need more, let me know.

Thanks,

---

### Post by kerry_s on 2009-11-02
in the terminal run: **lspci**
copy & paste the output here wrapped in code(# this on the top of reply box).

looks like this in term:

---

### Post by gahute on 2009-11-02
Hi,
Here is what lspci gives me:

```
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 630 Host (rev 30)
00:00.1 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev d0)
00:01.0 ISA bridge: Silicon Integrated Systems [SiS] SiS85C503/5513 (LPC Bridge)
00:01.1 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 84)
00:01.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 07)
00:01.3 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 07)
00:02.0 PCI bridge: Silicon Integrated Systems [SiS] Virtual PCI-to-PCI bridge (AGP)
00:0b.0 Multimedia audio controller: Fortemedia, Inc Xwave QS3000A [FM801] (rev b2)
00:0b.1 Input device controller: Fortemedia, Inc Xwave QS3000A [FM801 game port] (rev b2)
00:0f.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)
00:0f.1 Communication controller: C-Media Electronics Inc CM8738 (rev 20)
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 630/730 PCI/AGP VGA Display Adapter (rev 21)

```

Hope it helps...

---

### Post by gahute on 2009-11-02
See my system monitor since I started my computer a few minutes ago...

---

### Post by kerry_s on 2009-11-02
> 01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 630/730 PCI/AGP VGA Display Adapter (rev 21)

this tells me your vid card is "sis 630/730", you have a sis motherboard.

now we need to see the xorg log.

press: **alt+f2**
type: **gedit /var/log/Xorg.0.log**

copy & paste that the same way you did the other.

---

### Post by gahute on 2009-11-02
I hope you were waiting for as much text!!!

```
X.Org X Server 1.6.0
Release Date: 2009-2-25
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux eric-desktop 2.6.28-16-generic #55-Ubuntu SMP Tue Oct 20 19:48:24 UTC 2009 i686
Build Date: 09 April 2009  02:10:02AM
xorg-server 2:1.6.0-0ubuntu14 (buildd@rothera.buildd) 
    Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Mon Nov  2 17:26:53 2009
(==) Using config file: "/etc/X11/xorg.conf"
(==) No Layout section.  Using the first Screen section.
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Configured Monitor"
(**) |   |-->Device "Configured Video Device"
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

(--) PCI:*(0@1:0:0) Silicon Integrated Systems [SiS] 630/730 PCI/AGP VGA Display Adapter rev 33, Mem @ 0xe0000000/134217728, 0xefee0000/131072, I/O @ 0x0000cc80/128
(WW) Open ACPI failed (/var/run/acpid.socket) (No such file or directory)
(II) No APM support in BIOS or kernel
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
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 1.0.0
    ABI class: X.Org Server Extension, version 2.0
(==) AIGLX enabled
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
(II) Scanning /usr/share/xserver-xorg/pci directory for additional PCI ID's supported by the drivers
(II) Matched sis from file name sis.ids
(==) Matched sis for the autoconfigured driver
(==) Assigned the driver to the xf86ConfigLayout
(II) LoadModule: "sis"
(II) Loading /usr/lib/xorg/modules/drivers//sis_drv.so
(II) Module sis: vendor="X.Org Foundation"
    compiled for 1.5.99.902, module version = 0.10.1
    Module class: X.Org Video Driver
    ABI class: X.Org Video Driver, version 5.0
(II) SIS: driver for SiS chipsets: SIS5597/5598, SIS530/620,
    SIS6326/AGP/DVD, SIS300/305, SIS630/730, SIS540, SIS315, SIS315H,
    SIS315PRO/E, SIS550, SIS650/M650/651/740, SIS330(Xabre),
    SIS660/[M]661[F|M]X/[M]670/[M]741[GX]/[M]760[GX]/[M]761[GX]/[M]770[GX],
    SIS340
(II) SIS: driver for XGI chipsets: Volari Z7 (XG20),
    Volari V3XT/V5/V8/Duo (XG40)
(II) Primary Device is: PCI 01@00:00:0
(WW) Falling back to old probe method for sis
(WW) SIS: No matching Device section for instance (BusID PCI:0@0:0:0) found
(--) Assigning device section with no busID to primary device
(--) Chipset SIS630/730 found
(II) resource ranges after xf86ClaimFixedResources() call:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [4] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [5] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
(II) resource ranges after probing:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [4] 0    0    0x000a0000 - 0x000affff (0x10000) MS[B]
    [5] 0    0    0x000b0000 - 0x000b7fff (0x8000) MS[B]
    [6] 0    0    0x000b8000 - 0x000bffff (0x8000) MS[B]
    [7] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [8] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
    [9] 0    0    0x000003b0 - 0x000003bb (0xc) IS[B]
    [10] 0    0    0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) SIS(0): SiS driver (2005/09/20-1, compiled for X.org 1.5.99.902)
(II) SIS(0): Copyright (C) 2001-2005 Thomas Winischhofer <thomas@winischhofer.net> and others
(II) SIS(0): *** See http://www.winischhofer.at/linuxsisvga.shtml
(II) SIS(0): *** for documentation and updates.
(--) SIS(0): sisfb not found
(--) SIS(0): Relocated I/O registers at 0xCC80
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(II) SIS(0): Creating default Display subsection in Screen section
    "Default Screen" for depth/fbbpp 24/32
(==) SIS(0): Depth 24, (--) framebuffer bpp 32
(==) SIS(0): RGB weight 888
(==) SIS(0): Default visual is TrueColor
(WW) SIS(0): Could not find/read video BIOS
(==) SIS(0): Using XAA acceleration architecture
(==) SIS(0): Using HW cursor
(==) SIS(0): Color HW cursor is disabled
(==) SIS(0): TurboQueue enabled
(==) SIS(0): Hotkey display switching is disabled
(II) SIS(0): WARNING: Using the Hotkey might freeze your machine, regardless
(II) SIS(0):          whether enabled or disabled. This is no driver bug.
(==) SIS(0): SiSCtrl utility interface is disabled
(II) SIS(0): For information on SiSCtrl, see
        http://www.winischhofer.at/linuxsispart1.shtml#sisctrl
(==) SIS(0): DRI enabled
(II) SIS(0): Checking OS for SSE support is not supported in this version of X.org
(II) SIS(0): If your OS supports SSE, set the option "UseSSE" to "on".
(--) SIS(0): Shared Memory Area is on DIMM0
(--) SIS(0): DRAM type: SDR SDRAM
(--) SIS(0): Memory clock: 100.226 MHz
(--) SIS(0): (Adapter assumes MCLK being 100 Mhz)
(--) SIS(0): DRAM bus width: 64 bit
(--) SIS(0): Linear framebuffer at 0xE0000000
(--) SIS(0): MMIO registers at 0xEFEE0000 (size 64K)
(--) SIS(0): VideoRAM: 16384 KB
(II) SIS(0): Using 8192K of framebuffer memory at offset 0K
(--) SIS(0): Hardware supports two video overlays
(==) SIS(0): Using gamma correction (1.0, 1.0, 1.0)
(II) SIS(0): Gamma correction is enabled
(--) SIS(0): Memory bandwidth at 32 bpp is 200.452 MHz
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(--) SIS(0): CRT1 DDC supported
(--) SIS(0): CRT1 DDC level: 2 
(--) SIS(0): CRT1 DDC monitor info: *******************************************
(II) SIS(0): Manufacturer: OEC  Model: 7a75  Serial#: 0
(II) SIS(0): Year: 2001  Week: 49
(II) SIS(0): EDID Version: 1.2
(II) SIS(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) SIS(0): Sync:  Separate  Composite
(II) SIS(0): Max Image Size [cm]: horiz.: 32  vert.: 24
(II) SIS(0): Gamma: 3.20
(II) SIS(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) SIS(0): redX: 0.625 redY: 0.340   greenX: 0.310 greenY: 0.592
(II) SIS(0): blueX: 0.150 blueY: 0.063   whiteX: 0.281 whiteY: 0.311
(II) SIS(0): Supported VESA Video Modes:
(II) SIS(0): 720x400@70Hz
(II) SIS(0): 720x400@88Hz
(II) SIS(0): 640x480@60Hz
(II) SIS(0): 640x480@67Hz
(II) SIS(0): 640x480@72Hz
(II) SIS(0): 640x480@75Hz
(II) SIS(0): 800x600@56Hz
(II) SIS(0): 800x600@60Hz
(II) SIS(0): 800x600@72Hz
(II) SIS(0): 800x600@75Hz
(II) SIS(0): 832x624@75Hz
(II) SIS(0): 1024x768@87Hz (interlaced)
(II) SIS(0): 1024x768@60Hz
(II) SIS(0): 1024x768@70Hz
(II) SIS(0): 1024x768@75Hz
(II) SIS(0): 1152x870@75Hz
(II) SIS(0): Manufacturer's mask: 0
(II) SIS(0): Supported Future Video Modes:
(II) SIS(0): #0: hsize: 640  vsize 360  refresh: 85  vid: 55601
(II) SIS(0): #1: hsize: 720  vsize 405  refresh: 85  vid: 55611
(II) SIS(0): #3: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) SIS(0): #4: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) SIS(0): #5: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) SIS(0): #6: hsize: 1280  vsize 960  refresh: 60  vid: 16513
(II) SIS(0): #7: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(WW) SIS(0): Unknown vendor-specific block 0
(WW) SIS(0): Unknown vendor-specific block 0
(WW) SIS(0): Unknown vendor-specific block 0
(WW) SIS(0): Unknown vendor-specific block 0
(II) SIS(0): EDID (in hex):
(II) SIS(0):     20fb2c080000000028fb2c080f000000
(II) SIS(0):     88ffffff2190130880fb2c08f45f1e08
(II) SIS(0):     b86fc1bfca160d0880fb2c0801000000
(II) SIS(0):     80fb2c08ec6fc1bfabd41c08001dd4b7
(II) SIS(0):     00000000f45f1e085770c1bf4c000000
(II) SIS(0):     d870c1bfd86fc1bf9de5cdb75d70c1bf
(II) SIS(0):     01000000ffffffff73ad1c08f06fc1bf
(II) SIS(0):     7870c1bf970210085570c1bf01000000
(II) SIS(0): EDID vendor "OEC", prod id 31349
(II) SIS(0): Printing DDC gathered Modelines:
(II) SIS(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) SIS(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) SIS(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) SIS(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) SIS(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) SIS(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) SIS(0): Modeline "720x400"x0.0   35.50  720 738 846 900  400 421 423 449 -hsync -vsync (39.4 kHz)
(II) SIS(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) SIS(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) SIS(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) SIS(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) SIS(0): Modeline "1024x768"x0.0   44.90  1024 1032 1208 1264  768 768 772 817 interlace +hsync +vsync (35.5 kHz)
(II) SIS(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) SIS(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) SIS(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) SIS(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) SIS(0): Modeline "640x360"x85.0   25.77  640 656 720 800  360 361 364 379 -hsync +vsync (32.2 kHz)
(II) SIS(0): Modeline "720x405"x85.0   33.02  720 744 816 912  405 406 409 426 -hsync +vsync (36.2 kHz)
(II) SIS(0): Modeline "800x600"x0.0   56.25  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
(II) SIS(0): Modeline "1024x768"x0.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
(II) SIS(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) SIS(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
(II) SIS(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(--) SIS(0): End of CRT1 DDC monitor info *************************************
(==) SIS(0): Min pixel clock is 10 MHz
(--) SIS(0): Max pixel clock is 139 MHz
(II) SIS(0): Replaced default mode list with built-in modes
(II) SIS(0): "Unknown reason" in the following list means that the mode
(II) SIS(0): is not supported on the chipset/bridge/current output device.
(II) SIS(0): Configured Monitor: Using hsync range of 31.47-68.68 kHz
(II) SIS(0): Configured Monitor: Using vrefresh range of 43.48-87.85 Hz
(II) SIS(0): Estimated virtual size for aspect ratio 1.3333 is 1280x960
(II) SIS(0): Clock range:  10.00 to 139.09 MHz
(II) SIS(0): Not using driver mode "1280x1024" (height too large for virtual size)
(II) SIS(0): Not using default mode "800x600" (vrefresh out of range)
(II) SIS(0): Not using default mode "800x600" (hsync out of range)
(II) SIS(0): Not using default mode "800x600" (hsync out of range)
(II) SIS(0): Not using default mode "640x480" (vrefresh out of range)
(II) SIS(0): Not using default mode "640x480" (vrefresh out of range)
(II) SIS(0): Not using default mode "640x480" (hsync out of range)
(II) SIS(0): Not using default mode "640x480" (hsync out of range)
(II) SIS(0): Not using default mode "1024x768" (hsync out of range)
(II) SIS(0): Not using default mode "1024x768" (hsync out of range)
(II) SIS(0): Not using default mode "1280x1024" (height too large for virtual size)
(II) SIS(0): Not using default mode "1280x1024" (height too large for virtual size)
(II) SIS(0): Not using default mode "1280x1024" (height too large for virtual size)
(II) SIS(0): Not using default mode "1280x1024" (height too large for virtual size)
(II) SIS(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) SIS(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) SIS(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) SIS(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) SIS(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) SIS(0): Not using default mode "1920x1440" (width too large for virtual size)
(II) SIS(0): Not using default mode "2048x1536" (width too large for virtual size)
(II) SIS(0): Not using default mode "1280x960" (bad mode clock/interlace/doublescan)
(II) SIS(0): Not using default mode "1024x576" (hsync out of range)
(II) SIS(0): Not using default mode "1280x720" (hsync out of range)
(II) SIS(0): Not using default mode "1280x720" (bad mode clock/interlace/doublescan)
(II) SIS(0): Not using default mode "1152x864" (hsync out of range)
(II) SIS(0): Not using default mode "848x480" (hsync out of range)
(II) SIS(0): Not using default mode "848x480" (hsync out of range)
(II) SIS(0): Not using default mode "856x480" (hsync out of range)
(II) SIS(0): Not using default mode "1360x768" (width too large for virtual size)
(II) SIS(0): Not using default mode "1360x1024" (width too large for virtual size)
(--) SIS(0): Virtual size is 1280x960 (pitch 1280)
(**) SIS(0): *Driver mode "1280x960": 108.0 MHz, 60.0 kHz, 60.0 Hz
(II) SIS(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
(**) SIS(0): *Default mode "1280x960": 108.2 MHz, 60.1 kHz, 60.1 Hz
(II) SIS(0): Modeline "1280x960"x60.1  108.18  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.1 kHz)
(**) SIS(0): *Driver mode "1152x864": 108.0 MHz, 67.5 kHz, 75.0 Hz
(II) SIS(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(**) SIS(0): *Driver mode "1152x864": 108.0 MHz, 67.5 kHz, 75.0 Hz
(II) SIS(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(**) SIS(0): *Default mode "1152x864": 108.3 MHz, 67.7 kHz, 75.2 Hz
(II) SIS(0): Modeline "1152x864"x75.2  108.28  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.7 kHz)
(**) SIS(0): *Default mode "1152x864": 89.9 MHz, 53.5 kHz, 60.0 Hz
(II) SIS(0): Modeline "1152x864"x60.0   89.89  1152 1216 1472 1680  864 869 877 892 +hsync +vsync (53.5 kHz)
(**) SIS(0): *Default mode "1280x768": 80.9 MHz, 47.9 kHz, 59.8 Hz
(II) SIS(0): Modeline "1280x768"x59.8   80.90  1280 1328 1440 1688  768 772 777 802 +hsync +vsync (47.9 kHz)
(**) SIS(0): *Default mode "1280x720": 107.9 MHz, 63.9 kHz, 59.9 Hz
(II) SIS(0): Modeline "1280x720"x59.9  107.86  1280 1328 1440 1688  720 891 895 1066 +hsync +vsync (63.9 kHz)
(**) SIS(0): *Default mode "1152x768": 75.2 MHz, 51.1 kHz, 63.4 Hz
(II) SIS(0): Modeline "1152x768"x63.4   75.17  1152 1176 1184 1472  768 771 777 806 -hsync -vsync (51.1 kHz)
(**) SIS(0): *Driver mode "1024x768": 94.5 MHz, 68.7 kHz, 85.0 Hz
(II) SIS(0): Modeline "1024x768"x85.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
(**) SIS(0): *Driver mode "1024x768": 78.8 MHz, 60.0 kHz, 75.0 Hz
(II) SIS(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(**) SIS(0): *Driver mode "1024x768": 75.0 MHz, 56.5 kHz, 70.1 Hz
(II) SIS(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(**) SIS(0): *Driver mode "1024x768": 65.0 MHz, 48.4 kHz, 60.0 Hz
(II) SIS(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(**) SIS(0): *Driver mode "1024x768": 44.9 MHz, 35.5 kHz, 43.5 Hz (I)
(II) SIS(0): Modeline "1024x768"x43.5   44.90  1024 1032 1208 1264  768 768 772 817 interlace +hsync +vsync (35.5 kHz)
(**) SIS(0): *Default mode "1024x768": 94.5 MHz, 68.7 kHz, 85.0 Hz
(II) SIS(0): Modeline "1024x768"x85.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
(**) SIS(0): *Default mode "1024x768": 78.7 MHz, 60.0 kHz, 75.0 Hz
(II) SIS(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(**) SIS(0): *Default mode "1024x768": 75.2 MHz, 56.6 kHz, 70.2 Hz
(II) SIS(0): Modeline "1024x768"x70.2   75.17  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.6 kHz)
(**) SIS(0): *Default mode "1024x768": 65.1 MHz, 48.5 kHz, 60.1 Hz
(II) SIS(0): Modeline "1024x768"x60.1   65.15  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.5 kHz)
(**) SIS(0): *Default mode "1024x768": 44.9 MHz, 35.5 kHz, 86.8 Hz (I)
(II) SIS(0): Modeline "1024x768"x86.8   44.86  1024 1032 1208 1264  768 768 776 817 interlace +hsync +vsync (35.5 kHz)
(**) SIS(0): *Default mode "1024x600": 65.1 MHz, 48.5 kHz, 60.6 Hz
(II) SIS(0): Modeline "1024x600"x60.6   65.15  1024 1048 1184 1344  600 687 694 800 -hsync -vsync (48.5 kHz)
(**) SIS(0): *Default mode "1024x576": 78.7 MHz, 60.0 kHz, 75.0 Hz
(II) SIS(0): Modeline "1024x576"x75.0   78.75  1024 1040 1136 1312  576 686 690 800 +hsync +vsync (60.0 kHz)
(**) SIS(0): *Default mode "1024x576": 65.1 MHz, 48.5 kHz, 60.1 Hz
(II) SIS(0): Modeline "1024x576"x60.1   65.15  1024 1048 1184 1344  576 688 694 806 +hsync +vsync (48.5 kHz)
(**) SIS(0): *Driver mode "832x624": 57.3 MHz, 49.7 kHz, 74.6 Hz
(II) SIS(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(**) SIS(0): *Driver mode "800x600": 56.2 MHz, 53.7 kHz, 85.1 Hz
(II) SIS(0): Modeline "800x600"x85.1   56.25  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
(**) SIS(0): *Driver mode "800x600": 49.5 MHz, 46.9 kHz, 75.0 Hz
(II) SIS(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(**) SIS(0): *Driver mode "800x600": 50.0 MHz, 48.1 kHz, 72.2 Hz
(II) SIS(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(**) SIS(0): *Driver mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
(II) SIS(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(**) SIS(0): *Driver mode "800x600": 36.0 MHz, 35.2 kHz, 56.2 Hz
(II) SIS(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(**) SIS(0): *Default mode "800x600": 56.2 MHz, 53.7 kHz, 85.1 Hz
(II) SIS(0): Modeline "800x600"x85.1   56.25  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
(**) SIS(0): *Default mode "800x600": 49.5 MHz, 46.9 kHz, 75.0 Hz
(II) SIS(0): Modeline "800x600"x75.0   49.52  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(**) SIS(0): *Default mode "800x600": 50.1 MHz, 48.2 kHz, 72.4 Hz
(II) SIS(0): Modeline "800x600"x72.4   50.11  800 856 976 1040  600 637 643 666 +hsync +vsync (48.2 kHz)
(**) SIS(0): *Default mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
(II) SIS(0): Modeline "800x600"x60.3   39.97  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(**) SIS(0): *Default mode "800x600": 36.1 MHz, 35.2 kHz, 56.3 Hz
(II) SIS(0): Modeline "800x600"x56.3   36.06  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(**) SIS(0): *Default mode "768x576": 35.0 MHz, 35.9 kHz, 60.1 Hz
(II) SIS(0): Modeline "768x576"x60.1   35.00  768 792 872 976  576 578 581 597 +hsync +vsync (35.9 kHz)
(**) SIS(0): *Default mode "720x576": 32.7 MHz, 35.9 kHz, 60.1 Hz
(II) SIS(0): Modeline "720x576"x60.1   32.73  720 744 816 912  576 578 581 597 +hsync +vsync (35.9 kHz)
(**) SIS(0): *Default mode "856x480": 33.9 MHz, 31.7 kHz, 59.8 Hz
(II) SIS(0): Modeline "856x480"x59.8   33.94  856 872 1000 1072  480 492 495 529 -hsync -vsync (31.7 kHz)
(**) SIS(0): *Default mode "800x480": 56.2 MHz, 53.7 kHz, 85.2 Hz
(II) SIS(0): Modeline "800x480"x85.2   56.25  800 832 896 1048  480 554 557 630 +hsync +vsync (53.7 kHz)
(**) SIS(0): *Default mode "800x480": 49.5 MHz, 46.9 kHz, 75.1 Hz
(II) SIS(0): Modeline "800x480"x75.1   49.52  800 816 896 1056  480 551 554 624 +hsync +vsync (46.9 kHz)
(**) SIS(0): *Default mode "800x480": 39.8 MHz, 37.7 kHz, 60.0 Hz
(II) SIS(0): Modeline "800x480"x60.0   39.77  800 840 968 1056  480 552 556 628 +hsync +vsync (37.7 kHz)
(**) SIS(0): *Default mode "720x480": 28.3 MHz, 31.6 kHz, 61.0 Hz
(II) SIS(0): Modeline "720x480"x61.0   28.28  720 728 840 896  480 490 492 517 -hsync -vsync (31.6 kHz)
(**) SIS(0): *Driver mode "640x480": 31.5 MHz, 37.5 kHz, 75.0 Hz
(II) SIS(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(**) SIS(0): *Driver mode "640x480": 31.5 MHz, 37.9 kHz, 72.8 Hz
(II) SIS(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(**) SIS(0): *Driver mode "640x480": 30.2 MHz, 35.0 kHz, 66.7 Hz
(II) SIS(0): Modeline "640x480"x66.7   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(**) SIS(0): *Driver mode "640x480": 25.2 MHz, 31.5 kHz, 59.9 Hz
(II) SIS(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(**) SIS(0): *Default mode "640x480": 36.1 MHz, 43.3 kHz, 85.1 Hz
(II) SIS(0): Modeline "640x480"x85.1   36.06  640 696 752 832  480 481 484 509 -hsync -vsync (43.3 kHz)
(**) SIS(0): *Default mode "640x480": 31.5 MHz, 37.5 kHz, 75.0 Hz
(II) SIS(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(**) SIS(0): *Default mode "640x480": 31.5 MHz, 37.9 kHz, 72.8 Hz
(II) SIS(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz)
(**) SIS(0): *Default mode "640x480": 25.1 MHz, 31.3 kHz, 59.7 Hz
(II) SIS(0): Modeline "640x480"x59.7   25.06  640 656 752 800  480 490 492 525 -hsync -vsync (31.3 kHz)
(**) SIS(0): *Driver mode "720x405": 33.0 MHz, 36.2 kHz, 85.0 Hz
(II) SIS(0): Modeline "720x405"x85.0   33.02  720 744 816 912  405 406 409 426 -hsync +vsync (36.2 kHz)
(**) SIS(0): *Driver mode "720x400": 35.5 MHz, 39.4 kHz, 87.8 Hz
(II) SIS(0): Modeline "720x400"x87.8   35.50  720 738 846 900  400 421 423 449 -hsync -vsync (39.4 kHz)
(**) SIS(0): *Driver mode "720x400": 28.3 MHz, 31.5 kHz, 70.1 Hz
(II) SIS(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(**) SIS(0): *Default mode "640x400": 25.1 MHz, 31.6 kHz, 71.6 Hz
(II) SIS(0): Modeline "640x400"x71.6   25.06  640 656 752 792  400 413 415 442 -hsync +vsync (31.6 kHz)
(**) SIS(0): *Driver mode "640x360": 25.8 MHz, 32.2 kHz, 85.0 Hz
(II) SIS(0): Modeline "640x360"x85.0   25.77  640 656 720 800  360 361 364 379 -hsync +vsync (32.2 kHz)
(**) SIS(0): *Default mode "512x384": 32.6 MHz, 48.5 kHz, 60.1 Hz (D)
(II) SIS(0): Modeline "512x384"x60.1   32.57  512 528 592 672  384 385 388 403 doublescan -hsync -vsync (48.5 kHz)
(**) SIS(0): *Default mode "400x300": 20.0 MHz, 37.9 kHz, 60.3 Hz (D)
(II) SIS(0): Modeline "400x300"x60.3   19.98  400 416 480 528  300 300 302 314 doublescan +hsync +vsync (37.9 kHz)
(**) SIS(0): *Default mode "320x240": 12.5 MHz, 31.3 kHz, 60.7 Hz (D)
(II) SIS(0): Modeline "320x240"x60.7   12.53  320 328 376 400  240 245 246 258 doublescan -hsync -vsync (31.3 kHz)
(**) SIS(0): *Default mode "320x200": 12.5 MHz, 31.3 kHz, 70.9 Hz (D)
(II) SIS(0): Modeline "320x200"x70.9   12.53  320 328 376 400  200 206 207 221 doublescan -hsync +vsync (31.3 kHz)
(**) SIS(0): Display dimensions: (320, 240) mm
(**) SIS(0): DPI set to (101, 101)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 1.2.1
    ABI class: X.Org Video Driver, version 5.0
(II) SIS(0): 2D acceleration enabled
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [4] 0    0    0x000a0000 - 0x000affff (0x10000) MS[B](OprU)
    [5] 0    0    0x000b0000 - 0x000b7fff (0x8000) MS[B](OprU)
    [6] 0    0    0x000b8000 - 0x000bffff (0x8000) MS[B](OprU)
    [7] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [8] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
    [9] 0    0    0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
    [10] 0    0    0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 1.1.0
    ABI class: X.Org Video Driver, version 5.0
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 1.0.0
    ABI class: X.Org Video Driver, version 5.0
(II) SIS(0): initializing int10
(II) SIS(0): Primary V_BIOS segment is: 0xc000
(II) SIS(0): VESA BIOS detected
(II) SIS(0): VESA VBE Version 3.0
(II) SIS(0): VESA VBE Total Mem: 16384 kB
(II) SIS(0): VESA VBE OEM: 
(II) SIS(0): VESA VBE OEM Software Rev: 1.0
(II) SIS(0): VESA VBE OEM Vendor: 
(II) SIS(0): VESA VBE OEM Product: 
(II) SIS(0): VESA VBE OEM Product Rev: 
(II) SIS(0): Setting custom mode 1280x960 on CRT1
(II) SIS(0): Setting custom mode 1280x960 on CRT2
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: node name is /dev/dri/card0
drmOpenByBusid: Searching for BusID pci:0000:01:00.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 9, (OK)
drmOpenByBusid: drmOpenMinor returns 9
drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
(II) [drm] loaded kernel module for "sis" driver.
(II) [drm] DRM interface version 1.3
(II) [drm] DRM open master succeeded.
(II) SIS(0): [drm] Using the DRM lock SAREA also for drawables.
(II) SIS(0): [drm] framebuffer handle = 0xe0000000
(II) SIS(0): [drm] added 1 reserved context for kernel
(II) SIS(0): X context handle = 0x1
(II) SIS(0): [drm] installed DRM signal handler
(II) SIS(0): [dri] Video RAM memory heap: 0x800000 to 0xf7f000 (7676KB)
(II) SIS(0): [drm] MMIO registers mapped to 0xefee0000
(II) SIS(0): [drm] AGP enabled
(II) SIS(0): [drm] Allocated 8MB AGP memory
(II) SIS(0): [drm] Bound 8MB AGP memory
(II) SIS(0): [drm] No valid IRQ number for device 1:0:0 (code -22)
(II) SIS(0): [dri] Visual configs initialized
(II) SIS(0): Framebuffer from (0,0) to (1279,1635)
(II) SIS(0): Using XFree86 Acceleration Architecture (XAA)
    Screen to screen bit blits
    Solid filled rectangles
    8x8 mono pattern filled rectangles
    Indirect CPU to Screen color expansion
    Solid Lines
    Dashed Lines
    Setting up tile and stipple cache:
        26 128x128 slots
        6 256x256 slots
(--) SIS(0): CPU frequency 1002.22Mhz
(II) SIS(0): Benchmarking system RAM to video RAM memory transfer methods:
(--) SIS(0):     Checked libc memcpy()...     57.6 MiB/s
(--) SIS(0):     Checked built-in-1 memcpy()...     57.7 MiB/s
(--) SIS(0):     Checked built-in-2 memcpy()...     21.5 MiB/s
(--) SIS(0):     Checked MMX memcpy()...     34.2 MiB/s
(--) SIS(0):     Checked MMX2 memcpy()...     63.4 MiB/s
(--) SIS(0): Using MMX2 method for aligned data transfers to video RAM
(--) SIS(0): Using MMX2 method for unaligned data transfers to video RAM
(==) SIS(0): Backing store disabled
(==) SIS(0): Silken mouse enabled
(II) SIS(0): DPMS enabled
(II) SIS(0): Using SiS300/315/330/340 series HW Xv
(II) SIS(0): [DRI] installation complete
(II) SIS(0): Direct rendering enabled
(II) SIS(0): Initialized SISCTRL extension version 0.1
(II) SIS(0): Registered screen 0 with SISCTRL extension version 0.1
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
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 10, (OK)
drmOpenByBusid: Searching for BusID pci:0000:01:00.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 10, (OK)
drmOpenByBusid: drmOpenMinor returns 10
drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
(II) AIGLX: Loaded and initialized /usr/lib/dri/sis_dri.so
(II) GLX: Initialized DRI GL provider for screen 0
(II) config/hal: Adding input device AT Translated Set 2 keyboard
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 2.1.1
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 4.0
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event1"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) AT Translated Set 2 keyboard: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) AT Translated Set 2 keyboard: xkb_model: "pc105"
(**) Option "xkb_layout" "ca"
(**) AT Translated Set 2 keyboard: xkb_layout: "ca"
(**) Option "xkb_variant" "fr-legacy"
(**) AT Translated Set 2 keyboard: xkb_variant: "fr-legacy"
(II) config/hal: Adding input device Macintosh mouse button emulation
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event0"
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
(II) config/hal: Adding input device ImPS/2 Logitech Wheel Mouse
(**) ImPS/2 Logitech Wheel Mouse: always reports core events
(**) ImPS/2 Logitech Wheel Mouse: Device: "/dev/input/event3"
(II) ImPS/2 Logitech Wheel Mouse: Found 3 mouse buttons
(II) ImPS/2 Logitech Wheel Mouse: Found x and y relative axes
(II) ImPS/2 Logitech Wheel Mouse: Configuring as mouse
(**) ImPS/2 Logitech Wheel Mouse: YAxisMapping: buttons 4 and 5
(**) ImPS/2 Logitech Wheel Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "ImPS/2 Logitech Wheel Mouse" (type: MOUSE)
(**) ImPS/2 Logitech Wheel Mouse: (accel) keeping acceleration scheme 1
(**) ImPS/2 Logitech Wheel Mouse: (accel) filter chain progression: 2.00
(**) ImPS/2 Logitech Wheel Mouse: (accel) filter stage 0: 20.00 ms
(**) ImPS/2 Logitech Wheel Mouse: (accel) set acceleration profile 0
(II) SIS(0): Setting custom mode 1024x768 on CRT1
(II) SIS(0): Setting custom mode 1024x768 on CRT2
```

Sometimes, I look down and find I'm good with computers. I just need to look again at the top of the mountain and I see my ascension just begins!!! :)

---

### Post by kerry_s on 2009-11-02
it's using the sis driver so lets check if its a driver problem.

press: **alt+f2**
type: **gksudo gedit /etc/X11/xorg.conf**

in the device section your going to add a line:

```
Section "Device"
	Identifier	"Configured Video Device"
**        Driver          "vesa"**
EndSection
```

then log out & back in, to see how it runs with generic drivers.

---

### Post by gahute on 2009-11-02
I just changed the refresh rate from 85Hz to 60Hz and I think it help a little bit...

---

### Post by gahute on 2009-11-02
I think it's worse!
By the way, I changed many times the resolution and when I log back, it returns always to the maximum resolution of 1280 x 1024...

---

### Post by kerry_s on 2009-11-02
then just remove that line & logout again it will go back to the sis driver.

---

### Post by gahute on 2009-11-02
Done.
As I said, the resolution always get back to the maximum resolution in the list.

Thanks again!

---

### Post by gahute on 2009-11-02
Should I understand my problem can't be resolved simply?

---

### Post by Jerry N on 2009-11-02
My experience so far indicates that Xubuntu is no faster than Ubuntu.  Further, on the same computer I find little significant difference in speed between Win XP and Ubuntu.  In both cases, I have disabled all the video "effects" that I can get a handle on.  

Others will disagree but that is my experience. I have tried many Linux variations and haven't found anything much that works much better than Ubuntu except for the somewhat limited memory resident systems like Puppy and DSL.  

For your machine you definitely want to disable all "eye candy".

Jerry

---

### Post by gahute on 2009-11-03
Jerry N,

Can you tell me all the places in the system I can disable them? Is it only in the display menu?

Thank you,

---

### Post by Jerry N on 2009-11-03
I set the "no effects" button in the display menu in Ubuntu.  It has been several week since the last time I tried Xubuntu but it is probably the same.

---

