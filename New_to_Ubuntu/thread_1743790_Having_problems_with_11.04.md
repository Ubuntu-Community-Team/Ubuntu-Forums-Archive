---
title: "Having problems with 11.04"
date: 2011-04-29
forum: New to Ubuntu
---

### Post by myersmarkl on 2011-04-29
I am having problems after a fresh install of 11.04. The install seemed to work. However, when I boot after the install all I see is a message on the screen that says Out Of Range.  I have booted from the install media and looked at the Xorg log file found in /var/log. The log file says fatal error no screens found.

The PC is Pentium 4, with an Nvidia video card, a Hauppauge hvr1600 capture card, and a Westinghouse LCD monitor. 

Thanks

Mark

---

### Post by StarLab on 2011-04-29
> **myersmarkl said:**
> I am having problems after a fresh install of 11.04. The install seemed to work. However, when I boot after the install all I see is a message on the screen that says Out Of Range.  I have booted from the install media and looked at the Xorg log file found in /var/log. The log file says fatal error no screens found.

The PC is Pentium 4, with an Nvidia video card, a Hauppauge hvr1600 capture card, and a Westinghouse LCD monitor. 

Thanks

Mark

Happens to me on every boot. However, it only lasts 10-15 seconds and then the boot continues. At least it does for me. 

It's just putting out a signal that the monitor can't handle and it's the monitor itself telling you this. (At least in my case)

HTH

---

### Post by K_45 on 2011-04-29
Press Ctrl+Alt+F1 and log in to the terminal, then

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

then

```
sudo reboot
```

If that doesn't work post the output of:

```
xrandr
```

---

### Post by myersmarkl on 2011-04-29
alt+ctrl+f1 does not do anything. I know that it is supposed to the first virtual console but nothing happens.

---

### Post by K_45 on 2011-04-29
Its Ctrl+Alt,* not *Alt+Ctrl. If it still doesn't work try Ctrl+Alt+F2.

---

### Post by myersmarkl on 2011-04-29
None of these work ctrl+alt+ f1 or f2 or f3 or f4.

If it helps here is my Xorg log.
```

[    29.959] 
X.Org X Server 1.10.1
Release Date: 2011-04-15
[    29.959] X Protocol Version 11, Revision 0
[    29.959] Build Operating System: Linux 2.6.24-29-server i686 Ubuntu
[    29.959] Current Operating System: Linux tv23 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:50 UTC 2011 i686
[    29.959] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.38-8-generic root=UUID=07628262-8d7b-4dd7-bd3d-363879a05689 ro quiet splash vt.handoff=7
[    29.959] Build Date: 19 April 2011  03:33:17PM
[    29.959] xorg-server 2:1.10.1-1ubuntu1 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[    29.959] Current version of pixman: 0.20.2
[    29.959] 	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
[    29.959] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    29.959] (==) Log file: "/var/log/Xorg.0.log", Time: Fri Apr 29 17:15:51 2011
[    29.960] (==) Using config file: "/etc/X11/xorg.conf"
[    29.960] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    29.960] (==) No Layout section.  Using the first Screen section.
[    29.960] (==) No screen section available. Using defaults.
[    29.960] (**) |-->Screen "Default Screen Section" (0)
[    29.960] (**) |   |-->Monitor "<default monitor>"
[    29.961] (==) No device specified for screen "Default Screen Section".
	Using the first device section listed.
[    29.961] (**) |   |-->Device "Default Device"
[    29.961] (==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
[    29.961] (==) Automatically adding devices
[    29.961] (==) Automatically enabling devices
[    29.961] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    29.961] 	Entry deleted from font path.
[    29.961] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    29.961] 	Entry deleted from font path.
[    29.961] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    29.961] 	Entry deleted from font path.
[    29.961] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    29.961] 	Entry deleted from font path.
[    29.962] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    29.962] 	Entry deleted from font path.
[    29.962] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[    29.962] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    29.962] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    29.962] (II) Loader magic: 0x81ffde0
[    29.962] (II) Module ABI versions:
[    29.962] 	X.Org ANSI C Emulation: 0.4
[    29.962] 	X.Org Video Driver: 10.0
[    29.962] 	X.Org XInput driver : 12.3
[    29.962] 	X.Org Server Extension : 5.0
[    29.963] (--) PCI:*(0:1:0:0) 10de:02e2:19f1:04e3 rev 162, Mem @ 0xfc000000/16777216, 0xe0000000/268435456, 0xfd000000/16777216, BIOS @ 0x????????/131072
[    29.963] (--) PCI: (0:2:8:0) 14f1:5b7a:0070:7400 rev 0, Mem @ 0xf8000000/67108864
[    29.964] (II) Open ACPI successful (/var/run/acpid.socket)
[    29.964] (II) LoadModule: "extmod"
[    29.965] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    29.965] (II) Module extmod: vendor="X.Org Foundation"
[    29.965] 	compiled for 1.10.1, module version = 1.0.0
[    29.965] 	Module class: X.Org Server Extension
[    29.965] 	ABI class: X.Org Server Extension, version 5.0
[    29.965] (II) Loading extension MIT-SCREEN-SAVER
[    29.965] (II) Loading extension XFree86-VidModeExtension
[    29.965] (II) Loading extension XFree86-DGA
[    29.965] (II) Loading extension DPMS
[    29.965] (II) Loading extension XVideo
[    29.966] (II) Loading extension XVideo-MotionCompensation
[    29.966] (II) Loading extension X-Resource
[    29.966] (II) LoadModule: "dbe"
[    29.966] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    29.967] (II) Module dbe: vendor="X.Org Foundation"
[    29.967] 	compiled for 1.10.1, module version = 1.0.0
[    29.967] 	Module class: X.Org Server Extension
[    29.967] 	ABI class: X.Org Server Extension, version 5.0
[    29.967] (II) Loading extension DOUBLE-BUFFER
[    29.967] (II) LoadModule: "glx"
[    29.967] (II) Loading /usr/lib/xorg/extra-modules/libglx.so
[    30.022] (II) Module glx: vendor="NVIDIA Corporation"
[    30.153] 	compiled for 4.0.2, module version = 1.0.0
[    30.153] 	Module class: X.Org Server Extension
[    30.153] (II) NVIDIA GLX Module  173.14.30  Thu Apr 14 09:20:02 PDT 2011
[    30.153] (II) Loading extension GLX
[    30.153] (II) LoadModule: "record"
[    30.155] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    30.155] (II) Module record: vendor="X.Org Foundation"
[    30.155] 	compiled for 1.10.1, module version = 1.13.0
[    30.155] 	Module class: X.Org Server Extension
[    30.155] 	ABI class: X.Org Server Extension, version 5.0
[    30.155] (II) Loading extension RECORD
[    30.155] (II) LoadModule: "dri"
[    30.157] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    30.158] (II) Module dri: vendor="X.Org Foundation"
[    30.158] 	compiled for 1.10.1, module version = 1.0.0
[    30.158] 	ABI class: X.Org Server Extension, version 5.0
[    30.158] (II) Loading extension XFree86-DRI
[    30.158] (II) LoadModule: "dri2"
[    30.160] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    30.160] (II) Module dri2: vendor="X.Org Foundation"
[    30.160] 	compiled for 1.10.1, module version = 1.2.0
[    30.160] 	ABI class: X.Org Server Extension, version 5.0
[    30.160] (II) Loading extension DRI2
[    30.160] (==) Matched nvidia as autoconfigured driver 0
[    30.160] (==) Matched nouveau as autoconfigured driver 1
[    30.160] (==) Matched nv as autoconfigured driver 2
[    30.160] (==) Matched vesa as autoconfigured driver 3
[    30.161] (==) Matched fbdev as autoconfigured driver 4
[    30.161] (==) Assigned the driver to the xf86ConfigLayout
[    30.161] (II) LoadModule: "nvidia"
[    30.161] (II) Loading /usr/lib/xorg/extra-modules/nvidia_drv.so
[    30.163] (II) Module nvidia: vendor="NVIDIA Corporation"
[    30.163] 	compiled for 4.0.2, module version = 1.0.0
[    30.163] 	Module class: X.Org Video Driver
[    30.163] (II) LoadModule: "nouveau"
[    30.164] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[    30.164] (II) Module nouveau: vendor="X.Org Foundation"
[    30.164] 	compiled for 1.10.0, module version = 0.0.16
[    30.164] 	Module class: X.Org Video Driver
[    30.164] 	ABI class: X.Org Video Driver, version 10.0
[    30.164] (II) LoadModule: "nv"
[    30.166] (WW) Warning, couldn't open module nv
[    30.166] (II) UnloadModule: "nv"
[    30.166] (II) Unloading nv
[    30.166] (EE) Failed to load module "nv" (module does not exist, 0)
[    30.166] (II) LoadModule: "vesa"
[    30.166] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    30.167] (II) Module vesa: vendor="X.Org Foundation"
[    30.167] 	compiled for 1.10.0, module version = 2.3.0
[    30.167] 	Module class: X.Org Video Driver
[    30.167] 	ABI class: X.Org Video Driver, version 10.0
[    30.167] (II) LoadModule: "fbdev"
[    30.167] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    30.167] (II) Module fbdev: vendor="X.Org Foundation"
[    30.168] 	compiled for 1.10.0, module version = 0.4.2
[    30.168] 	ABI class: X.Org Video Driver, version 10.0
[    30.168] (II) NVIDIA dlloader X Driver  173.14.30  Thu Apr 14 08:56:42 PDT 2011
[    30.168] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    30.168] (II) NOUVEAU driver Date:   Fri Jan 7 13:33:36 2011 +1000
[    30.168] (II) NOUVEAU driver for NVIDIA chipset families :
[    30.168] 	RIVA TNT    (NV04)
[    30.168] 	RIVA TNT2   (NV05)
[    30.168] 	GeForce 256 (NV10)
[    30.168] 	GeForce 2   (NV11, NV15)
[    30.168] 	GeForce 4MX (NV17, NV18)
[    30.168] 	GeForce 3   (NV20)
[    30.168] 	GeForce 4Ti (NV25, NV28)
[    30.168] 	GeForce FX  (NV3x)
[    30.168] 	GeForce 6   (NV4x)
[    30.169] 	GeForce 7   (G7x)
[    30.169] 	GeForce 8   (G8x)
[    30.169] (II) VESA: driver for VESA chipsets: vesa
[    30.169] (II) FBDEV: driver for framebuffer: fbdev
[    30.169] (--) using VT number 1

[    30.345] (II) Loading sub module "fb"
[    30.352] (II) LoadModule: "fb"
[    30.353] (II) Loading /usr/lib/xorg/modules/libfb.so
[    30.354] (II) Module fb: vendor="X.Org Foundation"
[    30.354] 	compiled for 1.10.1, module version = 1.0.0
[    30.354] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    30.354] (II) Loading sub module "wfb"
[    30.354] (II) LoadModule: "wfb"
[    30.354] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    30.354] (II) Module wfb: vendor="X.Org Foundation"
[    30.354] 	compiled for 1.10.1, module version = 1.0.0
[    30.354] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    30.355] (II) Loading sub module "ramdac"
[    30.355] (II) LoadModule: "ramdac"
[    30.355] (II) Module "ramdac" already built-in
[    30.355] (II) Loading /usr/lib/xorg/extra-modules/nvidia_drv.so
[    30.355] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    30.355] (II) Loading /usr/lib/xorg/modules/libfb.so
[    30.355] (WW) Falling back to old probe method for vesa
[    30.355] (WW) Falling back to old probe method for fbdev
[    30.355] (II) Loading sub module "fbdevhw"
[    30.355] (II) LoadModule: "fbdevhw"
[    30.356] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    30.356] (II) Module fbdevhw: vendor="X.Org Foundation"
[    30.356] 	compiled for 1.10.1, module version = 0.0.2
[    30.356] 	ABI class: X.Org Video Driver, version 10.0
[    30.356] (II) NVIDIA(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
[    30.356] (==) NVIDIA(0): Depth 24, (==) framebuffer bpp 32
[    30.356] (==) NVIDIA(0): RGB weight 888
[    30.356] (==) NVIDIA(0): Default visual is TrueColor
[    30.356] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[    30.356] (**) NVIDIA(0): Option "NoLogo" "True"
[    30.356] (**) NVIDIA(0): Enabling RENDER acceleration
[    30.357] (II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
[    30.357] (II) NVIDIA(0):     enabled.
[    30.369] (EE) NVIDIA(0): Failed to initialize the NVIDIA graphics device PCI:1:0:0. 
[    30.369] (EE) NVIDIA(0):     Please see the COMMON PROBLEMS section in the README for
[    30.369] (EE) NVIDIA(0):     additional information.
[    30.369] (EE) NVIDIA(0): Failed to initialize the NVIDIA graphics device!
[    30.369] (II) UnloadModule: "nvidia"
[    30.369] (II) Unloading nvidia
[    30.369] (II) UnloadModule: "wfb"
[    30.370] (II) Unloading wfb
[    30.370] (II) UnloadModule: "fb"
[    30.370] (II) Unloading fb
[    30.370] (EE) Screen(s) found, but none have a usable configuration.
[    30.370] 
Fatal server error:
[    30.370] no screens found
[    30.370] 
Please consult the The X.Org Foundation support 
	 at [http://wiki.x.org](http://wiki.x.org)
 for help. 
[    30.370] Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[    30.370] 
[    30.701]  ddxSigGiveUp: Closing log
```

---

### Post by K_45 on 2011-04-29
Try the safe graphics mode midway down:  [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)  Then you can try setting up the monitor.

---

### Post by myersmarkl on 2011-04-29
I do not get presented with any of the options for changing anything. I see my bios screen then the screen is blank for maybe 2 seconds.  Then the message Out of Range.  I can ctrl+alt+del after the Out of Range message but nothing else seems to work. Also the PC never goes past the Out of Range message, probably because the Xorg log says there was a fatal error.

---

### Post by fabricator4 on 2011-04-29
> **myersmarkl said:**
> I do not get presented with any of the options for changing anything. I see my bios screen then the screen is blank for maybe 2 seconds.  Then the message Out of Range. 

To get to the grub boot screen keep pressing the shift key as it comes out of post.  You should see a range of options there including recovery mode which should get you into a default low-res mode.

Chris.

---

### Post by myersmarkl on 2011-04-29
Neither pressing and holding the shift key or repeatedly pressing the shift key does anything.  I tried the left shift key then after the Out of Range message showed up I rebooted and then I tried the the right shift key.

---

### Post by myersmarkl on 2011-04-30
I have temporary taken out my hvr1600 capture card and reinstalled 11.04.  This changed the symptoms such that the Out of Range message now only lasts for about 40 seconds then the desktop is loaded.  I found an app that I could install called Startup-Manager which I used to change the splash screen from 640x480 to 800x600 and now I no longer get the Out of Range message.  Now all that remains is to get 11.04 to work with my hvr1600 like 10.10 and 10.04 did.  Additionally I turned of Unity in favor of Ubuntu Classic since I found Unity far to simplistic for my tastes.  I hope that my turning off Unity does not make it harder to fix the Out of Range problem.

---

### Post by fabricator4 on 2011-04-30
> **myersmarkl said:**
> 10.04 did.  Additionally I turned of Unity in favor of Ubuntu Classic since I found Unity far to simplistic for my tastes.  I hope that my turning off Unity does not make it harder to fix the Out of Range problem.

I doubt that not using Unity will make things harder in that regard.  Investigate drivers for your card - you should be able to google some useful information.  Start a new thread if you get stuck.

Pulling extraneous cards is always a good way to simplify a problem.

For the record, shift is definitely the correct key to get the grub2 boot menu to come up at the start.  If you press and hold it while the computer is going through post it should work.  

Chris.

---

