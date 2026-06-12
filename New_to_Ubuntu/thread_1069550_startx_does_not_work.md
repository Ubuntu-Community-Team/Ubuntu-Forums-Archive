---
title: "startx does not work"
date: 2009-02-14
forum: New to Ubuntu
---

### Post by xItachi on 2009-02-14
So I switched to tty1 using CTRL+ALT+F1 and performed a restart

```
sudo shutdown -r now
```

and when my computer restarts, it now always boots into tty1 instead of the X window at tty7.  I checked and people said to try startx, so I try startx after logging into tty1 and it doesn't work.  I tried to write the result of startx to a textfile so you guys can see the error message, but I was unsuccessful, this is what I tried:

```
startx > error.txt
```


Thanks!

---

### Post by x33a on 2009-02-14
try sudo /etc/init.d/gdm start, then press ctrl+alt+f7

---

### Post by xItachi on 2009-02-14
I tried that and it says it failed.  I tried startx again and I got

```
Log File: "/var/log/xorg.0.log"
Using config file: "etc/X11/xorg.conf"
config/hal: couldn't initialise context: (null) ((null))
```

Then I tried 

```
sudo dpkg-reconfigure /etc/X11/xorg.conf
```

and it says

Package '/etc/X11/xorg.conf' is not installed and no info is available

---

### Post by x33a on 2009-02-14
what were you doing before this error started.

did you update the kernel, or video drivers?

---

### Post by xItachi on 2009-02-14
I was trying to use the Add/Remove GUI to install MySQL Server Admin and Query Browser.  After the installation, I tried to run it and nothing happened.  I tried opening the package manager but that didn't open either.  I tried to do a restart and it went the the Ubuntu loading screen, the bar almost got completely filled and it was about to restart but it just got stuck there, so I went to tty1 and did 'sudo shutdown -r now'.  Now it always boots into tty1 and I can't get the GNOME Display Manager to work.

---

### Post by x33a on 2009-02-14
try booting a previous kernel.

---

### Post by xItachi on 2009-02-14
I tried booting the other two kernels, and they both have the same problem.  I also tried going into recovery mode and do xfix to try to fix the x window fix, that didn't really work.  I think maybe it has something to do with mysql.. it says it's loading mysqld database and does some other things, and when it gets to Starting GNOME Display manager.. it says FAIL

---

### Post by x33a on 2009-02-14
well then i guess you should try to uninstall mysql first. then try again.

---

### Post by xItachi on 2009-02-14
I tried doing 

```
sudo apt-get remove mysql-server-5.0
sudo apt-get remove mysql-client
sudo apt-get remove mysql-gui-tools
sudo apt-get remove mysql-query-browser
```

but all of them said GLIB or something is missing and required.  x33a, thanks by the way for helping me, I really have no idea what to do.

---

### Post by hyperyoda on 2009-02-14
You may have removed your xserver. See what you have installed:

$ dpkg -l | grep xserver-

Zach

---

### Post by llamabr on 2009-02-14
What does

 sudo dpkg-reconfigure -phigh xserver-xorg

give you?

---

### Post by xItachi on 2009-02-14
dpkg -l | grep xserver-

gives me:

```
ii  x11-xserver-utils                          7.3+5                                   X server utilities
ii  xserver-common                             2:1.5.2-2ubuntu3                        common files used by various X servers
ii  xserver-xorg                               1:7.4~5ubuntu3                          the X.Org X server
ii  xserver-xorg-core                          2:1.5.2-2ubuntu3                        Xorg X server - core server
ii  xserver-xorg-input-all                     1:7.4~5ubuntu3                          the X.Org X server -- input driver metapacka
ii  xserver-xorg-input-evdev                   1:2.0.99+git20080912-0ubuntu6           X.Org X server -- evdev input driver
ii  xserver-xorg-input-kbd                     1:1.3.1-1ubuntu2                        X.Org X server -- keyboard input driver
ii  xserver-xorg-input-mouse                   1:1.3.0-1build1                         X.Org X server -- mouse input driver
ii  xserver-xorg-input-synaptics               0.15.2-0ubuntu7                         Synaptics TouchPad driver for X.Org/XFree86 
ii  xserver-xorg-input-vmmouse                 1:12.5.1-1ubuntu5.1                     X.Org X server -- VMMouse input driver to us
ii  xserver-xorg-input-wacom                   1:0.8.1.4-0ubuntu3                      X.Org X server -- Wacom input driver
ii  xserver-xorg-video-all                     1:7.4~5ubuntu3                          the X.Org X server -- output driver metapack
ii  xserver-xorg-video-apm                     1:1.2.0-1build2                         X.Org X server -- APM display driver
ii  xserver-xorg-video-ark                     1:0.7.0-1build2                         X.Org X server -- ark display driver
ii  xserver-xorg-video-ati                     1:6.9.0+git20081003.f9826a56-0ubuntu2.1 X.Org X server -- ATI display driver wrapper
ii  xserver-xorg-video-chips                   1:1.2.0-1build2                         X.Org X server -- Chips display driver
ii  xserver-xorg-video-cirrus                  1:1.2.1-1build2                         X.Org X server -- Cirrus display driver
ii  xserver-xorg-video-fbdev                   1:0.4.0-1build2                         X.Org X server -- fbdev display driver
ii  xserver-xorg-video-geode                   2.10.1-3build1                          X.Org server -- Geode GX2/LX display driver
ii  xserver-xorg-video-i128                    1:1.3.0-1build2                         X.Org X server -- i128 display driver
ii  xserver-xorg-video-i740                    1:1.2.0-1build2                         X.Org X server -- i740 display driver
ii  xserver-xorg-video-intel                   2:2.4.1-1ubuntu10.3                     X.Org X server -- Intel i8xx, i9xx display d
ii  xserver-xorg-video-mach64                  6.8.0-1build2                           X.Org X server -- ATI Mach64 display driver
ii  xserver-xorg-video-mga                     1:1.4.9.dfsg-1build1                    X.Org X server -- MGA display driver
ii  xserver-xorg-video-neomagic                1:1.2.1-1build2                         X.Org X server -- Neomagic display driver
ii  xserver-xorg-video-nv                      1:2.1.10-1ubuntu2                       X.Org X server -- NV display driver
ii  xserver-xorg-video-openchrome              1:0.2.903-0ubuntu3                      X.Org X server -- VIA display driver
ii  xserver-xorg-video-r128                    6.8.0-1ubuntu2                          X.Org X server -- ATI r128 display driver
ii  xserver-xorg-video-radeon                  1:6.9.0+git20081003.f9826a56-0ubuntu2.1 X.Org X server -- ATI Radeon display driver
ii  xserver-xorg-video-rendition               1:4.2.0.dfsg.1-2build2                  X.Org X server -- Rendition display driver
ii  xserver-xorg-video-s3                      1:0.6.0-1build2                         X.Org X server -- legacy S3 display driver
ii  xserver-xorg-video-s3virge                 1:1.10.1-1build2                        X.Org X server -- S3 ViRGE display driver
ii  xserver-xorg-video-savage                  1:2.2.1-1build2                         X.Org X server -- Savage display driver
ii  xserver-xorg-video-siliconmotion           1:1.6.0-1build2                         X.Org X server -- SiliconMotion display driv
ii  xserver-xorg-video-sis                     1:0.10.0-1build2                        X.Org X server -- SiS display driver
ii  xserver-xorg-video-sisusb                  1:0.9.0-1build2                         X.Org X server -- SiS USB display driver
ii  xserver-xorg-video-tdfx                    1:1.4.0-1build2                         X.Org X server -- tdfx display driver
ii  xserver-xorg-video-trident                 1:1.3.0-1build2                         X.Org X server -- Trident display driver
ii  xserver-xorg-video-tseng                   1:1.2.0-1build2                         X.Org X server -- Tseng display driver
ii  xserver-xorg-video-v4l                     1:0.2.0-1ubuntu3                        X.Org X server -- Video 4 Linux display driv
ii  xserver-xorg-video-vesa                    1:2.0.0-1ubuntu3                        X.Org X server -- VESA display driver
ii  xserver-xorg-video-vmware                  1:10.16.2-1build2                       X.Org X server -- VMware display driver
ii  xserver-xorg-video-voodoo                  1:1.2.0-1build2                         X.Org X server -- Voodoo display driver

```

sudo dpkg-reconfigure -phigh xserver-xorg

overwrites some kind of log file, I tried both and tried starting the GNOME Display Manager again and it still doesn't work

---

### Post by xItachi on 2009-02-15
When I try doing startx it says this:

```
Log File: "/var/log/xorg.0.log"
Using config file: "etc/X11/xorg.conf"
config/hal: couldn't initialise context: (null) ((null))

Waiting for X server to shut down...

xauth: error in locking authority file /home/stephen/.Xauthority
```

Any ideas?

---

### Post by xItachi on 2009-02-15
I was able to make a new authority file and backup the old one, and now the error about authority disappeared, but I still can't get gdm to start.  Here is the logfile as a result of 'startx':

```


X.Org X Server 1.5.2
Release Date: 10 October 2008
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-19-server i686 Ubuntu
Current Operating System: Linux stephen-laptop 2.6.27-11-generic #1 SMP Thu Jan 29 19:24:39 UTC 2009 i686
Build Date: 24 October 2008  08:00:16AM
xorg-server 2:1.5.2-2ubuntu3 (buildd@rothera.buildd) 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sun Feb 15 13:34:29 2009
(==) Using config file: "/etc/X11/xorg.conf"
(==) No Layout section.  Using the first Screen section.
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Configured Monitor"
(**) |   |-->Device "Configured Video Device"
(==) Automatically adding devices
(==) Automatically enabling devices
(==) No FontPath specified.  Using compiled-in default.
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Cannot locate a core pointer device.
(II) Cannot locate a core keyboard device.
(II) The server relies on HAL to provide the list of input devices.
	If no devices become available, reconfigure HAL or disable AllowEmptyInput.
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x81d9a40
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 4.1
	X.Org XInput driver : 2.1
	X.Org Server Extension : 1.1
	X.Org Font Renderer : 0.6
(II) Loader running on linux
(--) using VT number 7

(--) PCI:*(0@0:2:0) Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller rev 3, Mem @ 0xeff00000/0, 0xd0000000/0, 0xefec0000/0, I/O @ 0x0000eff8/0
(--) PCI: (0@0:2:1) Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller rev 3, Mem @ 0xeff80000/0
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
	compiled for 1.5.2, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 1.1
(II) Loading extension SHAPE
(II) Loading extension MIT-SUNDRY-NONSTANDARD
(II) Loading extension BIG-REQUESTS
(II) Loading extension SYNC
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XC-MISC
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-Misc
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"

(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 1.1
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"

(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	ABI class: X.Org Server Extension, version 1.1
(==) AIGLX enabled
(==) Exporting typical set of GLX visuals
(II) Loading extension GLX
(II) LoadModule: "freetype"

(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 1.5.2, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.6
(II) Loading font FreeType
(II) LoadModule: "record"

(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 1.1
(II) Loading extension RECORD
(II) LoadModule: "dri"

(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	ABI class: X.Org Server Extension, version 1.1
(II) Loading extension XFree86-DRI
(II) Scanning /usr/share/xserver-xorg/pci directory for additional PCI ID's supported by the drivers
(II) Matched intel from file name intel.ids
(==) Matched intel for the autoconfigured driver
(==) Assigned the driver to the xf86ConfigLayout
(II) LoadModule: "intel"

(II) Loading /usr/lib/xorg/modules/drivers//intel_drv.so
(II) Module intel: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 2.4.1
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 4.1
(II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
	i810-dc100, i810e, i815, i830M, 845G, 852GM/855GM, 865G, 915G,
	E7221 (i915), 915GM, 945G, 945GM, 945GME, 965G, G35, 965Q, 946GZ,
	965GM, 965GME/GLE, G33, Q35, Q33,
	Mobile Intel® GM45 Express Chipset,
	Intel Integrated Graphics Device, G45/G43, Q45/Q43
(II) Primary Device is: PCI 00@00:02:0
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) resource ranges after probing:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[5] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[6] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[7] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[8] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[9] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[10] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Loading sub module "int10"
(II) LoadModule: "int10"

(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	ABI class: X.Org Video Driver, version 4.1
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"

(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.1.0
	ABI class: X.Org Video Driver, version 4.1
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"

(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 0.1.0
	ABI class: X.Org Video Driver, version 4.1
(II) intel(0): Creating default Display subsection in Screen section
	"Default Screen" for depth/fbbpp 24/32
(==) intel(0): Depth 24, (==) framebuffer bpp 32
(==) intel(0): RGB weight 888
(==) intel(0): Default visual is TrueColor
(II) intel(0): Integrated Graphics Chipset: Intel(R) 945GM
(--) intel(0): Chipset: "945GM"
(--) intel(0): Linear framebuffer at 0xD0000000
(--) intel(0): IO registers at addr 0xEFF00000
(II) intel(0): 2 display pipes available.
(==) intel(0): Using EXA for acceleration
(II) Loading sub module "int10"
(II) LoadModule: "int10"

(II) Reloading /usr/lib/xorg/modules//libint10.so
(II) intel(0): initializing int10
(WW) intel(0): Bad V_BIOS checksum
(II) intel(0): Primary V_BIOS segment is: 0xc000
(II) intel(0): VESA BIOS detected
(II) intel(0): VESA VBE Version 3.0
(II) intel(0): VESA VBE Total Mem: 7872 kB
(II) intel(0): VESA VBE OEM: Intel(r) 82945GM Chipset Family Graphics Chip Accelerated VGA BIOS
(II) intel(0): VESA VBE OEM Software Rev: 1.0
(II) intel(0): VESA VBE OEM Vendor: Intel Corporation
(II) intel(0): VESA VBE OEM Product: Intel(r) 82945GM Chipset Family Graphics Controller
(II) intel(0): VESA VBE OEM Product Rev: Hardware Version 0.0
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"
(II) Module "i2c" already built-in
(II) intel(0): Output VGA using monitor section Configured Monitor
(II) intel(0): I2C bus "CRTDDC_A" initialized.
(II) intel(0): Output LVDS has no monitor section
(II) intel(0): I2C bus "LVDSDDC_C" initialized.
(II) intel(0): Attempting to determine panel fixed mode.
(II) intel(0): I2C device "LVDSDDC_C:ddc2" registered at address 0xA0.
(II) intel(0): EDID vendor "AUO", prod id 5236
(II) intel(0): DDCModeFromDetailedTiming: 1280x800 Warning: We only handle seperate sync.
(II) intel(0): found backlight control method /sys/class/backlight/acpi_video0
(II) intel(0): Output TV has no monitor section
(II) intel(0): EDID vendor "AUO", prod id 5236
(II) intel(0): DDCModeFromDetailedTiming: 1280x800 Warning: We only handle seperate sync.
(II) intel(0): Output VGA disconnected
(II) intel(0): Output LVDS connected
(II) intel(0): Output TV disconnected
(II) intel(0): Using exact sizes for initial modes
(II) intel(0): Output LVDS using initial mode 1280x800
(II) intel(0): Monitoring connected displays enabled
(II) intel(0): detected 256 kB GTT.
(II) intel(0): detected 7932 kB stolen memory.
(==) intel(0): video overlay key set to 0x101fe
(==) intel(0): Will not try to enable page flipping
(==) intel(0): Triple buffering disabled
(==) intel(0): Intel XvMC decoder disabled
(==) intel(0): Using gamma correction (1.0, 1.0, 1.0)
(==) intel(0): DPI set to (96, 96)
(II) Loading sub module "fb"
(II) LoadModule: "fb"

(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "exa"
(II) LoadModule: "exa"

(II) Loading /usr/lib/xorg/modules//libexa.so
(II) Module exa: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 2.4.0
	ABI class: X.Org Video Driver, version 4.1
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(II) intel(0): Comparing regs from server start up to After PreInit
(WW) intel(0): Register 0x61200 (PP_STATUS) changed from 0xc0000008 to 0xd0000009
(WW) intel(0): PP_STATUS before: on, ready, sequencing idle
(WW) intel(0): PP_STATUS after: on, ready, sequencing on
(WW) intel(0): Register 0x70024 (PIPEASTAT) changed from 0x80000203 to 0x00000000
(WW) intel(0): PIPEASTAT before: status: FIFO_UNDERRUN VSYNC_INT_STATUS VBLANK_INT_STATUS OREG_UPDATE_STATUS
(WW) intel(0): PIPEASTAT after: status:
(WW) intel(0): Register 0x71024 (PIPEBSTAT) changed from 0x80000202 to 0x00000202
(WW) intel(0): PIPEBSTAT before: status: FIFO_UNDERRUN VSYNC_INT_STATUS VBLANK_INT_STATUS
(WW) intel(0): PIPEBSTAT after: status: VSYNC_INT_STATUS VBLANK_INT_STATUS
(WW) intel(0): Register 0x68000 (TV_CTL) changed from 0x10000000 to 0x000c0000
(WW) intel(0): Register 0x68010 (TV_CSC_Y) changed from 0x00000000 to 0x0332012d
(WW) intel(0): Register 0x68014 (TV_CSC_Y2) changed from 0x00000000 to 0x07d30104
(WW) intel(0): Register 0x68018 (TV_CSC_U) changed from 0x00000000 to 0x0733052d
(WW) intel(0): Register 0x6801c (TV_CSC_U2) changed from 0x00000000 to 0x05c70200
(WW) intel(0): Register 0x68020 (TV_CSC_V) changed from 0x00000000 to 0x0340030c
(WW) intel(0): Register 0x68024 (TV_CSC_V2) changed from 0x00000000 to 0x06d00200
(WW) intel(0): Register 0x68028 (TV_CLR_KNOBS) changed from 0x00000000 to 0x00606000
(WW) intel(0): Register 0x6802c (TV_CLR_LEVEL) changed from 0x00000000 to 0x010b00e1
(WW) intel(0): Register 0x68030 (TV_H_CTL_1) changed from 0x00000000 to 0x00400359
(WW) intel(0): Register 0x68034 (TV_H_CTL_2) changed from 0x00000000 to 0x80480022
(WW) intel(0): Register 0x68038 (TV_H_CTL_3) changed from 0x00000000 to 0x007c0344
(WW) intel(0): Register 0x6803c (TV_V_CTL_1) changed from 0x00000000 to 0x00f01415
(WW) intel(0): Register 0x68040 (TV_V_CTL_2) changed from 0x00000000 to 0x00060607
(WW) intel(0): Register 0x68044 (TV_V_CTL_3) changed from 0x00000000 to 0x80120001
(WW) intel(0): Register 0x68048 (TV_V_CTL_4) changed from 0x00000000 to 0x000900f0
(WW) intel(0): Register 0x6804c (TV_V_CTL_5) changed from 0x00000000 to 0x000a00f0
(WW) intel(0): Register 0x68050 (TV_V_CTL_6) changed from 0x00000000 to 0x000900f0
(WW) intel(0): Register 0x68054 (TV_V_CTL_7) changed from 0x00000000 to 0x000a00f0
(WW) intel(0): Register 0x68060 (TV_SC_CTL_1) changed from 0x00000000 to 0xc1710088
(WW) intel(0): Register 0x68064 (TV_SC_CTL_2) changed from 0x00000000 to 0x4e2d1dc8
(WW) intel(0): Register 0x68070 (TV_WIN_POS) changed from 0x00000000 to 0x00360024
(WW) intel(0): Register 0x68074 (TV_WIN_SIZE) changed from 0x00000000 to 0x02640198
(WW) intel(0): Register 0x68080 (TV_FILTER_CTL_1) changed from 0x00000000 to 0x800010bb
(WW) intel(0): Register 0x68084 (TV_FILTER_CTL_2) changed from 0x00000000 to 0x00028283
(WW) intel(0): Register 0x68088 (TV_FILTER_CTL_3) changed from 0x00000000 to 0x00014141
(WW) intel(0): Register 0x68100 (TV_H_LUMA_0) changed from 0x00000000 to 0xb1403000
(WW) intel(0): Register 0x681ec (TV_H_LUMA_59) changed from 0x00000000 to 0x0000b060
(WW) intel(0): Register 0x68200 (TV_H_CHROMA_0) changed from 0x00000000 to 0xb1403000
(WW) intel(0): Register 0x682ec (TV_H_CHROMA_59) changed from 0x00000000 to 0x0000b060
(==) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
	[5] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
	[6] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
	[7] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[8] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[9] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[10] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) intel(0): Kernel reported 488960 total, 1 used
(II) intel(0): I830CheckAvailableMemory: 1955836 kB available
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenByBusid: Searching for BusID pci:0000:00:02.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 11, (OK)
drmOpenByBusid: drmOpenMinor returns 11
drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
(II) [drm] loaded kernel module for "i915" driver.
(II) [drm] DRM interface version 1.3
(II) [drm] DRM open master succeeded.
(II) intel(0): [drm] Using the DRM lock SAREA also for drawables.
(II) intel(0): [drm] framebuffer mapped by ddx driver
(II) intel(0): [drm] added 1 reserved context for kernel
(II) intel(0): X context handle = 0x1
(II) intel(0): [drm] installed DRM signal handler
(**) intel(0): Framebuffer compression enabled
(**) intel(0): Tiling enabled
(==) intel(0): VideoRam: 262144 KB
(II) intel(0): Attempting memory allocation with tiled buffers.
(II) intel(0): Tiled allocation successful.
(II) intel(0): [drm] Registers = 0xeff00000
(II) intel(0): [drm] ring buffer = 0xd0000000
(II) intel(0): [drm] mapped front buffer at 0xd1000000, handle = 0xd1000000
(II) intel(0): [drm] mapped back buffer at 0xd4000000, handle = 0xd4000000
(II) intel(0): [drm] mapped depth buffer at 0xd5000000, handle = 0xd5000000
(II) intel(0): [drm] mapped classic textures at 0xd6000000, handle = 0xd6000000
(II) intel(0): [drm] Initialized kernel agp heap manager, 33554432
(II) intel(0): [dri] visual configs initialized
(II) intel(0): Page Flipping disabled
(II) intel(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(II) EXA(0): Offscreen pixmap area of 31457280 bytes
(II) EXA(0): Driver registered support for the following operations:
(II)         Solid
(II)         Copy
(II)         Composite (RENDER acceleration)
(==) intel(0): Backing store disabled
(==) intel(0): Silken mouse enabled
(II) intel(0): Initializing HW Cursor
(II) intel(0): [DRI] installation complete
(II) intel(0): xf86BindGARTMemory: bind key 0 at 0x01000000 (pgoffset 4096)
(II) intel(0): xf86BindGARTMemory: bind key 1 at 0x02000000 (pgoffset 8192)
(II) intel(0): xf86BindGARTMemory: bind key 2 at 0x04000000 (pgoffset 16384)
(II) intel(0): xf86BindGARTMemory: bind key 3 at 0x05000000 (pgoffset 20480)
(II) intel(0): xf86BindGARTMemory: bind key 4 at 0x06000000 (pgoffset 24576)
(II) intel(0): Fixed memory allocation layout:
(II) intel(0): 0x00000000-0x0001ffff: ring buffer (128 kB)
(II) intel(0): 0x00020000-0x0061ffff: compressed frame buffer (6144 kB, 0x000000007f820000 physical
)
(II) intel(0): 0x00620000-0x00620fff: compressed ll buffer (4 kB, 0x000000007fe20000 physical
)
(II) intel(0): 0x00621000-0x0062afff: HW cursors (40 kB, 0x000000007fe21000 physical
)
(II) intel(0): 0x0062b000-0x00632fff: logical 3D context (32 kB)
(II) intel(0): 0x00633000-0x00633fff: overlay registers (4 kB, 0x000000007fe33000 physical
)
(II) intel(0): 0x007bf000:            end of stolen memory
(II) intel(0): 0x01000000-0x01ffffff: front buffer (10240 kB) X tiled
(II) intel(0): 0x02000000-0x03dfffff: exa offscreen (30720 kB)
(II) intel(0): 0x04000000-0x04ffffff: back buffer (10240 kB) X tiled
(II) intel(0): 0x05000000-0x05ffffff: depth buffer (10240 kB) X tiled
(II) intel(0): 0x06000000-0x07ffffff: classic textures (32768 kB)
(II) intel(0): 0x10000000:            end of aperture
(II) intel(0): using SSC reference clock of 96 MHz
(II) intel(0): Selecting standard 18 bit TMDS pixel format.
(II) intel(0): Output configuration:
(II) intel(0):   Pipe A is off
(II) intel(0):   Display plane A is now disabled and connected to pipe A.
(II) intel(0):   Pipe B is on
(II) intel(0):   Display plane B is now enabled and connected to pipe B.
(II) intel(0):   Output VGA is connected to pipe none
(II) intel(0):   Output LVDS is connected to pipe B
(II) intel(0):   Output TV is connected to pipe none
(II) intel(0): [drm] dma control initialized, using IRQ 16
(II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
(II) intel(0): using SSC reference clock of 96 MHz
(II) intel(0): Selecting standard 18 bit TMDS pixel format.
(II) intel(0): DPMS enabled
(II) intel(0): Set up textured video
(II) intel(0): Set up overlay video
(II) intel(0): direct rendering: Enabled
(--) RandR disabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 12, (OK)
drmOpenByBusid: Searching for BusID pci:0000:00:02.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 12, (OK)
drmOpenByBusid: drmOpenMinor returns 12
drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
(II) AIGLX: enabled GLX_MESA_copy_sub_buffer
(II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
(II) AIGLX: enabled GLX_texture_from_pixmap with driver support
(II) AIGLX: Loaded and initialized /usr/lib/dri/i915_dri.so
(II) GLX: Initialized DRI GL provider for screen 0
(II) intel(0): Setting screen physical size to 331 x 207
(EE) config/hal: couldn't initialise context: (null) ((null))
(II) intel(0): xf86UnbindGARTMemory: unbind key 0
(II) intel(0): xf86UnbindGARTMemory: unbind key 1
(II) intel(0): xf86UnbindGARTMemory: unbind key 2
(II) intel(0): xf86UnbindGARTMemory: unbind key 3
(II) intel(0): xf86UnbindGARTMemory: unbind key 4
(II) intel(0): [drm] removed 1 reserved context for kernel
(II) intel(0): [drm] unmapping 8192 bytes of SAREA 0xf8a69000 at 0xb7995000
(II) intel(0): [drm] Closed DRM master.

```

---

### Post by xItachi on 2009-02-15
I tried to reconfigure gdm:

$ sudo dpkg-reconfigure gdm

```

* Reloading GNOME Display Manager configuration... 
* Changes will take effect when all current X sessions have ended.  
invoke-rc.d: initscript gdm, action reload failed.

```

---

