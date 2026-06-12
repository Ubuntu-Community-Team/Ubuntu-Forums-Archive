---
title: "x Server - No screens found"
date: 2011-05-30
forum: New to Ubuntu
---

### Post by Sexraider on 2011-05-30
Seems to happened after I installed the packages for intel drivers, ect. After a reboot I'm stuck at command line before it'll start x server. I'm using a compaq presario cq50 139wm using Intel Graphics Media Accelerator 4500MHD as onboard graphics.

Here is the log.

```


X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-27-server i686 Ubuntu
Current Operating System: Linux bt 2.6.38 #1 SMP Thu Mar 17 20:52:18 EDT 2011 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.38 root=UUID=37bc7d66-dd8c-4db6-94f9-6195003f6239 ro text splash nomodeset vga=791
Build Date: 08 March 2011  08:22:50AM
xorg-server 2:1.7.6-2ubuntu7.6 (For technical support please see http://www.ubuntu.com/support) 
Current version of pixman: 0.16.4
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Mon May 30 21:38:52 2011
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
(WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
	Entry deleted from font path.
(==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
(==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
(II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
(II) Loader magic: 0x81f1e80
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 6.0
	X.Org XInput driver : 7.0
	X.Org Server Extension : 2.0
(--) using VT number 8

(--) PCI:*(0:0:2:0) 8086:2a42:103c:360b Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller rev 7, Mem @ 0x90000000/4194304, 0x80000000/268435456, I/O @ 0x00005110/8
(--) PCI: (0:0:2:1) 8086:2a43:103c:360b Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller rev 7, Mem @ 0x92500000/1048576
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
	compiled for 1.7.6, module version = 2.11.0
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
(WW) Falling back to old probe method for vesa
(WW) Falling back to old probe method for fbdev
(II) Loading sub module "fbdevhw"
(II) LoadModule: "fbdevhw"
(II) Loading /usr/lib/xorg/modules/linux/libfbdevhw.so
(II) Module fbdevhw: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 0.0.2
	ABI class: X.Org Video Driver, version 6.0
(EE) intel(0): No kernel modesetting driver detected.
(II) UnloadModule: "intel"
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found

Please consult the The X.Org Foundation support 
	 at http://wiki.x.org
 for help. 
Please also check the log file at "/var/log/Xorg.0.log" for additional information.

 ddxSigGiveUp: Closing log


```

Sudo fixvesa does nothing - command not found
sudo xconfigurator // xf86config - command not found

A fix would be wonderful.

---

### Post by jtarin on 2011-05-30
Have you tried "Recovery Mode"?

---

### Post by Sexraider on 2011-05-30
How exactly do i access that?

---

### Post by jtarin on 2011-05-30
From the Grub menu at boot.

---

### Post by wildmanne39 on 2011-05-31
> **Sexraider said:**
> How exactly do i access that?Hi, here is a guide to get you into recovery mode. [https://wiki.ubuntu.com/RecoveryMode](https://wiki.ubuntu.com/RecoveryMode)

---

### Post by Zorael on 2011-05-31
```
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.38 root=UUID=37bc7d66-dd8c-4db6-94f9-6195003f6239 ro text splash [COLOR="Red"]**nomodeset**[/COLOR] vga=791
```
This here is your error. The Intel driver doesn't support userspace mode setting anymore, so you need to remove that boot argument and have it use kernel mode setting. Alternatively use vesa or fbdev.

If you have a custom **xorg.conf**, try renaming it to something else and instead let xorg autodetect your hardware setup.

---

### Post by Sexraider on 2011-06-01
well see, how exactly do i go to change that.
I'm new to configuring xserv.

No, i'm not using a custom config.

---

### Post by jtarin on 2011-06-01
> **Sexraider said:**
> well see, how exactly do i go to change that.
I'm new to configuring xserv.

No, i'm not using a custom config.[Here is the solution......edit your Grub2 boot sequence.]("https://help.ubuntu.com/community/Grub2#Editing%20Menus%20During%20Boot")

---

