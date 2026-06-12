---
title: "Ubuntu &amp; Ati Radeon HD 5850."
date: 2010-08-18
forum: New to Ubuntu
---

### Post by stevoo on 2010-08-18
Hey all ... its been a while since i last posted.

I am having some issues with my graphic card and cant seem to be able to startx. 

The Radeon was working perfectly for 2 - 3 weeks. 
Then one fine day it just decided to stop working. 
I was using fglrx, that was from the ATI drivers. 

I was unable to startX using fglrx and always kept getting errors.
This is the xorg log
```

X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-27-server x86_64 Ubuntu
Current Operating System: Linux stevooDesktop 2.6.32-24-generic #39-Ubuntu SMP Wed Jul 28 05:14:15 UTC 2010 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-24-generic root=UUID=b5a8f59b-301a-48a0-ad7c-8266f255bd09 ro quiet splash
Build Date: 21 July 2010  01:03:39PM
xorg-server 2:1.7.6-2ubuntu7.3 (For technical support please see http://www.ubuntu.com/support) 
Current version of pixman: 0.16.4
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Wed Aug 18 00:11:31 2010
(==) Using config file: "/etc/X11/xorg.conf"
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"
(==) ServerLayout "aticonfig Layout"
(**) |-->Screen "aticonfig-Screen[0]-0" (0)
(**) |   |-->Monitor "aticonfig-Monitor[0]-0"
(**) |   |-->Device "aticonfig-Device[0]-0"
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
(--) using VT number 8

(--) PCI:*(0:1:0:0) 1002:6899:1787:2290 ATI Technologies Inc Cypress [Radeon HD 5800 Series] rev 0, Mem @ 0xd0000000/268435456, 0xfbdc0000/131072, I/O @ 0x0000c000/256, BIOS @ 0x????????/131072
(II) Open ACPI successful (/var/run/acpid.socket)
(II) "extmod" will be loaded by default.
(II) "dbe" will be loaded by default.
(II) "glx" will be loaded by default.
(II) "record" will be loaded by default.
(II) "dri" will be loaded by default.
(II) "dri2" will be loaded by default.
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
(II) Loading /usr/lib/xorg/extra-modules/modules/extensions/libglx.so
(II) Module glx: vendor="FireGL - ATI Technologies Inc."
	compiled for 7.5.0, module version = 1.0.0
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
(II) LoadModule: "fglrx"
(II) Loading /usr/lib/xorg/extra-modules/modules/drivers/fglrx_drv.so
(II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
	compiled for 1.7.1, module version = 8.72.11
	Module class: X.Org Video Driver
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Loading /usr/lib/xorg/extra-modules/modules/linux/libfglrxdrm.so
(II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
	compiled for 1.7.1, module version = 8.72.11
(II) ATI Proprietary Linux Driver Version Identifier:8.72.11
(II) ATI Proprietary Linux Driver Release Identifier: 8.723.1                              
(II) ATI Proprietary Linux Driver Build Date: Apr  8 2010 21:40:58
(II) Primary Device is: PCI 01@00:00:0
(WW) Falling back to old probe method for fglrx
(II) Loading PCS database from /etc/ati/amdpcsdb
(--) Chipset Supported AMD Graphics Processor (0x6899) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:17:0) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:18:0) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:18:1) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:18:2) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:19:0) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:19:1) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:19:2) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:0) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:1) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:2) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:3) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:4) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:5) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@1:0:1) found
(II) AMD Video driver is running on a device belonging to a group targeted for this release
(II) AMD Video driver is signed
(II) fglrx(0): pEnt->device->identifier=0x14a05e0
(II) fglrx(0): === [atiddxPreInit] === begin
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules/libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 0.1.0
	ABI class: X.Org Video Driver, version 6.0
(**) fglrx(0): Depth 24, (--) framebuffer bpp 32
(II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) fglrx(0): Default visual is TrueColor
(**) fglrx(0): Option "DPMS" "true"
(==) fglrx(0): RGB weight 888
(II) fglrx(0): Using 8 bits per RGB 
(==) fglrx(0): Buffer Tiling is ON
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Reloading /usr/lib/xorg/extra-modules/modules/linux/libfglrxdrm.so
ukiDynamicMajor: found major device number 251
ukiDynamicMajor: found major device number 251
ukiOpenByBusid: Searching for BusID PCI:1:0:0
ukiOpenDevice: node name is /dev/ati/card0
ukiOpenDevice: open result is 11, (OK)
ukiOpenByBusid: ukiOpenMinor returns 11
ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
(--) fglrx(0): Chipset: "ATI Radeon HD 5800 Series " (Chipset = 0x6899)
(--) fglrx(0): (PciSubVendor = 0x1787, PciSubDevice = 0x2290)
(==) fglrx(0): board vendor info: third party graphics adapter - NOT original ATI
(--) fglrx(0): Linear framebuffer (phys) at 0xd0000000
(--) fglrx(0): MMIO registers at 0xfbdc0000
(--) fglrx(0): I/O port at 0x0000c000
(==) fglrx(0): ROM-BIOS at 0x000c0000
(II) fglrx(0): AC Adapter is used
(II) fglrx(0): Primary V_BIOS segment is: 0xc000
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules/libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.1.0
	ABI class: X.Org Video Driver, version 6.0
(II) fglrx(0): VESA BIOS detected
(II) fglrx(0): VESA VBE Version 3.0
(II) fglrx(0): VESA VBE Total Mem: 16384 kB
(II) fglrx(0): VESA VBE OEM: ATI ATOMBIOS
(II) fglrx(0): VESA VBE OEM Software Rev: 12.19
(II) fglrx(0): VESA VBE OEM Vendor: (C) 1988-2005, ATI Technologies Inc. 
(II) fglrx(0): VESA VBE OEM Product: CYPRESS
(II) fglrx(0): VESA VBE OEM Product Rev: 01.00
(II) fglrx(0): ATI Video BIOS revision 9 or later detected
(--) fglrx(0): Video RAM: 1048576 kByte, Type: GDDR5
(II) fglrx(0): PCIE card detected
(--) fglrx(0): Using per-process page tables (PPPT) as GART.
(WW) fglrx(0): board is an unknown third party board, chipset is supported
(II) fglrx(0): Using adapter: 1:0.0.
(II) fglrx(0): [FB] MC range(MCFBBase = 0xf00000000, MCFBSize = 0x40000000)
(II) fglrx(0): Interrupt handler installed at IRQ 29.
(II) fglrx(0): RandR 1.2 support is enabled!
(II) fglrx(0): RandR 1.2 rotation support is enabled!
(==) fglrx(0): Center Mode is disabled 
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(II) fglrx(0): Finished Initialize PPLIB!
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(II) fglrx(0): Connected Display0: CRT on primary DAC [crt1]
(II) fglrx(0): Display0 EDID data ---------------------------
(II) fglrx(0): Manufacturer: ACI  Model: 22a9  Serial#: 16843009
(II) fglrx(0): Year: 2008  Week: 43
(II) fglrx(0): EDID Version: 1.3
(II) fglrx(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) fglrx(0): Sync:  Separate  Composite  SyncOnGreen
(II) fglrx(0): Max Image Size [cm]: horiz.: 43  vert.: 27
(II) fglrx(0): Gamma: 2.20
(II) fglrx(0): DPMS capabilities: Off; RGB/Color Display
(II) fglrx(0): Default color space is primary color space
(II) fglrx(0): First detailed timing is preferred mode
(II) fglrx(0): redX: 0.640 redY: 0.352   greenX: 0.288 greenY: 0.628
(II) fglrx(0): blueX: 0.144 blueY: 0.076   whiteX: 0.313 whiteY: 0.329
(II) fglrx(0): Supported established timings:
(II) fglrx(0): 720x400@70Hz
(II) fglrx(0): 640x480@60Hz
(II) fglrx(0): 640x480@67Hz
(II) fglrx(0): 640x480@72Hz
(II) fglrx(0): 640x480@75Hz
(II) fglrx(0): 800x600@56Hz
(II) fglrx(0): 800x600@60Hz
(II) fglrx(0): 800x600@72Hz
(II) fglrx(0): 800x600@75Hz
(II) fglrx(0): 832x624@75Hz
(II) fglrx(0): 1024x768@60Hz
(II) fglrx(0): 1024x768@70Hz
(II) fglrx(0): 1024x768@75Hz
(II) fglrx(0): 1280x1024@75Hz
(II) fglrx(0): 1152x864@75Hz
(II) fglrx(0): Manufacturer's mask: 0
(II) fglrx(0): Supported standard timings:
(II) fglrx(0): #0: hsize: 1680  vsize 1050  refresh: 60  vid: 179
(II) fglrx(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) fglrx(0): #2: hsize: 1280  vsize 960  refresh: 60  vid: 16513
(II) fglrx(0): #3: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) fglrx(0): #4: hsize: 1440  vsize 900  refresh: 60  vid: 149
(II) fglrx(0): #5: hsize: 1280  vsize 800  refresh: 60  vid: 129
(II) fglrx(0): #6: hsize: 1680  vsize 1050  refresh: 75  vid: 4019
(II) fglrx(0): #7: hsize: 1280  vsize 720  refresh: 60  vid: 49281
(II) fglrx(0): Supported detailed timing:
(II) fglrx(0): clock: 146.2 MHz   Image Size:  433 x 271 mm
(II) fglrx(0): h_active: 1680  h_sync: 1784  h_sync_end 1960 h_blank_end 2240 h_border: 0
(II) fglrx(0): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1089 v_border: 0
(II) fglrx(0): Serial No: 8ALMVD041862
(II) fglrx(0): Ranges: V min: 50 V max: 75 Hz, H min: 30 H max: 82 kHz, PixClock max 210 MHz
(II) fglrx(0): Monitor name: ASUS VW220
(II) fglrx(0): EDID (in hex):
(II) fglrx(0): 	00ffffffffffff000469a92201010101
(II) fglrx(0): 	2b1201030e2b1b782ecfe5a35a49a024
(II) fglrx(0): 	135054bfef80b30081808140714f9500
(II) fglrx(0): 	8100b30f81c021399030621a274068b0
(II) fglrx(0): 	3600b10f1100001c000000ff0038414c
(II) fglrx(0): 	4d56443034313836320a000000fd0032
(II) fglrx(0): 	4b1e5215000a202020202020000000fc
(II) fglrx(0): 	00415355532056573232300a202000d0
(II) fglrx(0): End of Display0 EDID data --------------------
(II) fglrx(0): Output DFP1 using monitor section aticonfig-Monitor[0]-0
(II) fglrx(0): Output DFP2 has no monitor section
(II) fglrx(0): Output DFP3 has no monitor section
(II) fglrx(0): Output DFP4 has no monitor section
(II) fglrx(0): Output CRT1 has no monitor section
(II) fglrx(0): Output CRT2 has no monitor section
(II) fglrx(0): Output DFP1 disconnected
(II) fglrx(0): Output DFP2 disconnected
(II) fglrx(0): Output DFP3 disconnected
(II) fglrx(0): Output DFP4 disconnected
(II) fglrx(0): Output CRT1 connected
(II) fglrx(0): Output CRT2 disconnected
(II) fglrx(0): Using exact sizes for initial modes
(II) fglrx(0): Output CRT1 using initial mode 1680x1050
(II) fglrx(0): DPI set to (96, 96)
(II) fglrx(0): Adapter ATI Radeon HD 5800 Series  has 2 configurable heads and 1 displays connected.
(==) fglrx(0): QBS disabled
(==) fglrx(0):  PseudoColor visuals disabled
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(==) fglrx(0): NoAccel = NO
(==) fglrx(0): NoDRI = NO
(==) fglrx(0): Capabilities: 0x00000000
(==) fglrx(0): CapabilitiesEx: 0x00000000
(==) fglrx(0): OpenGL ClientDriverName: "fglrx_dri.so"
(==) fglrx(0): UseFastTLS=0
(==) fglrx(0): BlockSignalsOnLock=1
(--) Depth 24 pixmap format is 32 bpp
(II) Loading extension ATIFGLRXDRI
(II) fglrx(0): doing swlDriScreenInit
(II) fglrx(0): swlDriScreenInit for fglrx driver
ukiDynamicMajor: found major device number 251
ukiDynamicMajor: found major device number 251
ukiDynamicMajor: found major device number 251
ukiOpenByBusid: Searching for BusID PCI:1:0:0
ukiOpenDevice: node name is /dev/ati/card0
ukiOpenDevice: open result is 16, (OK)
ukiOpenByBusid: ukiOpenMinor returns 16
ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
(II) fglrx(0): [uki] DRM interface version 1.0
(II) fglrx(0): [uki] created "fglrx" driver at busid "PCI:1:0:0"
(II) fglrx(0): [uki] added 8192 byte SAREA at 0x20000
(II) fglrx(0): [uki] mapped SAREA 0x20000 to 0x7ff4e6645000
(II) fglrx(0): [uki] framebuffer handle = 0x21000
(II) fglrx(0): [uki] added 1 reserved context for kernel
(II) fglrx(0): swlDriScreenInit done
(II) fglrx(0): Kernel Module Version Information:
(II) fglrx(0):     Name: fglrx
(II) fglrx(0):     Version: 8.72.11
(II) fglrx(0):     Date: Apr  8 2010
(II) fglrx(0):     Desc: ATI FireGL DRM kernel module
(II) fglrx(0): Kernel Module version matches driver.
(II) fglrx(0): Kernel Module Build Time Information:
(II) fglrx(0):     Build-Kernel UTS_RELEASE:        2.6.32-24-generic
(II) fglrx(0):     Build-Kernel MODVERSIONS:        yes
(II) fglrx(0):     Build-Kernel __SMP__:            yes
(II) fglrx(0):     Build-Kernel PAGE_SIZE:          0x1000
(II) fglrx(0): [uki] register handle = 0x00022000
(II) fglrx(0): Display width adjusted to to 1792 due to alignment constraints
(II) fglrx(0): DRI initialization successfull!
(II) fglrx(0): FBADPhys: 0xf00000000 FBMappedSize: 0x010a0000
(II) fglrx(0): FBMM initialized for area (0,0)-(1792,2432)
(II) fglrx(0): FBMM auto alloc for area (0,0)-(1792,1792) (front color buffer - assumption)
(II) fglrx(0): Largest offscreen area available: 1792 x 640
(==) fglrx(0): Backing store disabled
(II) Loading extension FGLRXEXTENSION
(**) fglrx(0): DPMS enabled
(II) fglrx(0): Initialized in-driver Xinerama extension
(**) fglrx(0): Textured Video is enabled.
(II) LoadModule: "glesx"
(II) Loading /usr/lib/xorg/extra-modules/modules/glesx.so
(II) Module glesx: vendor="X.Org Foundation"
	compiled for 1.7.1, module version = 1.0.0
(II) Loading extension GLESX
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules/libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.2.1
	ABI class: X.Org Video Driver, version 6.0
(II) fglrx(0): GLESX enableFlags = 94
(II) fglrx(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	Solid Horizontal and Vertical Lines
	Driver provided ScreenToScreenBitBlt replacement
	Driver provided FillSolidRects replacement
(II) fglrx(0): GLESX is enabled
(II) LoadModule: "amdxmm"
(II) Loading /usr/lib/xorg/extra-modules/modules/amdxmm.so
(II) Module amdxmm: vendor="X.Org Foundation"
	compiled for 1.7.1, module version = 1.0.0
(II) Loading extension AMDXVOPL
(II) fglrx(0): UVD2 feature is available
(II) fglrx(0): Enable composite support successfully
(WW) fglrx(0): Option "VendorName" is not used
(WW) fglrx(0): Option "ModelName" is not used
(II) fglrx(0): X context handle = 0x1
(II) fglrx(0): [DRI] installation complete
(==) fglrx(0): Silken mouse enabled
(==) fglrx(0): Using HW cursor of display infrastructure!
(II) fglrx(0): Disabling in-server RandR and enabling in-driver RandR 1.2.
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
ukiDynamicMajor: found major device number 251
ukiDynamicMajor: found major device number 251
ukiOpenByBusid: Searching for BusID PCI:1:0:0
ukiOpenDevice: node name is /dev/ati/card0
ukiOpenDevice: open result is 17, (OK)
ukiOpenByBusid: ukiOpenMinor returns 17
ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
(II) AIGLX: Loaded and initialized /usr/lib64/dri/fglrx_dri.so
(II) GLX: Initialized DRI GL provider for screen 0
(II) fglrx(0): Enable the clock gating!
(II) fglrx(0): Setting screen physical size to 444 x 277
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
(II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
(**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event3"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
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
(II) fglrx(0): Restoring Recent Mode via PCS is not supported in RANDR 1.2 capable environments
(II) fglrx(0): Preparing normal LeaveVT...
(II) AIGLX: Suspending AIGLX clients for VT switch
(II) fglrx(0): Backup framebuffer data.
(II) fglrx(0): Backup complete.
```



Since that wasnt working , i then tried the open source drivers for ATI which still gave me some other errors.

```

X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-27-server x86_64 Ubuntu
Current Operating System: Linux stevooDesktop 2.6.32-24-generic #39-Ubuntu SMP Wed Jul 28 05:14:15 UTC 2010 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-24-generic root=UUID=b5a8f59b-301a-48a0-ad7c-8266f255bd09 ro quiet splash
Build Date: 21 July 2010  01:03:39PM
xorg-server 2:1.7.6-2ubuntu7.3 (For technical support please see http://www.ubuntu.com/support) 
Current version of pixman: 0.16.4
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Tue Aug 17 23:38:19 2010
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
(II) Loader magic: 0x7ca300
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 6.0
	X.Org XInput driver : 7.0
	X.Org Server Extension : 2.0
(++) using VT number 7

(--) PCI:*(0:1:0:0) 1002:6899:1787:2290 ATI Technologies Inc Cypress [Radeon HD 5800 Series] rev 0, Mem @ 0xd0000000/268435456, 0xfbdc0000/131072, I/O @ 0x0000c000/256, BIOS @ 0x????????/131072
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
(==) Matched ati as autoconfigured driver 0
(==) Matched vesa as autoconfigured driver 1
(==) Matched fbdev as autoconfigured driver 2
(==) Assigned the driver to the xf86ConfigLayout
(II) LoadModule: "ati"
(II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
(II) Module ati: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 6.13.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 6.0
(II) LoadModule: "radeon"
(II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
(II) Module radeon: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 6.13.0
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
(II) RADEON: Driver for ATI Radeon chipsets:
	ATI Radeon Mobility X600 (M24) 3150 (PCIE), ATI FireMV 2400 (PCI),
	ATI Radeon Mobility X300 (M24) 3152 (PCIE),
	ATI FireGL M24 GL 3154 (PCIE), ATI Radeon X600 (RV380) 3E50 (PCIE),
	ATI FireGL V3200 (RV380) 3E54 (PCIE), ATI Radeon IGP320 (A3) 4136,
	ATI Radeon IGP330/340/350 (A4) 4137, ATI Radeon 9500 AD (AGP),
	ATI Radeon 9500 AE (AGP), ATI Radeon 9600TX AF (AGP),
	ATI FireGL Z1 AG (AGP), ATI Radeon 9800SE AH (AGP),
	ATI Radeon 9800 AI (AGP), ATI Radeon 9800 AJ (AGP),
	ATI FireGL X2 AK (AGP), ATI Radeon 9600 AP (AGP),
	ATI Radeon 9600SE AQ (AGP), ATI Radeon 9600XT AR (AGP),
	ATI Radeon 9600 AS (AGP), ATI FireGL T2 AT (AGP), ATI Radeon 9650,
	ATI FireGL RV360 AV (AGP), ATI Radeon 7000 IGP (A4+) 4237,
	ATI Radeon 8500 AIW BB (AGP), ATI Radeon 8500 AIW BC (AGP),
	ATI Radeon IGP320M (U1) 4336, ATI Radeon IGP330M/340M/350M (U2) 4337,
	ATI Radeon Mobility 7000 IGP 4437, ATI Radeon 9000/PRO If (AGP/PCI),
	ATI Radeon 9000 Ig (AGP/PCI), ATI Radeon X800 (R420) JH (AGP),
	ATI Radeon X800PRO (R420) JI (AGP),
	ATI Radeon X800SE (R420) JJ (AGP), ATI Radeon X800 (R420) JK (AGP),
	ATI Radeon X800 (R420) JL (AGP), ATI FireGL X3 (R420) JM (AGP),
	ATI Radeon Mobility 9800 (M18) JN (AGP),
	ATI Radeon X800 SE (R420) (AGP), ATI Radeon X800XT (R420) JP (AGP),
	ATI Radeon X800 VE (R420) JT (AGP), ATI Radeon X850 (R480) (AGP),
	ATI Radeon X850 XT (R480) (AGP), ATI Radeon X850 SE (R480) (AGP),
	ATI Radeon X850 PRO (R480) (AGP), ATI Radeon X850 XT PE (R480) (AGP),
	ATI Radeon Mobility M7 LW (AGP),
	ATI Mobility FireGL 7800 M7 LX (AGP),
	ATI Radeon Mobility M6 LY (AGP), ATI Radeon Mobility M6 LZ (AGP),
	ATI FireGL Mobility 9000 (M9) Ld (AGP),
	ATI Radeon Mobility 9000 (M9) Lf (AGP),
	ATI Radeon Mobility 9000 (M9) Lg (AGP), ATI Radeon 9700 Pro ND (AGP),
	ATI Radeon 9700/9500Pro NE (AGP), ATI Radeon 9600TX NF (AGP),
	ATI FireGL X1 NG (AGP), ATI Radeon 9800PRO NH (AGP),
	ATI Radeon 9800 NI (AGP), ATI FireGL X2 NK (AGP),
	ATI Radeon 9800XT NJ (AGP),
	ATI Radeon Mobility 9600/9700 (M10/M11) NP (AGP),
	ATI Radeon Mobility 9600 (M10) NQ (AGP),
	ATI Radeon Mobility 9600 (M11) NR (AGP),
	ATI Radeon Mobility 9600 (M10) NS (AGP),
	ATI FireGL Mobility T2 (M10) NT (AGP),
	ATI FireGL Mobility T2e (M11) NV (AGP), ATI Radeon QD (AGP),
	ATI Radeon QE (AGP), ATI Radeon QF (AGP), ATI Radeon QG (AGP),
	ATI FireGL 8700/8800 QH (AGP), ATI Radeon 8500 QL (AGP),
	ATI Radeon 9100 QM (AGP), ATI Radeon 7500 QW (AGP/PCI),
	ATI Radeon 7500 QX (AGP/PCI), ATI Radeon VE/7000 QY (AGP/PCI),
	ATI Radeon VE/7000 QZ (AGP/PCI), ATI ES1000 515E (PCI),
	ATI Radeon Mobility X300 (M22) 5460 (PCIE),
	ATI Radeon Mobility X600 SE (M24C) 5462 (PCIE),
	ATI FireGL M22 GL 5464 (PCIE), ATI Radeon X800 (R423) UH (PCIE),
	ATI Radeon X800PRO (R423) UI (PCIE),
	ATI Radeon X800LE (R423) UJ (PCIE),
	ATI Radeon X800SE (R423) UK (PCIE),
	ATI Radeon X800 XTP (R430) (PCIE), ATI Radeon X800 XL (R430) (PCIE),
	ATI Radeon X800 SE (R430) (PCIE), ATI Radeon X800 (R430) (PCIE),
	ATI FireGL V7100 (R423) (PCIE), ATI FireGL V5100 (R423) UQ (PCIE),
	ATI FireGL unknown (R423) UR (PCIE),
	ATI FireGL unknown (R423) UT (PCIE),
	ATI Mobility FireGL V5000 (M26) (PCIE),
	ATI Mobility FireGL V5000 (M26) (PCIE),
	ATI Mobility Radeon X700 XL (M26) (PCIE),
	ATI Mobility Radeon X700 (M26) (PCIE),
	ATI Mobility Radeon X700 (M26) (PCIE),
	ATI Radeon X550XTX 5657 (PCIE), ATI Radeon 9100 IGP (A5) 5834,
	ATI Radeon Mobility 9100 IGP (U3) 5835,
	ATI Radeon XPRESS 200 5954 (PCIE),
	ATI Radeon XPRESS 200M 5955 (PCIE), ATI Radeon 9250 5960 (AGP),
	ATI Radeon 9200 5961 (AGP), ATI Radeon 9200 5962 (AGP),
	ATI Radeon 9200SE 5964 (AGP), ATI FireMV 2200 (PCI),
	ATI ES1000 5969 (PCI), ATI Radeon XPRESS 200 5974 (PCIE),
	ATI Radeon XPRESS 200M 5975 (PCIE),
	ATI Radeon XPRESS 200 5A41 (PCIE),
	ATI Radeon XPRESS 200M 5A42 (PCIE),
	ATI Radeon XPRESS 200 5A61 (PCIE),
	ATI Radeon XPRESS 200M 5A62 (PCIE),
	ATI Radeon X300 (RV370) 5B60 (PCIE),
	ATI Radeon X600 (RV370) 5B62 (PCIE),
	ATI Radeon X550 (RV370) 5B63 (PCIE),
	ATI FireGL V3100 (RV370) 5B64 (PCIE),
	ATI FireMV 2200 PCIE (RV370) 5B65 (PCIE),
	ATI Radeon Mobility 9200 (M9+) 5C61 (AGP),
	ATI Radeon Mobility 9200 (M9+) 5C63 (AGP),
	ATI Mobility Radeon X800 XT (M28) (PCIE),
	ATI Mobility FireGL V5100 (M28) (PCIE),
	ATI Mobility Radeon X800 (M28) (PCIE), ATI Radeon X850 5D4C (PCIE),
	ATI Radeon X850 XT PE (R480) (PCIE),
	ATI Radeon X850 SE (R480) (PCIE), ATI Radeon X850 PRO (R480) (PCIE),
	ATI unknown Radeon / FireGL (R480) 5D50 (PCIE),
	ATI Radeon X850 XT (R480) (PCIE),
	ATI Radeon X800XT (R423) 5D57 (PCIE),
	ATI FireGL V5000 (RV410) (PCIE), ATI Radeon X700 XT (RV410) (PCIE),
	ATI Radeon X700 PRO (RV410) (PCIE),
	ATI Radeon X700 SE (RV410) (PCIE), ATI Radeon X700 (RV410) (PCIE),
	ATI Radeon X700 SE (RV410) (PCIE), ATI Radeon X1800,
	ATI Mobility Radeon X1800 XT, ATI Mobility Radeon X1800,
	ATI Mobility FireGL V7200, ATI FireGL V7200, ATI FireGL V5300,
	ATI Mobility FireGL V7100, ATI Radeon X1800, ATI Radeon X1800,
	ATI Radeon X1800, ATI Radeon X1800, ATI Radeon X1800,
	ATI FireGL V7300, ATI FireGL V7350, ATI Radeon X1600, ATI RV505,
	ATI Radeon X1300/X1550, ATI Radeon X1550, ATI M54-GL,
	ATI Mobility Radeon X1400, ATI Radeon X1300/X1550,
	ATI Radeon X1550 64-bit, ATI Mobility Radeon X1300,
	ATI Mobility Radeon X1300, ATI Mobility Radeon X1300,
	ATI Mobility Radeon X1300, ATI Radeon X1300, ATI Radeon X1300,
	ATI RV505, ATI RV505, ATI FireGL V3300, ATI FireGL V3350,
	ATI Radeon X1300, ATI Radeon X1550 64-bit, ATI Radeon X1300/X1550,
	ATI Radeon X1600, ATI Radeon X1300/X1550, ATI Mobility Radeon X1450,
	ATI Radeon X1300/X1550, ATI Mobility Radeon X2300,
	ATI Mobility Radeon X2300, ATI Mobility Radeon X1350,
	ATI Mobility Radeon X1350, ATI Mobility Radeon X1450,
	ATI Radeon X1300, ATI Radeon X1550, ATI Mobility Radeon X1350,
	ATI FireMV 2250, ATI Radeon X1550 64-bit, ATI Radeon X1600,
	ATI Radeon X1650, ATI Radeon X1600, ATI Radeon X1600,
	ATI Mobility FireGL V5200, ATI Mobility Radeon X1600,
	ATI Radeon X1650, ATI Radeon X1650, ATI Radeon X1600,
	ATI Radeon X1300 XT/X1600 Pro, ATI FireGL V3400,
	ATI Mobility FireGL V5250, ATI Mobility Radeon X1700,
	ATI Mobility Radeon X1700 XT, ATI FireGL V5200,
	ATI Mobility Radeon X1700, ATI Radeon X2300HD,
	ATI Mobility Radeon HD 2300, ATI Mobility Radeon HD 2300,
	ATI Radeon X1950, ATI Radeon X1900, ATI Radeon X1950,
	ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
	ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
	ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
	ATI AMD Stream Processor, ATI Radeon X1900, ATI Radeon X1950,
	ATI RV560, ATI RV560, ATI Mobility Radeon X1900, ATI RV560,
	ATI Radeon X1950 GT, ATI RV570, ATI RV570, ATI FireGL V7400,
	ATI RV560, ATI Radeon X1650, ATI Radeon X1650, ATI RV560,
	ATI Radeon 9100 PRO IGP 7834, ATI Radeon Mobility 9200 IGP 7835,
	ATI Radeon X1200, ATI Radeon X1200, ATI Radeon X1200,
	ATI Radeon X1200, ATI Radeon X1200, ATI RS740, ATI RS740M, ATI RS740,
	ATI RS740M, ATI Radeon HD 2900 XT, ATI Radeon HD 2900 XT,
	ATI Radeon HD 2900 XT, ATI Radeon HD 2900 Pro, ATI Radeon HD 2900 GT,
	ATI FireGL V8650, ATI FireGL V8600, ATI FireGL V7600,
	ATI Radeon 4800 Series, ATI Radeon HD 4870 x2,
	ATI Radeon 4800 Series, ATI Radeon HD 4850 x2,
	ATI FirePro V8750 (FireGL), ATI FirePro V7760 (FireGL),
	ATI Mobility RADEON HD 4850, ATI Mobility RADEON HD 4850 X2,
	ATI Radeon 4800 Series, ATI FirePro RV770, AMD FireStream 9270,
	AMD FireStream 9250, ATI FirePro V8700 (FireGL),
	ATI Mobility RADEON HD 4870, ATI Mobility RADEON M98,
	ATI Mobility RADEON HD 4870, ATI Radeon 4800 Series,
	ATI Radeon 4800 Series, ATI FirePro M7750, ATI M98, ATI M98, ATI M98,
	ATI Mobility Radeon HD 4650, ATI Radeon RV730 (AGP),
	ATI Mobility Radeon HD 4670, ATI FirePro M5750,
	ATI Mobility Radeon HD 4670, ATI Radeon RV730 (AGP),
	ATI RV730XT [Radeon HD 4670], ATI RADEON E4600,
	ATI Radeon HD 4600 Series, ATI RV730 PRO [Radeon HD 4650],
	ATI FirePro V7750 (FireGL), ATI FirePro V5700 (FireGL),
	ATI FirePro V3750 (FireGL), ATI Mobility Radeon HD 4830,
	ATI Mobility Radeon HD 4850, ATI FirePro M7740, ATI RV740,
	ATI Radeon HD 4770, ATI Radeon HD 4700 Series, ATI Radeon HD 4770,
	ATI FirePro M5750, ATI RV610, ATI Radeon HD 2400 XT,
	ATI Radeon HD 2400 Pro, ATI Radeon HD 2400 PRO AGP, ATI FireGL V4000,
	ATI RV610, ATI Radeon HD 2350, ATI Mobility Radeon HD 2400 XT,
	ATI Mobility Radeon HD 2400, ATI RADEON E2400, ATI RV610,
	ATI FireMV 2260, ATI RV670, ATI Radeon HD3870,
	ATI Mobility Radeon HD 3850, ATI Radeon HD3850,
	ATI Mobility Radeon HD 3850 X2, ATI RV670,
	ATI Mobility Radeon HD 3870, ATI Mobility Radeon HD 3870 X2,
	ATI Radeon HD3870 X2, ATI FireGL V7700, ATI Radeon HD3850,
	ATI Radeon HD3690, AMD Firestream 9170, ATI Radeon HD 4550,
	ATI Radeon RV710, ATI Radeon RV710, ATI Radeon RV710,
	ATI Radeon HD 4350, ATI Mobility Radeon 4300 Series,
	ATI Mobility Radeon 4500 Series, ATI Mobility Radeon 4500 Series,
	ATI FirePro RG220, ATI Mobility Radeon 4330, ATI RV630,
	ATI Mobility Radeon HD 2600, ATI Mobility Radeon HD 2600 XT,
	ATI Radeon HD 2600 XT AGP, ATI Radeon HD 2600 Pro AGP,
	ATI Radeon HD 2600 XT, ATI Radeon HD 2600 Pro, ATI Gemini RV630,
	ATI Gemini Mobility Radeon HD 2600 XT, ATI FireGL V5600,
	ATI FireGL V3600, ATI Radeon HD 2600 LE,
	ATI Mobility FireGL Graphics Processor, ATI Radeon HD 3470,
	ATI Mobility Radeon HD 3430, ATI Mobility Radeon HD 3400 Series,
	ATI Radeon HD 3450, ATI Radeon HD 3450, ATI Radeon HD 3430,
	ATI Radeon HD 3450, ATI FirePro V3700, ATI FireMV 2450,
	ATI FireMV 2260, ATI FireMV 2260, ATI Radeon HD 3600 Series,
	ATI Radeon HD 3650 AGP, ATI Radeon HD 3600 PRO,
	ATI Radeon HD 3600 XT, ATI Radeon HD 3600 PRO,
	ATI Mobility Radeon HD 3650, ATI Mobility Radeon HD 3670,
	ATI Mobility FireGL V5700, ATI Mobility FireGL V5725,
	ATI Radeon HD 3200 Graphics, ATI Radeon 3100 Graphics,
	ATI Radeon HD 3200 Graphics, ATI Radeon 3100 Graphics,
	ATI Radeon HD 3300 Graphics, ATI Radeon HD 3200 Graphics,
	ATI Radeon 3000 Graphics, ATI Radeon HD 4200, ATI Radeon 4100,
	ATI Mobility Radeon HD 4200, ATI Mobility Radeon 4100,
	ATI Radeon HD 4290, ATI Radeon HD 4290, CYPRESS,
	ATI FirePro (FireGL) Graphics Adapter,
	ATI FirePro (FireGL) Graphics Adapter,
	ATI FirePro (FireGL) Graphics Adapter, ATI Radeon HD 5800 Series,
	ATI Radeon HD 5800 Series, ATI Radeon HD 5800 Series,
	ATI Radeon HD 5900 Series, ATI Radeon HD 5900 Series,
	ATI Mobility Radeon HD 5800 Series,
	ATI Mobility Radeon HD 5800 Series,
	ATI FirePro (FireGL) Graphics Adapter,
	ATI FirePro (FireGL) Graphics Adapter,
	ATI Mobility Radeon HD 5800 Series, ATI Radeon HD 5700 Series,
	ATI Radeon HD 5700 Series, ATI Radeon HD 5700 Series,
	ATI Mobility Radeon HD 5000 Series,
	ATI Mobility Radeon HD 5000 Series, ATI Mobility Radeon HD 5570,
	ATI FirePro (FireGL) Graphics Adapter,
	ATI FirePro (FireGL) Graphics Adapter, ATI Radeon HD 5670,
	ATI Radeon HD 5570, ATI Radeon HD 5500 Series, REDWOOD,
	ATI Mobility Radeon HD 5000 Series,
	ATI Mobility Radeon HD 5000 Series, CEDAR, CEDAR, CEDAR,
	ATI FirePro (FireGL) Graphics Adapter,
	ATI FirePro (FireGL) Graphics Adapter, CEDAR, ATI Radeon HD 5450,
	CEDAR
(II) VESA: driver for VESA chipsets: vesa
(II) FBDEV: driver for framebuffer: fbdev
(II) Primary Device is: PCI 01@00:00:0
(II) [KMS] drm report modesetting isn't supported.
(WW) Falling back to old probe method for vesa
(WW) Falling back to old probe method for fbdev
(II) Loading sub module "fbdevhw"
(II) LoadModule: "fbdevhw"
(II) Loading /usr/lib/xorg/modules/linux/libfbdevhw.so
(II) Module fbdevhw: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 0.0.2
	ABI class: X.Org Video Driver, version 6.0
(II) RADEON(0): TOTO SAYS 00000000fbdc0000
(II) RADEON(0): MMIO registers at 0x00000000fbdc0000: size 128KB
(II) RADEON(0): PCI bus 1 card 0 func 0
(II) RADEON(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
(==) RADEON(0): Depth 24, (--) framebuffer bpp 32
(II) RADEON(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) RADEON(0): Default visual is TrueColor
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules/libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 0.1.0
	ABI class: X.Org Video Driver, version 6.0
(II) RADEON(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(==) RADEON(0): RGB weight 888
(II) RADEON(0): Using 8 bits per RGB (8 bit DAC)
(--) RADEON(0): Chipset: "ATI Radeon HD 5800 Series" (ChipID = 0x6899)
(--) RADEON(0): Linear framebuffer at 0x00000000d0000000
(II) RADEON(0): PCIE card detected
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules/libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	ABI class: X.Org Video Driver, version 6.0
(II) RADEON(0): initializing int10
(II) RADEON(0): Primary V_BIOS segment is: 0xc000
(II) RADEON(0): ATOM BIOS detected
(II) RADEON(0): ATOM BIOS Rom: 
	SubsystemVendorID: 0x1787 SubsystemID: 0x2290
	IOBaseAddress: 0xc000
	Filename: A4126BAA.HGW
	BIOS Bootup Message: 
CYPRESS PRO GDDR5 1024MB UC:126 A4126BAA.HGW                             
   
(II) RADEON(0): Framebuffer space used by Firmware (kb): 20
(II) RADEON(0): Start of VRAM area used by Firmware: 0xfffec
(II) RADEON(0): AtomBIOS requests 20kB of VRAM scratch space
(II) RADEON(0): AtomBIOS VRAM scratch base: 0xfffec
(II) RADEON(0): Cannot get VRAM scratch space. Allocating in main memory instead
(II) RADEON(0): Default Engine Clock: 400000
(II) RADEON(0): Default Memory Clock: 900000
(II) RADEON(0): Maximum Pixel ClockPLL Frequency Output: 1200000
(II) RADEON(0): Minimum Pixel ClockPLL Frequency Output: 0
(II) RADEON(0): Maximum Pixel ClockPLL Frequency Input: 27000
(II) RADEON(0): Minimum Pixel ClockPLL Frequency Input: 6750
(II) RADEON(0): Maximum Pixel Clock: 400000
(II) RADEON(0): Reference Clock: 27000
(II) RADEON(0): No DRI yet on Evergreen
(II) RADEON(0): using shadow framebuffer
(II) Loading sub module "shadow"
(II) LoadModule: "shadow"
(II) Loading /usr/lib/xorg/modules/libshadow.so
(II) Module shadow: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.1.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) RADEON(0): Detected total video RAM=1048576K, accessible=262144K (PCI BAR=262144K)
(--) RADEON(0): Mapped VideoRAM: 262144 kByte (128 bit DDR SDRAM)
(II) RADEON(0): Color tiling disabled
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"
(II) Module "i2c" already built-in
(II) RADEON(0): PLL parameters: rf=2700 rd=12 min=64800 max=120000; xclk=40000
(II) RADEON(0): Output DisplayPort-0 has no monitor section
(II) RADEON(0): I2C bus "DisplayPort-0-DP" initialized.
RADEONDPEncoderService: 19
(II) RADEON(0): I2C bus "DisplayPort-0" initialized.
(II) RADEON(0): Output HDMI-0 has no monitor section
(II) RADEON(0): I2C bus "HDMI-0" initialized.
(II) RADEON(0): Output DVI-1 has no monitor section
(II) RADEON(0): I2C bus "DVI-1" initialized.
(II) RADEON(0): Output DVI-0 has no monitor section
(II) RADEON(0): I2C bus "DVI-0" initialized.
(II) RADEON(0): Port0:
  XRANDR name: DisplayPort-0
  Connector: DisplayPort
  DFP1: INTERNAL_UNIPHY2
  DDC reg: 0x6430
(II) RADEON(0): Port1:
  XRANDR name: HDMI-0
  Connector: HDMI-A
  DFP2: INTERNAL_UNIPHY2
  DDC reg: 0x6460
(II) RADEON(0): Port2:
  XRANDR name: DVI-1
  Connector: DVI-I
  CRT2: INTERNAL_KLDSCP_DAC2
  DFP3: INTERNAL_UNIPHY1
  DDC reg: 0x6450
(II) RADEON(0): Port3:
  XRANDR name: DVI-0
  Connector: DVI-I
  CRT1: INTERNAL_KLDSCP_DAC1
  DFP4: INTERNAL_UNIPHY
  DDC reg: 0x6470
RADEONDPEncoderService: 19
(II) RADEON(0): I2C device "DisplayPort-0-DP:ddc2" registered at address 0xA0.
failed to get auxch 0030 40 30 02
failed to get auxch 0031 40 30 02
failed to get auxch 0037 40 30 02
failed to get auxch 0050 40 30 02
failed to get auxch 0050 40 30 02
failed to get auxch 0050 40 30 02
failed to get auxch 0050 40 30 02
(II) RADEON(0): I2C device "DisplayPort-0:ddc2" registered at address 0xA0.
(II) RADEON(0): Output: DisplayPort-0, Detected Monitor Type: 0
finished output detect: 0
(II) RADEON(0): I2C device "HDMI-0:ddc2" registered at address 0xA0.
(II) RADEON(0): Output: HDMI-0, Detected Monitor Type: 0
finished output detect: 1
(II) RADEON(0): I2C device "DVI-1:ddc2" registered at address 0xA0.
Dac detection success
(II) RADEON(0): Output: DVI-1, Detected Monitor Type: 0
Unhandled monitor type 0
finished output detect: 2
(II) RADEON(0): I2C device "DVI-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI-0:DDC control interface" registered at address 0x6E.
(II) RADEON(0): EDID for output DVI-0
(II) RADEON(0): Manufacturer: ACI  Model: 22a9  Serial#: 16843009
(II) RADEON(0): Year: 2008  Week: 43
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) RADEON(0): Sync:  Separate  Composite  SyncOnGreen
(II) RADEON(0): Max Image Size [cm]: horiz.: 43  vert.: 27
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: Off; RGB/Color Display
(II) RADEON(0): Default color space is primary color space
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.640 redY: 0.352   greenX: 0.288 greenY: 0.628
(II) RADEON(0): blueX: 0.144 blueY: 0.076   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@67Hz
(II) RADEON(0): 640x480@72Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@56Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@72Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@70Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): 1152x864@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported standard timings:
(II) RADEON(0): #0: hsize: 1680  vsize 1050  refresh: 60  vid: 179
(II) RADEON(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEON(0): #2: hsize: 1280  vsize 960  refresh: 60  vid: 16513
(II) RADEON(0): #3: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) RADEON(0): #4: hsize: 1440  vsize 900  refresh: 60  vid: 149
(II) RADEON(0): #5: hsize: 1280  vsize 800  refresh: 60  vid: 129
(II) RADEON(0): #6: hsize: 1680  vsize 1050  refresh: 75  vid: 4019
(II) RADEON(0): #7: hsize: 1280  vsize 720  refresh: 60  vid: 49281
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 146.2 MHz   Image Size:  433 x 271 mm
(II) RADEON(0): h_active: 1680  h_sync: 1784  h_sync_end 1960 h_blank_end 2240 h_border: 0
(II) RADEON(0): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1089 v_border: 0
(II) RADEON(0): Serial No: 8ALMVD041862
(II) RADEON(0): Ranges: V min: 50 V max: 75 Hz, H min: 30 H max: 82 kHz, PixClock max 210 MHz
(II) RADEON(0): Monitor name: ASUS VW220
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff000469a92201010101
(II) RADEON(0): 	2b1201030e2b1b782ecfe5a35a49a024
(II) RADEON(0): 	135054bfef80b30081808140714f9500
(II) RADEON(0): 	8100b30f81c021399030621a274068b0
(II) RADEON(0): 	3600b10f1100001c000000ff0038414c
(II) RADEON(0): 	4d56443034313836320a000000fd0032
(II) RADEON(0): 	4b1e5215000a202020202020000000fc
(II) RADEON(0): 	00415355532056573232300a202000d0
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 1
(II) RADEON(0): EDID data from the display on output: DVI-0 ----------------------
(II) RADEON(0): Manufacturer: ACI  Model: 22a9  Serial#: 16843009
(II) RADEON(0): Year: 2008  Week: 43
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) RADEON(0): Sync:  Separate  Composite  SyncOnGreen
(II) RADEON(0): Max Image Size [cm]: horiz.: 43  vert.: 27
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: Off; RGB/Color Display
(II) RADEON(0): Default color space is primary color space
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.640 redY: 0.352   greenX: 0.288 greenY: 0.628
(II) RADEON(0): blueX: 0.144 blueY: 0.076   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@67Hz
(II) RADEON(0): 640x480@72Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@56Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@72Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@70Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): 1152x864@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported standard timings:
(II) RADEON(0): #0: hsize: 1680  vsize 1050  refresh: 60  vid: 179
(II) RADEON(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEON(0): #2: hsize: 1280  vsize 960  refresh: 60  vid: 16513
(II) RADEON(0): #3: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) RADEON(0): #4: hsize: 1440  vsize 900  refresh: 60  vid: 149
(II) RADEON(0): #5: hsize: 1280  vsize 800  refresh: 60  vid: 129
(II) RADEON(0): #6: hsize: 1680  vsize 1050  refresh: 75  vid: 4019
(II) RADEON(0): #7: hsize: 1280  vsize 720  refresh: 60  vid: 49281
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 146.2 MHz   Image Size:  433 x 271 mm
(II) RADEON(0): h_active: 1680  h_sync: 1784  h_sync_end 1960 h_blank_end 2240 h_border: 0
(II) RADEON(0): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1089 v_border: 0
(II) RADEON(0): Serial No: 8ALMVD041862
(II) RADEON(0): Ranges: V min: 50 V max: 75 Hz, H min: 30 H max: 82 kHz, PixClock max 210 MHz
(II) RADEON(0): Monitor name: ASUS VW220
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff000469a92201010101
(II) RADEON(0): 	2b1201030e2b1b782ecfe5a35a49a024
(II) RADEON(0): 	135054bfef80b30081808140714f9500
(II) RADEON(0): 	8100b30f81c021399030621a274068b0
(II) RADEON(0): 	3600b10f1100001c000000ff0038414c
(II) RADEON(0): 	4d56443034313836320a000000fd0032
(II) RADEON(0): 	4b1e5215000a202020202020000000fc
(II) RADEON(0): 	00415355532056573232300a202000d0
finished output detect: 3
finished all detect
RADEONDPEncoderService: 19
failed to get auxch 0030 40 30 02
failed to get auxch 0031 40 30 02
failed to get auxch 0037 40 30 02
failed to get auxch 0050 40 30 02
failed to get auxch 0050 40 30 02
failed to get auxch 0050 40 30 02
failed to get auxch 0050 40 30 02
(II) RADEON(0): Output: DisplayPort-0, Detected Monitor Type: 0
(II) RADEON(0): EDID for output DisplayPort-0
(II) RADEON(0): Output: HDMI-0, Detected Monitor Type: 0
(II) RADEON(0): EDID for output HDMI-0
Dac detection success
(II) RADEON(0): Output: DVI-1, Detected Monitor Type: 0
Unhandled monitor type 0
(II) RADEON(0): EDID for output DVI-1
(II) RADEON(0): EDID for output DVI-0
(II) RADEON(0): Manufacturer: ACI  Model: 22a9  Serial#: 16843009
(II) RADEON(0): Year: 2008  Week: 43
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) RADEON(0): Sync:  Separate  Composite  SyncOnGreen
(II) RADEON(0): Max Image Size [cm]: horiz.: 43  vert.: 27
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: Off; RGB/Color Display
(II) RADEON(0): Default color space is primary color space
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.640 redY: 0.352   greenX: 0.288 greenY: 0.628
(II) RADEON(0): blueX: 0.144 blueY: 0.076   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@67Hz
(II) RADEON(0): 640x480@72Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@56Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@72Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@70Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): 1152x864@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported standard timings:
(II) RADEON(0): #0: hsize: 1680  vsize 1050  refresh: 60  vid: 179
(II) RADEON(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEON(0): #2: hsize: 1280  vsize 960  refresh: 60  vid: 16513
(II) RADEON(0): #3: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) RADEON(0): #4: hsize: 1440  vsize 900  refresh: 60  vid: 149
(II) RADEON(0): #5: hsize: 1280  vsize 800  refresh: 60  vid: 129
(II) RADEON(0): #6: hsize: 1680  vsize 1050  refresh: 75  vid: 4019
(II) RADEON(0): #7: hsize: 1280  vsize 720  refresh: 60  vid: 49281
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 146.2 MHz   Image Size:  433 x 271 mm
(II) RADEON(0): h_active: 1680  h_sync: 1784  h_sync_end 1960 h_blank_end 2240 h_border: 0
(II) RADEON(0): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1089 v_border: 0
(II) RADEON(0): Serial No: 8ALMVD041862
(II) RADEON(0): Ranges: V min: 50 V max: 75 Hz, H min: 30 H max: 82 kHz, PixClock max 210 MHz
(II) RADEON(0): Monitor name: ASUS VW220
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff000469a92201010101
(II) RADEON(0): 	2b1201030e2b1b782ecfe5a35a49a024
(II) RADEON(0): 	135054bfef80b30081808140714f9500
(II) RADEON(0): 	8100b30f81c021399030621a274068b0
(II) RADEON(0): 	3600b10f1100001c000000ff0038414c
(II) RADEON(0): 	4d56443034313836320a000000fd0032
(II) RADEON(0): 	4b1e5215000a202020202020000000fc
(II) RADEON(0): 	00415355532056573232300a202000d0
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 1
(II) RADEON(0): EDID data from the display on output: DVI-0 ----------------------
(II) RADEON(0): Manufacturer: ACI  Model: 22a9  Serial#: 16843009
(II) RADEON(0): Year: 2008  Week: 43
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) RADEON(0): Sync:  Separate  Composite  SyncOnGreen
(II) RADEON(0): Max Image Size [cm]: horiz.: 43  vert.: 27
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: Off; RGB/Color Display
(II) RADEON(0): Default color space is primary color space
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.640 redY: 0.352   greenX: 0.288 greenY: 0.628
(II) RADEON(0): blueX: 0.144 blueY: 0.076   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@67Hz
(II) RADEON(0): 640x480@72Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@56Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@72Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@70Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): 1152x864@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported standard timings:
(II) RADEON(0): #0: hsize: 1680  vsize 1050  refresh: 60  vid: 179
(II) RADEON(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEON(0): #2: hsize: 1280  vsize 960  refresh: 60  vid: 16513
(II) RADEON(0): #3: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) RADEON(0): #4: hsize: 1440  vsize 900  refresh: 60  vid: 149
(II) RADEON(0): #5: hsize: 1280  vsize 800  refresh: 60  vid: 129
(II) RADEON(0): #6: hsize: 1680  vsize 1050  refresh: 75  vid: 4019
(II) RADEON(0): #7: hsize: 1280  vsize 720  refresh: 60  vid: 49281
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 146.2 MHz   Image Size:  433 x 271 mm
(II) RADEON(0): h_active: 1680  h_sync: 1784  h_sync_end 1960 h_blank_end 2240 h_border: 0
(II) RADEON(0): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1089 v_border: 0
(II) RADEON(0): Serial No: 8ALMVD041862
(II) RADEON(0): Ranges: V min: 50 V max: 75 Hz, H min: 30 H max: 82 kHz, PixClock max 210 MHz
(II) RADEON(0): Monitor name: ASUS VW220
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff000469a92201010101
(II) RADEON(0): 	2b1201030e2b1b782ecfe5a35a49a024
(II) RADEON(0): 	135054bfef80b30081808140714f9500
(II) RADEON(0): 	8100b30f81c021399030621a274068b0
(II) RADEON(0): 	3600b10f1100001c000000ff0038414c
(II) RADEON(0): 	4d56443034313836320a000000fd0032
(II) RADEON(0): 	4b1e5215000a202020202020000000fc
(II) RADEON(0): 	00415355532056573232300a202000d0
(II) RADEON(0): EDID vendor "ACI", prod id 8873
(II) RADEON(0): Printing probed modes for output DVI-0
(II) RADEON(0): Modeline "1680x1050"x60.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
(II) RADEON(0): Modeline "1680x1050"x74.9  187.00  1680 1800 1976 2272  1050 1053 1059 1099 -hsync +vsync (82.3 kHz)
(II) RADEON(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) RADEON(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) RADEON(0): Modeline "1440x900"x59.9  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
(II) RADEON(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1280x800"x59.8   83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync (49.7 kHz)
(II) RADEON(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) RADEON(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.8 kHz)
(II) RADEON(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) RADEON(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) RADEON(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) RADEON(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x66.7   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) RADEON(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): Output DisplayPort-0 disconnected
(II) RADEON(0): Output HDMI-0 disconnected
(II) RADEON(0): Output DVI-1 disconnected
(II) RADEON(0): Output DVI-0 connected
(II) RADEON(0): Using exact sizes for initial modes
(II) RADEON(0): Output DVI-0 using initial mode 1680x1050
(II) RADEON(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
(==) RADEON(0): DPI set to (96, 96)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(!!) RADEON(0): MergedFB support has been removed and replaced with xrandr 1.2 support
(II) UnloadModule: "vesa"
(II) Unloading /usr/lib/xorg/modules/drivers/vesa_drv.so
(II) UnloadModule: "fbdev"
(II) Unloading /usr/lib/xorg/modules/drivers/fbdev_drv.so
(II) UnloadModule: "fbdevhw"
(II) Unloading /usr/lib/xorg/modules/linux/libfbdevhw.so
(--) Depth 24 pixmap format is 32 bpp
(II) RADEON(0): RADEONScreenInit d0000000 0 0
Output CRT1 disable success
Blank CRTC 0 success
Disable CRTC memreq 0 success
Disable CRTC 0 success
Blank CRTC 1 success
Disable CRTC memreq 1 success
Disable CRTC 1 success
Blank CRTC 2 success
Disable CRTC memreq 2 success
Disable CRTC 2 success
Blank CRTC 3 success
Disable CRTC memreq 3 success
Disable CRTC 3 success
Blank CRTC 4 success
Disable CRTC memreq 4 success
Disable CRTC 4 success
Blank CRTC 5 success
Disable CRTC memreq 5 success
Disable CRTC 5 success
(II) RADEON(0): Dynamic Power Management Disabled
mc fb loc is 00df00d0
(II) RADEON(0): RADEONInitMemoryMap() : 
(II) RADEON(0):   mem_size         : 0x10000000
(II) RADEON(0):   MC_FB_LOCATION   : 0x00df00d0
(II) RADEON(0):   MC_AGP_LOCATION  : 0x003f0000
(II) RADEON(0): Depth moves disabled by default
(II) RADEON(0): Memory manager initialized to (0,0) (1792,8191)
(II) RADEON(0): Reserved area from (0,1680) to (1792,1682)
(II) RADEON(0): Largest offscreen area available: 1792 x 6509
(II) RADEON(0): RADEONRestoreMemMapRegisters() : 
(II) RADEON(0):   MC_FB_LOCATION   : 0x00df00d0 0x003f0000
(II) RADEON(0):   MC_AGP_LOCATION  : 0x003f0000
(==) RADEON(0): Backing store disabled
(WW) RADEON(0): Direct rendering disabled
(EE) RADEON(0): Acceleration initialization failed
(II) RADEON(0): Acceleration disabled
(==) RADEON(0): DPMS enabled
(==) RADEON(0): Silken mouse enabled
(II) RADEON(0): Will use 96 kb for hardware cursor 0 at offset 0x00b80000
(II) RADEON(0): Will use 96 kb for hardware cursor 1 at offset 0x00b85000
(II) RADEON(0): Will use 96 kb for hardware cursor 2 at offset 0x00b8a000
(II) RADEON(0): Will use 96 kb for hardware cursor 3 at offset 0x00b90000
(II) RADEON(0): Will use 96 kb for hardware cursor 4 at offset 0x00b95000
(II) RADEON(0): Will use 96 kb for hardware cursor 5 at offset 0x00b9a000
(II) RADEON(0): Largest offscreen area available: 1792 x 6491
(II) RADEON(0): Textured video requires CP on R5xx/R6xx/R7xx/IGP
Output DIG-1 encoder setup success
Output UNIPHY2 transmitter setup success
Output UNIPHY2 transmitter setup success
Output CRT1 disable success
Blank CRTC 0 success
Disable CRTC memreq 0 success
Disable CRTC 0 success
Blank CRTC 1 success
Disable CRTC memreq 1 success
Disable CRTC 1 success
Blank CRTC 2 success
Disable CRTC memreq 2 success
Disable CRTC 2 success
Blank CRTC 3 success
Disable CRTC memreq 3 success
Disable CRTC 3 success
Blank CRTC 4 success
Disable CRTC memreq 4 success
Disable CRTC 4 success
Blank CRTC 5 success
Disable CRTC memreq 5 success
Disable CRTC 5 success
Output CRT1 disable success
Blank CRTC 0 success
Disable CRTC memreq 0 success
Disable CRTC 0 success
Mode 1680x1050 - 2240 1089 6
(II) RADEON(0): RADEONRestoreMemMapRegisters() : 
(II) RADEON(0):   MC_FB_LOCATION   : 0x00df00d0 0x00df00d0
(II) RADEON(0):   MC_AGP_LOCATION  : 0x003f0000
Set DCPLL success
Picked PLL 0
before 14625 0x20
after 14625 0 0
best_freq: 146250
best_feedback_div: 130
best_frac_feedback_div: 0
best_ref_div: 3
best_post_div: 8
(II) RADEON(0): crtc(0) Clock: mode 146250, PLL 1462500
(II) RADEON(0): crtc(0) PLL  : refdiv 3, fbdiv 0x82(130), fracfbdiv 0, pdiv 8
Set CRTC 0 PLL success
Set DTD CRTC Timing success
Set CRTC 0 Overscan success
Not using RMX
scaler 0 setup success
Set CRTC 0 Source success
crtc 0 YUV disable setup success
Output DAC1 setup success
Output CRT1 enable success
Enable CRTC 0 success
Enable CRTC memreq 0 success
Unblank CRTC 0 success
Output DIG-1 encoder setup success
Output UNIPHY2 transmitter setup success
Output UNIPHY2 transmitter setup success
Blank CRTC 1 success
Disable CRTC memreq 1 success
Disable CRTC 1 success
Blank CRTC 2 success
Disable CRTC memreq 2 success
Disable CRTC 2 success
Blank CRTC 3 success
Disable CRTC memreq 3 success
Disable CRTC 3 success
Blank CRTC 4 success
Disable CRTC memreq 4 success
Disable CRTC 4 success
Blank CRTC 5 success
Disable CRTC memreq 5 success
Disable CRTC 5 success
(II) RADEON(0): RandR 1.2 enabled, ignore the following RandR disabled message.
Output CRT1 disable success
Blank CRTC 0 success
Disable CRTC memreq 0 success
Disable CRTC 0 success
Mode 1680x1050 - 2240 1089 6
(II) RADEON(0): RADEONRestoreMemMapRegisters() : 
(II) RADEON(0):   MC_FB_LOCATION   : 0x00df00d0 0x00df00d0
(II) RADEON(0):   MC_AGP_LOCATION  : 0x003f0000
Set DCPLL success
Picked PLL 0
before 14625 0x20
after 14625 0 0
best_freq: 146250
best_feedback_div: 130
best_frac_feedback_div: 0
best_ref_div: 3
best_post_div: 8
(II) RADEON(0): crtc(0) Clock: mode 146250, PLL 1462500
(II) RADEON(0): crtc(0) PLL  : refdiv 3, fbdiv 0x82(130), fracfbdiv 0, pdiv 8
Set CRTC 0 PLL success
Set DTD CRTC Timing success
Set CRTC 0 Overscan success
Not using RMX
scaler 0 setup success
Set CRTC 0 Source success
crtc 0 YUV disable setup success
Output DAC1 setup success
Output CRT1 enable success
Enable CRTC 0 success
Enable CRTC memreq 0 success
Unblank CRTC 0 success
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
(II) RADEON(0): Setting screen physical size to 444 x 277
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
(II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
(**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event3"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
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
(II) Power Button: Close
(II) UnloadModule: "evdev"
(II) Power Button: Close
(II) UnloadModule: "evdev"
(II) AT Translated Set 2 keyboard: Close
(II) UnloadModule: "evdev"
(II) Macintosh mouse button emulation: Close
(II) UnloadModule: "evdev"
Output CRT1 disable success
Blank CRTC 0 success
Disable CRTC memreq 0 success
Disable CRTC 0 success
Blank CRTC 1 success
Disable CRTC memreq 1 success
Disable CRTC 1 success
Blank CRTC 2 success
Disable CRTC memreq 2 success
Disable CRTC 2 success
Blank CRTC 3 success
Disable CRTC memreq 3 success
Disable CRTC 3 success
Blank CRTC 4 success
Disable CRTC memreq 4 success
Disable CRTC 4 success
Blank CRTC 5 success
Disable CRTC memreq 5 success
Disable CRTC 5 success
(II) RADEON(0): RADEONRestoreMemMapRegisters() : 
(II) RADEON(0):   MC_FB_LOCATION   : 0x003f0000 0x00df00d0
(II) RADEON(0):   MC_AGP_LOCATION  : 0x00000000
 ddxSigGiveUp: Closing log
```



I am just wondering if someone has any idea how to get my graphic card working again ? 
Ive at it for 2 days, removing and reinstalling stuff in a desperate attempt.


-Stevoo

---

### Post by Peter09 on 2010-08-18
Looking through the bugs it appears that this card should work. Can you show the output of the terminal command
 
```
lshw -C video
```

---

### Post by Zorgoth on 2010-08-18
How did you install the drivers?

If you installed them from Ubuntu's Hardware Drivers tool, you shouldn't need to do anything extra, but the drivers might be too old.

If you got Catalyst 10.7 from the website, there are two things which could easily mess things up for you -

a) did you run sudo aticonfig --initial

b) did you upgrade your kernel - with the installer script from ATI you will need to reinstall your Catalyst with each kernel update.

EDIT catalyst 10.7, not 20.7

---

### Post by wynand2020 on 2010-08-18
Install Windows

---

### Post by stevoo on 2010-08-18
```
lshw -C video
```

```
  *-display
       description: VGA compatible controller
       product: Cypress [Radeon HD 5800 Series]
       vendor: ATI Technologies Inc
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom
       configuration: driver=fglrx_pci latency=0
       resources: irq:29 memory:d0000000-dfffffff(prefetchable) memory:fbdc0000-fbddffff ioport:c000(size=256) memory:fbda0000-fbdbffff(prefetchable)

```

looks fine i guess.....

```
a) did you run sudo aticonfig --initial
```
Yes i did. I purged everything to the point that nothing would load and reloaded the fglrx with aticonfig --initial to set it up.
Still nothing. The first log i posted has the issues for that.

```
b) did you upgrade your kernel - with the installer script from ATI you will need to reinstall your Catalyst with each kernel update.
```
I am aware of that and i did reinstall with the official ati script.
This is the second time that i upgraded, fairly new pc, the first time i just reinstalled it ok and it worked, this time ... it just craps up.



Also, i can see that the first time i start it up, the login window pops up and i am given the option to login, i do that ... but it just takes me back to the login screen. I guess X doesnt start, i tried looking at the logs but it had nothing important there.

```
Install Windows
```
Who said that windows doesnt have this kind of crap ? 
If it isnt graphic problem it is other stuff !

---

### Post by khelben1979 on 2010-08-18
If the problem is not with the card itself (like bad cooling), I suspect that when the Ubuntu system made an kernel upgrade, your present ATi drivers got broken in the process.

Reinstallation of the ATi drivers should fix the problem and if it doesn't, go back to the previous version of the Ubuntu kernel.

---

### Post by stevoo on 2010-08-18
```
If the problem is not with the card itself (like bad cooling), 
```
I dont believe that is the case, as it would have also affected windows that i also have installed on. 
Also it should at least boot up and only after a while when getting hot to brake up

```
I suspect that when the Ubuntu system made an kernel upgrade, your present ATi drivers got broken in the process. Reinstallation of the ATi drivers should fix the problem and if it doesn't, go back to the previous version of the Ubuntu kernel.
```
I suspected that my self. So i removed all the kernels and left .21 if i recall 
reinstall ati drivers which i redownloaded just in case.
Still Nothing.
So reinstall .25 latest version , reinstalled drivers ( aticonfig ) 
Still nothing .... 

I believe that this is the time that i make backups and re format ! 
I wasted a lot of time, so unless anyone has a better idea in the next 20mins  am pulling the plug !

---

### Post by BadgerKid on 2010-08-18
> **khelben1979 said:**
> If the problem is not with the card itself (like bad cooling), I suspect that when the Ubuntu system made an kernel upgrade, your present ATi drivers got broken in the process.

Reinstallation of the ATi drivers should fix the problem and if it doesn't, go back to the previous version of the Ubuntu kernel.

Different user here, but similar ATI issue. The new kernel starts booting in console mode, but the screen goes black eventually. The syslog suggests the video driver isn't being loaded. With a black screen, there isn't a way to install the ATI driver again unless you can work around it, such as sshing into your machine. 

I haven't tried it, but probably the driver in xorg.conf should be changed to something generic before installing the new kernel. (Probably just make a copy first to have available in a few steps....) This should prevent the screen from going black. After rebooting, install the ATI drivers again and edit or replace xorg.conf with the previous version.

---

### Post by stevoo on 2010-08-18
> **BadgerKid said:**
> Different user here, but similar ATI issue. The new kernel starts booting in console mode, but the screen goes black eventually. The syslog suggests the video driver isn't being loaded. With a black screen, there isn't a way to install the ATI driver again unless you can work around it, such as sshing into your machine. 

I haven't tried it, but probably the driver in xorg.conf should be changed to something generic before installing the new kernel. (Probably just make a copy first to have available in a few steps....) This should prevent the screen from going black. After rebooting, install the ATI drivers again and edit or replace xorg.conf with the previous version.

Unfortunately that will not do anything to me.
I tried the ones that you have mentioned when upgrading kernel and still nothing.
Also i dont have the issue with black screen ( had it 1 - 2 times ) but the rest it managed to go back correctly. 
Beside recovery mode never fails ! 


I am formatting !


EDIT : Now that i have formated i am a bit worried in installing the ATI drivers ...  any reccomendations ?

---

### Post by khelben1979 on 2010-08-18
> **stevoo said:**
> EDIT : Now that i have formated i am a bit worried in installing the ATI drivers ...  any reccomendations ?

Slow down the pace for starters. Then read through the ATi Catalyst PDF file for proper instructions on how to install it and what problems or features the driver contains. :-k

---

