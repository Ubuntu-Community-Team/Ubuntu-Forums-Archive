---
title: "Interesting Video Issue"
date: 2009-10-01
forum: New to Ubuntu
---

### Post by ncc1701e on 2009-10-01
I just installed Ubuntu 9.04 on an older machine and cannot seem to get it to work at the resolution that this machine is capable of offering in windows. The specs of the machine are:

IBM Aptiva Intel Pentium II 300 MHZ
6GB HD
224 MB RAM
Monitor is Envision En-775e (17 inch)

Resolutions available to me are:

832x624 (4:32) thru 320x175 (9:5)
and some in between those two have a (16:10) ratio

I used to get 1024x768 with windows. I'd like to get this resolution back in Ubuntu if possible. I am new to linux and will attempt to provide below the information that I think is helpful to anyone who tries to help me. Thank you.

Here is the output of lspci:

00:00.0 Host bridge: Intel Corporation 440LX/EX - 82443LX/EX Host bridge (rev 03)
00:01.0 PCI bridge: Intel Corporation 440LX/EX - 82443LX/EX AGP bridge (rev 03)
00:07.0 ISA bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 01)
00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 01)
00:0b.0 Ethernet controller: Accton Technology Corporation EN-1216 Ethernet Adapter (rev 11)
00:12.0 Multimedia audio controller: Cirrus Logic CS 4610/11 [CrystalClear SoundFusion Audio Accelerator] (rev 01)
01:00.0 VGA compatible controller: ATI Technologies Inc 3D Rage Pro AGP 1X/2X (rev 5c)


Here is the /var/log/Xorg.0.log file:


X.Org X Server 1.6.0
Release Date: 2009-2-25
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux mercury 2.6.28-15-generic #52-Ubuntu SMP Wed Sep 9 10:49:34 UTC 2009 i686
Build Date: 09 April 2009  02:10:02AM
xorg-server 2:1.6.0-0ubuntu14 (buildd@rothera.buildd) 
    Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Thu Oct  1 09:37:00 2009
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

(--) PCI:*(0@1:0:0) ATI Technologies Inc 3D Rage Pro AGP 1X/2X rev 92, Mem @ 0x21000000/16777216, 0x20000000/4096, I/O @ 0x00002000/256, BIOS @ 0x????????/131072
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
(II) Matched mach64 from file name mach64.ids
(==) Matched mach64 for the autoconfigured driver
(==) Assigned the driver to the xf86ConfigLayout
(II) LoadModule: "mach64"
(II) Loading /usr/lib/xorg/modules/drivers//mach64_drv.so
(II) Module mach64: vendor="X.Org Foundation"
    compiled for 1.5.99.3, module version = 6.8.0
    Module class: X.Org Video Driver
    ABI class: X.Org Video Driver, version 5.0
(II) MACH64: Driver for ATI Mach64 chipsets
(II) Primary Device is: PCI 01@00:00:0
(II) resource ranges after probing:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [4] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [5] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
(II) MACH64(0): Creating default Display subsection in Screen section
    "Default Screen" for depth/fbbpp 24/32
(==) MACH64(0): Depth 24, (--) framebuffer bpp 32
(==) MACH64(0): Using XAA acceleration architecture
(II) MACH64: Mach64 in slot 1:0:0 detected.
(II) resource ranges after xf86ClaimFixedResources() call:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [4] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [5] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 1.0.0
    ABI class: X.Org Video Driver, version 5.0
(II) MACH64(0): Bad V_BIOS checksum
(II) MACH64(0): Primary V_BIOS segment is: 0xc000
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 1.1.0
    ABI class: X.Org Video Driver, version 5.0
(II) MACH64(0): VESA BIOS detected
(II) MACH64(0): VESA VBE Version 2.0
(II) MACH64(0): VESA VBE Total Mem: 2048 kB
(II) MACH64(0): VESA VBE OEM: ATI MACH64
(II) MACH64(0): VESA VBE OEM Software Rev: 1.0
(II) MACH64(0): VESA VBE OEM Vendor: ATI Technologies Inc.
(II) MACH64(0): VESA VBE OEM Product: MACH64GT
(II) MACH64(0): VESA VBE OEM Product Rev: 01.00
(II) MACH64(0): VESA VBE DDC supported
(II) MACH64(0): VESA VBE DDC Level 2
(II) MACH64(0): VESA VBE DDC transfer in appr. 2 sec.
(II) MACH64(0): VESA VBE DDC read successfully
(II) MACH64(0): Manufacturer: EPI  Model: d775  Serial#: 693567
(II) MACH64(0): Year: 2004  Week: 2
(II) MACH64(0): EDID Version: 1.3
(II) MACH64(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) MACH64(0): Sync:  Separate
(II) MACH64(0): Max Image Size [cm]: horiz.: 32  vert.: 24
(II) MACH64(0): Gamma: 2.20
(II) MACH64(0): DPMS capabilities: Off; RGB/Color Display
(II) MACH64(0): First detailed timing is preferred mode
(II) MACH64(0): redX: 0.631 redY: 0.329   greenX: 0.276 greenY: 0.600
(II) MACH64(0): blueX: 0.143 blueY: 0.057   whiteX: 0.283 whiteY: 0.297
(II) MACH64(0): Supported VESA Video Modes:
(II) MACH64(0): 720x400@70Hz
(II) MACH64(0): 640x480@60Hz
(II) MACH64(0): 640x480@75Hz
(II) MACH64(0): 800x600@75Hz
(II) MACH64(0): 1024x768@75Hz
(II) MACH64(0): Manufacturer's mask: 0
(II) MACH64(0): Supported Future Video Modes:
(II) MACH64(0): #0: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) MACH64(0): #1: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) MACH64(0): #2: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) MACH64(0): #3: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) MACH64(0): Supported additional Video Mode:
(II) MACH64(0): clock: 94.5 MHz   Image Size:  310 x 230 mm
(II) MACH64(0): h_active: 1024  h_sync: 1072  h_sync_end 1168 h_blank_end 1376 h_border: 0
(II) MACH64(0): v_active: 768  v_sync: 769  v_sync_end 772 v_blanking: 808 v_border: 0
(II) MACH64(0): Supported additional Video Mode:
(II) MACH64(0): clock: 56.2 MHz   Image Size:  310 x 230 mm
(II) MACH64(0): h_active: 800  h_sync: 832  h_sync_end 896 h_blank_end 1048 h_border: 0
(II) MACH64(0): v_active: 600  v_sync: 601  v_sync_end 604 v_blanking: 631 v_border: 0
(II) MACH64(0): Monitor name: EN-775e
(II) MACH64(0): Ranges: V min: 50 V max: 160 Hz, H min: 30 H max: 72 kHz, PixClock max 110 MHz
(II) MACH64(0): EDID (in hex):
(II) MACH64(0):     00ffffffffffff00160975d73f950a00
(II) MACH64(0):     020e0103682018782a9ea8a154469924
(II) MACH64(0):     0e484ca4420031594559615981800101
(II) MACH64(0):     010101010101ea240060410028303060
(II) MACH64(0):     130036e61000001ef91520f830581f20
(II) MACH64(0):     2040130036e61000001e000000fc0045
(II) MACH64(0):     4e2d373735650a2020202020000000fd
(II) MACH64(0):     0032a01e480b000a20202020202000a0
(II) MACH64(0): EDID vendor "EPI", prod id 55157
(II) MACH64(0): Using EDID range info for horizontal sync
(II) MACH64(0): Using EDID range info for vertical refresh
(II) MACH64(0): Printing DDC gathered Modelines:
(II) MACH64(0): Modeline "1024x768"x0.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
(II) MACH64(0): Modeline "800x600"x0.0   56.25  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
(II) MACH64(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) MACH64(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) MACH64(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) MACH64(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) MACH64(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) MACH64(0): Modeline "640x480"x0.0   36.00  640 696 752 832  480 481 484 509 -hsync -vsync (43.3 kHz)
(II) MACH64(0): Modeline "800x600"x0.0   56.25  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
(II) MACH64(0): Modeline "1024x768"x0.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
(II) MACH64(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) MACH64(0): BIOS Data:  BIOSSize=0xC000, ROMTable=0x00E2.
(II) MACH64(0): BIOS Data:  ClockTable=0x0898, FrequencyTable=0x0000.
(II) MACH64(0): BIOS Data:  LCDTable=0x0000.
(II) MACH64(0): BIOS Data:  VideoTable=0x0000, HardwareTable=0x012C.
(II) MACH64(0): BIOS Data:  I2CType=0x02, Tuner=0x00, Decoder=0x00, Audio=0x0F.
(--) MACH64(0): ATI 3D Rage Pro graphics controller detected.
(--) MACH64(0): Chip type 4742 "GB", version 4, foundry UMC, class 0, revision 0x01.
(--) MACH64(0): AGP bus interface detected;  block I/O base is 0x2000.
(--) MACH64(0): ATI Mach64 adapter detected.
(!!) MACH64(0): For information on using the multimedia capabilities
    of this adapter, please see [http://gatos.sf.net](http://gatos.sf.net).
(--) MACH64(0): Internal RAMDAC (subtype 1) detected.
(==) MACH64(0): RGB weight 888
(==) MACH64(0): Default visual is TrueColor
(==) MACH64(0): Using gamma correction (1.0, 1.0, 1.0)
(II) MACH64(0): Using Mach64 accelerator CRTC.
(WW) MACH64(0): Logic error setting operating state for VGA I/O.
(II) MACH64(0): Storing hardware cursor image at 0x211FFC00.
(II) MACH64(0): Using 8 MB linear aperture at 0x21000000.
(!!) MACH64(0): Virtual resolutions will be limited to 2047 kB
 due to linear aperture size and/or placement of hardware cursor image area.
(II) MACH64(0): Using Block 0 MMIO aperture at 0x20000400.
(II) MACH64(0): Using Block 1 MMIO aperture at 0x20000000.
(WW) MACH64(0): Logic error setting operating state for VGA memory aperture.
(II) MACH64(0): MMIO write caching enabled.
(--) MACH64(0): 2048 kB of SGRAM (1:1) detected (using 2047 kB).
(WW) MACH64(0): Cannot shadow an accelerated frame buffer.
(II) MACH64(0): Engine XCLK 99.765 MHz;  Refresh rate code 7.
(--) MACH64(0): Internal programmable clock generator detected.
(--) MACH64(0): Reference clock 157.5/11 (14.318) MHz.
(II) MACH64(0): Configured Monitor: Using hsync range of 30.00-72.00 kHz
(II) MACH64(0): Configured Monitor: Using vrefresh range of 50.00-160.00 Hz
(II) MACH64(0): Configured Monitor: Using maximum pixel clock of 110.00 MHz
(II) MACH64(0): Estimated virtual size for aspect ratio 1.3333 is 1024x768
(II) MACH64(0): Maximum clock: 199.00 MHz
(II) MACH64(0): Not using default mode "1024x768" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "1024x768" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "1024x768" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "1024x768" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "1024x768" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "1152x864" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "1280x960" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "1280x960" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "640x480" (hsync out of range)
(II) MACH64(0): Not using default mode "1280x1024" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "1280x1024" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "640x512" (hsync out of range)
(II) MACH64(0): Not using default mode "1280x1024" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "640x512" (hsync out of range)
(II) MACH64(0): Not using default mode "1600x1200" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "800x600" (hsync out of range)
(II) MACH64(0): Not using default mode "1600x1200" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "800x600" (hsync out of range)
(II) MACH64(0): Not using default mode "1600x1200" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "800x600" (hsync out of range)
(II) MACH64(0): Not using default mode "1600x1200" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "800x600" (hsync out of range)
(II) MACH64(0): Not using default mode "1600x1200" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "800x600" (hsync out of range)
(II) MACH64(0): Not using default mode "1792x1344" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "896x672" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "1792x1344" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "896x672" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "1856x1392" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "928x696" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "1856x1392" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "928x696" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "1920x1440" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "960x720" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "1920x1440" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "960x720" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "1152x864" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "1152x864" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "1152x864" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "1152x864" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "576x432" (hsync out of range)
(II) MACH64(0): Not using default mode "1152x864" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "576x432" (hsync out of range)
(II) MACH64(0): Not using default mode "1152x864" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "576x432" (hsync out of range)
(II) MACH64(0): Not using default mode "1360x768" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "1360x768" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "1400x1050" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "1400x1050" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "700x525" (hsync out of range)
(II) MACH64(0): Not using default mode "1400x1050" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "700x525" (hsync out of range)
(II) MACH64(0): Not using default mode "1400x1050" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "700x525" (hsync out of range)
(II) MACH64(0): Not using default mode "1440x900" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "1600x1024" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "1680x1050" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "1680x1050" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "1680x1050" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "840x525" (hsync out of range)
(II) MACH64(0): Not using default mode "1680x1050" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "840x525" (hsync out of range)
(II) MACH64(0): Not using default mode "1680x1050" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "840x525" (hsync out of range)
(II) MACH64(0): Not using default mode "1920x1080" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "1920x1200" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "960x600" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "1920x1440" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "960x720" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "2048x1536" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "1024x768" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "2048x1536" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "1024x768" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "2048x1536" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "1024x768" (insufficient memory for mode)
(II) MACH64(0): Not using driver mode "1024x768" (insufficient memory for mode)
(II) MACH64(0): Not using driver mode "1024x768" (insufficient memory for mode)
(II) MACH64(0): Not using driver mode "1024x768" (insufficient memory for mode)
(II) MACH64(0): Not using driver mode "1280x1024" (insufficient memory for mode)
(WW) MACH64(0): Shrinking virtual size estimate from 1024x768 to 832x624
(--) MACH64(0): Virtual size is 832x624 (pitch 832)
(**) MACH64(0): *Default mode "832x624": 57.3 MHz, 49.7 kHz, 74.6 Hz
(II) MACH64(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(**) MACH64(0): *Driver mode "800x600": 56.2 MHz, 53.7 kHz, 85.1 Hz
(II) MACH64(0): Modeline "800x600"x85.1   56.25  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
(**) MACH64(0): *Driver mode "800x600": 56.2 MHz, 53.7 kHz, 85.1 Hz
(II) MACH64(0): Modeline "800x600"x85.1   56.25  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
(**) MACH64(0): *Driver mode "800x600": 49.5 MHz, 46.9 kHz, 75.0 Hz
(II) MACH64(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(**) MACH64(0): *Default mode "800x600": 56.3 MHz, 53.7 kHz, 85.1 Hz
(II) MACH64(0): Modeline "800x600"x85.1   56.30  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
(**) MACH64(0): *Default mode "800x600": 49.5 MHz, 46.9 kHz, 75.0 Hz
(II) MACH64(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(**) MACH64(0): *Default mode "800x600": 50.0 MHz, 48.1 kHz, 72.2 Hz
(II) MACH64(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(**) MACH64(0): *Default mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
(II) MACH64(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(**) MACH64(0): *Default mode "800x600": 36.0 MHz, 35.2 kHz, 56.2 Hz
(II) MACH64(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(**) MACH64(0): *Default mode "840x525": 73.1 MHz, 65.3 kHz, 60.0 Hz (D)
(II) MACH64(0): Modeline "840x525"x60.0   73.12  840 892 980 1120  525 526 529 544 doublescan -hsync +vsync (65.3 kHz)
(**) MACH64(0): *Default mode "700x525": 61.0 MHz, 64.9 kHz, 60.0 Hz (D)
(II) MACH64(0): Modeline "700x525"x60.0   61.00  700 744 820 940  525 526 532 541 doublescan +hsync +vsync (64.9 kHz)
(**) MACH64(0): *Default mode "640x512": 54.0 MHz, 64.0 kHz, 60.0 Hz (D)
(II) MACH64(0): Modeline "640x512"x60.0   54.00  640 664 720 844  512 512 514 533 doublescan +hsync +vsync (64.0 kHz)
(**) MACH64(0): *Default mode "720x450": 53.2 MHz, 55.9 kHz, 59.9 Hz (D)
(II) MACH64(0): Modeline "720x450"x59.9   53.25  720 760 836 952  450 451 454 467 doublescan -hsync +vsync (55.9 kHz)
(**) MACH64(0): *Driver mode "640x480": 36.0 MHz, 43.3 kHz, 85.0 Hz
(II) MACH64(0): Modeline "640x480"x85.0   36.00  640 696 752 832  480 481 484 509 -hsync -vsync (43.3 kHz)
(**) MACH64(0): *Driver mode "640x480": 31.5 MHz, 37.5 kHz, 75.0 Hz
(II) MACH64(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(**) MACH64(0): *Driver mode "640x480": 25.2 MHz, 31.5 kHz, 59.9 Hz
(II) MACH64(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(**) MACH64(0): *Default mode "640x480": 36.0 MHz, 43.3 kHz, 85.0 Hz
(II) MACH64(0): Modeline "640x480"x85.0   36.00  640 696 752 832  480 481 484 509 -hsync -vsync (43.3 kHz)
(**) MACH64(0): *Default mode "640x480": 31.5 MHz, 37.5 kHz, 75.0 Hz
(II) MACH64(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(**) MACH64(0): *Default mode "640x480": 31.5 MHz, 37.9 kHz, 72.8 Hz
(II) MACH64(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(**) MACH64(0): *Default mode "640x480": 54.0 MHz, 60.0 kHz, 60.0 Hz (D)
(II) MACH64(0): Modeline "640x480"x60.0   54.00  640 688 744 900  480 480 482 500 doublescan +hsync +vsync (60.0 kHz)
(**) MACH64(0): *Default mode "640x480": 25.2 MHz, 31.5 kHz, 59.9 Hz
(II) MACH64(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(**) MACH64(0): *Driver mode "720x400": 28.3 MHz, 31.5 kHz, 70.1 Hz
(II) MACH64(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(**) MACH64(0): *Default mode "720x400": 35.5 MHz, 37.9 kHz, 85.0 Hz
(II) MACH64(0): Modeline "720x400"x85.0   35.50  720 756 828 936  400 401 404 446 -hsync +vsync (37.9 kHz)
(**) MACH64(0): *Default mode "680x384": 36.0 MHz, 47.4 kHz, 60.0 Hz (D)
(II) MACH64(0): Modeline "680x384"x60.0   36.00  680 704 720 760  384 385 390 395 doublescan +hsync -vsync (47.4 kHz)
(**) MACH64(0): *Default mode "680x384": 42.4 MHz, 47.7 kHz, 59.8 Hz (D)
(II) MACH64(0): Modeline "680x384"x59.8   42.38  680 716 784 888  384 385 390 399 doublescan -hsync +vsync (47.7 kHz)
(**) MACH64(0): *Default mode "640x400": 31.5 MHz, 37.9 kHz, 85.1 Hz
(II) MACH64(0): Modeline "640x400"x85.1   31.50  640 672 736 832  400 401 404 445 -hsync +vsync (37.9 kHz)
(**) MACH64(0): *Default mode "576x432": 54.0 MHz, 67.5 kHz, 75.0 Hz (D)
(II) MACH64(0): Modeline "576x432"x75.0   54.00  576 608 672 800  432 432 434 450 doublescan +hsync +vsync (67.5 kHz)
(**) MACH64(0): *Default mode "576x432": 52.5 MHz, 67.6 kHz, 75.0 Hz (D)
(II) MACH64(0): Modeline "576x432"x75.0   52.49  576 612 676 776  432 432 434 451 doublescan -hsync +vsync (67.6 kHz)
(**) MACH64(0): *Default mode "576x432": 48.4 MHz, 63.0 kHz, 70.0 Hz (D)
(II) MACH64(0): Modeline "576x432"x70.0   48.38  576 612 672 768  432 432 434 450 doublescan -hsync +vsync (63.0 kHz)
(**) MACH64(0): *Default mode "576x432": 40.8 MHz, 53.7 kHz, 60.1 Hz (D)
(II) MACH64(0): Modeline "576x432"x60.1   40.81  576 608 668 760  432 432 434 447 doublescan -hsync +vsync (53.7 kHz)
(**) MACH64(0): *Default mode "640x350": 31.5 MHz, 37.9 kHz, 85.1 Hz
(II) MACH64(0): Modeline "640x350"x85.1   31.50  640 672 736 832  350 382 385 445 +hsync -vsync (37.9 kHz)
(**) MACH64(0): *Default mode "512x384": 47.2 MHz, 68.7 kHz, 85.0 Hz (D)
(II) MACH64(0): Modeline "512x384"x85.0   47.25  512 536 584 688  384 384 386 404 doublescan +hsync +vsync (68.7 kHz)
(**) MACH64(0): *Default mode "512x384": 39.4 MHz, 60.0 kHz, 75.0 Hz (D)
(II) MACH64(0): Modeline "512x384"x75.0   39.38  512 520 568 656  384 384 386 400 doublescan +hsync +vsync (60.0 kHz)
(**) MACH64(0): *Default mode "512x384": 37.5 MHz, 56.5 kHz, 70.1 Hz (D)
(II) MACH64(0): Modeline "512x384"x70.1   37.50  512 524 592 664  384 385 388 403 doublescan -hsync -vsync (56.5 kHz)
(**) MACH64(0): *Default mode "512x384": 32.5 MHz, 48.4 kHz, 60.0 Hz (D)
(II) MACH64(0): Modeline "512x384"x60.0   32.50  512 524 592 672  384 385 388 403 doublescan -hsync -vsync (48.4 kHz)
(**) MACH64(0): *Default mode "512x384": 22.4 MHz, 35.5 kHz, 86.6 Hz (D)
(II) MACH64(0): Modeline "512x384"x86.6   22.45  512 516 604 632  384 384 388 409 interlace doublescan +hsync +vsync (35.5 kHz)
(**) MACH64(0): *Default mode "416x312": 28.6 MHz, 49.7 kHz, 74.7 Hz (D)
(II) MACH64(0): Modeline "416x312"x74.7   28.64  416 432 464 576  312 312 314 333 doublescan -hsync -vsync (49.7 kHz)
(**) MACH64(0): *Default mode "400x300": 28.1 MHz, 53.7 kHz, 85.3 Hz (D)
(II) MACH64(0): Modeline "400x300"x85.3   28.15  400 416 448 524  300 300 302 315 doublescan +hsync +vsync (53.7 kHz)
(**) MACH64(0): *Default mode "400x300": 24.8 MHz, 46.9 kHz, 75.1 Hz (D)
(II) MACH64(0): Modeline "400x300"x75.1   24.75  400 408 448 528  300 300 302 312 doublescan +hsync +vsync (46.9 kHz)
(**) MACH64(0): *Default mode "400x300": 25.0 MHz, 48.1 kHz, 72.2 Hz (D)
(II) MACH64(0): Modeline "400x300"x72.2   25.00  400 428 488 520  300 318 321 333 doublescan +hsync +vsync (48.1 kHz)
(**) MACH64(0): *Default mode "400x300": 20.0 MHz, 37.9 kHz, 60.3 Hz (D)
(II) MACH64(0): Modeline "400x300"x60.3   20.00  400 420 484 528  300 300 302 314 doublescan +hsync +vsync (37.9 kHz)
(**) MACH64(0): *Default mode "400x300": 18.0 MHz, 35.2 kHz, 56.3 Hz (D)
(II) MACH64(0): Modeline "400x300"x56.3   18.00  400 412 448 512  300 300 301 312 doublescan +hsync +vsync (35.2 kHz)
(**) MACH64(0): *Default mode "320x240": 18.0 MHz, 43.3 kHz, 85.2 Hz (D)
(II) MACH64(0): Modeline "320x240"x85.2   18.00  320 348 376 416  240 240 242 254 doublescan -hsync -vsync (43.3 kHz)
(**) MACH64(0): *Default mode "320x240": 15.8 MHz, 37.5 kHz, 75.0 Hz (D)
(II) MACH64(0): Modeline "320x240"x75.0   15.75  320 328 360 420  240 240 242 250 doublescan -hsync -vsync (37.5 kHz)
(**) MACH64(0): *Default mode "320x240": 15.8 MHz, 37.9 kHz, 72.8 Hz (D)
(II) MACH64(0): Modeline "320x240"x72.8   15.75  320 332 352 416  240 244 246 260 doublescan -hsync -vsync (37.9 kHz)
(**) MACH64(0): *Default mode "320x240": 12.6 MHz, 31.5 kHz, 60.1 Hz (D)
(II) MACH64(0): Modeline "320x240"x60.1   12.59  320 328 376 400  240 245 246 262 doublescan -hsync -vsync (31.5 kHz)
(**) MACH64(0): *Default mode "360x200": 17.8 MHz, 37.9 kHz, 85.0 Hz (D)
(II) MACH64(0): Modeline "360x200"x85.0   17.75  360 378 414 468  200 200 202 223 doublescan -hsync +vsync (37.9 kHz)
(**) MACH64(0): *Default mode "320x200": 15.8 MHz, 37.9 kHz, 85.3 Hz (D)
(II) MACH64(0): Modeline "320x200"x85.3   15.75  320 336 368 416  200 200 202 222 doublescan -hsync +vsync (37.9 kHz)
(**) MACH64(0): *Default mode "320x175": 15.8 MHz, 37.9 kHz, 85.3 Hz (D)
(II) MACH64(0): Modeline "320x175"x85.3   15.75  320 336 368 416  175 191 192 222 doublescan +hsync -vsync (37.9 kHz)
(**) MACH64(0): Display dimensions: (320, 240) mm
(**) MACH64(0): DPI set to (66, 66)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 1.2.1
    ABI class: X.Org Video Driver, version 5.0
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"
(II) Module "i2c" already built-in
(II) MACH64(0): I2C bus "Mach64" initialized.
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [4] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [5] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
(WW) MACH64(0): DRI static buffer allocation failed -- need at least 5070 kB video memory
(II) MACH64(0): Largest offscreen areas (with overlaps):
(II) MACH64(0):     832 x 5 rectangle at 0,624
(II) MACH64(0):     704 x 6 rectangle at 0,624
(II) MACH64(0): Using XFree86 Acceleration Architecture (XAA)
    Screen to screen bit blits
    Solid filled rectangles
    8x8 mono pattern filled rectangles
    Indirect CPU to Screen color expansion
    Solid Lines
    Setting up tile and stipple cache:
        Not enough video memory for pixmap cache
(==) MACH64(0): Backing store disabled
(==) MACH64(0): Silken mouse enabled
(II) MACH64(0): DPMS enabled
(II) MACH64(0): Direct rendering disabled
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
(**) Option "xkb_layout" "us"
(**) AT Translated Set 2 keyboard: xkb_layout: "us"
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

Thank you for any assitance.
Much appreciated.

---

### Post by LewRockwell on 2009-10-01
```
> **ncc1701e said:**
> I just installed Ubuntu 9.04 on an older machine and cannot seem to get it to work at the resolution that this machine is capable of offering in windows. The specs of the machine are:

IBM Aptiva Intel Pentium II 300 MHZ
6GB HD
224 MB RAM
Monitor is Envision En-775e (17 inch)

Resolutions available to me are:

832x624 (4:32) thru 320x175 (9:5)
and some in between those two have a (16:10) ratio

I used to get 1024x768 with windows. I'd like to get this resolution back in Ubuntu if possible. I am new to linux and will attempt to provide below the information that I think is helpful to anyone who tries to help me. Thank you.

Here is the output of lspci:

00:00.0 Host bridge: Intel Corporation 440LX/EX - 82443LX/EX Host bridge (rev 03)
00:01.0 PCI bridge: Intel Corporation 440LX/EX - 82443LX/EX AGP bridge (rev 03)
00:07.0 ISA bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 01)
00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 01)
00:0b.0 Ethernet controller: Accton Technology Corporation EN-1216 Ethernet Adapter (rev 11)
00:12.0 Multimedia audio controller: Cirrus Logic CS 4610/11 [CrystalClear SoundFusion Audio Accelerator] (rev 01)
01:00.0 VGA compatible controller: ATI Technologies Inc 3D Rage Pro AGP 1X/2X (rev 5c)


Here is the /var/log/Xorg.0.log file:


X.Org X Server 1.6.0
Release Date: 2009-2-25
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux mercury 2.6.28-15-generic #52-Ubuntu SMP Wed Sep 9 10:49:34 UTC 2009 i686
Build Date: 09 April 2009  02:10:02AM
xorg-server 2:1.6.0-0ubuntu14 (buildd@rothera.buildd) 
    Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Thu Oct  1 09:37:00 2009
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

(--) PCI:*(0@1:0:0) ATI Technologies Inc 3D Rage Pro AGP 1X/2X rev 92, Mem @ 0x21000000/16777216, 0x20000000/4096, I/O @ 0x00002000/256, BIOS @ 0x????????/131072
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
(II) Matched mach64 from file name mach64.ids
(==) Matched mach64 for the autoconfigured driver
(==) Assigned the driver to the xf86ConfigLayout
(II) LoadModule: "mach64"
(II) Loading /usr/lib/xorg/modules/drivers//mach64_drv.so
(II) Module mach64: vendor="X.Org Foundation"
    compiled for 1.5.99.3, module version = 6.8.0
    Module class: X.Org Video Driver
    ABI class: X.Org Video Driver, version 5.0
(II) MACH64: Driver for ATI Mach64 chipsets
(II) Primary Device is: PCI 01@00:00:0
(II) resource ranges after probing:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [4] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [5] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
(II) MACH64(0): Creating default Display subsection in Screen section
    "Default Screen" for depth/fbbpp 24/32
(==) MACH64(0): Depth 24, (--) framebuffer bpp 32
(==) MACH64(0): Using XAA acceleration architecture
(II) MACH64: Mach64 in slot 1:0:0 detected.
(II) resource ranges after xf86ClaimFixedResources() call:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [4] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [5] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 1.0.0
    ABI class: X.Org Video Driver, version 5.0
(II) MACH64(0): Bad V_BIOS checksum
(II) MACH64(0): Primary V_BIOS segment is: 0xc000
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 1.1.0
    ABI class: X.Org Video Driver, version 5.0
(II) MACH64(0): VESA BIOS detected
(II) MACH64(0): VESA VBE Version 2.0
(II) MACH64(0): VESA VBE Total Mem: 2048 kB
(II) MACH64(0): VESA VBE OEM: ATI MACH64
(II) MACH64(0): VESA VBE OEM Software Rev: 1.0
(II) MACH64(0): VESA VBE OEM Vendor: ATI Technologies Inc.
(II) MACH64(0): VESA VBE OEM Product: MACH64GT
(II) MACH64(0): VESA VBE OEM Product Rev: 01.00
(II) MACH64(0): VESA VBE DDC supported
(II) MACH64(0): VESA VBE DDC Level 2
(II) MACH64(0): VESA VBE DDC transfer in appr. 2 sec.
(II) MACH64(0): VESA VBE DDC read successfully
(II) MACH64(0): Manufacturer: EPI  Model: d775  Serial#: 693567
(II) MACH64(0): Year: 2004  Week: 2
(II) MACH64(0): EDID Version: 1.3
(II) MACH64(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) MACH64(0): Sync:  Separate
(II) MACH64(0): Max Image Size [cm]: horiz.: 32  vert.: 24
(II) MACH64(0): Gamma: 2.20
(II) MACH64(0): DPMS capabilities: Off; RGB/Color Display
(II) MACH64(0): First detailed timing is preferred mode
(II) MACH64(0): redX: 0.631 redY: 0.329   greenX: 0.276 greenY: 0.600
(II) MACH64(0): blueX: 0.143 blueY: 0.057   whiteX: 0.283 whiteY: 0.297
(II) MACH64(0): Supported VESA Video Modes:
(II) MACH64(0): 720x400@70Hz
(II) MACH64(0): 640x480@60Hz
(II) MACH64(0): 640x480@75Hz
(II) MACH64(0): 800x600@75Hz
(II) MACH64(0): 1024x768@75Hz
(II) MACH64(0): Manufacturer's mask: 0
(II) MACH64(0): Supported Future Video Modes:
(II) MACH64(0): #0: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) MACH64(0): #1: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) MACH64(0): #2: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) MACH64(0): #3: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) MACH64(0): Supported additional Video Mode:
(II) MACH64(0): clock: 94.5 MHz   Image Size:  310 x 230 mm
(II) MACH64(0): h_active: 1024  h_sync: 1072  h_sync_end 1168 h_blank_end 1376 h_border: 0
(II) MACH64(0): v_active: 768  v_sync: 769  v_sync_end 772 v_blanking: 808 v_border: 0
(II) MACH64(0): Supported additional Video Mode:
(II) MACH64(0): clock: 56.2 MHz   Image Size:  310 x 230 mm
(II) MACH64(0): h_active: 800  h_sync: 832  h_sync_end 896 h_blank_end 1048 h_border: 0
(II) MACH64(0): v_active: 600  v_sync: 601  v_sync_end 604 v_blanking: 631 v_border: 0
(II) MACH64(0): Monitor name: EN-775e
(II) MACH64(0): Ranges: V min: 50 V max: 160 Hz, H min: 30 H max: 72 kHz, PixClock max 110 MHz
(II) MACH64(0): EDID (in hex):
(II) MACH64(0):     00ffffffffffff00160975d73f950a00
(II) MACH64(0):     020e0103682018782a9ea8a154469924
(II) MACH64(0):     0e484ca4420031594559615981800101
(II) MACH64(0):     010101010101ea240060410028303060
(II) MACH64(0):     130036e61000001ef91520f830581f20
(II) MACH64(0):     2040130036e61000001e000000fc0045
(II) MACH64(0):     4e2d373735650a2020202020000000fd
(II) MACH64(0):     0032a01e480b000a20202020202000a0
(II) MACH64(0): EDID vendor "EPI", prod id 55157
(II) MACH64(0): Using EDID range info for horizontal sync
(II) MACH64(0): Using EDID range info for vertical refresh
(II) MACH64(0): Printing DDC gathered Modelines:
(II) MACH64(0): Modeline "1024x768"x0.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
(II) MACH64(0): Modeline "800x600"x0.0   56.25  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
(II) MACH64(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) MACH64(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) MACH64(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) MACH64(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) MACH64(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) MACH64(0): Modeline "640x480"x0.0   36.00  640 696 752 832  480 481 484 509 -hsync -vsync (43.3 kHz)
(II) MACH64(0): Modeline "800x600"x0.0   56.25  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
(II) MACH64(0): Modeline "1024x768"x0.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
(II) MACH64(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) MACH64(0): BIOS Data:  BIOSSize=0xC000, ROMTable=0x00E2.
(II) MACH64(0): BIOS Data:  ClockTable=0x0898, FrequencyTable=0x0000.
(II) MACH64(0): BIOS Data:  LCDTable=0x0000.
(II) MACH64(0): BIOS Data:  VideoTable=0x0000, HardwareTable=0x012C.
(II) MACH64(0): BIOS Data:  I2CType=0x02, Tuner=0x00, Decoder=0x00, Audio=0x0F.
(--) MACH64(0): ATI 3D Rage Pro graphics controller detected.
(--) MACH64(0): Chip type 4742 "GB", version 4, foundry UMC, class 0, revision 0x01.
(--) MACH64(0): AGP bus interface detected;  block I/O base is 0x2000.
(--) MACH64(0): ATI Mach64 adapter detected.
(!!) MACH64(0): For information on using the multimedia capabilities
    of this adapter, please see [http://gatos.sf.net](http://gatos.sf.net).
(--) MACH64(0): Internal RAMDAC (subtype 1) detected.
(==) MACH64(0): RGB weight 888
(==) MACH64(0): Default visual is TrueColor
(==) MACH64(0): Using gamma correction (1.0, 1.0, 1.0)
(II) MACH64(0): Using Mach64 accelerator CRTC.
(WW) MACH64(0): Logic error setting operating state for VGA I/O.
(II) MACH64(0): Storing hardware cursor image at 0x211FFC00.
(II) MACH64(0): Using 8 MB linear aperture at 0x21000000.
(!!) MACH64(0): Virtual resolutions will be limited to 2047 kB
 due to linear aperture size and/or placement of hardware cursor image area.
(II) MACH64(0): Using Block 0 MMIO aperture at 0x20000400.
(II) MACH64(0): Using Block 1 MMIO aperture at 0x20000000.
(WW) MACH64(0): Logic error setting operating state for VGA memory aperture.
(II) MACH64(0): MMIO write caching enabled.
(--) MACH64(0): 2048 kB of SGRAM (1:1) detected (using 2047 kB).
(WW) MACH64(0): Cannot shadow an accelerated frame buffer.
(II) MACH64(0): Engine XCLK 99.765 MHz;  Refresh rate code 7.
(--) MACH64(0): Internal programmable clock generator detected.
(--) MACH64(0): Reference clock 157.5/11 (14.318) MHz.
(II) MACH64(0): Configured Monitor: Using hsync range of 30.00-72.00 kHz
(II) MACH64(0): Configured Monitor: Using vrefresh range of 50.00-160.00 Hz
(II) MACH64(0): Configured Monitor: Using maximum pixel clock of 110.00 MHz
(II) MACH64(0): Estimated virtual size for aspect ratio 1.3333 is 1024x768
(II) MACH64(0): Maximum clock: 199.00 MHz
(II) MACH64(0): Not using default mode "1024x768" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "1024x768" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "1024x768" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "1024x768" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "1024x768" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "1152x864" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "1280x960" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "1280x960" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "640x480" (hsync out of range)
(II) MACH64(0): Not using default mode "1280x1024" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "1280x1024" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "640x512" (hsync out of range)
(II) MACH64(0): Not using default mode "1280x1024" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "640x512" (hsync out of range)
(II) MACH64(0): Not using default mode "1600x1200" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "800x600" (hsync out of range)
(II) MACH64(0): Not using default mode "1600x1200" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "800x600" (hsync out of range)
(II) MACH64(0): Not using default mode "1600x1200" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "800x600" (hsync out of range)
(II) MACH64(0): Not using default mode "1600x1200" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "800x600" (hsync out of range)
(II) MACH64(0): Not using default mode "1600x1200" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "800x600" (hsync out of range)
(II) MACH64(0): Not using default mode "1792x1344" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "896x672" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "1792x1344" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "896x672" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "1856x1392" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "928x696" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "1856x1392" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "928x696" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "1920x1440" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "960x720" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "1920x1440" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "960x720" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "1152x864" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "1152x864" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "1152x864" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "1152x864" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "576x432" (hsync out of range)
(II) MACH64(0): Not using default mode "1152x864" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "576x432" (hsync out of range)
(II) MACH64(0): Not using default mode "1152x864" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "576x432" (hsync out of range)
(II) MACH64(0): Not using default mode "1360x768" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "1360x768" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "1400x1050" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "1400x1050" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "700x525" (hsync out of range)
(II) MACH64(0): Not using default mode "1400x1050" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "700x525" (hsync out of range)
(II) MACH64(0): Not using default mode "1400x1050" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "700x525" (hsync out of range)
(II) MACH64(0): Not using default mode "1440x900" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "1600x1024" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "1680x1050" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "1680x1050" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "1680x1050" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "840x525" (hsync out of range)
(II) MACH64(0): Not using default mode "1680x1050" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "840x525" (hsync out of range)
(II) MACH64(0): Not using default mode "1680x1050" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "840x525" (hsync out of range)
(II) MACH64(0): Not using default mode "1920x1080" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "1920x1200" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "960x600" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "1920x1440" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "960x720" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "2048x1536" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "1024x768" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "2048x1536" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "1024x768" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "2048x1536" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "1024x768" (insufficient memory for mode)
(II) MACH64(0): Not using driver mode "1024x768" (insufficient memory for mode)
(II) MACH64(0): Not using driver mode "1024x768" (insufficient memory for mode)
(II) MACH64(0): Not using driver mode "1024x768" (insufficient memory for mode)
(II) MACH64(0): Not using driver mode "1280x1024" (insufficient memory for mode)
(WW) MACH64(0): Shrinking virtual size estimate from 1024x768 to 832x624
(--) MACH64(0): Virtual size is 832x624 (pitch 832)
(**) MACH64(0): *Default mode "832x624": 57.3 MHz, 49.7 kHz, 74.6 Hz
(II) MACH64(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(**) MACH64(0): *Driver mode "800x600": 56.2 MHz, 53.7 kHz, 85.1 Hz
(II) MACH64(0): Modeline "800x600"x85.1   56.25  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
(**) MACH64(0): *Driver mode "800x600": 56.2 MHz, 53.7 kHz, 85.1 Hz
(II) MACH64(0): Modeline "800x600"x85.1   56.25  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
(**) MACH64(0): *Driver mode "800x600": 49.5 MHz, 46.9 kHz, 75.0 Hz
(II) MACH64(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(**) MACH64(0): *Default mode "800x600": 56.3 MHz, 53.7 kHz, 85.1 Hz
(II) MACH64(0): Modeline "800x600"x85.1   56.30  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
(**) MACH64(0): *Default mode "800x600": 49.5 MHz, 46.9 kHz, 75.0 Hz
(II) MACH64(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(**) MACH64(0): *Default mode "800x600": 50.0 MHz, 48.1 kHz, 72.2 Hz
(II) MACH64(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(**) MACH64(0): *Default mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
(II) MACH64(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(**) MACH64(0): *Default mode "800x600": 36.0 MHz, 35.2 kHz, 56.2 Hz
(II) MACH64(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(**) MACH64(0): *Default mode "840x525": 73.1 MHz, 65.3 kHz, 60.0 Hz (D)
(II) MACH64(0): Modeline "840x525"x60.0   73.12  840 892 980 1120  525 526 529 544 doublescan -hsync +vsync (65.3 kHz)
(**) MACH64(0): *Default mode "700x525": 61.0 MHz, 64.9 kHz, 60.0 Hz (D)
(II) MACH64(0): Modeline "700x525"x60.0   61.00  700 744 820 940  525 526 532 541 doublescan +hsync +vsync (64.9 kHz)
(**) MACH64(0): *Default mode "640x512": 54.0 MHz, 64.0 kHz, 60.0 Hz (D)
(II) MACH64(0): Modeline "640x512"x60.0   54.00  640 664 720 844  512 512 514 533 doublescan +hsync +vsync (64.0 kHz)
(**) MACH64(0): *Default mode "720x450": 53.2 MHz, 55.9 kHz, 59.9 Hz (D)
(II) MACH64(0): Modeline "720x450"x59.9   53.25  720 760 836 952  450 451 454 467 doublescan -hsync +vsync (55.9 kHz)
(**) MACH64(0): *Driver mode "640x480": 36.0 MHz, 43.3 kHz, 85.0 Hz
(II) MACH64(0): Modeline "640x480"x85.0   36.00  640 696 752 832  480 481 484 509 -hsync -vsync (43.3 kHz)
(**) MACH64(0): *Driver mode "640x480": 31.5 MHz, 37.5 kHz, 75.0 Hz
(II) MACH64(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(**) MACH64(0): *Driver mode "640x480": 25.2 MHz, 31.5 kHz, 59.9 Hz
(II) MACH64(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(**) MACH64(0): *Default mode "640x480": 36.0 MHz, 43.3 kHz, 85.0 Hz
(II) MACH64(0): Modeline "640x480"x85.0   36.00  640 696 752 832  480 481 484 509 -hsync -vsync (43.3 kHz)
(**) MACH64(0): *Default mode "640x480": 31.5 MHz, 37.5 kHz, 75.0 Hz
(II) MACH64(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(**) MACH64(0): *Default mode "640x480": 31.5 MHz, 37.9 kHz, 72.8 Hz
(II) MACH64(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(**) MACH64(0): *Default mode "640x480": 54.0 MHz, 60.0 kHz, 60.0 Hz (D)
(II) MACH64(0): Modeline "640x480"x60.0   54.00  640 688 744 900  480 480 482 500 doublescan +hsync +vsync (60.0 kHz)
(**) MACH64(0): *Default mode "640x480": 25.2 MHz, 31.5 kHz, 59.9 Hz
(II) MACH64(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(**) MACH64(0): *Driver mode "720x400": 28.3 MHz, 31.5 kHz, 70.1 Hz
(II) MACH64(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(**) MACH64(0): *Default mode "720x400": 35.5 MHz, 37.9 kHz, 85.0 Hz
(II) MACH64(0): Modeline "720x400"x85.0   35.50  720 756 828 936  400 401 404 446 -hsync +vsync (37.9 kHz)
(**) MACH64(0): *Default mode "680x384": 36.0 MHz, 47.4 kHz, 60.0 Hz (D)
(II) MACH64(0): Modeline "680x384"x60.0   36.00  680 704 720 760  384 385 390 395 doublescan +hsync -vsync (47.4 kHz)
(**) MACH64(0): *Default mode "680x384": 42.4 MHz, 47.7 kHz, 59.8 Hz (D)
(II) MACH64(0): Modeline "680x384"x59.8   42.38  680 716 784 888  384 385 390 399 doublescan -hsync +vsync (47.7 kHz)
(**) MACH64(0): *Default mode "640x400": 31.5 MHz, 37.9 kHz, 85.1 Hz
(II) MACH64(0): Modeline "640x400"x85.1   31.50  640 672 736 832  400 401 404 445 -hsync +vsync (37.9 kHz)
(**) MACH64(0): *Default mode "576x432": 54.0 MHz, 67.5 kHz, 75.0 Hz (D)
(II) MACH64(0): Modeline "576x432"x75.0   54.00  576 608 672 800  432 432 434 450 doublescan +hsync +vsync (67.5 kHz)
(**) MACH64(0): *Default mode "576x432": 52.5 MHz, 67.6 kHz, 75.0 Hz (D)
(II) MACH64(0): Modeline "576x432"x75.0   52.49  576 612 676 776  432 432 434 451 doublescan -hsync +vsync (67.6 kHz)
(**) MACH64(0): *Default mode "576x432": 48.4 MHz, 63.0 kHz, 70.0 Hz (D)
(II) MACH64(0): Modeline "576x432"x70.0   48.38  576 612 672 768  432 432 434 450 doublescan -hsync +vsync (63.0 kHz)
(**) MACH64(0): *Default mode "576x432": 40.8 MHz, 53.7 kHz, 60.1 Hz (D)
(II) MACH64(0): Modeline "576x432"x60.1   40.81  576 608 668 760  432 432 434 447 doublescan -hsync +vsync (53.7 kHz)
(**) MACH64(0): *Default mode "640x350": 31.5 MHz, 37.9 kHz, 85.1 Hz
(II) MACH64(0): Modeline "640x350"x85.1   31.50  640 672 736 832  350 382 385 445 +hsync -vsync (37.9 kHz)
(**) MACH64(0): *Default mode "512x384": 47.2 MHz, 68.7 kHz, 85.0 Hz (D)
(II) MACH64(0): Modeline "512x384"x85.0   47.25  512 536 584 688  384 384 386 404 doublescan +hsync +vsync (68.7 kHz)
(**) MACH64(0): *Default mode "512x384": 39.4 MHz, 60.0 kHz, 75.0 Hz (D)
(II) MACH64(0): Modeline "512x384"x75.0   39.38  512 520 568 656  384 384 386 400 doublescan +hsync +vsync (60.0 kHz)
(**) MACH64(0): *Default mode "512x384": 37.5 MHz, 56.5 kHz, 70.1 Hz (D)
(II) MACH64(0): Modeline "512x384"x70.1   37.50  512 524 592 664  384 385 388 403 doublescan -hsync -vsync (56.5 kHz)
(**) MACH64(0): *Default mode "512x384": 32.5 MHz, 48.4 kHz, 60.0 Hz (D)
(II) MACH64(0): Modeline "512x384"x60.0   32.50  512 524 592 672  384 385 388 403 doublescan -hsync -vsync (48.4 kHz)
(**) MACH64(0): *Default mode "512x384": 22.4 MHz, 35.5 kHz, 86.6 Hz (D)
(II) MACH64(0): Modeline "512x384"x86.6   22.45  512 516 604 632  384 384 388 409 interlace doublescan +hsync +vsync (35.5 kHz)
(**) MACH64(0): *Default mode "416x312": 28.6 MHz, 49.7 kHz, 74.7 Hz (D)
(II) MACH64(0): Modeline "416x312"x74.7   28.64  416 432 464 576  312 312 314 333 doublescan -hsync -vsync (49.7 kHz)
(**) MACH64(0): *Default mode "400x300": 28.1 MHz, 53.7 kHz, 85.3 Hz (D)
(II) MACH64(0): Modeline "400x300"x85.3   28.15  400 416 448 524  300 300 302 315 doublescan +hsync +vsync (53.7 kHz)
(**) MACH64(0): *Default mode "400x300": 24.8 MHz, 46.9 kHz, 75.1 Hz (D)
(II) MACH64(0): Modeline "400x300"x75.1   24.75  400 408 448 528  300 300 302 312 doublescan +hsync +vsync (46.9 kHz)
(**) MACH64(0): *Default mode "400x300": 25.0 MHz, 48.1 kHz, 72.2 Hz (D)
(II) MACH64(0): Modeline "400x300"x72.2   25.00  400 428 488 520  300 318 321 333 doublescan +hsync +vsync (48.1 kHz)
(**) MACH64(0): *Default mode "400x300": 20.0 MHz, 37.9 kHz, 60.3 Hz (D)
(II) MACH64(0): Modeline "400x300"x60.3   20.00  400 420 484 528  300 300 302 314 doublescan +hsync +vsync (37.9 kHz)
(**) MACH64(0): *Default mode "400x300": 18.0 MHz, 35.2 kHz, 56.3 Hz (D)
(II) MACH64(0): Modeline "400x300"x56.3   18.00  400 412 448 512  300 300 301 312 doublescan +hsync +vsync (35.2 kHz)
(**) MACH64(0): *Default mode "320x240": 18.0 MHz, 43.3 kHz, 85.2 Hz (D)
(II) MACH64(0): Modeline "320x240"x85.2   18.00  320 348 376 416  240 240 242 254 doublescan -hsync -vsync (43.3 kHz)
(**) MACH64(0): *Default mode "320x240": 15.8 MHz, 37.5 kHz, 75.0 Hz (D)
(II) MACH64(0): Modeline "320x240"x75.0   15.75  320 328 360 420  240 240 242 250 doublescan -hsync -vsync (37.5 kHz)
(**) MACH64(0): *Default mode "320x240": 15.8 MHz, 37.9 kHz, 72.8 Hz (D)
(II) MACH64(0): Modeline "320x240"x72.8   15.75  320 332 352 416  240 244 246 260 doublescan -hsync -vsync (37.9 kHz)
(**) MACH64(0): *Default mode "320x240": 12.6 MHz, 31.5 kHz, 60.1 Hz (D)
(II) MACH64(0): Modeline "320x240"x60.1   12.59  320 328 376 400  240 245 246 262 doublescan -hsync -vsync (31.5 kHz)
(**) MACH64(0): *Default mode "360x200": 17.8 MHz, 37.9 kHz, 85.0 Hz (D)
(II) MACH64(0): Modeline "360x200"x85.0   17.75  360 378 414 468  200 200 202 223 doublescan -hsync +vsync (37.9 kHz)
(**) MACH64(0): *Default mode "320x200": 15.8 MHz, 37.9 kHz, 85.3 Hz (D)
(II) MACH64(0): Modeline "320x200"x85.3   15.75  320 336 368 416  200 200 202 222 doublescan -hsync +vsync (37.9 kHz)
(**) MACH64(0): *Default mode "320x175": 15.8 MHz, 37.9 kHz, 85.3 Hz (D)
(II) MACH64(0): Modeline "320x175"x85.3   15.75  320 336 368 416  175 191 192 222 doublescan +hsync -vsync (37.9 kHz)
(**) MACH64(0): Display dimensions: (320, 240) mm
(**) MACH64(0): DPI set to (66, 66)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 1.2.1
    ABI class: X.Org Video Driver, version 5.0
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"
(II) Module "i2c" already built-in
(II) MACH64(0): I2C bus "Mach64" initialized.
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [4] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [5] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
(WW) MACH64(0): DRI static buffer allocation failed -- need at least 5070 kB video memory
(II) MACH64(0): Largest offscreen areas (with overlaps):
(II) MACH64(0):     832 x 5 rectangle at 0,624
(II) MACH64(0):     704 x 6 rectangle at 0,624
(II) MACH64(0): Using XFree86 Acceleration Architecture (XAA)
    Screen to screen bit blits
    Solid filled rectangles
    8x8 mono pattern filled rectangles
    Indirect CPU to Screen color expansion
    Solid Lines
    Setting up tile and stipple cache:
        Not enough video memory for pixmap cache
(==) MACH64(0): Backing store disabled
(==) MACH64(0): Silken mouse enabled
(II) MACH64(0): DPMS enabled
(II) MACH64(0): Direct rendering disabled
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
(**) Option "xkb_layout" "us"
(**) AT Translated Set 2 keyboard: xkb_layout: "us"
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

Thank you for any assitance.
Much appreciated.
```

please use code blocks to encase/encapsule long data posts

.

---

### Post by LewRockwell on 2009-10-01
we have a few of those machines left around

it's good to experiment with them but their hardware isn't up to the task of running Ubuntu as a full-time production machine

we use Damn Small Linux and/or Puppy Linux on stuff like that

.

---

### Post by ncc1701e on 2009-10-01
sorry about not using code block. Im kinda new on the forums and didn't know how to do that I'll make sure I use them next time. 


Do Damn Small Linux and Puppy Linux have a driver for this ATI card that you know of?

I will use this machine primarily for displaying PDF documents and to display a moving map in mozilla (google map) to aid me in my hobby which is flying the x-plane simulator on my main machine. It does these two tasks satisfactorily even now. but if I could just get that resolution up one notch im set. I don't demand any more from this old box than that. :)

thanks

---

### Post by halitech on 2009-10-01
that is a really old ATI card so 9.04 might not be the best choice to try and get running. I would go with 8.04 and a lighter desktop like XFCE or LXDE or one of the *box's.

Puppy or DSL would also be a good choice. DSL is built on Debian so the commands you are used to with Ubuntu will mostly work as well since you already know Ubuntu.

---

### Post by LewRockwell on 2009-10-01
> **ncc1701e said:**
> sorry about not using code block. Im kinda new on the forums and didn't know how to do that I'll make sure I use them next time. 


Do Damn Small Linux and Puppy Linux have a driver for this ATI card that you know of?

thanks

Damn Small Linux is a 50MB LiveCD *nix distro

[http://www.damnsmalllinux.org/download.html](http://www.damnsmalllinux.org/download.html)


Puppy Linux is a 100MB LiveCD *nix distro

[http://www.puppylinux.org/main/index.php?file=Download%20Latest%20Release.htm](http://www.puppylinux.org/main/index.php?file=Download%20Latest%20Release.htm)


DSL does a pretty good job of setting things automatically(usually even getting your DHCP and connection up and running)


Puppy is a little more manual with both display settings and connectivity


We never go anywhere without a CD case of *nix distro LiveCDs and DSL and Puppy are almost always quick crowd-pleasers no matter what the machine...

.

---

