---
title: "Aurora TNT-2 M64 video card not recognized"
date: 2009-03-19
forum: New to Ubuntu
---

### Post by peyre on 2009-03-19
I'm all pumped up about switching full-time from Windows to linux!  But I'm stuck on one thing: my video card doesn't seem to be recognized by Xubuntu 8.10.  My resolution won't go higher than 800x600, and to confirm, I don't see my video card in Device Manager.

The card is an SIIG Aurora AGP 32MB TNT-2 M64, Model VD1755.

Does anyone know if there's a driver or something available for it?

---

### Post by 73ckn797 on 2009-03-19
In a terminal enter:
```
sudo lspci
```
Does the video card show up there? It might list it as "VGA compatible controller".

---

### Post by peyre on 2009-03-19
> **73ckn797 said:**
> In a terminal enter:
```
sudo lspci
```
Does the video card show up there? It might list it as "VGA compatible controller".

It does!  It shows as an nVidia NV5 [RIVA TNT2/TNT2 Pro] (rev 15).  And looking again, I see it DOES show in Device Manager.  I must be blind, or not paying enough attention.  But, so what does this mean?  Would nVidia cards likely widen my display options, or is there some other trick, or am I stuck with 800x600?  That's really not adequate for my main system.  I'm not looking for anything fancy, just plain old 1024x768.

---

### Post by 73ckn797 on 2009-03-19
I should of had you post the results of the command I recommended. If it is a Nvidia chipset you may need to go to System/Administration/Hardware Drivers. If there is a recommended video driver listed, you will want to "activate" that one. That ought to get you going.

---

### Post by peyre on 2009-03-20
> **73ckn797 said:**
> I should of had you post the results of the command I recommended. If it is a Nvidia chipset you may need to go to System/Administration/Hardware Drivers. If there is a recommended video driver listed, you will want to "activate" that one. That ought to get you going.

That's the funny thing!  I've been in Hardware Drivers before (and just double-checked), and it says there are no proprietary drivers in use on the system.  There are no drivers listed in there either.  :frown:

---

### Post by 73ckn797 on 2009-03-20
Go to System/Administration/Software Sources.

Do you have the "(restricted)" and "(multiverse) repositories selected?

---

### Post by Bachstelze on 2009-03-20
Your card requires the 71.* version of the nvidia driver. If it does not appear in the restricted drivers manager, you can install it with

```
sudo apt-get install nvidia-glx-71
```

---

### Post by peyre on 2009-03-20
> **73ckn797 said:**
> Go to System/Administration/Software Sources.

Do you have the "(restricted)" and "(multiverse) repositories selected?

**Of course!**  Why didn't I think of that?  I'll add those and see what happens.  (Sadly I may not be able to get to my computer again until Sunday, so I may have to go dark here for a bit.)

---

### Post by peyre on 2009-03-20
> **HymnToLife said:**
> Your card requires the 71.* version of the nvidia driver. If it does not appear in the restricted drivers manager, you can install it with

```
sudo apt-get install nvidia-glx-71
```

Très bien!  Thanks--I'll try that if adding those repositories doesn't do the trick.

---

### Post by Bachstelze on 2009-03-20
> **peyre said:**
> Très bien!  Thanks--I'll try that if adding those repositories doesn't do the trick.

You'll have to add the repositories for that to work anyway. ;) It's just the command-line way if the restricted driver manager somehow fails, but they both do the same thing.

---

### Post by peyre on 2009-03-22
> **73ckn797 said:**
> Go to System/Administration/Software Sources.

Do you have the "(restricted)" and "(multiverse) repositories selected?

Ok, I'm finally home.  I've checked, and yes, I do have those repositories selected.  :(

---

### Post by peyre on 2009-03-22
> **HymnToLife said:**
> You'll have to add the repositories for that to work anyway. ;) It's just the command-line way if the restricted driver manager somehow fails, but they both do the same thing.

Ok.  But, damn, it doesn't seem to have worked.  I ran it and restarted, but Display properties still don't offer anything higher than 800x600, and there are still no proprietary drivers available in Hardware Drivers.

---

### Post by peyre on 2009-03-23
I seem to be making some headway, at least as far as finding some more revealing error messages.  I don't know what to make of 'em, but maybe one of you can.

I went to nVidia's site and downloaded the linux driver for my video card, then installed it.  On reboot, one of the lines of text that comes up shows the number of the device driver (71.86.09, IIRC).  It sits there for a few seconds, then the next line comes up: DKMS auto installation service, and the result is a red [COLOR="Red"][fail][/COLOR].  Then an error message comes up in X:

Ubuntu is running in low-graphics mode.
(EE) Failed to load /usr/lib/xorg/modules/drivers//nvidia_drv.so
(EE) Failed to load module driver "nvidia" (loader failed, 7)
(EE) No drivers available.

Any ideas?

---

### Post by Bachstelze on 2009-03-23
The error you're getting now is because you have two version of the drivers installed: the ubuntu packages and the version from nvidia. You can only have one of them, so make up your mind. ;)

I think it's better for you to go with the Ubuntu version, so:

Uninstall the nvidia version:

```
sudo sh NVIDIA**** --uninstall
```

---

### Post by peyre on 2009-03-23
> **HymnToLife said:**
> The error you're getting now is because you have two version of the drivers installed: the ubuntu packages and the version from nvidia. You can only have one of them, so make up your mind. ;)

I think it's better for you to go with the Ubuntu version, so:

Uninstall the nvidia version:

```
sudo sh NVIDIA**** --uninstall
```

Wait, Ubuntu installed a generic driver that doesn't allow resolutions higher than 800x600, which really is inadequate for my main computer.  The whole point of this exercise was to install a driver that enables higher resolutions than the generic one.

Also, I forgot to mention that I became fed up with it and wanted to start over fresh (this is a brand-new install anyway), so I reinstalled Xubuntu.  This time instead of installing the nVidia driver directly, I installed EnvyNG first thing, and had it install the driver it recommended, which was the 71.  Unfortunately I got the same result, same errors, etc.

I've been surfing around for information about these errors, and am finding there may be a built-in incompatibility between the nVidia drivers and the latest version of X server (e.g., [here]("https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-96/+bug/251107")).  Does that sound like it might be the problem?

Also, someone reported there's a beta driver out there that might do the job: [http://www.nvnews.net/vbulletin/showthread.php?t=122139]("http://www.nvnews.net/vbulletin/showthread.php?t=122139").  I might have to give that one a try, unless you think that's a bad idea.

---

### Post by Bachstelze on 2009-03-23
Now I need to have a look at your X log and config files. Those two files are located at [font="monospace"]/var/log/Xorg.0.log[/font] and [font="monospace"]/etc/X11/xorg.conf[/font], respectively. You can paste them here with CODE tags around them to make them more readable.

---

### Post by peyre on 2009-03-23
> **HymnToLife said:**
> Now I need to have a look at your X log and config files. Those two files are located at [font="monospace"]/var/log/Xorg.0.log[/font] and [font="monospace"]/etc/X11/xorg.conf[/font], respectively. You can paste them here with CODE tags around them to make them more readable.

Here they are...

==============================================================
Xorg.0.log:
```

X.Org X Server 1.5.2
Release Date: 10 October 2008
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-19-server i686 Ubuntu
Current Operating System: Linux peyretower 2.6.27-7-generic #1 SMP Fri Oct 24 06:42:44 UTC 2008 i686
Build Date: 24 October 2008  08:00:16AM
xorg-server 2:1.5.2-2ubuntu3 (buildd@rothera.buildd) 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Mon Mar 23 17:56:07 2009
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
(++) using VT number 7

(--) PCI:*(0@1:0:0) nVidia Corporation NV5 [RIVA TNT2/TNT2 Pro] rev 21, Mem @ 0xfd000000/0, 0xf2000000/0, BIOS @ 0x????????/65536
(II) System resource ranges:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) "extmod" will be loaded by default.
(II) "dbe" will be loaded by default.
(II) "glx" will be loaded by default.
(II) "freetype" will be loaded by default.
(II) "record" will be loaded by default.
(II) "dri" will be loaded. This was enabled by default and also specified in the config file.
(II) LoadModule: "dri"

(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	ABI class: X.Org Server Extension, version 1.1
(II) Loading extension XFree86-DRI
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
(II) LoadModule: "nv"

(II) Loading /usr/lib/xorg/modules/drivers//nv_drv.so
(II) Module nv: vendor="X.Org Foundation"
	compiled for 1.5.0, module version = 2.1.10
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 4.1
(II) NV: driver for NVIDIA chipsets: RIVA 128, RIVA TNT, RIVA TNT2,
	Unknown TNT2, Vanta, RIVA TNT2 Ultra, RIVA TNT2 Model 64,
	Aladdin TNT2, GeForce 256, GeForce DDR, Quadro, GeForce2 MX/MX 400,
	GeForce2 MX 100/200, GeForce2 Go, Quadro2 MXR/EX/Go,
	GeForce2 Integrated GPU, GeForce2 GTS, GeForce2 Ti, GeForce2 Ultra,
	Quadro2 Pro, GeForce4 MX 460, GeForce4 MX 440, GeForce4 MX 420,
	GeForce4 MX 440-SE, GeForce4 440 Go, GeForce4 420 Go,
	GeForce4 420 Go 32M, GeForce4 460 Go, Quadro4 550 XGL,
	GeForce4 440 Go 64M, Quadro NVS, Quadro4 500 GoGL,
	GeForce4 410 Go 16M, GeForce4 MX 440 with AGP8X,
	GeForce4 MX 440SE with AGP8X, GeForce4 MX 420 with AGP8X,
	GeForce4 MX 4000, GeForce4 448 Go, GeForce4 488 Go, Quadro4 580 XGL,
	Quadro4 NVS 280 SD, Quadro4 380 XGL, Quadro NVS 50 PCI,
	GeForce4 448 Go, GeForce4 MX Integrated GPU, GeForce3,
	GeForce3 Ti 200, GeForce3 Ti 500, Quadro DCC, GeForce4 Ti 4600,
	GeForce4 Ti 4400, GeForce4 Ti 4200, Quadro4 900 XGL, Quadro4 750 XGL,
	Quadro4 700 XGL, GeForce4 Ti 4800, GeForce4 Ti 4200 with AGP8X,
	GeForce4 Ti 4800 SE, GeForce4 4200 Go, Quadro4 700 GoGL,
	Quadro4 980 XGL, Quadro4 780 XGL, GeForce FX 5800 Ultra,
	GeForce FX 5800, Quadro FX 2000, Quadro FX 1000,
	GeForce FX 5600 Ultra, GeForce FX 5600, GeForce FX 5600XT,
	GeForce FX Go5600, GeForce FX Go5650, Quadro FX Go700,
	GeForce FX 5200, GeForce FX 5200 Ultra, GeForce FX 5200,
	GeForce FX 5200LE, GeForce FX Go5200, GeForce FX Go5250,
	GeForce FX 5500, GeForce FX 5100, GeForce FX Go5200 32M/64M,
	Quadro NVS 55/280 PCI, Quadro FX 500/600 PCI,
	GeForce FX Go53xx Series, GeForce FX Go5100, GeForce FX 5900 Ultra,
	GeForce FX 5900, GeForce FX 5900XT, GeForce FX 5950 Ultra,
	GeForce FX 5900ZT, Quadro FX 3000, Quadro FX 700,
	GeForce FX 5700 Ultra, GeForce FX 5700, GeForce FX 5700LE,
	GeForce FX 5700VE, GeForce FX Go5700, GeForce FX Go5700,
	Quadro FX Go1000, Quadro FX 1100, GeForce 6800 Ultra, GeForce 6800,
	GeForce 6800 LE, GeForce 6800 XE, GeForce 6800 XT, GeForce 6800 GT,
	GeForce 6800 GT, GeForce 6800 GS, GeForce 6800 XT, Quadro FX 4000,
	GeForce 6800 GS, GeForce 6800, GeForce 6800 LE, GeForce 6800 XT,
	GeForce Go 6800, GeForce Go 6800 Ultra, Quadro FX Go1400,
	Quadro FX 3450/4000 SDI, Quadro FX 1400, GeForce 6600 GT,
	GeForce 6600, GeForce 6600 LE, GeForce 6600 VE, GeForce Go 6600,
	GeForce 6610 XL, GeForce Go 6600 TE/6200 TE, GeForce 6700 XL,
	GeForce Go 6600, GeForce Go 6600 GT, Quadro FX 550, Quadro FX 550,
	Quadro FX 540, GeForce 6200, GeForce 6500,
	GeForce 6200 TurboCache(TM), GeForce 6200SE TurboCache(TM),
	GeForce 6200 LE, GeForce Go 6200, Quadro NVS 285, GeForce Go 6400,
	GeForce Go 6200, GeForce Go 6400, GeForce 6250, GeForce 6800,
	GeForce 6800 LE, GeForce 6800 GT, GeForce 6800 XT, GeForce 6200,
	GeForce 6200 A-LE, GeForce 7800 GTX, GeForce 7800 GTX,
	GeForce 7800 GT, GeForce 7800 GS, GeForce 7800 SLI, GeForce Go 7800,
	GeForce Go 7800 GTX, Quadro FX 4500, GeForce 7300 LE,
	GeForce 7300 SE, GeForce Go 7200, GeForce Go 7300, GeForce Go 7400,
	GeForce Go 7400 GS, Quadro NVS 110M, Quadro NVS 120M, Quadro FX 350M,
	GeForce 7500 LE, Quadro FX 350, GeForce 7300 GS, GeForce 7600 GT,
	GeForce 7600 GS, GeForce 7300 GT, GeForce 7600 LE, GeForce 7300 GT,
	GeForce Go 7700, GeForce Go 7600, GeForce Go 7600 GT,
	Quadro NVS 300M, GeForce Go 7900 SE, Quadro FX 550M, Quadro FX 560,
	GeForce 7900 GTX, GeForce 7900 GT, GeForce 7900 GS,
	GeForce Go 7900 GS, GeForce Go 7900 GTX, Quadro FX 2500M,
	Quadro FX 1500M, Quadro FX 5500, Quadro FX 3500, Quadro FX 1500,
	Quadro FX 4500 X2, GeForce 6150, GeForce 6150 LE, GeForce 6100,
	GeForce Go 6150, GeForce Go 6100, GeForce 8800 GTX, GeForce 8800 GTS,
	GeForce 8800 Ultra, Quadro FX 5600, Quadro FX 4600, GeForce 8600 GTS,
	GeForce 8600 GT, GeForce 8600 GT, GeForce 8400 GS, GeForce 9500M GS,
	GeForce 8600M GT, GeForce 9650M GS, GeForce 8700M GT, Quadro FX 370,
	Quadro NVS 320M, Quadro FX 570M, Quadro FX 1600M, Quadro FX 570,
	Quadro FX 1700, GeForce 8400 SE, GeForce 8500 GT, GeForce 8400 GS,
	GeForce 8300 GS, GeForce 8400 GS, GeForce 8600M GS, GeForce 8400M GT,
	GeForce 8400M GS, GeForce 8400M G, Quadro NVS 140M, Quadro NVS 130M,
	Quadro NVS 135M, Quadro FX 360M, GeForce 9300M G, Quadro NVS 290,
	GeForce GTX 280, GeForce GTX 260, GeForce 8800 GTS 512,
	GeForce 8800 GT, GeForce 9800 GX2, GeForce 8800 GS,
	GeForce 8800M GTS, GeForce 8800M GTX, GeForce 8800 GS,
	GeForce 9600 GSO, GeForce 8800 GT, GeForce 9800 GTX, Quadro FX 3700,
	Quadro FX 3600M, GeForce 9600 GT, GeForce 9600M GT, GeForce 9600M GS,
	GeForce 9600M GT, GeForce 9500M G, GeForce 8400 GS, GeForce 9300M GS,
	GeForce 9200M GS, GeForce 9300M GS
(II) Primary Device is: PCI 01@00:00:0
(--) NV: Found NVIDIA RIVA TNT2 at 01@00:00:0
(II) resource ranges after probing:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) Loading sub module "int10"
(II) LoadModule: "int10"

(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	ABI class: X.Org Video Driver, version 4.1
(II) NV(0): Initializing int10
(II) NV(0): Primary V_BIOS segment is: 0xc000
(--) NV(0): Chipset: "RIVA TNT2"
(II) NV(0): Creating default Display subsection in Screen section
	"Default Screen" for depth/fbbpp 24/32
(**) NV(0): Depth 24, (--) framebuffer bpp 32
(==) NV(0): RGB weight 888
(==) NV(0): Default visual is TrueColor
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"

(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 0.1.0
	ABI class: X.Org Video Driver, version 4.1
(==) NV(0): Using HW cursor
(--) NV(0): Linear framebuffer at 0xF2000000
(--) NV(0): MMIO registers at 0xFD000000
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"
(II) Module "i2c" already built-in
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(II) NV(0): I2C bus "DDC" initialized.
(II) NV(0): Probing for EDID on I2C bus A...
(II) NV(0): I2C device "DDC:ddc2" registered at address 0xA0.
(II) NV(0): I2C device "DDC:ddc2" removed.
(II) NV(0):   ... none found
(--) NV(0): HW is currently programmed for CRT
(II) NV(0): Using CRT on CRTC 0
(--) NV(0): VideoRAM: 16384 kBytes
(==) NV(0): Using gamma correction (1.0, 1.0, 1.0)
(II) NV(0): Configured Monitor: Using default hsync range of 31.50-37.90 kHz
(II) NV(0): Configured Monitor: Using default vrefresh range of 50.00-70.00 Hz
(WW) NV(0): Unable to estimate virtual size
(II) NV(0): Clock range:  12.00 to 350.00 MHz
(II) NV(0): Not using default mode "640x350" (vrefresh out of range)
(II) NV(0): Not using default mode "320x175" (vrefresh out of range)
(II) NV(0): Not using default mode "640x400" (vrefresh out of range)
(II) NV(0): Not using default mode "320x200" (vrefresh out of range)
(II) NV(0): Not using default mode "720x400" (vrefresh out of range)
(II) NV(0): Not using default mode "360x200" (vrefresh out of range)
(II) NV(0): Not using default mode "640x480" (vrefresh out of range)
(II) NV(0): Not using default mode "320x240" (vrefresh out of range)
(II) NV(0): Not using default mode "640x480" (vrefresh out of range)
(II) NV(0): Not using default mode "320x240" (vrefresh out of range)
(II) NV(0): Not using default mode "640x480" (hsync out of range)
(II) NV(0): Not using default mode "320x240" (hsync out of range)
(II) NV(0): Not using default mode "800x600" (hsync out of range)
(II) NV(0): Not using default mode "400x300" (hsync out of range)
(II) NV(0): Not using default mode "800x600" (hsync out of range)
(II) NV(0): Not using default mode "400x300" (hsync out of range)
(II) NV(0): Not using default mode "800x600" (hsync out of range)
(II) NV(0): Not using default mode "400x300" (hsync out of range)
(II) NV(0): Not using default mode "1024x768" (vrefresh out of range)
(II) NV(0): Not using default mode "512x384" (vrefresh out of range)
(II) NV(0): Not using default mode "1024x768" (hsync out of range)
(II) NV(0): Not using default mode "512x384" (hsync out of range)
(II) NV(0): Not using default mode "1024x768" (hsync out of range)
(II) NV(0): Not using default mode "512x384" (hsync out of range)
(II) NV(0): Not using default mode "1024x768" (hsync out of range)
(II) NV(0): Not using default mode "512x384" (hsync out of range)
(II) NV(0): Not using default mode "1024x768" (hsync out of range)
(II) NV(0): Not using default mode "512x384" (hsync out of range)
(II) NV(0): Not using default mode "1152x864" (hsync out of range)
(II) NV(0): Not using default mode "576x432" (hsync out of range)
(II) NV(0): Not using default mode "1280x960" (hsync out of range)
(II) NV(0): Not using default mode "640x480" (hsync out of range)
(II) NV(0): Not using default mode "1280x960" (hsync out of range)
(II) NV(0): Not using default mode "640x480" (hsync out of range)
(II) NV(0): Not using default mode "1280x1024" (hsync out of range)
(II) NV(0): Not using default mode "640x512" (hsync out of range)
(II) NV(0): Not using default mode "1280x1024" (hsync out of range)
(II) NV(0): Not using default mode "640x512" (hsync out of range)
(II) NV(0): Not using default mode "1280x1024" (hsync out of range)
(II) NV(0): Not using default mode "640x512" (hsync out of range)
(II) NV(0): Not using default mode "1600x1200" (hsync out of range)
(II) NV(0): Not using default mode "800x600" (hsync out of range)
(II) NV(0): Not using default mode "1600x1200" (hsync out of range)
(II) NV(0): Not using default mode "800x600" (hsync out of range)
(II) NV(0): Not using default mode "1600x1200" (hsync out of range)
(II) NV(0): Not using default mode "800x600" (hsync out of range)
(II) NV(0): Not using default mode "1600x1200" (hsync out of range)
(II) NV(0): Not using default mode "800x600" (hsync out of range)
(II) NV(0): Not using default mode "1600x1200" (hsync out of range)
(II) NV(0): Not using default mode "800x600" (hsync out of range)
(II) NV(0): Not using default mode "1792x1344" (hsync out of range)
(II) NV(0): Not using default mode "896x672" (hsync out of range)
(II) NV(0): Not using default mode "1792x1344" (hsync out of range)
(II) NV(0): Not using default mode "896x672" (hsync out of range)
(II) NV(0): Not using default mode "1856x1392" (hsync out of range)
(II) NV(0): Not using default mode "928x696" (hsync out of range)
(II) NV(0): Not using default mode "1856x1392" (hsync out of range)
(II) NV(0): Not using default mode "928x696" (hsync out of range)
(II) NV(0): Not using default mode "1920x1440" (hsync out of range)
(II) NV(0): Not using default mode "960x720" (hsync out of range)
(II) NV(0): Not using default mode "1920x1440" (hsync out of range)
(II) NV(0): Not using default mode "960x720" (hsync out of range)
(II) NV(0): Not using default mode "832x624" (hsync out of range)
(II) NV(0): Not using default mode "416x312" (hsync out of range)
(II) NV(0): Not using default mode "1152x864" (hsync out of range)
(II) NV(0): Not using default mode "576x432" (hsync out of range)
(II) NV(0): Not using default mode "1152x864" (hsync out of range)
(II) NV(0): Not using default mode "576x432" (hsync out of range)
(II) NV(0): Not using default mode "1152x864" (hsync out of range)
(II) NV(0): Not using default mode "576x432" (hsync out of range)
(II) NV(0): Not using default mode "1152x864" (hsync out of range)
(II) NV(0): Not using default mode "576x432" (hsync out of range)
(II) NV(0): Not using default mode "1152x864" (hsync out of range)
(II) NV(0): Not using default mode "576x432" (hsync out of range)
(II) NV(0): Not using default mode "1152x864" (hsync out of range)
(II) NV(0): Not using default mode "576x432" (hsync out of range)
(II) NV(0): Not using default mode "1360x768" (hsync out of range)
(II) NV(0): Not using default mode "680x384" (hsync out of range)
(II) NV(0): Not using default mode "1360x768" (hsync out of range)
(II) NV(0): Not using default mode "680x384" (hsync out of range)
(II) NV(0): Not using default mode "1400x1050" (hsync out of range)
(II) NV(0): Not using default mode "700x525" (hsync out of range)
(II) NV(0): Not using default mode "1400x1050" (hsync out of range)
(II) NV(0): Not using default mode "700x525" (hsync out of range)
(II) NV(0): Not using default mode "1400x1050" (hsync out of range)
(II) NV(0): Not using default mode "700x525" (hsync out of range)
(II) NV(0): Not using default mode "1400x1050" (hsync out of range)
(II) NV(0): Not using default mode "700x525" (hsync out of range)
(II) NV(0): Not using default mode "1440x900" (hsync out of range)
(II) NV(0): Not using default mode "720x450" (hsync out of range)
(II) NV(0): Not using default mode "1600x1024" (hsync out of range)
(II) NV(0): Not using default mode "800x512" (hsync out of range)
(II) NV(0): Not using default mode "1680x1050" (hsync out of range)
(II) NV(0): Not using default mode "840x525" (hsync out of range)
(II) NV(0): Not using default mode "1680x1050" (hsync out of range)
(II) NV(0): Not using default mode "840x525" (hsync out of range)
(II) NV(0): Not using default mode "1680x1050" (hsync out of range)
(II) NV(0): Not using default mode "840x525" (hsync out of range)
(II) NV(0): Not using default mode "1680x1050" (hsync out of range)
(II) NV(0): Not using default mode "840x525" (hsync out of range)
(II) NV(0): Not using default mode "1680x1050" (hsync out of range)
(II) NV(0): Not using default mode "840x525" (hsync out of range)
(II) NV(0): Not using default mode "1920x1080" (hsync out of range)
(II) NV(0): Not using default mode "960x540" (hsync out of range)
(II) NV(0): Not using default mode "1920x1200" (hsync out of range)
(II) NV(0): Not using default mode "960x600" (hsync out of range)
(II) NV(0): Not using default mode "1920x1440" (hsync out of range)
(II) NV(0): Not using default mode "960x720" (hsync out of range)
(II) NV(0): Not using default mode "2048x1536" (width requires unsupported line pitch)
(II) NV(0): Not using default mode "1024x768" (hsync out of range)
(II) NV(0): Not using default mode "2048x1536" (width requires unsupported line pitch)
(II) NV(0): Not using default mode "1024x768" (hsync out of range)
(II) NV(0): Not using default mode "2048x1536" (width requires unsupported line pitch)
(II) NV(0): Not using default mode "1024x768" (hsync out of range)
(--) NV(0): Virtual size is 800x600 (pitch 800)
(**) NV(0): *Default mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
(II) NV(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(**) NV(0): *Default mode "800x600": 36.0 MHz, 35.2 kHz, 56.2 Hz
(II) NV(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(**) NV(0): *Default mode "640x480": 25.2 MHz, 31.5 kHz, 59.9 Hz
(II) NV(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(**) NV(0): *Default mode "400x300": 20.0 MHz, 37.9 kHz, 60.3 Hz (D)
(II) NV(0): Modeline "400x300"x60.3   20.00  400 420 484 528  300 300 302 314 doublescan +hsync +vsync (37.9 kHz)
(**) NV(0): *Default mode "400x300": 18.0 MHz, 35.2 kHz, 56.3 Hz (D)
(II) NV(0): Modeline "400x300"x56.3   18.00  400 412 448 512  300 300 301 312 doublescan +hsync +vsync (35.2 kHz)
(**) NV(0): *Default mode "320x240": 12.6 MHz, 31.5 kHz, 60.1 Hz (D)
(II) NV(0): Modeline "320x240"x60.1   12.59  320 328 376 400  240 245 246 262 doublescan -hsync -vsync (31.5 kHz)
(==) NV(0): DPI set to (96, 96)
(II) Loading sub module "fb"
(II) LoadModule: "fb"

(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"

(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.2.0
	ABI class: X.Org Video Driver, version 4.1
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) NV(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	8x8 mono pattern filled rectangles
	Indirect CPU to Screen color expansion
	Solid Lines
	Scanline Image Writes
	Setting up tile and stipple cache:
		32 128x128 slots
		20 256x256 slots
		6 512x512 slots
(==) NV(0): Backing store disabled
(==) NV(0): Silken mouse enabled
(II) NV(0): DPMS enabled
(==) RandR enabled
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
(II) AIGLX: Screen 0 is not DRI capable
(II) AIGLX: Loaded and initialized /usr/lib/dri/swrast_dri.so
(II) GLX: Initialized DRISWRAST GL provider for screen 0
(II) config/hal: Adding input device Macintosh mouse button emulation
(II) LoadModule: "evdev"

(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 2.0.99
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.1
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event0"
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Configuring as mouse
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) config/hal: Adding input device PS/2 Logitech Mouse
(**) PS/2 Logitech Mouse: always reports core events
(**) PS/2 Logitech Mouse: Device: "/dev/input/event6"
(II) PS/2 Logitech Mouse: Found x and y relative axes
(II) PS/2 Logitech Mouse: Found 2 mouse buttons
(II) PS/2 Logitech Mouse: Configuring as mouse
(II) XINPUT: Adding extended input device "PS/2 Logitech Mouse" (type: MOUSE)
(**) PS/2 Logitech Mouse: YAxisMapping: buttons 4 and 5
(**) PS/2 Logitech Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) config/hal: Adding input device AT Translated Set 2 keyboard
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
AUDIT: Mon Mar 23 18:09:01 2009: 4785 X: client 4 rejected from local host ( uid=1000 gid=1000 pid=4997 )
AUDIT: Mon Mar 23 18:09:01 2009: 4785 X: client 4 rejected from local host ( uid=1000 gid=1000 pid=4998 )
AUDIT: Mon Mar 23 18:09:01 2009: 4785 X: client 4 rejected from local host ( uid=1000 gid=1000 pid=4999 )

```

==============================================================
xorg.conf:
```
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"dri"
	Load	"GLcore"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"nv"
EndSection


```

---

### Post by peyre on 2009-03-25
Well I'll be.  Turns out the problem was I had it plugged into a KVM switch.  I didn't think to mention it 'cause who would think that was the problem?  Silly me.  So I plugged a monitor in directly, and problem solved, it seems.

Thanks for your help!

---

