---
title: "Ati radeon problem"
date: 2011-08-12
forum: New to Ubuntu
---

### Post by waqas300 on 2011-08-12
Friends, 
   i am having problem when using ATI graphics. when loading ubuntu in normal mode black screen comes and stays there. please help

---

### Post by waqas300 on 2011-08-12
> **waqas300 said:**
> Friends, 
   i am having problem when using ATI graphics. when loading ubuntu in normal mode black screen comes and stays there. please help
help please

---

### Post by waqas300 on 2011-08-12
```
[    12.916] 
X.Org X Server 1.10.1
Release Date: 2011-04-15
[    12.916] X Protocol Version 11, Revision 0
[    12.916] Build Operating System: Linux 2.6.24-27-server i686 Ubuntu
[    12.916] Current Operating System: Linux ubuntu 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:50 UTC 2011 i686
[    12.916] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.38-8-generic root=UUID=08114BE14EF585E9 loop=/ubuntu/disks/root.disk ro quiet splash
[    12.916] Build Date: 21 May 2011  11:38:35AM
[    12.916] xorg-server 2:1.10.1-1ubuntu1.1 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[    12.916] Current version of pixman: 0.20.2
[    12.916] 	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
[    12.916] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    12.916] (==) Log file: "/var/log/Xorg.0.log", Time: Sat Aug 13 00:34:24 2011
[    12.917] (==) Using config file: "/etc/X11/xorg.conf"
[    12.917] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    12.917] (==) ServerLayout "aticonfig Layout"
[    12.917] (**) |-->Screen "aticonfig-Screen[0]-0" (0)
[    12.917] (**) |   |-->Monitor "aticonfig-Monitor[0]-0"
[    12.917] (**) |   |-->Device "aticonfig-Device[0]-0"
[    12.917] (==) Automatically adding devices
[    12.917] (==) Automatically enabling devices
[    12.918] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    12.918] 	Entry deleted from font path.
[    12.918] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    12.918] 	Entry deleted from font path.
[    12.918] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    12.918] 	Entry deleted from font path.
[    12.918] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    12.918] 	Entry deleted from font path.
[    12.918] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    12.918] 	Entry deleted from font path.
[    12.918] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[    12.918] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    12.918] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    12.918] (II) Loader magic: 0x81ffde0
[    12.918] (II) Module ABI versions:
[    12.918] 	X.Org ANSI C Emulation: 0.4
[    12.918] 	X.Org Video Driver: 10.0
[    12.918] 	X.Org XInput driver : 12.3
[    12.918] 	X.Org Server Extension : 5.0
[    12.919] (--) PCI:*(0:1:0:0) 1002:6758:1682:3181 rev 0, Mem @ 0x80000000/268435456, 0x90100000/131072, I/O @ 0x00002000/256, BIOS @ 0x????????/131072
[    12.919] (II) Open ACPI successful (/var/run/acpid.socket)
[    12.919] (II) "extmod" will be loaded by default.
[    12.919] (II) "dbe" will be loaded by default.
[    12.919] (II) "glx" will be loaded by default.
[    12.919] (II) "record" will be loaded by default.
[    12.919] (II) "dri" will be loaded by default.
[    12.919] (II) "dri2" will be loaded by default.
[    12.919] (II) LoadModule: "extmod"
[    12.988] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    12.988] (II) Module extmod: vendor="X.Org Foundation"
[    12.988] 	compiled for 1.10.1, module version = 1.0.0
[    12.988] 	Module class: X.Org Server Extension
[    12.988] 	ABI class: X.Org Server Extension, version 5.0
[    12.988] (II) Loading extension MIT-SCREEN-SAVER
[    12.988] (II) Loading extension XFree86-VidModeExtension
[    12.988] (II) Loading extension XFree86-DGA
[    12.988] (II) Loading extension DPMS
[    12.988] (II) Loading extension XVideo
[    12.988] (II) Loading extension XVideo-MotionCompensation
[    12.988] (II) Loading extension X-Resource
[    12.988] (II) LoadModule: "dbe"
[    12.988] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    12.989] (II) Module dbe: vendor="X.Org Foundation"
[    12.989] 	compiled for 1.10.1, module version = 1.0.0
[    12.989] 	Module class: X.Org Server Extension
[    12.989] 	ABI class: X.Org Server Extension, version 5.0
[    12.989] (II) Loading extension DOUBLE-BUFFER
[    12.989] (II) LoadModule: "glx"
[    12.989] (II) Loading /usr/lib/xorg/extra-modules/modules/extensions/fglrx/libglx.so
[    12.989] (II) Module glx: vendor="FireGL - ATI Technologies Inc."
[    12.989] 	compiled for 6.9.0, module version = 1.0.0
[    12.989] (II) Loading extension GLX
[    12.989] (II) LoadModule: "record"
[    12.990] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    12.990] (II) Module record: vendor="X.Org Foundation"
[    12.990] 	compiled for 1.10.1, module version = 1.13.0
[    12.990] 	Module class: X.Org Server Extension
[    12.990] 	ABI class: X.Org Server Extension, version 5.0
[    12.990] (II) Loading extension RECORD
[    12.990] (II) LoadModule: "dri"
[    12.990] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    12.990] (II) Module dri: vendor="X.Org Foundation"
[    12.990] 	compiled for 1.10.1, module version = 1.0.0
[    12.990] 	ABI class: X.Org Server Extension, version 5.0
[    12.990] (II) Loading extension XFree86-DRI
[    12.990] (II) LoadModule: "dri2"
[    12.991] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    12.991] (II) Module dri2: vendor="X.Org Foundation"
[    12.991] 	compiled for 1.10.1, module version = 1.2.0
[    12.991] 	ABI class: X.Org Server Extension, version 5.0
[    12.991] (II) Loading extension DRI2
[    12.991] (II) LoadModule: "fglrx"
[    12.991] (II) Loading /usr/lib/xorg/extra-modules/modules/drivers/fglrx_drv.so
[    13.010] (II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
[    13.010] 	compiled for 1.4.99.906, module version = 8.84.60
[    13.010] 	Module class: X.Org Video Driver
[    13.011] (II) Loading sub module "fglrxdrm"
[    13.011] (II) LoadModule: "fglrxdrm"
[    13.011] (II) Loading /usr/lib/xorg/extra-modules/modules/linux/libfglrxdrm.so
[    13.011] (II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
[    13.011] 	compiled for 1.4.99.906, module version = 8.84.60
[    13.011] (II) ATI Proprietary Linux Driver Version Identifier:8.84.60
[    13.011] (II) ATI Proprietary Linux Driver Release Identifier: 8.84.6                               
[    13.011] (II) ATI Proprietary Linux Driver Build Date: Mar 24 2011 19:27:41
[    13.011] (++) using VT number 7

[    13.013] (WW) Falling back to old probe method for fglrx
[    13.033] (II) PCS database file /etc/ati/amdpcsdb not found
[    13.034] (II)   Creating PCS database from initial defaults instead
[    13.036] (--) Chipset Supported AMD Graphics Processor (0x6758) found
[    13.040] (WW) fglrx: No matching Device section for instance (BusID PCI:0@1:0:1) found
[    13.040] (II) AMD Video driver is running on a device belonging to a group targeted for this release
[    13.040] (II) AMD Video driver is signed
[    13.040] (II) Loading /usr/lib/xorg/extra-modules/modules/drivers/fglrx_drv.so
[    13.040] (II) Loading /usr/lib/xorg/extra-modules/modules/linux/libfglrxdrm.so
[    13.040] (II) fglrx(0): pEnt->device->identifier=0x9e8a3f0
[    13.040] (II) fglrx(0): === [xdl_xs110_atiddxPreInit] === begin
[    13.040] (II) Loading sub module "vgahw"
[    13.040] (II) LoadModule: "vgahw"
[    13.041] (II) Loading /usr/lib/xorg/modules/libvgahw.so
[    13.041] (II) Module vgahw: vendor="X.Org Foundation"
[    13.041] 	compiled for 1.10.1, module version = 0.1.0
[    13.041] 	ABI class: X.Org Video Driver, version 10.0
[    13.041] (**) fglrx(0): Depth 24, (--) framebuffer bpp 32
[    13.041] (II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[    13.041] (==) fglrx(0): Default visual is TrueColor
[    13.041] (**) fglrx(0): Option "DPMS" "true"
[    13.041] (==) fglrx(0): RGB weight 888
[    13.041] (II) fglrx(0): Using 8 bits per RGB 
[    13.041] (==) fglrx(0): Buffer Tiling is ON
[    13.041] (II) Loading sub module "fglrxdrm"
[    13.041] (II) LoadModule: "fglrxdrm"
[    13.041] (II) Loading /usr/lib/xorg/extra-modules/modules/linux/libfglrxdrm.so
[    13.041] (II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
[    13.041] 	compiled for 1.4.99.906, module version = 8.84.60
[    13.043] ukiDynamicMajor: found major device number 250
[    13.043] ukiDynamicMajor: found major device number 250
[    13.043] ukiOpenByBusid: Searching for BusID PCI:1:0:0
[    13.043] ukiOpenDevice: node name is /dev/ati/card0
[    13.044] ukiOpenDevice: open result is 11, (OK)
[    13.044] ukiOpenByBusid: ukiOpenMinor returns 11
[    13.044] ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
[    13.044] (==) fglrx(0): NoAccel = NO
[    13.044] (==) fglrx(0): ATI 2D Acceleration Architecture enabled
[    13.044] (--) fglrx(0): Chipset: "AMD Radeon HD 6600 Series" (Chipset = 0x6758)
[    13.044] (--) fglrx(0): (PciSubVendor = 0x1682, PciSubDevice = 0x3181)
[    13.044] (==) fglrx(0): board vendor info: third party graphics adapter - NOT original ATI
[    13.044] (--) fglrx(0): Linear framebuffer (phys) at 0x80000000
[    13.044] (--) fglrx(0): MMIO registers at 0x90100000
[    13.044] (--) fglrx(0): I/O port at 0x00002000
[    13.044] (==) fglrx(0): ROM-BIOS at 0x000c0000
[    13.045] (II) fglrx(0): AC Adapter is used
[    13.048] (II) fglrx(0): Primary V_BIOS segment is: 0xc000
[    13.246] (II) Loading sub module "vbe"
[    13.246] (II) LoadModule: "vbe"
[    13.246] (II) Loading /usr/lib/xorg/modules/libvbe.so
[    13.246] (II) Module vbe: vendor="X.Org Foundation"
[    13.246] 	compiled for 1.10.1, module version = 1.1.0
[    13.247] 	ABI class: X.Org Video Driver, version 10.0
[    13.247] (II) fglrx(0): VESA BIOS detected
[    13.247] (II) fglrx(0): VESA VBE Version 3.0
[    13.247] (II) fglrx(0): VESA VBE Total Mem: 16384 kB
[    13.247] (II) fglrx(0): VESA VBE OEM: AMD ATOMBIOS
[    13.247] (II) fglrx(0): VESA VBE OEM Software Rev: 13.12
[    13.247] (II) fglrx(0): VESA VBE OEM Vendor: (C) 1988-2010, AMD Technologies Inc. 
[    13.247] (II) fglrx(0): VESA VBE OEM Product: TURKS
[    13.247] (II) fglrx(0): VESA VBE OEM Product Rev: 01.00
[    13.282] (II) fglrx(0): ATI Video BIOS revision 9 or later detected
[    13.282] (--) fglrx(0): Video RAM: 1048576 kByte, Type: DDR3
[    13.282] (II) fglrx(0): PCIE card detected
[    13.282] (--) fglrx(0): Using per-process page tables (PPPT) as GART.
[    13.282] (WW) fglrx(0): board is an unknown third party board, chipset is supported
[    13.288] (II) fglrx(0): Using adapter: 1:0.0.
[    13.324] (II) fglrx(0): [FB] MC range(MCFBBase = 0xf00000000, MCFBSize = 0x40000000)
[    13.409] (II) fglrx(0): Interrupt handler installed at IRQ 49.
[    13.409] (II) fglrx(0): RandR 1.2 support is enabled!
[    13.409] (II) fglrx(0): RandR 1.2 rotation support is enabled!
[    13.409] (==) fglrx(0): Center Mode is disabled 
[    13.409] (II) Loading sub module "fb"
[    13.409] (II) LoadModule: "fb"
[    13.409] (II) Loading /usr/lib/xorg/modules/libfb.so
[    13.410] (II) Module fb: vendor="X.Org Foundation"
[    13.410] 	compiled for 1.10.1, module version = 1.0.0
[    13.410] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    13.410] (II) Loading sub module "ddc"
[    13.410] (II) LoadModule: "ddc"
[    13.410] (II) Module "ddc" already built-in
[    13.563] (II) fglrx(0): Finished Initialize PPLIB!
[    13.563] (II) fglrx(0): Output DFP1 using monitor section aticonfig-Monitor[0]-0
[    13.563] (II) fglrx(0): Output DFP2 has no monitor section
[    13.563] (II) fglrx(0): Output DFP3 has no monitor section
[    13.563] (II) fglrx(0): Output CRT1 has no monitor section
[    13.563] (II) Loading sub module "ddc"
[    13.563] (II) LoadModule: "ddc"
[    13.563] (II) Module "ddc" already built-in
[    13.563] (II) fglrx(0): Connected Display0: CRT1
[    13.563] (II) fglrx(0):  Display0: Failed to get EDID information. 
[    13.567] (II) fglrx(0): EDID for output DFP1
[    13.567] (II) fglrx(0): EDID for output DFP2
[    13.567] (II) fglrx(0): EDID for output DFP3
[    13.567] (II) fglrx(0): Cannot get EDID information for CRT1
[    13.567] (II) fglrx(0): EDID for output CRT1
[    13.567] (II) fglrx(0): Not using mode "640x350" (vrefresh out of range)
[    13.567] (II) fglrx(0): Not using mode "640x400" (vrefresh out of range)
[    13.568] (II) fglrx(0): Not using mode "720x400" (vrefresh out of range)
[    13.568] (II) fglrx(0): Not using mode "640x480" (vrefresh out of range)
[    13.568] (II) fglrx(0): Not using mode "640x480" (vrefresh out of range)
[    13.568] (II) fglrx(0): Not using mode "640x480" (vrefresh out of range)
[    13.568] (II) fglrx(0): Not using mode "800x600" (vrefresh out of range)
[    13.568] (II) fglrx(0): Not using mode "800x600" (vrefresh out of range)
[    13.568] (II) fglrx(0): Not using mode "800x600" (vrefresh out of range)
[    13.568] (II) fglrx(0): Not using mode "800x600" (vrefresh out of range)
[    13.568] (II) fglrx(0): Not using mode "800x600" (vrefresh out of range)
[    13.568] (II) fglrx(0): Not using mode "848x480" (unknown reason)
[    13.568] (II) fglrx(0): Not using mode "1024x768i" (vrefresh out of range)
[    13.568] (II) fglrx(0): Not using mode "1024x768" (vrefresh out of range)
[    13.568] (II) fglrx(0): Not using mode "1024x768" (vrefresh out of range)
[    13.568] (II) fglrx(0): Not using mode "1024x768" (vrefresh out of range)
[    13.568] (II) fglrx(0): Not using mode "1024x768" (vrefresh out of range)
[    13.568] (II) fglrx(0): Not using mode "1152x864" (vrefresh out of range)
[    13.568] (II) fglrx(0): Not using mode "1280x768" (monitor doesn't support reduced blanking)
[    13.568] (II) fglrx(0): Not using mode "1280x768" (vrefresh out of range)
[    13.568] (II) fglrx(0): Not using mode "1280x768" (vrefresh out of range)
[    13.568] (II) fglrx(0): Not using mode "1280x768" (vrefresh out of range)
[    13.568] (II) fglrx(0): Not using mode "1280x800" (monitor doesn't support reduced blanking)
[    13.568] (II) fglrx(0): Not using mode "1280x800" (vrefresh out of range)
[    13.568] (II) fglrx(0): Not using mode "1280x800" (vrefresh out of range)
[    13.568] (II) fglrx(0): Not using mode "1280x800" (vrefresh out of range)
[    13.568] (II) fglrx(0): Not using mode "1280x960" (unknown reason)
[    13.568] (II) fglrx(0): Not using mode "1280x960" (vrefresh out of range)
[    13.568] (II) fglrx(0): Not using mode "1280x960" (vrefresh out of range)
[    13.568] (II) fglrx(0): Not using mode "1280x1024" (vrefresh out of range)
[    13.568] (II) fglrx(0): Not using mode "1280x1024" (vrefresh out of range)
[    13.568] (II) fglrx(0): Not using mode "1280x1024" (vrefresh out of range)
[    13.568] (II) fglrx(0): Not using mode "1360x768" (vrefresh out of range)
[    13.568] (II) fglrx(0): Not using mode "1400x1050" (monitor doesn't support reduced blanking)
[    13.568] (II) fglrx(0): Not using mode "1400x1050" (unknown reason)
[    13.568] (II) fglrx(0): Not using mode "1400x1050" (vrefresh out of range)
[    13.568] (II) fglrx(0): Not using mode "1400x1050" (vrefresh out of range)
[    13.568] (II) fglrx(0): Not using mode "1400x1050" (vrefresh out of range)
[    13.568] (II) fglrx(0): Not using mode "1440x900" (monitor doesn't support reduced blanking)
[    13.568] (II) fglrx(0): Not using mode "1440x900" (vrefresh out of range)
[    13.568] (II) fglrx(0): Not using mode "1440x900" (vrefresh out of range)
[    13.568] (II) fglrx(0): Not using mode "1440x900" (vrefresh out of range)
[    13.568] (II) fglrx(0): Not using mode "1600x1200" (vrefresh out of range)
[    13.568] (II) fglrx(0): Not using mode "1600x1200" (vrefresh out of range)
[    13.568] (II) fglrx(0): Not using mode "1600x1200" (vrefresh out of range)
[    13.568] (II) fglrx(0): Not using mode "1600x1200" (vrefresh out of range)
[    13.568] (II) fglrx(0): Not using mode "1600x1200" (vrefresh out of range)
[    13.568] (II) fglrx(0): Not using mode "1680x1050" (width too large for virtual size)
[    13.568] (II) fglrx(0): Not using mode "1680x1050" (width too large for virtual size)
[    13.568] (II) fglrx(0): Not using mode "1680x1050" (width too large for virtual size)
[    13.568] (II) fglrx(0): Not using mode "1680x1050" (width too large for virtual size)
[    13.568] (II) fglrx(0): Not using mode "1680x1050" (width too large for virtual size)
[    13.568] (II) fglrx(0): Not using mode "1792x1344" (width too large for virtual size)
[    13.568] (II) fglrx(0): Not using mode "1792x1344" (width too large for virtual size)
[    13.568] (II) fglrx(0): Not using mode "1792x1344" (width too large for virtual size)
[    13.568] (II) fglrx(0): Not using mode "1856x1392" (width too large for virtual size)
[    13.568] (II) fglrx(0): Not using mode "1856x1392" (width too large for virtual size)
[    13.568] (II) fglrx(0): Not using mode "1856x1392" (width too large for virtual size)
[    13.568] (II) fglrx(0): Not using mode "1920x1200" (width too large for virtual size)
[    13.568] (II) fglrx(0): Not using mode "1920x1200" (width too large for virtual size)
[    13.568] (II) fglrx(0): Not using mode "1920x1200" (width too large for virtual size)
[    13.568] (II) fglrx(0): Not using mode "1920x1200" (width too large for virtual size)
[    13.568] (II) fglrx(0): Not using mode "1920x1200" (width too large for virtual size)
[    13.568] (II) fglrx(0): Not using mode "1920x1440" (width too large for virtual size)
[    13.568] (II) fglrx(0): Not using mode "1920x1440" (width too large for virtual size)
[    13.568] (II) fglrx(0): Not using mode "1920x1440" (width too large for virtual size)
[    13.568] (II) fglrx(0): Not using mode "2560x1600" (width too large for virtual size)
[    13.568] (II) fglrx(0): Not using mode "2560x1600" (width too large for virtual size)
[    13.568] (II) fglrx(0): Not using mode "2560x1600" (width too large for virtual size)
[    13.568] (II) fglrx(0): Not using mode "2560x1600" (width too large for virtual size)
[    13.568] (II) fglrx(0): Not using mode "2560x1600" (width too large for virtual size)
[    13.568] (II) fglrx(0): Printing probed modes for output CRT1
[    13.568] (II) fglrx(0): Modeline "1600x1200"x60.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz)
[    13.568] (II) fglrx(0): Modeline "1400x1050"x60.0  122.61  1400 1488 1640 1880  1050 1051 1054 1087 -hsync +vsync (65.2 kHz)
[    13.568] (II) fglrx(0): Modeline "1600x900"x60.0  108.00  1600 1624 1704 1800  900 901 904 1000 +hsync +vsync (60.0 kHz)
[    13.568] (II) fglrx(0): Modeline "1360x1024"x60.0  116.01  1360 1448 1592 1824  1024 1025 1028 1060 -hsync +vsync (63.6 kHz)
[    13.568] (II) fglrx(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    13.569] (II) fglrx(0): Modeline "1440x900"x60.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
[    13.569] (II) fglrx(0): Modeline "1280x960"x60.0  102.10  1280 1360 1496 1712  960 961 964 994 -hsync +vsync (59.6 kHz)
[    13.569] (II) fglrx(0): Modeline "1366x768"x60.0   85.50  1366 1436 1579 1792  768 771 774 798 +hsync +vsync (47.7 kHz)
[    13.569] (II) fglrx(0): Modeline "1360x768"x60.0   85.50  1360 1424 1536 1792  768 771 777 795 +hsync +vsync (47.7 kHz)
[    13.569] (II) fglrx(0): Modeline "1280x800"x60.0   83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync (49.7 kHz)
[    13.569] (II) fglrx(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 -hsync +vsync (53.7 kHz)
[    13.569] (II) fglrx(0): Modeline "1280x768"x60.0   79.50  1280 1344 1472 1664  768 771 778 798 -hsync +vsync (47.8 kHz)
[    13.569] (II) fglrx(0): Modeline "1280x720"x60.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz)
[    13.569] (II) fglrx(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    13.569] (II) fglrx(0): Modeline "800x600"x60.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    13.569] (II) fglrx(0): Modeline "720x480"x60.0   27.03  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz)
[    13.569] (II) fglrx(0): Modeline "640x480"x60.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    13.569] (II) fglrx(0): Output DFP1 disconnected
[    13.569] (II) fglrx(0): Output DFP2 disconnected
[    13.569] (II) fglrx(0): Output DFP3 disconnected
[    13.569] (II) fglrx(0): Output CRT1 connected
[    13.569] (II) fglrx(0): Using exact sizes for initial modes
[    13.569] (II) fglrx(0): Output CRT1 using initial mode 1600x1200
[    13.569] (II) fglrx(0): DPI set to (96, 96)
[    13.569] (II) fglrx(0): Eyefinity capable adapter detected.
[    13.569] (II) fglrx(0): Adapter AMD Radeon HD 6600 Series has 3 configurable heads and 1 displays connected.
[    13.569] (==) fglrx(0):  PseudoColor visuals disabled
[    13.569] (II) Loading sub module "ramdac"
[    13.569] (II) LoadModule: "ramdac"
[    13.569] (II) Module "ramdac" already built-in
[    13.569] (==) fglrx(0): NoDRI = NO
[    13.569] (==) fglrx(0): Capabilities: 0x00000000
[    13.569] (==) fglrx(0): CapabilitiesEx: 0x00000000
[    13.569] (==) fglrx(0): OpenGL ClientDriverName: "fglrx_dri.so"
[    13.569] (==) fglrx(0): UseFastTLS=0
[    13.569] (==) fglrx(0): BlockSignalsOnLock=1
[    13.569] (--) Depth 24 pixmap format is 32 bpp
[    13.569] (II) Loading extension ATIFGLRXDRI
[    13.569] (II) fglrx(0): doing swlDriScreenInit
[    13.569] (II) fglrx(0): swlDriScreenInit for fglrx driver
[    13.569] ukiDynamicMajor: found major device number 250
[    13.570] ukiDynamicMajor: found major device number 250
[    13.570] ukiDynamicMajor: found major device number 250
[    13.570] ukiOpenByBusid: Searching for BusID PCI:1:0:0
[    13.570] ukiOpenDevice: node name is /dev/ati/card0
[    13.570] ukiOpenDevice: open result is 16, (OK)
[    13.570] ukiOpenByBusid: ukiOpenMinor returns 16
[    13.570] ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
[    13.570] (II) fglrx(0): [uki] DRM interface version 1.0
[    13.570] (II) fglrx(0): [uki] created "fglrx" driver at busid "PCI:1:0:0"
[    13.570] (II) fglrx(0): [uki] added 8192 byte SAREA at 0x2000
[    13.570] (II) fglrx(0): [uki] mapped SAREA 0x2000 to 0xb77e1000
[    13.570] (II) fglrx(0): [uki] framebuffer handle = 0x3000
[    13.570] (II) fglrx(0): [uki] added 1 reserved context for kernel
[    13.570] (II) fglrx(0): swlDriScreenInit done
[    13.570] (II) fglrx(0): Kernel Module Version Information:
[    13.570] (II) fglrx(0):     Name: fglrx
[    13.570] (II) fglrx(0):     Version: 8.87.5
[    13.570] (II) fglrx(0):     Date: Jul  7 2011
[    13.570] (II) fglrx(0):     Desc: ATI FireGL DRM kernel module
[    13.570] (WW) fglrx(0): Kernel Module version does *not* match driver.
[    13.570] (EE) fglrx(0): incompatible kernel module detected - HW accelerated OpenGL will not work
[    13.570] (II) fglrx(0): [uki] removed 1 reserved context for kernel
[    13.570] (II) fglrx(0): [uki] unmapping 8192 bytes of SAREA 0x2000 at 0xb77e1000
[    13.570] (WW) fglrx(0): ***********************************************************
[    13.570] (WW) fglrx(0): * DRI initialization failed                               *
[    13.570] (WW) fglrx(0): * kernel module (fglrx.ko) may be missing or incompatible *
[    13.570] (WW) fglrx(0): * 2D and 3D acceleration disabled                         *
[    13.570] (WW) fglrx(0): ***********************************************************
[    13.570] (II) fglrx(0): FBADPhys: 0xf00000000 FBMappedSize: 0x10000000
[    13.624] (II) fglrx(0): FBMM initialized for area (0,0)-(1600,8191)
[    13.624] (II) fglrx(0): FBMM auto alloc for area (0,0)-(1600,1600) (front color buffer - assumption)
[    13.624] (II) fglrx(0): Largest offscreen area available: 1600 x 6591
[    13.624] (==) fglrx(0): Backing store disabled
[    13.624] (II) Loading extension FGLRXEXTENSION
[    13.624] (**) fglrx(0): DPMS enabled
[    13.625] (II) fglrx(0): Initialized in-driver Xinerama extension
[    13.625] (WW) fglrx(0): Textured Video not supported without DRI enabled.
[    13.625] (II) LoadModule: "glesx"
[    13.625] (II) Loading /usr/lib/xorg/extra-modules/modules/glesx.so
[    13.627] (II) Module glesx: vendor="X.Org Foundation"
[    13.627] 	compiled for 1.4.99.906, module version = 1.0.0
[    13.627] (II) Loading extension GLESX
[    13.627] (II) fglrx(0): GLESX enableFlags = 576
[    13.627] (II) LoadModule: "amdxmm"
[    13.627] (II) Loading /usr/lib/xorg/extra-modules/modules/amdxmm.so
[    13.627] (II) Module amdxmm: vendor="X.Org Foundation"
[    13.627] 	compiled for 1.4.99.906, module version = 2.0.0
[    13.627] (EE) fglrx(0): XMM failed to open CMMQS connection.(EE) fglrx(0): 
[    13.627] (EE) fglrx(0): XMM failed to initialize
[    13.627] (WW) fglrx(0): No XV video playback available
[    13.627] (II) fglrx(0): Enable composite support successfully
[    13.627] (WW) fglrx(0): Option "VendorName" is not used
[    13.627] (WW) fglrx(0): Option "ModelName" is not used
[    13.627] (==) fglrx(0): Silken mouse enabled
[    13.627] (==) fglrx(0): Using HW cursor of display infrastructure!
[    13.628] (II) fglrx(0): Disabling in-server RandR and enabling in-driver RandR 1.2.
[    13.714] (--) RandR disabled
[    13.714] (II) Initializing built-in extension Generic Event Extension
[    13.714] (II) Initializing built-in extension SHAPE
[    13.714] (II) Initializing built-in extension MIT-SHM
[    13.714] (II) Initializing built-in extension XInputExtension
[    13.714] (II) Initializing built-in extension XTEST
[    13.714] (II) Initializing built-in extension BIG-REQUESTS
[    13.714] (II) Initializing built-in extension SYNC
[    13.714] (II) Initializing built-in extension XKEYBOARD
[    13.714] (II) Initializing built-in extension XC-MISC
[    13.714] (II) Initializing built-in extension SECURITY
[    13.714] (II) Initializing built-in extension XINERAMA
[    13.714] (II) Initializing built-in extension XFIXES
[    13.714] (II) Initializing built-in extension RENDER
[    13.714] (II) Initializing built-in extension RANDR
[    13.714] (II) Initializing built-in extension COMPOSITE
[    13.714] (II) Initializing built-in extension DAMAGE
[    13.714] (II) Initializing built-in extension GESTURE
[    13.718] (II) AIGLX: Screen 0 is not DRI capable
[    13.720] [glesx] __glESXExtensionInit: No GL ES2.0 capable screen found!
[    13.727] (II) fglrx(0): Setting screen physical size to 423 x 317
[    13.775] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    13.785] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    13.785] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    13.785] (II) LoadModule: "evdev"
[    13.785] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    13.786] (II) Module evdev: vendor="X.Org Foundation"
[    13.786] 	compiled for 1.10.0.902, module version = 2.6.0
[    13.786] 	Module class: X.Org XInput Driver
[    13.786] 	ABI class: X.Org XInput driver, version 12.3
[    13.786] (II) Using input driver 'evdev' for 'Power Button'
[    13.786] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    13.786] (**) Power Button: always reports core events
[    13.786] (**) Power Button: Device: "/dev/input/event1"
[    13.786] (--) Power Button: Found keys
[    13.786] (II) Power Button: Configuring as keyboard
[    13.786] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[    13.786] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    13.786] (**) Option "xkb_rules" "evdev"
[    13.786] (**) Option "xkb_model" "pc105"
[    13.786] (**) Option "xkb_layout" "us"
[    13.789] (II) config/udev: Adding input device Sleep Button (/dev/input/event0)
[    13.789] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[    13.789] (II) Using input driver 'evdev' for 'Sleep Button'
[    13.789] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    13.789] (**) Sleep Button: always reports core events
[    13.789] (**) Sleep Button: Device: "/dev/input/event0"
[    13.789] (--) Sleep Button: Found keys
[    13.789] (II) Sleep Button: Configuring as keyboard
[    13.789] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input0/event0"
[    13.789] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD)
[    13.790] (**) Option "xkb_rules" "evdev"
[    13.790] (**) Option "xkb_model" "pc105"
[    13.790] (**) Option "xkb_layout" "us"
[    13.792] (II) config/udev: Adding input device Dell Dell USB Keyboard (/dev/input/event2)
[    13.792] (**) Dell Dell USB Keyboard: Applying InputClass "evdev keyboard catchall"
[    13.792] (II) Using input driver 'evdev' for 'Dell Dell USB Keyboard'
[    13.792] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    13.792] (**) Dell Dell USB Keyboard: always reports core events
[    13.792] (**) Dell Dell USB Keyboard: Device: "/dev/input/event2"
[    13.792] (--) Dell Dell USB Keyboard: Found keys
[    13.792] (II) Dell Dell USB Keyboard: Configuring as keyboard
[    13.792] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.1/usb4/4-1/4-1:1.0/input/input2/event2"
[    13.792] (II) XINPUT: Adding extended input device "Dell Dell USB Keyboard" (type: KEYBOARD)
[    13.792] (**) Option "xkb_rules" "evdev"
[    13.792] (**) Option "xkb_model" "pc105"
[    13.792] (**) Option "xkb_layout" "us"
[    13.793] (II) config/udev: Adding input device USB Optical Mouse (/dev/input/event3)
[    13.793] (**) USB Optical Mouse: Applying InputClass "evdev pointer catchall"
[    13.793] (II) Using input driver 'evdev' for 'USB Optical Mouse'
[    13.793] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    13.793] (**) USB Optical Mouse: always reports core events
[    13.793] (**) USB Optical Mouse: Device: "/dev/input/event3"
[    13.793] (--) USB Optical Mouse: Found 3 mouse buttons
[    13.793] (--) USB Optical Mouse: Found scroll wheel(s)
[    13.793] (--) USB Optical Mouse: Found relative axes
[    13.793] (--) USB Optical Mouse: Found x and y relative axes
[    13.793] (II) USB Optical Mouse: Configuring as mouse
[    13.793] (II) USB Optical Mouse: Adding scrollwheel support
[    13.793] (**) USB Optical Mouse: YAxisMapping: buttons 4 and 5
[    13.793] (**) USB Optical Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    13.793] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.1/usb4/4-2/4-2:1.0/input/input3/event3"
[    13.793] (II) XINPUT: Adding extended input device "USB Optical Mouse" (type: MOUSE)
[    13.793] (II) USB Optical Mouse: initialized for relative axes.
[    13.793] (**) USB Optical Mouse: (accel) keeping acceleration scheme 1
[    13.793] (**) USB Optical Mouse: (accel) acceleration profile 0
[    13.793] (**) USB Optical Mouse: (accel) acceleration factor: 2.000
[    13.793] (**) USB Optical Mouse: (accel) acceleration threshold: 4
[    13.794] (II) config/udev: Adding input device USB Optical Mouse (/dev/input/mouse0)
[    13.794] (II) No input driver/identifier specified (ignoring)
[    13.815] (II) fglrx(0): Restoring Recent Mode via PCS is not supported in RANDR 1.2 capable environments
[    14.449] (II) fglrx(0): Cannot get EDID information for CRT1
[    14.457] (II) fglrx(0): Cannot get EDID information for CRT1
[    14.466] (II) fglrx(0): Cannot get EDID information for CRT1
[    14.474] (II) fglrx(0): Cannot get EDID information for CRT1
[    76.924] (II) Power Button: Close
[    76.924] (II) UnloadModule: "evdev"
[    76.924] (II) Unloading evdev
[    76.976] (II) Sleep Button: Close
[    76.976] (II) UnloadModule: "evdev"
[    76.976] (II) Unloading evdev
[    77.008] (II) Dell Dell USB Keyboard: Close
[    77.008] (II) UnloadModule: "evdev"
[    77.008] (II) Unloading evdev
[    77.052] (II) USB Optical Mouse: Close
[    77.052] (II) UnloadModule: "evdev"
[    77.052] (II) Unloading evdev
[    77.257] (II) fglrx(0): Interrupt handler Shutdown.
[    77.406]  ddxSigGiveUp: Closing log
```

---

### Post by Dorsenstein on 2011-08-12
Did you install the driver for your graphics card?

This:
> **waqas300 said:**
> 
[    12.988] (II) Loading extension XFree86-VidModeExtension
[    12.988] (II) Loading extension XFree86-DGA


It seems like you're just loading XFree86, not the driver that's appropriate for your graphics card.

---

### Post by waqas300 on 2011-08-12
yes i have downloaded from here

[http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.42&lang=English](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.42&lang=English)

---

### Post by waqas300 on 2011-08-13
I have ATI Radeon 6670

---

### Post by kaldor on 2011-08-13
You should install the driver through the "Additional Drivers" application.

---

### Post by waqas300 on 2011-08-13
Its showing installed in additional drivers. is this the problem for black screen?:(

---

### Post by waqas300 on 2011-08-13
How do i make things right now?

---

### Post by realzippy on 2011-08-13
As kaldor said,you should try to install amd driver from hardware drivers
instead of downloading from amd/ati website.

---

### Post by mastablasta on 2011-08-13
> **waqas300 said:**
> How do i make things right now?

you need to clean the installed drivers. and then reinstall them from additional drivers application. those should be adapted a bit to work well with Ubuntu (no guarantee there).

have a look here on how to do it:

[https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch]("https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch")

FGLRX is proprietary (ATI/AMD driver) while -ati is opensource driver (should offer some basic support for the card though i am not sure how well it handles with these modern cards, but there should be at least some basic "safe mode" available). you can copy and paste the commands in the terminal (just saying in case you planned to type them :-) )

---

### Post by waqas300 on 2011-08-13
Ok now how do i revert things back? so that i can install it from the hardware side.:)

---

### Post by Mark Phelps on 2011-08-13
> **waqas300 said:**
> Ok now how do i revert things back? so that i can install it from the hardware side.:)

This is NOT Windows -- you don't install from the hardware side (where Windows detects the new hardware and prompts you for the drivers).

You have to install the drivers yourself.

---

### Post by realzippy on 2011-08-13
> **waqas300 said:**
> Ok now how do i revert things back? so that i can install it from the hardware side.:)
Open a terminal and run those commands:

```
sudo apt-get remove --purge xorg-driver-fglrx fglrx*
```
```
sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri fglrx-modaliases
```
```
sudo dpkg-reconfigure xserver-xorg
```
```
sudo apt-get install --reinstall xserver-xorg-core
```
Reboot,then go to system =>admin =>hardware/additional drivers    #@MarkPhelp: guess this is what OP calls hardware side...
and install the ati/amd driver from there...

---

### Post by waqas300 on 2011-08-14
sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri fglrx-modaliases

running this command says
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package fglrx-modaliases is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  fglrx

E: Package 'fglrx-modaliases' has no installation candidate



When i click activate from additional drivers its says

SystemError: installArchives() failed



And when through update manager its says


The package system is broken

Check if you are using third party repositories. If so disable them, since they are a common source of problems.
Furthermore run the following command in a Terminal: apt-get install -f

---

### Post by realzippy on 2011-08-14
So run
```
sudo apt-get install -f
```
as suggested...

---

### Post by waqas300 on 2011-08-14
> **realzippy said:**
> So run
```
sudo apt-get install -f
```
as suggested...


i did what it said now getting this error


Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  fglrx
The following NEW packages will be installed:
  fglrx
0 upgraded, 1 newly installed, 0 to remove and 120 not upgraded.
1 not fully installed or removed.
Need to get 0 B/22.1 MB of archives.
After this operation, 68.1 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 133929 files and directories currently installed.)
Unpacking fglrx (from .../fglrx_2%3a8.840-0ubuntu4_i386.deb) ...
/usr/share/ati/fglrx-uninstall.sh: 32: cannot create /etc/ati/fglrx-uninstall.log: Directory nonexistent

[Warning] Uninstall : inst_path_default or inst_path_override
 does not exist in /etc/ati.  This suggests that the ATI driver
 is not installed, the ATI driver is only partially installed,
 or the current ATI driver installed is an older version than the
 one this script was designed for.  Both files listed above are
 required for determining where installed files are located.
 To force uninstallation of the driver by guessing where the
 uninstallation files are located, set the force option
 re-run /usr/share/ati/fglrx-uninstall.sh (this is not recommended).

dpkg: error processing /var/cache/apt/archives/fglrx_2%3a8.840-0ubuntu4_i386.deb (--unpack):
 subprocess new pre-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/fglrx_2%3a8.840-0ubuntu4_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by realzippy on 2011-08-14
?
Open synaptics package manager,search for 
fglrx
and mark for complete removal,apply.

---

### Post by waqas300 on 2011-08-14
> **realzippy said:**
> ?
Open synaptics package manager,search for 
fglrx
and mark for complete removal,apply.

Did that too now what? :confused:

---

### Post by waqas300 on 2011-08-14
> **waqas300 said:**
> Did that too now what? :confused:

still shows ATI catalyst control center in system---preferences now what?:mad:

---

### Post by realzippy on 2011-08-14
Try "more agressive recipe" from that link kaldor gave:

```
sudo /usr/share/ati/fglrx-uninstall.sh  # (if it exists)
```
```
sudo apt-get remove --purge fglrx*
```
```
sudo apt-get remove --purge xserver-xorg-video-ati xserver-xorg-video-radeon 
```
```
sudo apt-get install xserver-xorg-video-ati
```
```
sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
```
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by waqas300 on 2011-08-15
Brother i did what you said now heres what


angel@ubuntu:~$ sudo /usr/share/ati/fglrx-uninstall.sh
One or more files have been altered since installation.
Uninstall will not be completed. See /etc/ati/fglrx-uninstall.log for details.
angel@ubuntu:~$ sudo apt-get remove --purge fglrx*
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'fglrx' for regex 'fglrx*'
Note, selecting 'fglrx-amdcccle' for regex 'fglrx*'
Note, selecting 'fglrx-driver' for regex 'fglrx*'
Note, selecting 'fglrx-kernel-source' for regex 'fglrx*'
Note, selecting 'fglrx-modaliases' for regex 'fglrx*'
Note, selecting 'xfree86-driver-fglrx' for regex 'fglrx*'
Note, selecting 'xorg-driver-fglrx' for regex 'fglrx*'
Note, selecting 'fglrx-control' for regex 'fglrx*'
Note, selecting 'fglrx-control-qt2' for regex 'fglrx*'
Note, selecting 'fglrx-dev' for regex 'fglrx*'
Note, selecting 'fglrx-driver-dev' for regex 'fglrx*'
Note, selecting 'xfree86-driver-fglrx-dev' for regex 'fglrx*'
Note, selecting 'xorg-driver-fglrx-dev' for regex 'fglrx*'
Package fglrx is not installed, so not removed
Package fglrx-amdcccle is not installed, so not removed
Package fglrx-dev is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 116 not upgraded.
angel@ubuntu:~$ sudo apt-get remove --purge xserver-xorg-video-ati xserver-xorg-video-radeon
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package xserver-xorg-video-ati is not installed, so not removed
Package xserver-xorg-video-radeon is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 116 not upgraded.
angel@ubuntu:~$ sudo apt-get install xserver-xorg-video-ati
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  xserver-xorg-video-mach64 xserver-xorg-video-r128 xserver-xorg-video-radeon
Suggested packages:
  firmware-linux
The following NEW packages will be installed:
  xserver-xorg-video-ati xserver-xorg-video-mach64 xserver-xorg-video-r128
  xserver-xorg-video-radeon
0 upgraded, 4 newly installed, 0 to remove and 116 not upgraded.
Need to get 0 B/578 kB of archives.
After this operation, 2,081 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Selecting previously deselected package xserver-xorg-video-r128.
(Reading database ... 133780 files and directories currently installed.)
Unpacking xserver-xorg-video-r128 (from .../xserver-xorg-video-r128_6.8.1-4ubuntu3_i386.deb) ...
Selecting previously deselected package xserver-xorg-video-mach64.
Unpacking xserver-xorg-video-mach64 (from .../xserver-xorg-video-mach64_6.8.2+git20101202.d60087f0-4ubuntu3_i386.deb) ...
Selecting previously deselected package xserver-xorg-video-radeon.
Unpacking xserver-xorg-video-radeon (from .../xserver-xorg-video-radeon_1%3a6.14.0-0ubuntu4.1_i386.deb) ...
Selecting previously deselected package xserver-xorg-video-ati.
Unpacking xserver-xorg-video-ati (from .../xserver-xorg-video-ati_1%3a6.14.0-0ubuntu4.1_i386.deb) ...
Processing triggers for man-db ...
Setting up xserver-xorg-video-r128 (6.8.1-4ubuntu3) ...
Setting up xserver-xorg-video-mach64 (6.8.2+git20101202.d60087f0-4ubuntu3) ...
Setting up xserver-xorg-video-radeon (1:6.14.0-0ubuntu4.1) ...
Setting up xserver-xorg-video-ati (1:6.14.0-0ubuntu4.1) ...
angel@ubuntu:~$ sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 3 reinstalled, 0 to remove and 116 not upgraded.
Need to get 0 B/4,097 kB of archives.
After this operation, 0 B of additional disk space will be used.
(Reading database ... 133814 files and directories currently installed.)
Preparing to replace libgl1-mesa-dri 7.10.2-0ubuntu2 (using .../libgl1-mesa-dri_7.10.2-0ubuntu2_i386.deb) ...
Unpacking replacement libgl1-mesa-dri ...
Preparing to replace libgl1-mesa-glx 7.10.2-0ubuntu2 (using .../libgl1-mesa-glx_7.10.2-0ubuntu2_i386.deb) ...
Unpacking replacement libgl1-mesa-glx ...
Preparing to replace xserver-xorg-core 2:1.10.1-1ubuntu1.1 (using .../xserver-xorg-core_2%3a1.10.1-1ubuntu1.1_i386.deb) ...
Unpacking replacement xserver-xorg-core ...
Processing triggers for man-db ...
Setting up libgl1-mesa-dri (7.10.2-0ubuntu2) ...
Setting up libgl1-mesa-glx (7.10.2-0ubuntu2) ...
Setting up xserver-xorg-core (2:1.10.1-1ubuntu1.1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
angel@ubuntu:~$ sudo dpkg-reconfigure xserver-xorg
angel@ubuntu:~$ lspci |more vga
00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller
 (rev 02)
00:01.0 PCI bridge: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root
 Port (rev 02)
00:03.0 Communication controller: Intel Corporation 82G33/G31/P35/P31 Express ME
I Controller (rev 02)
00:19.0 Ethernet controller: Intel Corporation 82566DC-2 Gigabit Network Connect
ion (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controll
er #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controll
er #5 (rev 02)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controll
er #6 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Control
ler #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller
 (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (r
ev 02)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (r
ev 02)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (r
ev 02)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (r
ev 02)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (r
ev 02)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controll
er #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controll
er #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controll
er #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Control
ler #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92)
00:1f.0 ISA bridge: Intel Corporation 82801IH (ICH9DH) LPC Interface Controller 
(rev 02)
00:1f.2 IDE interface: Intel Corporation 82801IR/IO/IH (ICH9R/DO/DH) 4 port SATA
 IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02)
00:1f.5 IDE interface: Intel Corporation 82801I (ICH9 Family) 2 port SATA IDE Co
ntroller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc Device 6758
01:00.1 Audio device: ATI Technologies Inc Device aa90
03:00.0 IDE interface: Marvell Technology Group Ltd. 88SE6101/6102 single-port P
ATA133 interface (rev b2)
vga: No such file or directory
angel@ubuntu:~$ lspci |more VGA
00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller
 (rev 02)
00:01.0 PCI bridge: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root
 Port (rev 02)
00:03.0 Communication controller: Intel Corporation 82G33/G31/P35/P31 Express ME
I Controller (rev 02)
00:19.0 Ethernet controller: Intel Corporation 82566DC-2 Gigabit Network Connect
ion (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controll
er #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controll
er #5 (rev 02)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controll
er #6 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Control
ler #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller
 (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (r
ev 02)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (r
ev 02)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (r
ev 02)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (r
ev 02)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (r
ev 02)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controll
er #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controll
er #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controll
er #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Control
ler #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92)
00:1f.0 ISA bridge: Intel Corporation 82801IH (ICH9DH) LPC Interface Controller 
(rev 02)
00:1f.2 IDE interface: Intel Corporation 82801IR/IO/IH (ICH9R/DO/DH) 4 port SATA
 IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02)
00:1f.5 IDE interface: Intel Corporation 82801I (ICH9 Family) 2 port SATA IDE Co
ntroller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc Device 6758
01:00.1 Audio device: ATI Technologies Inc Device aa90
03:00.0 IDE interface: Marvell Technology Group Ltd. 88SE6101/6102 single-port P
ATA133 interface (rev b2)
VGA: No such file or directory
angel@ubuntu:~$  
:confused:

---

### Post by realzippy on 2011-08-15
*Uninstall will not be completed. See /etc/ati/fglrx-uninstall.log for details.*

So,as the terminal suggests,have a look at that log file:

```
gedit /etc/ati/fglrx-uninstall.log
```

---

### Post by waqas300 on 2011-08-15
here is the uninstall log



*** ATI Catalyst(TM) Proprietary Driver Uninstall Log 2011-08-15 09:45:25 ***
File is missing from system /usr/share/doc/ati/ATI_LICENSE.TXT.
File is missing from system /usr/share/doc/ati/user-manual/index.html.
File is missing from system /usr/share/doc/ati/examples/etc/init.d/atieventsd.sh.
File is missing from system /usr/share/doc/ati/examples/etc/acpi/events/a-lid-aticonfig.
File is missing from system /usr/share/doc/ati/examples/etc/acpi/events/a-ac-aticonfig.
File is missing from system /usr/share/doc/ati/examples/etc/acpi/ati-powermode.sh.
File is missing from system /usr/share/doc/ati/articles/1gbhang.html.
File is missing from system /usr/share/doc/ati/articles/4461.html.
File is missing from system /usr/share/doc/ati/articles/4462.html.
File is missing from system /usr/share/doc/ati/articles/4463.html.
File is missing from system /usr/share/doc/ati/articles/4464.html.
File is missing from system /usr/share/doc/ati/articles/4469.html.
File is missing from system /usr/share/doc/ati/articles/4470.html.
File is missing from system /usr/share/doc/ati/articles/4475.html.
File is missing from system /usr/share/doc/ati/articles/4478.html.
File is missing from system /usr/share/doc/ati/articles/4479.html.
File is missing from system /usr/share/doc/ati/articles/4480.html.
File is missing from system /usr/share/doc/ati/articles/4481.html.
File is missing from system /usr/share/doc/ati/articles/4482.html.
File is missing from system /usr/share/doc/ati/articles/4483.html.
File is missing from system /usr/share/doc/ati/articles/4484.html.
File is missing from system /usr/share/doc/ati/articles/4485.html.
File is missing from system /usr/share/doc/ati/articles/corruptstereo.html.
File is missing from system /usr/share/doc/ati/articles/corruptvtswitch.html.
File is missing from system /usr/share/doc/ati/articles/devshm.html.
File is missing from system /usr/share/doc/ati/articles/dga3dhang.html.
File is missing from system /usr/share/doc/ati/articles/doom3corrupt.html.
File is missing from system /usr/share/doc/ati/articles/dualheadvideo.html.
File is missing from system /usr/share/doc/ati/articles/laptopsuspend.html.
File is missing from system /usr/share/doc/ati/articles/missingdrmheaders.html.
File is missing from system /usr/share/doc/ati/articles/mousecursorhang.html.
File is missing from system /usr/share/doc/ati/articles/no3d-aiw8500dv.html.
File is missing from system /usr/share/doc/ati/articles/no3d-kt400.html.
File is missing from system /usr/share/doc/ati/articles/nomembercount.html.
File is missing from system /usr/share/doc/ati/articles/pcie3dmemoryleak.html.
File is missing from system /usr/share/doc/ati/articles/r420blankdisplay.html.
File is missing from system /usr/share/doc/ati/articles/rv280dviblankdisplay.html.
File is missing from system /usr/share/doc/ati/articles/rv350springdale.html.
File is missing from system /usr/share/doc/ati/articles/secondheadcorruption.html.
File is missing from system /usr/share/doc/ati/articles/xf86_enodev.html.
File is missing from system /usr/share/doc/ati/articles/xrestartpcie.html.
File is missing from system /usr/share/doc/ati/articles/xvsatshift.html.
File is missing from system /usr/share/doc/ati/configure.html.
File is missing from system /usr/share/doc/ati/driverfaq.html.
File is missing from system /usr/share/doc/ati/index.html.
File is missing from system /usr/share/doc/ati/installer.html.
File is missing from system /usr/share/doc/ati/issues.html.
File is missing from system /usr/share/doc/ati/linuxfaq.html.
File is missing from system /usr/share/doc/ati/tips-linux.html.
File is missing from system /usr/share/man/man8/atieventsd.8.
File is missing from system /usr/lib/xorg/modules/linux/libfglrxdrm.so.
File is missing from system /usr/lib/xorg/modules/drivers/fglrx_drv.so.
File is missing from system /usr/lib/xorg/modules/glesx.so.
File is missing from system /usr/lib/xorg/modules/amdxmm.so.
File is missing from system /usr/lib/libAMDXvBA.cap.
File is missing from system /usr/lib/libAMDXvBA.so.1.0.
File is missing from system /usr/lib/libXvBAW.so.1.0.
File is missing from system /usr/lib/libatiadlxx.so.
File is missing from system /usr/lib/libaticalcl.so.
File is missing from system /usr/lib/libaticaldd.so.
File is missing from system /usr/lib/libaticalrt.so.
File is missing from system /usr/lib/libatiuki.so.1.0.
File is missing from system /usr/lib/libfglrx_dm.a.
File is missing from system /usr/lib/libfglrx_dm.so.1.0.
File is missing from system /usr/lib/fglrx/fglrx-libGL.so.1.2.
File is missing from system /usr/lib/fglrx/switchlibGL.
File is missing from system /usr/lib/fglrx/switchlibglx.
File is missing from system /usr/lib/dri/fglrx_dri.so.
File is missing from system /usr/lib/xorg/modules/extensions/fglrx/fglrx-libglx.so.
File is missing from system /usr/include/GL/glATI.h.
File is missing from system /usr/include/GL/glxATI.h.
File is missing from system /usr/include/ATI/GL/glx.h.
File is missing from system /usr/include/ATI/GL/glxext.h.
File is missing from system /usr/bin/fgl_glxgears.
File is missing from system /usr/bin/fglrxinfo.
File is missing from system /usr/bin/aticonfig.
File is missing from system /usr/bin/atiodcli.
File is missing from system /usr/bin/atiode.
File is missing from system /usr/src/ati/fglrx_sample_source.tgz.
File is missing from system /usr/sbin/amdnotifyui.
File is missing from system /usr/sbin/atieventsd.
File is missing from system /usr/sbin/atigetsysteminfo.sh.
File is missing from system /etc/ati/amdpcsdb.default.
File is missing from system /etc/ati/atiogl.xml.
File is missing from system /etc/ati/authatieventsd.sh.
File is missing from system /etc/ati/control.
File is missing from system /etc/ati/logo.xbm.example.
File is missing from system /etc/ati/logo_mask.xbm.example.
File is missing from system /etc/ati/signature.
File is missing from system /usr/X11R6/lib/modules/dri/fglrx_dri.so.
File is missing from system /etc/modprobe.d/blacklist-fglrx.conf.
File has been removed, //usr/lib/libGL.so.1.2, since last install.
One or more files have been altered since installation.
Uninstall will not be completed.

To force uninstall, removing all installed files without verification,
run /usr/share/ati/amd-uninstall.sh --force.

Forcing uninstall is not recommended and may cause system corruption.
:confused:

---

### Post by realzippy on 2011-08-15
?
Live is always dangerous.I would force uninstall.
Backup important data before.
```
sudo /usr/share/ati/amd-uninstall.sh --force
```

..but doubt that it works (uninstalling).
:

---

### Post by jeremy101 on 2011-08-15
Try uninstalling the driver via Additional Drivers and install the official ATI driver: [http://www2.ati.com/drivers/linux/ati-driver-installer-11-7-x86.x86_64.run]("http://www2.ati.com/drivers/linux/ati-driver-installer-11-7-x86.x86_64.run"). Hope this helps! :) BTW, I see you have files missing from your system. Run ```
sudo /usr/share/ati/amd-uninstall.sh --force
``` to force uninstall the driver. Install the driver from the download link and lets hope it works.

---

### Post by waqas300 on 2011-08-15
here i did as you guys suggested

angel@ubuntu:~$ sudo /usr/share/ati/amd-uninstall.sh --force
[sudo] password for angel: 
Forcing uninstall of ATI Catalyst(TM) Proprietary Driver.
No integrity verification is done.
cat: /usr/share/ati/libGLdir.txt: No such file or directory
ln: creating symbolic link `/libGL.so': File exists
rm: cannot remove `/usr/share/ati/libGLdir.txt': No such file or directory
restore of system environment completed

Error! There are no instances of module: fglrx
8.872 located in the DKMS tree.
Errors during DKMS module removal
Warning: No support for locale: en_US.utf8
Warning: No support for locale: en_US.utf8
Uninstall fglrx driver complete.
For detailed log of uninstall, please see /etc/ati/fglrx-uninstall.log
System must be rebooted to avoid system instability and potential data loss

---

### Post by waqas300 on 2011-08-15
And here is the uninstall log


*** ATI Catalyst(TM) Proprietary Driver Uninstall Log 2011-08-15 22:44:56 ***
Forcing uninstall.
Installed file is missing from system /usr/share/doc/ati/ATI_LICENSE.TXT.
Installed file is missing from system /usr/share/doc/ati/user-manual/index.html.
Installed file is missing from system /usr/share/doc/ati/examples/etc/init.d/atieventsd.sh.
Installed file is missing from system /usr/share/doc/ati/examples/etc/acpi/events/a-lid-aticonfig.
Installed file is missing from system /usr/share/doc/ati/examples/etc/acpi/events/a-ac-aticonfig.
Installed file is missing from system /usr/share/doc/ati/examples/etc/acpi/ati-powermode.sh.
Installed file is missing from system /usr/share/doc/ati/articles/1gbhang.html.
Installed file is missing from system /usr/share/doc/ati/articles/4461.html.
Installed file is missing from system /usr/share/doc/ati/articles/4462.html.
Installed file is missing from system /usr/share/doc/ati/articles/4463.html.
Installed file is missing from system /usr/share/doc/ati/articles/4464.html.
Installed file is missing from system /usr/share/doc/ati/articles/4469.html.
Installed file is missing from system /usr/share/doc/ati/articles/4470.html.
Installed file is missing from system /usr/share/doc/ati/articles/4475.html.
Installed file is missing from system /usr/share/doc/ati/articles/4478.html.
Installed file is missing from system /usr/share/doc/ati/articles/4479.html.
Installed file is missing from system /usr/share/doc/ati/articles/4480.html.
Installed file is missing from system /usr/share/doc/ati/articles/4481.html.
Installed file is missing from system /usr/share/doc/ati/articles/4482.html.
Installed file is missing from system /usr/share/doc/ati/articles/4483.html.
Installed file is missing from system /usr/share/doc/ati/articles/4484.html.
Installed file is missing from system /usr/share/doc/ati/articles/4485.html.
Installed file is missing from system /usr/share/doc/ati/articles/corruptstereo.html.
Installed file is missing from system /usr/share/doc/ati/articles/corruptvtswitch.html.
Installed file is missing from system /usr/share/doc/ati/articles/devshm.html.
Installed file is missing from system /usr/share/doc/ati/articles/dga3dhang.html.
Installed file is missing from system /usr/share/doc/ati/articles/doom3corrupt.html.
Installed file is missing from system /usr/share/doc/ati/articles/dualheadvideo.html.
Installed file is missing from system /usr/share/doc/ati/articles/laptopsuspend.html.
Installed file is missing from system /usr/share/doc/ati/articles/missingdrmheaders.html.
Installed file is missing from system /usr/share/doc/ati/articles/mousecursorhang.html.
Installed file is missing from system /usr/share/doc/ati/articles/no3d-aiw8500dv.html.
Installed file is missing from system /usr/share/doc/ati/articles/no3d-kt400.html.
Installed file is missing from system /usr/share/doc/ati/articles/nomembercount.html.
Installed file is missing from system /usr/share/doc/ati/articles/pcie3dmemoryleak.html.
Installed file is missing from system /usr/share/doc/ati/articles/r420blankdisplay.html.
Installed file is missing from system /usr/share/doc/ati/articles/rv280dviblankdisplay.html.
Installed file is missing from system /usr/share/doc/ati/articles/rv350springdale.html.
Installed file is missing from system /usr/share/doc/ati/articles/secondheadcorruption.html.
Installed file is missing from system /usr/share/doc/ati/articles/xf86_enodev.html.
Installed file is missing from system /usr/share/doc/ati/articles/xrestartpcie.html.
Installed file is missing from system /usr/share/doc/ati/articles/xvsatshift.html.
Installed file is missing from system /usr/share/doc/ati/configure.html.
Installed file is missing from system /usr/share/doc/ati/driverfaq.html.
Installed file is missing from system /usr/share/doc/ati/index.html.
Installed file is missing from system /usr/share/doc/ati/installer.html.
Installed file is missing from system /usr/share/doc/ati/issues.html.
Installed file is missing from system /usr/share/doc/ati/linuxfaq.html.
Installed file is missing from system /usr/share/doc/ati/tips-linux.html.
Installed file is missing from system /usr/share/man/man8/atieventsd.8.
Installed file is missing from system /usr/lib/xorg/modules/linux/libfglrxdrm.so.
Installed file is missing from system /usr/lib/xorg/modules/drivers/fglrx_drv.so.
Installed file is missing from system /usr/lib/xorg/modules/glesx.so.
Installed file is missing from system /usr/lib/xorg/modules/amdxmm.so.
Installed file is missing from system /usr/lib/libAMDXvBA.cap.
Installed file is missing from system /usr/lib/libAMDXvBA.so.1.0.
Installed file is missing from system /usr/lib/libXvBAW.so.1.0.
Installed file is missing from system /usr/lib/libatiadlxx.so.
Installed file is missing from system /usr/lib/libaticalcl.so.
Installed file is missing from system /usr/lib/libaticaldd.so.
Installed file is missing from system /usr/lib/libaticalrt.so.
Installed file is missing from system /usr/lib/libatiuki.so.1.0.
Installed file is missing from system /usr/lib/libfglrx_dm.a.
Installed file is missing from system /usr/lib/libfglrx_dm.so.1.0.
Installed file is missing from system /usr/lib/fglrx/fglrx-libGL.so.1.2.
Installed file is missing from system /usr/lib/fglrx/switchlibGL.
Installed file is missing from system /usr/lib/fglrx/switchlibglx.
Installed file is missing from system /usr/lib/dri/fglrx_dri.so.
Installed file is missing from system /usr/lib/xorg/modules/extensions/fglrx/fglrx-libglx.so.
Installed file is missing from system /usr/include/GL/glATI.h.
Installed file is missing from system /usr/include/GL/glxATI.h.
Installed file is missing from system /usr/include/ATI/GL/glx.h.
Installed file is missing from system /usr/include/ATI/GL/glxext.h.
Installed file is missing from system /usr/bin/fgl_glxgears.
Installed file is missing from system /usr/bin/fglrxinfo.
Installed file is missing from system /usr/bin/aticonfig.
Installed file is missing from system /usr/bin/atiodcli.
Installed file is missing from system /usr/bin/atiode.
Installed file is missing from system /usr/src/ati/fglrx_sample_source.tgz.
Installed file is missing from system /usr/sbin/amdnotifyui.
Installed file is missing from system /usr/sbin/atieventsd.
Installed file is missing from system /usr/sbin/atigetsysteminfo.sh.
Installed file is missing from system /etc/ati/amdpcsdb.default.
Installed file is missing from system /etc/ati/atiogl.xml.
Installed file is missing from system /etc/ati/authatieventsd.sh.
Installed file is missing from system /etc/ati/control.
Installed file is missing from system /etc/ati/logo.xbm.example.
Installed file is missing from system /etc/ati/logo_mask.xbm.example.
Installed file is missing from system /etc/ati/signature.
Installed file is missing from system /usr/X11R6/lib/modules/dri/fglrx_dri.so.
Installed file is missing from system /etc/modprobe.d/blacklist-fglrx.conf.

---

### Post by realzippy on 2011-08-15
Guess it is okay after reboot.
control center still there?

---

### Post by waqas300 on 2011-08-16
> **realzippy said:**
> Guess it is okay after reboot.
control center still there?


No the control center is not there :)

---

### Post by realzippy on 2011-08-16
So everything is ok now?

---

### Post by waqas300 on 2011-08-16
So whats next? :-)

---

### Post by realzippy on 2011-08-17
System=?>Admin=>AdditionalDrivers
Install that offered ATI driver,reboot.

Btw,I have no idea if that driver works for your card/system.
Just wanted to help uninstalling the manually installed ATI drivers.
Although some forum members claim "ATI drivers are great meanwhile",
I doubt this.Friend of mine,only has trouble with his ATI
and uses the free driver.
Interesting thing is I never "see" those ATI fans when it comes to trouble in Catalyst threads here in the forum....

---

### Post by mastablasta on 2011-08-17
> **realzippy said:**
> Although some forum members claim "ATI drivers are great meanwhile",
I doubt this.Friend of mine,only has trouble with his ATI
and uses the free driver.

Free drivers have their limits. For some old ATI cards they work perfect while others not good at all. This are improving through time.
 
> 
Interesting thing is I never "see" those ATI fans when it comes to trouble in Catalyst threads here in the forum....
 
Perhaps they do not have issues as they are not using the latest and greatest of the AMD cards. Those don't have the good drivers yet. AMD works together with ubuntu and their linux driver releases are scheduled for Ubuntu release. at least they were a couple of times. Anyway 5x series and some 6x series should already have full support. some new 6x series have might have issues as propper drivers are not made yet. i am sure they will be in time for 11.10.
 
but yes, you would expect that the fans would know more about thier card and as ssuch could offer better help. i guess this is not the case.

---

### Post by waqas300 on 2011-08-18
AMD just updated the drivers

[http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.42&lang=English](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.42&lang=English)

Should i give it a try? :(

---

### Post by realzippy on 2011-08-18
??
So have you tried
System=?>Admin=>AdditionalDrivers  now??

---

### Post by waqas300 on 2011-08-18
i cannot find Additional drivers in system administration:confused:

---

### Post by realzippy on 2011-08-18
maybe it is called "hardware drivers"

but you can also run
```
jockey-gtk
```
to open it.

---

### Post by waqas300 on 2011-08-18
No it was there but gone now :(

---

### Post by waqas300 on 2011-08-18
Jockey-gtk is not working:confused:
Error stating file '/home/angel/jockey-gtk': No such file or directory

---

### Post by realzippy on 2011-08-18
??????????

then run 
```
sudo apt-get install jockey-gtk
```

---

### Post by waqas300 on 2011-08-18
> **realzippy said:**
> ??????????

then run 
```
sudo apt-get install jockey-gtk
```

Wow thanks :P

---

### Post by waqas300 on 2011-08-18
Same black screen problem after ubuntu loads.

Additional driver says this driver is activated and currently in use for ATI.:confused:

---

### Post by waqas300 on 2011-08-18
[    13.685] 
X.Org X Server 1.10.1
Release Date: 2011-04-15
[    13.685] X Protocol Version 11, Revision 0
[    13.685] Build Operating System: Linux 2.6.24-27-server i686 Ubuntu
[    13.685] Current Operating System: Linux ubuntu 2.6.38-10-generic #46-Ubuntu SMP Tue Jun 28 15:05:41 UTC 2011 i686
[    13.685] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.38-10-generic root=UUID=08114BE14EF585E9 loop=/ubuntu/disks/root.disk ro quiet splash
[    13.685] Build Date: 21 May 2011  11:38:35AM
[    13.685] xorg-server 2:1.10.1-1ubuntu1.1 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[    13.685] Current version of pixman: 0.20.2
[    13.685] 	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
[    13.685] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    13.686] (==) Log file: "/var/log/Xorg.0.log", Time: Thu Aug 18 23:03:13 2011
[    13.686] (==) Using config file: "/etc/X11/xorg.conf"
[    13.686] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    13.686] (==) ServerLayout "aticonfig Layout"
[    13.686] (**) |-->Screen "aticonfig-Screen[0]-0" (0)
[    13.686] (**) |   |-->Monitor "aticonfig-Monitor[0]-0"
[    13.686] (**) |   |-->Device "aticonfig-Device[0]-0"
[    13.686] (==) Automatically adding devices
[    13.686] (==) Automatically enabling devices
[    13.686] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    13.686] 	Entry deleted from font path.
[    13.686] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    13.686] 	Entry deleted from font path.
[    13.686] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    13.687] 	Entry deleted from font path.
[    13.687] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    13.687] 	Entry deleted from font path.
[    13.687] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    13.687] 	Entry deleted from font path.
[    13.687] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[    13.687] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    13.687] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    13.687] (II) Loader magic: 0x81ffde0
[    13.687] (II) Module ABI versions:
[    13.687] 	X.Org ANSI C Emulation: 0.4
[    13.687] 	X.Org Video Driver: 10.0
[    13.687] 	X.Org XInput driver : 12.3
[    13.687] 	X.Org Server Extension : 5.0
[    13.697] (--) PCI:*(0:1:0:0) 1002:6758:1682:3181 rev 0, Mem @ 0x80000000/268435456, 0x90100000/131072, I/O @ 0x00002000/256, BIOS @ 0x????????/131072
[    13.697] (WW) Open ACPI failed (/var/run/acpid.socket) (No such file or directory)
[    13.697] (II) "extmod" will be loaded by default.
[    13.697] (II) "dbe" will be loaded by default.
[    13.697] (II) "glx" will be loaded. This was enabled by default and also specified in the config file.
[    13.697] (II) "record" will be loaded by default.
[    13.697] (II) "dri" will be loaded by default.
[    13.697] (II) "dri2" will be loaded by default.
[    13.697] (II) LoadModule: "glx"
[    13.707] (II) Loading /usr/lib/xorg/extra-modules/modules/extensions/fglrx/libglx.so
[    13.709] (II) Module glx: vendor="FireGL - ATI Technologies Inc."
[    13.709] 	compiled for 6.9.0, module version = 1.0.0
[    13.710] (II) Loading extension GLX
[    13.710] (II) LoadModule: "extmod"
[    13.788] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    13.788] (II) Module extmod: vendor="X.Org Foundation"
[    13.788] 	compiled for 1.10.1, module version = 1.0.0
[    13.788] 	Module class: X.Org Server Extension
[    13.788] 	ABI class: X.Org Server Extension, version 5.0
[    13.788] (II) Loading extension MIT-SCREEN-SAVER
[    13.788] (II) Loading extension XFree86-VidModeExtension
[    13.788] (II) Loading extension XFree86-DGA
[    13.788] (II) Loading extension DPMS
[    13.788] (II) Loading extension XVideo
[    13.788] (II) Loading extension XVideo-MotionCompensation
[    13.788] (II) Loading extension X-Resource
[    13.788] (II) LoadModule: "dbe"
[    13.788] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    13.789] (II) Module dbe: vendor="X.Org Foundation"
[    13.789] 	compiled for 1.10.1, module version = 1.0.0
[    13.789] 	Module class: X.Org Server Extension
[    13.789] 	ABI class: X.Org Server Extension, version 5.0
[    13.789] (II) Loading extension DOUBLE-BUFFER
[    13.789] (II) LoadModule: "record"
[    13.789] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    13.789] (II) Module record: vendor="X.Org Foundation"
[    13.789] 	compiled for 1.10.1, module version = 1.13.0
[    13.789] 	Module class: X.Org Server Extension
[    13.789] 	ABI class: X.Org Server Extension, version 5.0
[    13.789] (II) Loading extension RECORD
[    13.789] (II) LoadModule: "dri"
[    13.789] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    13.789] (II) Module dri: vendor="X.Org Foundation"
[    13.789] 	compiled for 1.10.1, module version = 1.0.0
[    13.790] 	ABI class: X.Org Server Extension, version 5.0
[    13.790] (II) Loading extension XFree86-DRI
[    13.790] (II) LoadModule: "dri2"
[    13.790] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    13.790] (II) Module dri2: vendor="X.Org Foundation"
[    13.790] 	compiled for 1.10.1, module version = 1.2.0
[    13.790] 	ABI class: X.Org Server Extension, version 5.0
[    13.790] (II) Loading extension DRI2
[    13.790] (II) LoadModule: "fglrx"
[    13.790] (II) Loading /usr/lib/xorg/extra-modules/modules/drivers/fglrx_drv.so
[    13.824] (II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
[    13.824] 	compiled for 1.4.99.906, module version = 8.84.60
[    13.824] 	Module class: X.Org Video Driver
[    13.825] (II) Loading sub module "fglrxdrm"
[    13.825] (II) LoadModule: "fglrxdrm"
[    13.825] (II) Loading /usr/lib/xorg/extra-modules/modules/linux/libfglrxdrm.so
[    13.825] (II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
[    13.825] 	compiled for 1.4.99.906, module version = 8.84.60
[    13.825] (II) ATI Proprietary Linux Driver Version Identifier:8.84.60
[    13.825] (II) ATI Proprietary Linux Driver Release Identifier: 8.84.6                               
[    13.825] (II) ATI Proprietary Linux Driver Build Date: Mar 24 2011 19:27:41
[    13.825] (++) using VT number 7

[    13.827] (WW) Falling back to old probe method for fglrx
[    13.835] (II) Loading PCS database from /etc/ati/amdpcsdb
[    13.836] (--) Chipset Supported AMD Graphics Processor (0x6758) found
[    13.836] (WW) fglrx: No matching Device section for instance (BusID PCI:0@1:0:1) found
[    13.836] (II) AMD Video driver is running on a device belonging to a group targeted for this release
[    13.836] (II) AMD Video driver is signed
[    13.836] (II) Loading /usr/lib/xorg/extra-modules/modules/drivers/fglrx_drv.so
[    13.836] (II) Loading /usr/lib/xorg/extra-modules/modules/linux/libfglrxdrm.so
[    13.836] (II) fglrx(0): pEnt->device->identifier=0x9f27420
[    13.836] (II) fglrx(0): === [xdl_xs110_atiddxPreInit] === begin
[    13.837] (II) Loading sub module "vgahw"
[    13.837] (II) LoadModule: "vgahw"
[    13.837] (II) Loading /usr/lib/xorg/modules/libvgahw.so
[    13.837] (II) Module vgahw: vendor="X.Org Foundation"
[    13.837] 	compiled for 1.10.1, module version = 0.1.0
[    13.837] 	ABI class: X.Org Video Driver, version 10.0
[    13.837] (**) fglrx(0): Depth 24, (--) framebuffer bpp 32
[    13.837] (II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[    13.837] (==) fglrx(0): Default visual is TrueColor
[    13.837] (**) fglrx(0): Option "DPMS" "true"
[    13.837] (==) fglrx(0): RGB weight 888
[    13.837] (II) fglrx(0): Using 8 bits per RGB 
[    13.837] (==) fglrx(0): Buffer Tiling is ON
[    13.837] (II) Loading sub module "fglrxdrm"
[    13.837] (II) LoadModule: "fglrxdrm"
[    13.837] (II) Loading /usr/lib/xorg/extra-modules/modules/linux/libfglrxdrm.so
[    13.838] (II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
[    13.838] 	compiled for 1.4.99.906, module version = 8.84.60
[    13.839] ukiDynamicMajor: found major device number 250
[    13.839] ukiDynamicMajor: found major device number 250
[    13.839] ukiOpenByBusid: Searching for BusID PCI:1:0:0
[    13.839] ukiOpenDevice: node name is /dev/ati/card0
[    13.839] ukiOpenDevice: open result is 10, (OK)
[    13.839] ukiOpenByBusid: ukiOpenMinor returns 10
[    13.839] ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
[    13.840] (==) fglrx(0): NoAccel = NO
[    13.840] (==) fglrx(0): ATI 2D Acceleration Architecture enabled
[    13.840] (--) fglrx(0): Chipset: "AMD Radeon HD 6600 Series" (Chipset = 0x6758)
[    13.840] (--) fglrx(0): (PciSubVendor = 0x1682, PciSubDevice = 0x3181)
[    13.840] (==) fglrx(0): board vendor info: third party graphics adapter - NOT original ATI
[    13.840] (--) fglrx(0): Linear framebuffer (phys) at 0x80000000
[    13.840] (--) fglrx(0): MMIO registers at 0x90100000
[    13.840] (--) fglrx(0): I/O port at 0x00002000
[    13.840] (==) fglrx(0): ROM-BIOS at 0x000c0000
[    13.840] (II) fglrx(0): AC Adapter is used
[    13.844] (II) fglrx(0): Primary V_BIOS segment is: 0xc000
[    14.030] (II) Loading sub module "vbe"
[    14.030] (II) LoadModule: "vbe"
[    14.030] (II) Loading /usr/lib/xorg/modules/libvbe.so
[    14.030] (II) Module vbe: vendor="X.Org Foundation"
[    14.030] 	compiled for 1.10.1, module version = 1.1.0
[    14.030] 	ABI class: X.Org Video Driver, version 10.0
[    14.030] (II) fglrx(0): VESA BIOS detected
[    14.030] (II) fglrx(0): VESA VBE Version 3.0
[    14.030] (II) fglrx(0): VESA VBE Total Mem: 16384 kB
[    14.030] (II) fglrx(0): VESA VBE OEM: AMD ATOMBIOS
[    14.030] (II) fglrx(0): VESA VBE OEM Software Rev: 13.12
[    14.030] (II) fglrx(0): VESA VBE OEM Vendor: (C) 1988-2010, AMD Technologies Inc. 
[    14.031] (II) fglrx(0): VESA VBE OEM Product: TURKS
[    14.031] (II) fglrx(0): VESA VBE OEM Product Rev: 01.00
[    14.068] (II) fglrx(0): ATI Video BIOS revision 9 or later detected
[    14.069] (--) fglrx(0): Video RAM: 1048576 kByte, Type: DDR3
[    14.069] (II) fglrx(0): PCIE card detected
[    14.069] (--) fglrx(0): Using per-process page tables (PPPT) as GART.
[    14.069] (WW) fglrx(0): board is an unknown third party board, chipset is supported
[    14.075] (II) fglrx(0): Using adapter: 1:0.0.
[    14.112] (II) fglrx(0): [FB] MC range(MCFBBase = 0xf00000000, MCFBSize = 0x40000000)
[    14.197] (II) fglrx(0): Interrupt handler installed at IRQ 49.
[    14.197] (II) fglrx(0): RandR 1.2 support is enabled!
[    14.197] (II) fglrx(0): RandR 1.2 rotation support is enabled!
[    14.197] (==) fglrx(0): Center Mode is disabled 
[    14.197] (II) Loading sub module "fb"
[    14.197] (II) LoadModule: "fb"
[    14.197] (II) Loading /usr/lib/xorg/modules/libfb.so
[    14.197] (II) Module fb: vendor="X.Org Foundation"
[    14.197] 	compiled for 1.10.1, module version = 1.0.0
[    14.197] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    14.197] (II) Loading sub module "ddc"
[    14.197] (II) LoadModule: "ddc"
[    14.197] (II) Module "ddc" already built-in
[    14.339] (II) fglrx(0): Finished Initialize PPLIB!
[    14.339] (II) fglrx(0): Output DFP1 using monitor section aticonfig-Monitor[0]-0
[    14.339] (II) fglrx(0): Output DFP2 has no monitor section
[    14.339] (II) fglrx(0): Output DFP3 has no monitor section
[    14.340] (II) fglrx(0): Output CRT1 has no monitor section
[    14.340] (II) Loading sub module "ddc"
[    14.340] (II) LoadModule: "ddc"
[    14.340] (II) Module "ddc" already built-in
[    14.340] (II) fglrx(0): Connected Display0: CRT1
[    14.340] (II) fglrx(0):  Display0: Failed to get EDID information. 
[    14.344] (II) fglrx(0): EDID for output DFP1
[    14.344] (II) fglrx(0): EDID for output DFP2
[    14.344] (II) fglrx(0): EDID for output DFP3
[    14.344] (II) fglrx(0): Cannot get EDID information for CRT1
[    14.344] (II) fglrx(0): EDID for output CRT1
[    14.344] (II) fglrx(0): Not using mode "640x350" (vrefresh out of range)
[    14.344] (II) fglrx(0): Not using mode "640x400" (vrefresh out of range)
[    14.344] (II) fglrx(0): Not using mode "720x400" (vrefresh out of range)
[    14.344] (II) fglrx(0): Not using mode "640x480" (vrefresh out of range)
[    14.344] (II) fglrx(0): Not using mode "640x480" (vrefresh out of range)
[    14.344] (II) fglrx(0): Not using mode "640x480" (vrefresh out of range)
[    14.344] (II) fglrx(0): Not using mode "800x600" (vrefresh out of range)
[    14.344] (II) fglrx(0): Not using mode "800x600" (vrefresh out of range)
[    14.344] (II) fglrx(0): Not using mode "800x600" (vrefresh out of range)
[    14.344] (II) fglrx(0): Not using mode "800x600" (vrefresh out of range)
[    14.344] (II) fglrx(0): Not using mode "800x600" (vrefresh out of range)
[    14.344] (II) fglrx(0): Not using mode "848x480" (unknown reason)
[    14.344] (II) fglrx(0): Not using mode "1024x768i" (vrefresh out of range)
[    14.344] (II) fglrx(0): Not using mode "1024x768" (vrefresh out of range)
[    14.344] (II) fglrx(0): Not using mode "1024x768" (vrefresh out of range)
[    14.344] (II) fglrx(0): Not using mode "1024x768" (vrefresh out of range)
[    14.344] (II) fglrx(0): Not using mode "1024x768" (vrefresh out of range)
[    14.344] (II) fglrx(0): Not using mode "1152x864" (vrefresh out of range)
[    14.344] (II) fglrx(0): Not using mode "1280x768" (monitor doesn't support reduced blanking)
[    14.344] (II) fglrx(0): Not using mode "1280x768" (vrefresh out of range)
[    14.344] (II) fglrx(0): Not using mode "1280x768" (vrefresh out of range)
[    14.344] (II) fglrx(0): Not using mode "1280x768" (vrefresh out of range)
[    14.344] (II) fglrx(0): Not using mode "1280x800" (monitor doesn't support reduced blanking)
[    14.344] (II) fglrx(0): Not using mode "1280x800" (vrefresh out of range)
[    14.344] (II) fglrx(0): Not using mode "1280x800" (vrefresh out of range)
[    14.344] (II) fglrx(0): Not using mode "1280x800" (vrefresh out of range)
[    14.344] (II) fglrx(0): Not using mode "1280x960" (unknown reason)
[    14.344] (II) fglrx(0): Not using mode "1280x960" (vrefresh out of range)
[    14.344] (II) fglrx(0): Not using mode "1280x960" (vrefresh out of range)
[    14.344] (II) fglrx(0): Not using mode "1280x1024" (vrefresh out of range)
[    14.344] (II) fglrx(0): Not using mode "1280x1024" (vrefresh out of range)
[    14.344] (II) fglrx(0): Not using mode "1280x1024" (vrefresh out of range)
[    14.344] (II) fglrx(0): Not using mode "1360x768" (vrefresh out of range)
[    14.344] (II) fglrx(0): Not using mode "1400x1050" (monitor doesn't support reduced blanking)
[    14.344] (II) fglrx(0): Not using mode "1400x1050" (unknown reason)
[    14.344] (II) fglrx(0): Not using mode "1400x1050" (vrefresh out of range)
[    14.344] (II) fglrx(0): Not using mode "1400x1050" (vrefresh out of range)
[    14.344] (II) fglrx(0): Not using mode "1400x1050" (vrefresh out of range)
[    14.344] (II) fglrx(0): Not using mode "1440x900" (monitor doesn't support reduced blanking)
[    14.344] (II) fglrx(0): Not using mode "1440x900" (vrefresh out of range)
[    14.344] (II) fglrx(0): Not using mode "1440x900" (vrefresh out of range)
[    14.344] (II) fglrx(0): Not using mode "1440x900" (vrefresh out of range)
[    14.344] (II) fglrx(0): Not using mode "1600x1200" (vrefresh out of range)
[    14.344] (II) fglrx(0): Not using mode "1600x1200" (vrefresh out of range)
[    14.344] (II) fglrx(0): Not using mode "1600x1200" (vrefresh out of range)
[    14.344] (II) fglrx(0): Not using mode "1600x1200" (vrefresh out of range)
[    14.344] (II) fglrx(0): Not using mode "1600x1200" (vrefresh out of range)
[    14.344] (II) fglrx(0): Not using mode "1680x1050" (width too large for virtual size)
[    14.344] (II) fglrx(0): Not using mode "1680x1050" (width too large for virtual size)
[    14.344] (II) fglrx(0): Not using mode "1680x1050" (width too large for virtual size)
[    14.344] (II) fglrx(0): Not using mode "1680x1050" (width too large for virtual size)
[    14.344] (II) fglrx(0): Not using mode "1680x1050" (width too large for virtual size)
[    14.345] (II) fglrx(0): Not using mode "1792x1344" (width too large for virtual size)
[    14.345] (II) fglrx(0): Not using mode "1792x1344" (width too large for virtual size)
[    14.345] (II) fglrx(0): Not using mode "1792x1344" (width too large for virtual size)
[    14.345] (II) fglrx(0): Not using mode "1856x1392" (width too large for virtual size)
[    14.345] (II) fglrx(0): Not using mode "1856x1392" (width too large for virtual size)
[    14.345] (II) fglrx(0): Not using mode "1856x1392" (width too large for virtual size)
[    14.345] (II) fglrx(0): Not using mode "1920x1200" (width too large for virtual size)
[    14.345] (II) fglrx(0): Not using mode "1920x1200" (width too large for virtual size)
[    14.345] (II) fglrx(0): Not using mode "1920x1200" (width too large for virtual size)
[    14.345] (II) fglrx(0): Not using mode "1920x1200" (width too large for virtual size)
[    14.345] (II) fglrx(0): Not using mode "1920x1200" (width too large for virtual size)
[    14.345] (II) fglrx(0): Not using mode "1920x1440" (width too large for virtual size)
[    14.345] (II) fglrx(0): Not using mode "1920x1440" (width too large for virtual size)
[    14.345] (II) fglrx(0): Not using mode "1920x1440" (width too large for virtual size)
[    14.345] (II) fglrx(0): Not using mode "2560x1600" (width too large for virtual size)
[    14.345] (II) fglrx(0): Not using mode "2560x1600" (width too large for virtual size)
[    14.345] (II) fglrx(0): Not using mode "2560x1600" (width too large for virtual size)
[    14.345] (II) fglrx(0): Not using mode "2560x1600" (width too large for virtual size)
[    14.345] (II) fglrx(0): Not using mode "2560x1600" (width too large for virtual size)
[    14.345] (II) fglrx(0): Printing probed modes for output CRT1
[    14.345] (II) fglrx(0): Modeline "1600x1200"x60.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz)
[    14.345] (II) fglrx(0): Modeline "1400x1050"x60.0  122.61  1400 1488 1640 1880  1050 1051 1054 1087 -hsync +vsync (65.2 kHz)
[    14.345] (II) fglrx(0): Modeline "1600x900"x60.0  108.00  1600 1624 1704 1800  900 901 904 1000 +hsync +vsync (60.0 kHz)
[    14.345] (II) fglrx(0): Modeline "1360x1024"x60.0  116.01  1360 1448 1592 1824  1024 1025 1028 1060 -hsync +vsync (63.6 kHz)
[    14.345] (II) fglrx(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    14.345] (II) fglrx(0): Modeline "1440x900"x60.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
[    14.345] (II) fglrx(0): Modeline "1280x960"x60.0  102.10  1280 1360 1496 1712  960 961 964 994 -hsync +vsync (59.6 kHz)
[    14.345] (II) fglrx(0): Modeline "1366x768"x60.0   85.50  1366 1436 1579 1792  768 771 774 798 +hsync +vsync (47.7 kHz)
[    14.345] (II) fglrx(0): Modeline "1360x768"x60.0   85.50  1360 1424 1536 1792  768 771 777 795 +hsync +vsync (47.7 kHz)
[    14.345] (II) fglrx(0): Modeline "1280x800"x60.0   83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync (49.7 kHz)
[    14.345] (II) fglrx(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 -hsync +vsync (53.7 kHz)
[    14.345] (II) fglrx(0): Modeline "1280x768"x60.0   79.50  1280 1344 1472 1664  768 771 778 798 -hsync +vsync (47.8 kHz)
[    14.345] (II) fglrx(0): Modeline "1280x720"x60.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz)
[    14.345] (II) fglrx(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    14.345] (II) fglrx(0): Modeline "800x600"x60.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    14.345] (II) fglrx(0): Modeline "720x480"x60.0   27.03  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz)
[    14.345] (II) fglrx(0): Modeline "640x480"x60.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    14.345] (II) fglrx(0): Output DFP1 disconnected
[    14.345] (II) fglrx(0): Output DFP2 disconnected
[    14.345] (II) fglrx(0): Output DFP3 disconnected
[    14.345] (II) fglrx(0): Output CRT1 connected
[    14.345] (II) fglrx(0): Using exact sizes for initial modes
[    14.345] (II) fglrx(0): Output CRT1 using initial mode 1600x1200
[    14.345] (II) fglrx(0): DPI set to (96, 96)
[    14.345] (II) fglrx(0): Eyefinity capable adapter detected.
[    14.345] (II) fglrx(0): Adapter AMD Radeon HD 6600 Series has 3 configurable heads and 1 displays connected.
[    14.345] (==) fglrx(0):  PseudoColor visuals disabled
[    14.345] (II) Loading sub module "ramdac"
[    14.345] (II) LoadModule: "ramdac"
[    14.345] (II) Module "ramdac" already built-in
[    14.345] (==) fglrx(0): NoDRI = NO
[    14.345] (==) fglrx(0): Capabilities: 0x00000000
[    14.345] (==) fglrx(0): CapabilitiesEx: 0x00000000
[    14.345] (==) fglrx(0): OpenGL ClientDriverName: "fglrx_dri.so"
[    14.345] (==) fglrx(0): UseFastTLS=0
[    14.346] (==) fglrx(0): BlockSignalsOnLock=1
[    14.346] (--) Depth 24 pixmap format is 32 bpp
[    14.346] (II) Loading extension ATIFGLRXDRI
[    14.346] (II) fglrx(0): doing swlDriScreenInit
[    14.346] (II) fglrx(0): swlDriScreenInit for fglrx driver
[    14.346] ukiDynamicMajor: found major device number 250
[    14.346] ukiDynamicMajor: found major device number 250
[    14.346] ukiDynamicMajor: found major device number 250
[    14.346] ukiOpenByBusid: Searching for BusID PCI:1:0:0
[    14.346] ukiOpenDevice: node name is /dev/ati/card0
[    14.346] ukiOpenDevice: open result is 15, (OK)
[    14.346] ukiOpenByBusid: ukiOpenMinor returns 15
[    14.346] ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
[    14.346] (II) fglrx(0): [uki] DRM interface version 1.0
[    14.346] (II) fglrx(0): [uki] created "fglrx" driver at busid "PCI:1:0:0"
[    14.346] (II) fglrx(0): [uki] added 8192 byte SAREA at 0x2000
[    14.346] (II) fglrx(0): [uki] mapped SAREA 0x2000 to 0xb780c000
[    14.346] (II) fglrx(0): [uki] framebuffer handle = 0x3000
[    14.346] (II) fglrx(0): [uki] added 1 reserved context for kernel
[    14.346] (II) fglrx(0): swlDriScreenInit done
[    14.346] (II) fglrx(0): Kernel Module Version Information:
[    14.346] (II) fglrx(0):     Name: fglrx
[    14.346] (II) fglrx(0):     Version: 8.84.60
[    14.346] (II) fglrx(0):     Date: Mar 24 2011
[    14.346] (II) fglrx(0):     Desc: ATI FireGL DRM kernel module
[    14.346] (II) fglrx(0): Kernel Module version matches driver.
[    14.346] (II) fglrx(0): Kernel Module Build Time Information:
[    14.346] (II) fglrx(0):     Build-Kernel UTS_RELEASE:        2.6.38-10-generic
[    14.346] (II) fglrx(0):     Build-Kernel MODVERSIONS:        yes
[    14.346] (II) fglrx(0):     Build-Kernel __SMP__:            yes
[    14.346] (II) fglrx(0):     Build-Kernel PAGE_SIZE:          0x1000
[    14.346] (II) fglrx(0): [uki] register handle = 0x00004000
[    14.363] (II) fglrx(0): DRI initialization successfull
[    14.363] (II) fglrx(0): FBADPhys: 0xf00000000 FBMappedSize: 0x01004000
[    14.363] (==) fglrx(0): Backing store disabled
[    14.363] (II) Loading extension FGLRXEXTENSION
[    14.363] (**) fglrx(0): DPMS enabled
[    14.364] (II) fglrx(0): Initialized in-driver Xinerama extension
[    14.364] (**) fglrx(0): Textured Video is enabled.
[    14.364] (II) LoadModule: "glesx"
[    14.364] (II) Loading /usr/lib/xorg/extra-modules/modules/glesx.so
[    14.365] (II) Module glesx: vendor="X.Org Foundation"
[    14.365] 	compiled for 1.4.99.906, module version = 1.0.0
[    14.365] (II) Loading extension GLESX
[    14.365] (II) fglrx(0): GLESX enableFlags = 592
[    14.365] (II) fglrx(0): GLESX is enabled
[    14.365] (II) LoadModule: "amdxmm"
[    14.366] (II) Loading /usr/lib/xorg/extra-modules/modules/amdxmm.so
[    14.366] (II) Module amdxmm: vendor="X.Org Foundation"
[    14.366] 	compiled for 1.4.99.906, module version = 2.0.0
[    14.421] (II) Loading extension AMDXVOPL
[    14.421] (II) Loading extension AMDXVBA
[    14.422] (II) fglrx(0): UVD feature is enabled(II) fglrx(0): 
[    14.425] (II) fglrx(0): Enable composite support successfully
[    14.425] (WW) fglrx(0): Option "VendorName" is not used
[    14.425] (WW) fglrx(0): Option "ModelName" is not used
[    14.425] (II) fglrx(0): X context handle = 0x1
[    14.425] (II) fglrx(0): [DRI] installation complete
[    14.425] (==) fglrx(0): Silken mouse enabled
[    14.426] (==) fglrx(0): Using HW cursor of display infrastructure!
[    14.426] (II) fglrx(0): Disabling in-server RandR and enabling in-driver RandR 1.2.
[    14.514] (--) RandR disabled
[    14.514] (II) Initializing built-in extension Generic Event Extension
[    14.514] (II) Initializing built-in extension SHAPE
[    14.514] (II) Initializing built-in extension MIT-SHM
[    14.514] (II) Initializing built-in extension XInputExtension
[    14.514] (II) Initializing built-in extension XTEST
[    14.514] (II) Initializing built-in extension BIG-REQUESTS
[    14.514] (II) Initializing built-in extension SYNC
[    14.514] (II) Initializing built-in extension XKEYBOARD
[    14.514] (II) Initializing built-in extension XC-MISC
[    14.514] (II) Initializing built-in extension SECURITY
[    14.515] (II) Initializing built-in extension XINERAMA
[    14.515] (II) Initializing built-in extension XFIXES
[    14.515] (II) Initializing built-in extension RENDER
[    14.515] (II) Initializing built-in extension RANDR
[    14.515] (II) Initializing built-in extension COMPOSITE
[    14.515] (II) Initializing built-in extension DAMAGE
[    14.515] (II) Initializing built-in extension GESTURE
[    14.538] ukiDynamicMajor: found major device number 250
[    14.538] ukiDynamicMajor: found major device number 250
[    14.538] ukiOpenByBusid: Searching for BusID PCI:1:0:0
[    14.538] ukiOpenDevice: node name is /dev/ati/card0
[    14.538] ukiOpenDevice: open result is 17, (OK)
[    14.538] ukiOpenByBusid: ukiOpenMinor returns 17
[    14.538] ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
[    14.636] (II) AIGLX: Loaded and initialized OpenGL driver(II) GLX: Initialized DRI GL provider for screen 0
[    14.636] (II) fglrx(0): Enable the clock gating!
[    14.636] (II) fglrx(0): Setting screen physical size to 423 x 317
[    14.648] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    14.658] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    14.658] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    14.658] (II) LoadModule: "evdev"
[    14.658] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    14.659] (II) Module evdev: vendor="X.Org Foundation"
[    14.659] 	compiled for 1.10.0.902, module version = 2.6.0
[    14.659] 	Module class: X.Org XInput Driver
[    14.659] 	ABI class: X.Org XInput driver, version 12.3
[    14.659] (II) Using input driver 'evdev' for 'Power Button'
[    14.659] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    14.659] (**) Power Button: always reports core events
[    14.659] (**) Power Button: Device: "/dev/input/event1"
[    14.659] (--) Power Button: Found keys
[    14.659] (II) Power Button: Configuring as keyboard
[    14.659] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[    14.659] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    14.659] (**) Option "xkb_rules" "evdev"
[    14.659] (**) Option "xkb_model" "pc105"
[    14.659] (**) Option "xkb_layout" "us"
[    14.662] (II) config/udev: Adding input device Sleep Button (/dev/input/event0)
[    14.662] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[    14.662] (II) Using input driver 'evdev' for 'Sleep Button'
[    14.662] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    14.662] (**) Sleep Button: always reports core events
[    14.662] (**) Sleep Button: Device: "/dev/input/event0"
[    14.676] (--) Sleep Button: Found keys
[    14.676] (II) Sleep Button: Configuring as keyboard
[    14.676] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input0/event0"
[    14.676] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD)
[    14.676] (**) Option "xkb_rules" "evdev"
[    14.676] (**) Option "xkb_model" "pc105"
[    14.676] (**) Option "xkb_layout" "us"
[    14.678] (II) config/udev: Adding input device Dell Dell USB Keyboard (/dev/input/event2)
[    14.678] (**) Dell Dell USB Keyboard: Applying InputClass "evdev keyboard catchall"
[    14.678] (II) Using input driver 'evdev' for 'Dell Dell USB Keyboard'
[    14.678] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    14.678] (**) Dell Dell USB Keyboard: always reports core events
[    14.678] (**) Dell Dell USB Keyboard: Device: "/dev/input/event2"
[    14.678] (--) Dell Dell USB Keyboard: Found keys
[    14.678] (II) Dell Dell USB Keyboard: Configuring as keyboard
[    14.678] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.1/usb4/4-1/4-1:1.0/input/input2/event2"
[    14.678] (II) XINPUT: Adding extended input device "Dell Dell USB Keyboard" (type: KEYBOARD)
[    14.678] (**) Option "xkb_rules" "evdev"
[    14.678] (**) Option "xkb_model" "pc105"
[    14.678] (**) Option "xkb_layout" "us"
[    14.679] (II) config/udev: Adding input device USB Optical Mouse (/dev/input/event3)
[    14.679] (**) USB Optical Mouse: Applying InputClass "evdev pointer catchall"
[    14.679] (II) Using input driver 'evdev' for 'USB Optical Mouse'
[    14.679] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    14.679] (**) USB Optical Mouse: always reports core events
[    14.679] (**) USB Optical Mouse: Device: "/dev/input/event3"
[    14.679] (--) USB Optical Mouse: Found 3 mouse buttons
[    14.679] (--) USB Optical Mouse: Found scroll wheel(s)
[    14.679] (--) USB Optical Mouse: Found relative axes
[    14.679] (--) USB Optical Mouse: Found x and y relative axes
[    14.679] (II) USB Optical Mouse: Configuring as mouse
[    14.679] (II) USB Optical Mouse: Adding scrollwheel support
[    14.679] (**) USB Optical Mouse: YAxisMapping: buttons 4 and 5
[    14.679] (**) USB Optical Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    14.679] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.1/usb4/4-2/4-2:1.0/input/input3/event3"
[    14.679] (II) XINPUT: Adding extended input device "USB Optical Mouse" (type: MOUSE)
[    14.679] (II) USB Optical Mouse: initialized for relative axes.
[    14.680] (**) USB Optical Mouse: (accel) keeping acceleration scheme 1
[    14.680] (**) USB Optical Mouse: (accel) acceleration profile 0
[    14.680] (**) USB Optical Mouse: (accel) acceleration factor: 2.000
[    14.680] (**) USB Optical Mouse: (accel) acceleration threshold: 4
[    14.680] (II) config/udev: Adding input device USB Optical Mouse (/dev/input/mouse0)
[    14.680] (II) No input driver/identifier specified (ignoring)
[    14.701] (II) fglrx(0): Restoring Recent Mode via PCS is not supported in RANDR 1.2 capable environments
[    14.922] (II) fglrx(0): Cannot get EDID information for CRT1
[    14.931] (II) fglrx(0): Cannot get EDID information for CRT1
[    14.940] (II) fglrx(0): Cannot get EDID information for CRT1
[    14.948] (II) fglrx(0): Cannot get EDID information for CRT1
[    25.813] (II) AIGLX: Suspending AIGLX clients for VT switch
[    25.814] (II) fglrx(0): Backup framebuffer data.
[    25.816] (II) fglrx(0): Backup complete.
[    31.957] (II) AIGLX: Resuming AIGLX clients after VT switch
[    32.070] (II) fglrx(0): UVD feature is enabled(II) fglrx(0): 
[    32.176] (II) fglrx(0): Hot-plug event occurs on device: 1:0:0 
[    39.041] (II) AIGLX: Suspending AIGLX clients for VT switch
[    39.042] (II) fglrx(0): Backup framebuffer data.
[    39.044] (II) fglrx(0): Backup complete.
[    54.021] (II) AIGLX: Resuming AIGLX clients after VT switch
[    54.142] (II) fglrx(0): UVD feature is enabled(II) fglrx(0): 
[    54.233] (II) fglrx(0): Hot-plug event occurs on device: 1:0:0 
[    58.297] (II) AIGLX: Suspending AIGLX clients for VT switch
[    58.298] (II) fglrx(0): Backup framebuffer data.
[    58.299] (II) fglrx(0): Backup complete.
[    64.421] (II) AIGLX: Resuming AIGLX clients after VT switch
[    64.534] (II) fglrx(0): UVD feature is enabled(II) fglrx(0): 
[    64.640] (II) fglrx(0): Hot-plug event occurs on device: 1:0:0 
[    85.591] (II) AIGLX: Suspending AIGLX clients for VT switch
[    85.592] (II) fglrx(0): Backup framebuffer data.
[    85.593] (II) fglrx(0): Backup complete.
[   107.179] (II) USB Optical Mouse: Close
[   107.179] (II) UnloadModule: "evdev"
[   107.179] (II) Unloading evdev
[   107.179] (II) Dell Dell USB Keyboard: Close
[   107.179] (II) UnloadModule: "evdev"
[   107.179] (II) Unloading evdev
[   107.182] (II) Sleep Button: Close
[   107.182] (II) UnloadModule: "evdev"
[   107.182] (II) Unloading evdev
[   107.183] (II) Power Button: Close
[   107.183] (II) UnloadModule: "evdev"
[   107.183] (II) Unloading evdev
[   107.208] (II) fglrx(0): Shutdown CMMQS
[   107.208] (II) fglrx(0): [uki] removed 1 reserved context for kernel
[   107.208] (II) fglrx(0): [uki] unmapping 8192 bytes of SAREA 0x2000 at 0xb780c000
[   107.210] (II) fglrx(0): Interrupt handler Shutdown.
[   107.213]  ddxSigGiveUp: Closing log

---

### Post by realzippy on 2011-08-18
But  you don't get the error you posted in your 1rst post,do you?
According to your Xlog driver loads,but cannot read monitor data
(edid).Don 't understand why it doesn 't use fallback to vesa or something or starts X/fglrx with low resolution.
Also I am no fglrx expert at all.
Post your xorg.conf maybe someone else has ideas.

Did you run that ati-config-initial thingy?

---

### Post by waqas300 on 2011-08-18
> **realzippy said:**
> But  you don't get the error you posted in your 1rst post,do you?
According to your Xlog driver loads,but cannot read monitor data
(edid).Don 't understand why it doesn 't use fallback to vesa or something or starts X/fglrx with low resolution.
Also I am no fglrx expert at all.
Post your xorg.conf maybe someone else has ideas.

Did you run that ati-config-initial thingy?


Well here is the xorg.conf 



Section "ServerLayout"
	Identifier     "aticonfig Layout"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Module"
	Load  "glx"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "Default Screen"
	DefaultDepth     24
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-0"
	Device     "aticonfig-Device[0]-0"
	Monitor    "aticonfig-Monitor[0]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

---

### Post by realzippy on 2011-08-19
So which monitor model do you use ?

---

### Post by waqas300 on 2011-08-19
> **realzippy said:**
> So which monitor model do you use ?

i have got Compaq 151FS monitor

---

### Post by realzippy on 2011-08-19
run 
```
gksudo gedit /etc/X11/xorg.conf
```

and add in the "monitor" section
Hsync and Vrefresh like:

```
Section "ServerLayout"
Identifier "aticonfig Layout"
Screen 0 "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Module"
Load "glx"
EndSection

Section "Monitor"
Identifier "aticonfig-Monitor[0]-0"
Option "VendorName" "ATI Proprietary Driver"
Option "ModelName" "Generic Autodetecting Monitor"
HorizSync	30-58     # added
VertRefresh	50-100    # added
Option "DPMS" "true"
EndSection

Section "Device"
Identifier "aticonfig-Device[0]-0"
Driver "fglrx"
BusID "PCI:1:0:0"
EndSection

Section "Screen"
Identifier "Default Screen"
DefaultDepth 24
EndSection

Section "Screen"
Identifier "aticonfig-Screen[0]-0"
Device "aticonfig-Device[0]-0"
Monitor "aticonfig-Monitor[0]-0"
DefaultDepth 24
SubSection "Display"
Viewport 0 0
Depth 24
EndSubSection
EndSection

```

reboot/or restart X

---

### Post by waqas300 on 2011-08-19
> **realzippy said:**
> run 
```
gksudo gedit /etc/X11/xorg.conf
```

and add in the "monitor" section
Hsync and Vrefresh like:

```
Section "ServerLayout"
Identifier "aticonfig Layout"
Screen 0 "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Module"
Load "glx"
EndSection

Section "Monitor"
Identifier "aticonfig-Monitor[0]-0"
Option "VendorName" "ATI Proprietary Driver"
Option "ModelName" "Generic Autodetecting Monitor"
HorizSync	30-58     # added
VertRefresh	50-100    # added
Option "DPMS" "true"
EndSection

Section "Device"
Identifier "aticonfig-Device[0]-0"
Driver "fglrx"
BusID "PCI:1:0:0"
EndSection

Section "Screen"
Identifier "Default Screen"
DefaultDepth 24
EndSection

Section "Screen"
Identifier "aticonfig-Screen[0]-0"
Device "aticonfig-Device[0]-0"
Monitor "aticonfig-Monitor[0]-0"
DefaultDepth 24
SubSection "Display"
Viewport 0 0
Depth 24
EndSubSection
EndSection

```

reboot/or restart X




i tried
HorizSync	30-58     
VertRefresh	50-100 


also vertRefresh as 50-65

but the problem persist :-(

---

### Post by waqas300 on 2011-08-29
> **waqas300 said:**
> i tried
HorizSync    30-58 
VertRefresh    50-100 
 
 
also vertRefresh as 50-65
 
but the problem persist :-(
 
 
What next? Anyone got suggestion?:KS

---

### Post by realzippy on 2011-08-29
it is 100,not 65
[http://www.monitorworld.com/Monitors/compaq/151fs.html](http://www.monitorworld.com/Monitors/compaq/151fs.html)

Anyway,
you mean still black screen ?

---

### Post by waqas300 on 2011-09-01
> **realzippy said:**
> it is 100,not 65
[http://www.monitorworld.com/Monitors/compaq/151fs.html](http://www.monitorworld.com/Monitors/compaq/151fs.html)

Anyway,
you mean still black screen ?

Yes i did what you said but the screen still black it wont load the gui :-(

---

### Post by waqas300 on 2011-09-05
Any suggestions? :confused:

---

### Post by realzippy on 2011-09-05
No,sorry.
This seems to be a fglrx problem,since X-server does not seem to start with
the fglrx driver.I already said that I am no fglrx expert at all.
Maybe you should start a new thread,with **fglrx** in the title,
so someone also running fglrx may jump in.
Something like:
*Black screen when installing ATI/fglrx driver*

---

### Post by Mark Phelps on 2011-09-05
You also might try a couple of other things:
1) Post your new thread to the video subforum.  Folks there are more used to dealing with video problems.
2) Go over the the Phoronix forum and look around there.  They do a LOT of work with the fglrx drivers and might be able to offer you more technical advice.

---

### Post by waqas300 on 2011-09-07
Thanks guys for your kind support:D

---

