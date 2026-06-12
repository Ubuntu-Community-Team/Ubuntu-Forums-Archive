---
title: "Compiz not functioning with new video card everything is borked"
date: 2010-05-08
forum: New to Ubuntu
---

### Post by evil_urna on 2010-05-08
I got a new video card the other day, a Nvidia 7300GT, and it has been a god dammed albatross around my neck.

I had to regress from 10.4 to 9.10 because of its all consuming fail. It took me forever just to be able to get into 9.10 without going into low graphics mode. And the HITS JUST KEEP COMING!

I need to have 3d acceleration, thats why I bought a new card. The problem is that even with the NVIDIA version 185 enabled, it is not working.

It will not let me turn on desktop effects, play half-life, or even run steam at a non snails pace.

here is some sweet, sweet data

my card

```
01:00.0 VGA compatible controller: nVidia Corporation G73 [GeForce 7300 GT] (rev a2)

```

HOT HOT LSHW ACTION
```
    description: Computer
    vendor: PDS Inc.
    serial: 933761
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3
    configuration: boot=normal uuid=9790B192-2DAE-11D6-AEE1-0030D3006EA4
  *-core
       description: Motherboard
       product: D845BG
       vendor: Intel Corporation
       physical id: 0
       version: AAA74060-403
       serial: IMBG20903714
     *-firmware
          description: BIOS
          vendor: Intel Corp.
          physical id: 0
          version: PT84510A.86A.0021.P03.0202251254 (02/25/2002)
          size: 64KiB
          capacity: 448KiB
          capabilities: pci pnp upgrade shadowing escd cdboot bootselect edd int13floppynec int13floppytoshiba int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp ls120boot zipboot biosbootspecification netboot
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) 4 CPU 2.20GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 15.2.4
          slot: J1D1
          size: 2200MHz
          capacity: 2200MHz
          width: 32 bits
          clock: 100MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm up pebs bts
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: None
             size: 8KiB
             capacity: 8KiB
             clock: 25MHz (40.0ns)
             capabilities: pipeline-burst synchronous internal write-back data
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: None
             size: 512KiB
             capacity: 512KiB
             capabilities: synchronous internal write-back unified
     *-memory
          description: System Memory
          physical id: 2f
          slot: System board or motherboard
          size: 1536MiB
          capacity: 2GiB
        *-bank:0
             description: DIMM DDR Synchronous 266 MHz (3.8 ns)
             physical id: 0
             slot: J5E3
             size: 512MiB
             width: 64 bits
             clock: 266MHz (3.8ns)
        *-bank:1
             description: DIMM DDR Synchronous 266 MHz (3.8 ns)
             physical id: 1
             slot: J5E1
             size: 1GiB
             width: 64 bits
             clock: 266MHz (3.8ns)
     *-pci
          description: Host bridge
          product: 82845 845 [Brookdale] Chipset Host Bridge
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 04
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0 memory:e0000000-efffffff(prefetchable)
        *-pci:0
             description: PCI bridge
             product: 82845 845 [Brookdale] Chipset AGP Bridge
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 04
             width: 32 bits
             clock: 66MHz
             capabilities: pci bus_master
             resources: memory:fa900000-fe9fffff memory:ba600000-da6fffff(prefetchable)
           *-display
                description: VGA compatible controller
                product: G73 [GeForce 7300 GT]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a2
                width: 32 bits
                clock: 66MHz
                capabilities: pm agp agp-3.0 bus_master cap_list rom
                configuration: driver=nvidia latency=248 maxlatency=1 mingnt=5
                resources: irq:16 memory:fd000000-fdffffff memory:c0000000-cfffffff(prefetchable) memory:fc000000-fcffffff memory:fe9e0000-fe9fffff(prefetchable)
        *-pci:1
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master
             resources: ioport:d000(size=4096) memory:fea00000-feafffff memory:da700000-da7fffff(prefetchable)
           *-network
                description: Ethernet interface
                product: 82801BA/BAM/CA/CAM Ethernet Controller
                vendor: Intel Corporation
                physical id: 8
                bus info: pci@0000:02:08.0
                logical name: eth0
                version: 03
                serial: 00:03:47:e6:67:f7
                size: 100MB/s
                capacity: 100MB/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=full firmware=N/A ip=192.168.1.102 latency=32 link=yes maxlatency=56 mingnt=8 multicast=yes port=MII speed=100MB/s
                resources: irq:20 memory:feaff000-feafffff ioport:df00(size=64)
           *-usb:0
                description: USB Controller
                product: USB
                vendor: NEC Corporation
                physical id: c
                bus info: pci@0000:02:0c.0
                version: 43
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=ohci_hcd latency=32 maxlatency=42 mingnt=1
                resources: irq:17 memory:feafc000-feafcfff
           *-usb:1
                description: USB Controller
                product: USB
                vendor: NEC Corporation
                physical id: c.1
                bus info: pci@0000:02:0c.1
                version: 43
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=ohci_hcd latency=32 maxlatency=42 mingnt=1
                resources: irq:21 memory:feafd000-feafdfff
           *-usb:2
                description: USB Controller
                product: USB 2.0
                vendor: NEC Corporation
                physical id: c.2
                bus info: pci@0000:02:0c.2
                version: 04
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=ehci_hcd latency=32 maxlatency=34 mingnt=16
                resources: irq:22 memory:feafec00-feafecff
        *-isa
             description: ISA bridge
             product: 82801BA ISA Bridge (LPC)
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801BA IDE U100 Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             logical name: scsi0
             logical name: scsi1
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=ata_piix latency=0
             resources: irq:0 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:ffa0(size=16)
           *-disk:0
                description: ATA Disk
                product: WDC WD400JB-00JJ
                vendor: Western Digital
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 05.0
                serial: WD-WMAMA1033889
                size: 37GiB (40GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=e58ee58e
              *-volume:0
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   version: 1.0
                   serial: efa724d8-f56e-450a-a0ec-7abeb16e6370
                   size: 36GiB
                   capacity: 36GiB
                   capabilities: primary bootable journaled extended_attributes large_files recover ext3 ext2 initialized
                   configuration: created=2010-05-04 17:51:56 filesystem=ext3 modified=2010-05-07 20:11:38 mount.fstype=ext3 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2010-05-08 09:03:38 state=mounted
              *-volume:1
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 4
                   bus info: scsi@0:0.0.0,4
                   logical name: /dev/sda4
                   version: 1.0
                   serial: f1fd02e0-08e3-47eb-ad66-e0b2d71db6ba
                   size: 28GiB
                   capabilities: primary extended partitioned partitioned:extended journaled extended_attributes large_files ext3 ext2 initialized
                   configuration: created=2009-09-09 21:53:19 filesystem=ext3 modified=2009-10-09 23:25:35 mounted=2009-10-09 21:00:15 state=clean
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 531MiB
                      capabilities: nofs
           *-disk:1
                description: ATA Disk
                product: WDC WD3200AAJB-0
                vendor: Western Digital
                physical id: 1
                bus info: scsi@0:0.1.0
                logical name: /dev/sdb
                version: 00.0
                serial: WD-WCARW3323922
                size: 298GiB (320GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=000d99b3
              *-volume
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.1.0,1
                   logical name: /dev/sdb1
                   logical name: /home
                   version: 1.0
                   serial: 5f434f9a-9d70-4570-a309-8a57ac76fd54
                   size: 298GiB
                   capacity: 298GiB
                   capabilities: primary journaled extended_attributes large_files recover ext3 ext2 initialized
                   configuration: created=2010-04-28 03:01:28 filesystem=ext3 modified=2010-05-08 09:03:38 mount.fstype=ext3 mount.options=rw,relatime,errors=continue,data=ordered mounted=2010-05-08 09:03:38 state=mounted
           *-cdrom:0
                description: DVD writer
                physical id: 2
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom1
                logical name: /dev/cdrw1
                logical name: /dev/dvd1
                logical name: /dev/dvdrw1
                logical name: /dev/scd0
                logical name: /dev/sr0
                capabilities: audio cd-r cd-rw dvd dvd-r
                configuration: status=nodisc
           *-cdrom:1
                description: DVD reader
                product: CDW/DVD TS-H492A
                vendor: TSSTcorp
                physical id: 3
                bus info: scsi@1:0.1.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/scd1
                logical name: /dev/sr1
                version: HP03
                capabilities: removable audio cd-r cd-rw dvd
                configuration: ansiversion=5 status=nodisc
        *-usb:0
             description: USB Controller
             product: 82801BA/BAM USB Controller #1
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:ef40(size=32)
        *-serial UNCLAIMED
             description: SMBus
             product: 82801BA/BAM SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 05
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:efa0(size=16)
        *-usb:1
             description: USB Controller
             product: 82801BA/BAM USB Controller #1
             vendor: Intel Corporation
             physical id: 1f.4
             bus info: pci@0000:00:1f.4
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:23 ioport:ef80(size=32)
        *-multimedia
             description: Multimedia audio controller
             product: 82801BA/BAM AC'97 Audio Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=Intel ICH latency=0
             resources: irq:17 ioport:e800(size=256) ioport:ef00(size=64)

```

my Xorg.0.log
```
cat /var/log/Xorg.0.log

X.Org X Server 1.6.4
Release Date: 2009-9-27
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux Dorbert 2.6.31-21-generic #59-Ubuntu SMP Wed Mar 24 07:28:56 UTC 2010 i686
Kernel command line: root=UUID=efa724d8-f56e-450a-a0ec-7abeb16e6370 ro quiet splash 
Build Date: 04 March 2010  09:56:47AM
xorg-server 2:1.6.4-2ubuntu4.2 (buildd@) 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sat May  8 07:15:09 2010
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Layout0"
(**) |-->Screen "Screen0" (0)
(**) |   |-->Monitor "Monitor0"
(**) |   |-->Device "Device0"
(**) |-->Input Device "Keyboard0"
(**) |-->Input Device "Mouse0"
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
(WW) AllowEmptyInput is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
(WW) Disabling Keyboard0
(WW) Disabling Mouse0
(II) Loader magic: 0x3bc0
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 5.0
	X.Org XInput driver : 4.0
	X.Org Server Extension : 2.0
(II) Loader running on linux
(++) using VT number 7

(--) PCI:*(0:1:0:0) 10de:02e2:19f1:04e3 nVidia Corporation G73 [GeForce 7300 GT] rev 162, Mem @ 0xfd000000/16777216, 0xc0000000/268435456, 0xfc000000/16777216, BIOS @ 0x????????/131072
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
dlopen: /usr/lib/xorg/modules/extensions//libglx.so: undefined symbol: _nv000028gl
(EE) Failed to load /usr/lib/xorg/modules/extensions//libglx.so
(II) UnloadModule: "glx"
(EE) Failed to load module "glx" (loader failed, 7)
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
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Video Driver
(II) NVIDIA dlloader X Driver  185.18.36  Fri Aug 14 17:24:40 PDT 2009
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 01@00:00:0
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "wfb"
(II) LoadModule: "wfb"
(II) Loading /usr/lib/xorg/modules//libwfb.so
(II) Module wfb: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(II) resource ranges after probing:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Enabling RENDER acceleration
(EE) NVIDIA(0): Failed to initialize the GLX module; please check in your X
(EE) NVIDIA(0):     log file that the GLX module has been loaded in your X
(EE) NVIDIA(0):     server, and that the module is the NVIDIA GLX module.  If
(EE) NVIDIA(0):     you continue to encounter problems, Please try
(EE) NVIDIA(0):     reinstalling the NVIDIA driver.
(II) NVIDIA(0): NVIDIA GPU GeForce 7300 GT (G73) at PCI:1:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 524288 kBytes
(--) NVIDIA(0): VideoBIOS: 05.73.22.51.61
(II) NVIDIA(0): Detected AGP rate: 4X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce 7300 GT at PCI:1:0:0:
(--) NVIDIA(0):     HP vs15c (CRT-1)
(--) NVIDIA(0): HP vs15c (CRT-1): 400.0 MHz maximum pixel clock
(II) NVIDIA(0): Assigned Display Device: CRT-1
(==) NVIDIA(0): 
(==) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
(==) NVIDIA(0):     will be used as the requested mode.
(==) NVIDIA(0): 
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "nvidia-auto-select"
(II) NVIDIA(0): Virtual screen size determined to be 1024 x 768
(--) NVIDIA(0): DPI set to (86, 88); computed from "UseEdidDpi" X config
(--) NVIDIA(0):     option
(==) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) NVIDIA(0): Initialized AGP GART.
(II) NVIDIA(0): Setting mode "nvidia-auto-select"
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(==) NVIDIA(0): Disabling shared memory pixmaps
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(**) Option "dpms"
(**) NVIDIA(0): DPMS enabled
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
(II) config/hal: Adding input device Logitech USB Optical Mouse
(**) Logitech USB Optical Mouse: always reports core events
(**) Logitech USB Optical Mouse: Device: "/dev/input/event4"
(II) Logitech USB Optical Mouse: Found 3 mouse buttons
(II) Logitech USB Optical Mouse: Found x and y relative axes
(II) Logitech USB Optical Mouse: Found scroll wheel(s)
(II) Logitech USB Optical Mouse: Configuring as mouse
(**) Logitech USB Optical Mouse: YAxisMapping: buttons 4 and 5
(**) Logitech USB Optical Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Logitech USB Optical Mouse" (type: MOUSE)
(**) Logitech USB Optical Mouse: (accel) keeping acceleration scheme 1
(**) Logitech USB Optical Mouse: (accel) filter chain progression: 2.00
(**) Logitech USB Optical Mouse: (accel) filter stage 0: 20.00 ms
(**) Logitech USB Optical Mouse: (accel) set acceleration profile 0
(II) Logitech USB Optical Mouse: initialized for relative axes.
```

Results of compiz check program
```
Gathering information about your system...

 Distribution:          Ubuntu 9.10
 Desktop environment:   GNOME
 Graphics chip:         nVidia Corporation G73 [GeForce 7300 GT] (rev a2)
 Driver in use:         nvidia
 Rendering method:      Nvidia

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [FAIL]
 Checking for non power of two support...          [FAIL]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [FAIL]
 Checking for hardware/setup problems...           [SKIP]

At least one check had to be skipped:
 Error: Unable to detect maximum 3D texture size 

```

Please god help me. This is driving me up the god damm wall.

PS 

I have used envy, terminal, and the package installer to install drivers all to no avail

---

### Post by cariboo on 2010-05-08
Have you tried running:

```
sudo nvidia-xconfig
```

in a terminal, it may be that you need to have an /etc/X11/xorg.conf file in order for the driver to work correctly. Once you have created the file, just reboot.

BTW, watch your language, as this is a family friendly forum, we have members as young as 8 years old.

---

### Post by ranch hand on 2010-05-08
I think the big question here is whether or not you actually did research the    	 	 	 	 	compatibility of the card before you got it.

---

### Post by TheNerdAL on 2010-05-08
> **ranch hand said:**
> I think the big question here is whether or not you actually did research the    	 	 	 	 	compatibility of the card before you got it.

True, always check if it's supported before buying it. Don't worry though, Nvidia 7300GT is supported.

---

### Post by ranch hand on 2010-05-08
That is good to hear.  As an ATI user I know little about nvidia cards.

If it is supported it should work.

I do know that in testing for 10.04 there were folks talking about some ppa that has a sweet driver for nvida but as to if this is for your card I haven't a clue.

---

### Post by sandyd on 2010-05-08
```

(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
dlopen: /usr/lib/xorg/modules/extensions//libglx.so: undefined symbol: _nv000028gl
(EE) Failed to load /usr/lib/xorg/modules/extensions//libglx.so
(II) UnloadModule: "glx"
(EE) Failed to load module "glx" (loader failed, 7)

``````

(EE) NVIDIA(0): Failed to initialize the GLX module; please check in your X
(EE) NVIDIA(0):     log file that the GLX module has been loaded in your X
(EE) NVIDIA(0):     server, and that the module is the NVIDIA GLX module.  If
(EE) NVIDIA(0):     you continue to encounter problems, Please try
(EE) NVIDIA(0):     reinstalling the NVIDIA driver.

```there ya go.

the glx modules aren't installed properly
I believe they **should** come with the nvidia driver.
try downloading and installing the driver from nvidia.com

---

### Post by sixthwheel on 2010-05-08
> Please god help me. This is driving me up the god damm wall.
I don't think he'll be helping much.:p

---

### Post by evil_urna on 2010-05-09
I downloaded the 196 drivers and finally got GDM to shutdown after about 20 min of screwing around wif it (sudo etc/init.d/gdm stop was not working) and it freaking works.

I could kiss everyone of you except sixthwheel cuz that was a jerkish thing to say. But to everyone else thank you very much

and to ranch hand, even I am not that much of a nub.

---

