---
title: "Upgrade to Jaunty, screen size shrunk!"
date: 2009-04-29
forum: New to Ubuntu
---

### Post by ReedMace on 2009-04-29
Have just upgraded to Jaunty from Intrepid. Screen resolution and display size was fine on my 15" laptop on Intrepid (1024x768') and filled the screen. Now I have an inch of blank screen either side of the display area on the same resolution setting.

I've done the lshw command and for the graphics it shows the following:
```

 *-pci
          description: Host bridge
          product: Mobile PM965/GM965/GL960 Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel module=intel_agp
        *-display:0 UNCLAIMED
             description: VGA compatible controller
             product: Mobile GM965/GL960 Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 03
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: latency=0
        *-display:1 UNCLAIMED
             description: Display controller
             product: Mobile GM965/GL960 Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 03
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: latency=0
```

It appears that my Intel graphics card is unsupported now? Is that correct? What can I do about this?

Thanks

ReedMace

---

### Post by scribaniwannabe on 2009-04-29
jaunty sucks.

---

### Post by alphacrucis2 on 2009-04-29
> **ReedMace said:**
> Have just upgraded to Jaunty from Intrepid. Screen resolution and display size was fine on my 15" laptop on Intrepid (1024x768') and filled the screen. Now I have an inch of blank screen either side of the display area on the same resolution setting.

I've done the lshw command and for the graphics it shows the following:
```

 *-pci
          description: Host bridge
          product: Mobile PM965/GM965/GL960 Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel module=intel_agp
        *-display:0 UNCLAIMED
             description: VGA compatible controller
             product: Mobile GM965/GL960 Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 03
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: latency=0
        *-display:1 UNCLAIMED
             description: Display controller
             product: Mobile GM965/GL960 Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 03
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: latency=0
```

It appears that my Intel graphics card is unsupported now? Is that correct? What can I do about this?

Thanks

ReedMace

Do you see a proprietary driver available under the menu System Administration Hardware Drivers. When I upgraded to Jaunty, the fglrx driver wasn't set up when it first booted up but I was able to install it afterwards.

---

### Post by ReedMace on 2009-04-29
> **alphacrucis2 said:**
> Do you see a proprietary driver available under the menu System Administration Hardware Drivers. When I upgraded to Jaunty, the fglrx driver wasn't set up when it first booted up but I was able to install it afterwards.

There were no proprietary drivers shown at all under Intrepid. There is one shown now, but that is for a software modem. Nothing else. Do I need the fglrx driver? If so how do I install it?

Thanks

ReedMace

---

### Post by kansasnoob on 2009-04-29
I don't use Intel but I recalled reading about them in the release notes:

[http://www.ubuntu.com/getubuntu/releasenotes/904#Performance%20regressions%20on%20Intel%20graphics%20cards](http://www.ubuntu.com/getubuntu/releasenotes/904#Performance%20regressions%20on%20Intel%20graphics%20cards)

> Performance regressions on Intel graphics cards

Users of Intel video chipsets have reported performance regressions in Ubuntu 8.10 compared with previous releases (252094). Many of the issues have been resolved in Ubuntu 9.04, but some remain.

    *

      Some users have found improved performance by using the "greedy" migration heuristic. This can be done by running "sudo gedit /etc/X11/xorg.conf", and adding Option "MigrationHeuristic" "greedy" to the Device section of your xorg.conf.
    *

      Alternatively, a new experimental acceleration architecture option, "DRI2/UXA", is available for Intel graphics users which our testing has found provides significant performance improvements in some cases, but has also shown risk of severe stability problems. You can opt-in to enable this by running "sudo gedit /etc/X11/xorg.conf", and adding Option "AccelMethod" "UXA" to the Device section of your xorg.conf. Users wishing to maximize stability should stay with the standard default acceleration method, "EXA".

      /!\ In some cases this will lead to the graphical environment not starting at all or becoming entirely unusable. In that case, start into rescue mode or press Ctrl+Alt+F2 and log into the text console, and use sudo nano /etc/X11/xorg.conf to revert the UXA option.
    *

      If none of the above helps, some users reported success with using an older driver version. 

Reverting the Jaunty Xorg intel driver to 2.4:

[https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4](https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4)

---

### Post by alphacrucis2 on 2009-04-29
> **ReedMace said:**
> There were no proprietary drivers shown at all under Intrepid. There is one shown now, but that is for a software modem. Nothing else. Do I need the fglrx driver? If so how do I install it?

Thanks

ReedMace

No. Fglrx is only for ATI cards (which is what my PC has), you would need an Intel equivalent.

---

### Post by kansasnoob on 2009-04-29
> **scribaniwannabe said:**
> jaunty sucks.

That's harsh!

I'll grant you though that I once felt that way about Hardy due to the roll-out of pulse audio. Now I'm still using Hardy for production although Jaunty is stable for me after a few tweaks.

But, by all means, if Hardy or Intrepid is better for you stick with it! Or try a different distro altogether!

---

### Post by prshah on 2009-04-29
> **ReedMace said:**
> 
It appears that my Intel graphics card is unsupported now? Is that correct? What can I do about this?


Intel is very much supported; I'm using the Intel 945, and though I had some [teething troubles]("http://ubuntuforums.org/showpost.php?p=7132514&postcount=2") I was able to set it right by manually specifying the settings in xorg.conf (details in linked post).

This is not really a good solution, since ubuntu is moving away from dependence on xorg.conf (and other such static files), but in the absence of any other suitable tools (like displayconfig-gtk in Hardy), this seems to be the only recourse when using hardware that does not follow specifications (such as VESA) properly.

With Jaunty onwards, a new acceleration method has debuted for Intel chipsets, called UXA/DRI2; maybe enabling that will help; post back for details if the above solution does not work.

If the linked solution does not work out for you, please post back the following output: Open a terminal (Applications-Accessories-Terminal) and give the commands```
cat /var/log/Xorg.0.log | grep -E -i driver\|accel

```

---

### Post by dsnettleton on 2009-04-29
I have basically the same problem, so I think I can speed things along by giving you my own output.
> 
dsnettleton@dsn-desktop:~$ cat /var/log/Xorg.0.log | grep -E -i driver\|accel
	X.Org Video Driver: 5.0
	X.Org XInput driver : 4.0
(II) Scanning /usr/share/xserver-xorg/pci directory for additional PCI ID's supported by the drivers
(==) Matched intel for the autoconfigured driver
(==) Assigned the driver to the xf86ConfigLayout
(II) Loading /usr/lib/xorg/modules/drivers//intel_drv.so
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 5.0
(II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
	ABI class: X.Org Video Driver, version 5.0
	ABI class: X.Org Video Driver, version 5.0
	ABI class: X.Org Video Driver, version 5.0
(==) intel(0): Using EXA for acceleration
(II) intel(0): VESA VBE OEM: Intel(r)865G Graphics Chip Accelerated VGA BIOS
(II) Loading /usr/lib/xorg/modules/drivers//sil164.so
	ABI class: X.Org Video Driver, version 5.0
(II) Loading /usr/lib/xorg/modules/drivers//ch7xxx.so
	ABI class: X.Org Video Driver, version 5.0
(II) Loading /usr/lib/xorg/modules/drivers//ivch.so
	ABI class: X.Org Video Driver, version 5.0
(II) Loading /usr/lib/xorg/modules/drivers//tfp410.so
	ABI class: X.Org Video Driver, version 5.0
(II) Loading /usr/lib/xorg/modules/drivers//ch7017.so
	ABI class: X.Org Video Driver, version 5.0
	ABI class: X.Org Video Driver, version 5.0
(II) intel(0): [drm] framebuffer mapped by ddx driver
(II) EXA(0): Driver registered support for the following operations:
(II)         Composite (RENDER acceleration)
(II) AIGLX: enabled GLX_texture_from_pixmap with driver support
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 4.0
(**) Macintosh mouse button emulation: (accel) keeping acceleration scheme 1
(**) Macintosh mouse button emulation: (accel) filter chain progression: 2.00
(**) Macintosh mouse button emulation: (accel) filter stage 0: 20.00 ms
(**) Macintosh mouse button emulation: (accel) set acceleration profile 0
(**) Logitech USB-PS/2 Optical Mouse: (accel) keeping acceleration scheme 1
(**) Logitech USB-PS/2 Optical Mouse: (accel) filter chain progression: 2.00
(**) Logitech USB-PS/2 Optical Mouse: (accel) filter stage 0: 20.00 ms
(**) Logitech USB-PS/2 Optical Mouse: (accel) set acceleration profile 0


I've tried all of the solutions offered (and a few others) and nothing seems to work reliably.

Thanks

---

### Post by ReedMace on 2009-04-29
> **kansasnoob said:**
> I don't use Intel but I recalled reading about them in the release notes:

[http://www.ubuntu.com/getubuntu/releasenotes/904#Performance%20regressions%20on%20Intel%20graphics%20cards](http://www.ubuntu.com/getubuntu/releasenotes/904#Performance%20regressions%20on%20Intel%20graphics%20cards)



Reverting the Jaunty Xorg intel driver to 2.4:

[https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4](https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4)

Just tried this and was a disaster. Ended up with no graphics at all. Had to boot up in Windows to get back onto internet to work out how to rollback. Rollback now done successfully.

> Intel is very much supported; I'm using the Intel 945, and though I had some teething troubles I was able to set it right by manually specifying the settings in xorg.conf (details in linked post).

Tried this amendment but also caused complete loss of graphics as I guess syntax has changed. Taking out the "x" from the display subsection (again using nano) allowed me to get back in. However I ended up with the screen divided into four sections and still with the blank screen around the display.

> If the linked solution does not work out for you, please post back the following output: Open a terminal (Applications-Accessories-Terminal) and give the commands

```
cat /var/log/Xorg.0.log | grep -E -i driver\|accel

```

Output as follows

```
	X.Org Video Driver: 5.0
	X.Org XInput driver : 4.0
(II) Scanning /usr/share/xserver-xorg/pci directory for additional PCI ID's supported by the drivers
(==) Matched intel for the autoconfigured driver
(==) Assigned the driver to the xf86ConfigLayout
(II) Loading /usr/lib/xorg/modules/drivers//intel_drv.so
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 5.0
(II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
	ABI class: X.Org Video Driver, version 5.0
(==) intel(0): Using EXA for acceleration
	ABI class: X.Org Video Driver, version 5.0
(II) [drm] loaded kernel module for "i915" driver.
(II) intel(0): [drm] framebuffer mapped by ddx driver
(II) EXA(0): Driver registered support for the following operations:
(II)         Composite (RENDER acceleration)
(II) AIGLX: enabled GLX_texture_from_pixmap with driver support
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 4.0
(**) Macintosh mouse button emulation: (accel) keeping acceleration scheme 1
(**) Macintosh mouse button emulation: (accel) filter chain progression: 2.00
(**) Macintosh mouse button emulation: (accel) filter stage 0: 20.00 ms
(**) Macintosh mouse button emulation: (accel) set acceleration profile 0
(**) Microsoft Microsoft? 2.4GHz Transceiver V2.0: (accel) keeping acceleration scheme 1
(**) Microsoft Microsoft? 2.4GHz Transceiver V2.0: (accel) filter chain progression: 2.00
(**) Microsoft Microsoft? 2.4GHz Transceiver V2.0: (accel) filter stage 0: 20.00 ms
(**) Microsoft Microsoft? 2.4GHz Transceiver V2.0: (accel) set acceleration profile 0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 4.0
(II) Synaptics touchpad driver version 0.99.3
(**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
(**) SynPS/2 Synaptics TouchPad: (accel) filter chain progression: 2.00
(**) SynPS/2 Synaptics TouchPad: (accel) filter stage 0: 20.00 ms
(**) SynPS/2 Synaptics TouchPad: (accel) set acceleration profile 0
```

Thanks for all help so far

ReedMace

---

### Post by ReedMace on 2009-04-29
> **prshah said:**
> 
If the linked solution does not work out for you, please post back the following output: Open a terminal (Applications-Accessories-Terminal) and give the commands```
cat /var/log/Xorg.0.log | grep -E -i driver\|accel

```

See message No 7 for my response

Thanks

ReedMace

---

### Post by ReedMace on 2009-04-30
I still have no solution for my screen size. Any other help?

ReedMace

---

### Post by Nicholi on 2009-04-30
I'm having the same problem and nothing has worked.
Any help out there?

---

### Post by prshah on 2009-04-30
> **ReedMace said:**
> I still have no solution for my screen size. Any other help?


> **Nicholi said:**
> I'm having the same problem and nothing has worked.
Any help out there?

Can you please post the output of the below command from the terminal (Applications-Accessories-Terminal) 
```
cat /var/log/Xorg.0.log | grep -E -i virtual\|"setting mode"
```?

---

### Post by Nicholi on 2009-04-30
ubuntu@ubuntu:~$ cat /var/log/Xorg.0.log | grep -E -i driver\|accel
	X.Org Video Driver: 5.0
	X.Org XInput driver : 4.0
(II) Scanning /usr/share/xserver-xorg/pci directory for additional PCI ID's supported by the drivers
(==) Matched intel for the autoconfigured driver
(==) Assigned the driver to the xf86ConfigLayout
(II) Loading /usr/lib/xorg/modules/drivers//intel_drv.so
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 5.0
(II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
	ABI class: X.Org Video Driver, version 5.0
(==) intel(0): Using EXA for acceleration
	ABI class: X.Org Video Driver, version 5.0
(II) EXA(0): Driver registered support for the following operations:
(II)         Composite (RENDER acceleration)
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 4.0
(**) Macintosh mouse button emulation: (accel) keeping acceleration scheme 1
(**) Macintosh mouse button emulation: (accel) filter chain progression: 2.00
(**) Macintosh mouse button emulation: (accel) filter stage 0: 20.00 ms
(**) Macintosh mouse button emulation: (accel) set acceleration profile 0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 4.0
(II) Synaptics touchpad driver version 0.99.3
(**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
(**) SynPS/2 Synaptics TouchPad: (accel) filter chain progression: 2.00
(**) SynPS/2 Synaptics TouchPad: (accel) filter stage 0: 20.00 ms
(**) SynPS/2 Synaptics TouchPad: (accel) set acceleration profile 0

---

### Post by ReedMace on 2009-05-01
X.Org X Server 1.6.0
Release Date: 2009-2-25
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-15-server x86_64 Ubuntu
Current Operating System: Linux hydrology-laptop 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:58:03 UTC 2009 x86_64
Build Date: 09 April 2009  02:11:54AM
xorg-server 2:1.6.0-0ubuntu14 (buildd@crested.buildd) 
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Wed Apr 29 18:42:00 2009
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
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
(II) Loader magic: 0xb40
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 5.0
	X.Org XInput driver : 4.0
	X.Org Server Extension : 2.0
(II) Loader running on linux
(++) using VT number 7

(--) PCI:*(0@0:2:0) Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller rev 3, Mem @ 0xfc000000/1048576, 0xd0000000/268435456, I/O @ 0x00001800/8
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
(II) Matched intel from file name intel.ids
(==) Matched intel for the autoconfigured driver
(==) Assigned the driver to the xf86ConfigLayout
(II) LoadModule: "intel"
(II) Loading /usr/lib/xorg/modules/drivers//intel_drv.so
(II) Module intel: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 2.6.3
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 5.0
(II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
	i810-dc100, i810e, i815, i830M, 845G, 852GM/855GM, 865G, 915G,
	E7221 (i915), 915GM, 945G, 945GM, 945GME, 965G, G35, 965Q, 946GZ,
	965GM, 965GME/GLE, G33, Q35, Q33,
	Mobile Intel® GM45 Express Chipset,
	Intel Integrated Graphics Device, G45/G43, Q45/Q43, G41
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
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 0.1.0
	ABI class: X.Org Video Driver, version 5.0
(**) intel(0): Depth 24, (--) framebuffer bpp 32
(==) intel(0): RGB weight 888
(==) intel(0): Default visual is TrueColor
(II) intel(0): Integrated Graphics Chipset: Intel(R) 965GM
(--) intel(0): Chipset: "965GM"
(--) intel(0): Linear framebuffer at 0xD0000000
(--) intel(0): IO registers at addr 0xFC000000
(WW) intel(0): libpciaccess reported 0 rom size, guessing 64kB
(==) intel(0): Using EXA for acceleration
(II) intel(0): 2 display pipes available.
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"
(II) Module "i2c" already built-in
(II) intel(0): Output VGA using monitor section Configured Monitor
(II) intel(0): Output LVDS has no monitor section
(II) intel(0): I2C bus "LVDSDDC_C" initialized.
(II) intel(0): Attempting to determine panel fixed mode.
(II) intel(0): I2C device "LVDSDDC_C:E-EDID segment register" registered at address 0x60.
(II) intel(0): I2C device "LVDSDDC_C:ddc2" registered at address 0xA0.
(II) intel(0): EDID vendor "AUO", prod id 6516
(II) intel(0): found backlight control method /sys/class/backlight/acpi_video0
(II) intel(0): I2C bus "SDVOCTRL_E for SDVOC" initialized.
(II) intel(0): I2C device "SDVOCTRL_E for SDVOC:SDVO Controller C" registered at address 0x72.
(II) intel(0): No SDVO device found on SDVOC
(II) intel(0): I2C device "SDVOCTRL_E for SDVOC:SDVO Controller C" removed.
(II) intel(0): I2C bus "SDVOCTRL_E for SDVOC" removed.
(II) intel(0): Output TV has no monitor section
(II) intel(0): Resizable framebuffer: not available (1 3)
(II) intel(0): EDID vendor "AUO", prod id 6516
(II) intel(0): Output VGA disconnected
(II) intel(0): Output LVDS connected
(II) intel(0): Output TV disconnected
(II) intel(0): Using exact sizes for initial modes
(II) intel(0): Output LVDS using initial mode 640x400
(II) intel(0): detected 512 kB GTT.
(II) intel(0): detected 7676 kB stolen memory.
(==) intel(0): video overlay key set to 0x101fe
(==) intel(0): Using gamma correction (1.0, 1.0, 1.0)
(==) intel(0): DPI set to (96, 96)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "exa"
(II) LoadModule: "exa"
(II) Loading /usr/lib/xorg/modules//libexa.so
(II) Module exa: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 2.4.0
	ABI class: X.Org Video Driver, version 5.0
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(II) intel(0): Comparing regs from server start up to After PreInit
(WW) intel(0): Register 0x61200 (PP_STATUS) changed from 0xc0000008 to 0xd000000a
(WW) intel(0): PP_STATUS before: on, ready, sequencing idle
(WW) intel(0): PP_STATUS after: on, ready, sequencing on
(WW) intel(0): Register 0x70024 (PIPEASTAT) changed from 0x00000203 to 0x00000207
(WW) intel(0): PIPEASTAT before: status: VSYNC_INT_STATUS VBLANK_INT_STATUS OREG_UPDATE_STATUS
(WW) intel(0): PIPEASTAT after: status: VSYNC_INT_STATUS SVBLANK_INT_STATUS VBLANK_INT_STATUS OREG_UPDATE_STATUS
(WW) intel(0): Register 0x71024 (PIPEBSTAT) changed from 0x00000206 to 0x80000206
(WW) intel(0): PIPEBSTAT before: status: VSYNC_INT_STATUS SVBLANK_INT_STATUS VBLANK_INT_STATUS
(WW) intel(0): PIPEBSTAT after: status: FIFO_UNDERRUN VSYNC_INT_STATUS SVBLANK_INT_STATUS VBLANK_INT_STATUS
(WW) intel(0): Register 0x68000 (TV_CTL) changed from 0x100000c0 to 0x000c00c0
(WW) intel(0): Register 0x68010 (TV_CSC_Y) changed from 0x00000000 to 0x0332012d
(WW) intel(0): Register 0x68014 (TV_CSC_Y2) changed from 0x00000000 to 0x07d30104
(WW) intel(0): Register 0x68018 (TV_CSC_U) changed from 0x00000000 to 0x0733052d
(WW) intel(0): Register 0x6801c (TV_CSC_U2) changed from 0x00000000 to 0x05c70200
(WW) intel(0): Register 0x68020 (TV_CSC_V) changed from 0x00000000 to 0x0340030c
(WW) intel(0): Register 0x68024 (TV_CSC_V2) changed from 0x00000000 to 0x06d00200
(WW) intel(0): Register 0x68028 (TV_CLR_KNOBS) changed from 0x00000000 to 0x00404000
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
(WW) intel(0): Register 0x68060 (TV_SC_CTL_1) changed from 0x00000000 to 0xc1710087
(WW) intel(0): Register 0x68064 (TV_SC_CTL_2) changed from 0x00000000 to 0x6b405140
(WW) intel(0): Register 0x68070 (TV_WIN_POS) changed from 0x00000000 to 0x00360024
(WW) intel(0): Register 0x68074 (TV_WIN_SIZE) changed from 0x00000000 to 0x02640198
(WW) intel(0): Register 0x68080 (TV_FILTER_CTL_1) changed from 0x00000000 to 0x8000085e
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
(II) intel(0): Kernel reported 746496 total, 1 used
(II) intel(0): I830CheckAvailableMemory: 2985980 kB available
(WW) intel(0): DRI2 requires UXA
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: node name is /dev/dri/card0
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
(**) intel(0): Framebuffer compression disabled
(**) intel(0): Tiling enabled
(==) intel(0): VideoRam: 262144 KB
(II) intel(0): Attempting memory allocation with tiled buffers.
(II) intel(0): Tiled allocation successful.
(II) intel(0): [drm] Registers = 0xfc000000
(II) intel(0): [dri] visual configs initialized
(II) intel(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(II) EXA(0): Offscreen pixmap area of 9437184 bytes
(II) EXA(0): Driver registered support for the following operations:
(II)         Solid
(II)         Copy
(II)         Composite (RENDER acceleration)
(==) intel(0): Backing store disabled
(==) intel(0): Silken mouse enabled
(II) intel(0): Initializing HW Cursor
(II) intel(0): [DRI] installation complete
(II) intel(0): xf86BindGARTMemory: bind key 0 at 0x0f700000 (pgoffset 63232)
(II) intel(0): Fixed memory allocation layout:
(II) intel(0): 0x00000000-0x00000fff: power context (4 kB)
(II) intel(0): 0x0077f000:            end of stolen memory
(II) intel(0): 0x0077f000-0x0f6fffff: DRI memory manager (245252 kB)
(II) intel(0): 0x0f700000-0x0fffffff: exa offscreen (9216 kB)
(II) intel(0): 0x10000000:            end of aperture
(II) intel(0): BO memory allocation layout:
(II) intel(0): 0x0077f000:            start of memory manager
(II) intel(0): 0x0079f000-0x00a9efff: depth buffer (3072 kB) Y tiled
(II) intel(0): 0x00b9f000-0x00e9efff: back buffer (3072 kB) X tiled
(II) intel(0): 0x00f9f000-0x0139efff: front buffer (4096 kB) X tiled
(II) intel(0): 0x0139f000-0x0139ffff: overlay registers (4 kB)
(II) intel(0): 0x013a0000-0x013a9fff: HW cursors (40 kB)
(II) intel(0): 0x0f700000:            end of memory manager
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
(II) intel(0): [drm] mapped front buffer at 0xd0f9f000, handle = 0xd0f9f000
(II) intel(0): [drm] mapped back buffer at 0xd0b9f000, handle = 0xd0b9f000
(II) intel(0): [drm] mapped depth buffer at 0xd079f000, handle = 0xd079f000
(II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
(II) intel(0): DPMS enabled
(==) intel(0): Intel XvMC decoder disabled
(II) intel(0): Set up textured video
(II) intel(0): Set up overlay video
(II) intel(0): direct rendering: XF86DRI Enabled
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
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 12, (OK)
drmOpenByBusid: Searching for BusID pci:0000:00:02.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 12, (OK)
drmOpenByBusid: drmOpenMinor returns 12
drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
(II) AIGLX: enabled GLX_SGI_make_current_read
(II) AIGLX: enabled GLX_MESA_copy_sub_buffer
(II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
(II) AIGLX: enabled GLX_texture_from_pixmap with driver support
(II) AIGLX: Loaded and initialized /usr/lib/dri/i965_dri.so
(II) GLX: Initialized DRI GL provider for screen 0
(II) intel(0): Setting screen physical size to 331 x 207
(II) config/hal: Adding input device AT Translated Set 2 keyboard
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 2.1.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 4.0
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event5"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) AT Translated Set 2 keyboard: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) AT Translated Set 2 keyboard: xkb_model: "pc105"
(**) Option "xkb_layout" "gb"
(**) AT Translated Set 2 keyboard: xkb_layout: "gb"
(II) config/hal: Adding input device Video Bus
(**) Video Bus: always reports core events
(**) Video Bus: Device: "/dev/input/event7"
(II) Video Bus: Found keys
(II) Video Bus: Configuring as keyboard
(II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Video Bus: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) Video Bus: xkb_model: "pc105"
(**) Option "xkb_layout" "gb"
(**) Video Bus: xkb_layout: "gb"
(II) config/hal: Adding input device Macintosh mouse button emulation
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event4"
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
(II) config/hal: Adding input device Microsoft Microsoft? 2.4GHz Transceiver V2.0
(**) Microsoft Microsoft? 2.4GHz Transceiver V2.0: always reports core events
(**) Microsoft Microsoft? 2.4GHz Transceiver V2.0: Device: "/dev/input/event6"
(II) Microsoft Microsoft? 2.4GHz Transceiver V2.0: Found 5 mouse buttons
(II) Microsoft Microsoft? 2.4GHz Transceiver V2.0: Found x and y relative axes
(II) Microsoft Microsoft? 2.4GHz Transceiver V2.0: Configuring as mouse
(**) Microsoft Microsoft? 2.4GHz Transceiver V2.0: YAxisMapping: buttons 4 and 5
(**) Microsoft Microsoft? 2.4GHz Transceiver V2.0: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Microsoft Microsoft? 2.4GHz Transceiver V2.0" (type: MOUSE)
(**) Microsoft Microsoft? 2.4GHz Transceiver V2.0: (accel) keeping acceleration scheme 1
(**) Microsoft Microsoft? 2.4GHz Transceiver V2.0: (accel) filter chain progression: 2.00
(**) Microsoft Microsoft? 2.4GHz Transceiver V2.0: (accel) filter stage 0: 20.00 ms
(**) Microsoft Microsoft? 2.4GHz Transceiver V2.0: (accel) set acceleration profile 0
(II) config/hal: Adding input device SynPS/2 Synaptics TouchPad
(II) LoadModule: "synaptics"
(II) Loading /usr/lib/xorg/modules/input//synaptics_drv.so
(II) Module synaptics: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 0.99.3
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 4.0
(II) Synaptics touchpad driver version 0.99.3
(**) Option "Device" "/dev/input/event9"
(II) SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5472
(II) SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4448
(II) SynPS/2 Synaptics TouchPad: pressure range 0 - 255
(II) SynPS/2 Synaptics TouchPad: finger width range 0 - 0
(II) SynPS/2 Synaptics TouchPad: buttons: left right middle double triple
(--) SynPS/2 Synaptics TouchPad touchpad found
(**) SynPS/2 Synaptics TouchPad: always reports core events
(II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD)
(**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
(**) SynPS/2 Synaptics TouchPad: (accel) filter chain progression: 2.00
(**) SynPS/2 Synaptics TouchPad: (accel) filter stage 0: 20.00 ms
(**) SynPS/2 Synaptics TouchPad: (accel) set acceleration profile 0
(--) SynPS/2 Synaptics TouchPad touchpad found
(II) intel(0): EDID vendor "AUO", prod id 6516
(II) intel(0): Using EDID range info for horizontal sync
(II) intel(0): Using EDID range info for vertical refresh
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1280x800"x0.0   68.90  1280 1301 1333 1408  800 804 808 816 -hsync -vsync (48.9 kHz)
(II) intel(0): EDID vendor "AUO", prod id 6516
(II) intel(0): EDID vendor "AUO", prod id 6516
(II) intel(0): Using hsync ranges from config file
(II) intel(0): Using vrefresh ranges from config file
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1280x800"x0.0   68.90  1280 1301 1333 1408  800 804 808 816 -hsync -vsync (48.9 kHz)
(II) intel(0): EDID vendor "AUO", prod id 6516
(II) intel(0): EDID vendor "AUO", prod id 6516
(II) intel(0): Using hsync ranges from config file
(II) intel(0): Using vrefresh ranges from config file
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1280x800"x0.0   68.90  1280 1301 1333 1408  800 804 808 816 -hsync -vsync (48.9 kHz)
(II) intel(0): EDID vendor "AUO", prod id 6516
(II) intel(0): using SSC reference clock of 96 MHz
(II) intel(0): Selecting standard 18 bit TMDS pixel format.
(II) intel(0): EDID vendor "AUO", prod id 6516
(II) intel(0): Using hsync ranges from config file
(II) intel(0): Using vrefresh ranges from config file
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1280x800"x0.0   68.90  1280 1301 1333 1408  800 804 808 816 -hsync -vsync (48.9 kHz)
(II) intel(0): EDID vendor "AUO", prod id 6516
(II) intel(0): EDID vendor "AUO", prod id 6516
(II) intel(0): Using hsync ranges from config file
(II) intel(0): Using vrefresh ranges from config file
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1280x800"x0.0   68.90  1280 1301 1333 1408  800 804 808 816 -hsync -vsync (48.9 kHz)
(II) intel(0): EDID vendor "AUO", prod id 6516
(II) intel(0): EDID vendor "AUO", prod id 6516
(II) intel(0): Using hsync ranges from config file
(II) intel(0): Using vrefresh ranges from config file
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1280x800"x0.0   68.90  1280 1301 1333 1408  800 804 808 816 -hsync -vsync (48.9 kHz)
(II) intel(0): EDID vendor "AUO", prod id 6516
(II) intel(0): using SSC reference clock of 96 MHz
(II) intel(0): Selecting standard 18 bit TMDS pixel format.
(II) intel(0): EDID vendor "AUO", prod id 6516
(II) intel(0): Using hsync ranges from config file
(II) intel(0): Using vrefresh ranges from config file
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1280x800"x0.0   68.90  1280 1301 1333 1408  800 804 808 816 -hsync -vsync (48.9 kHz)
(II) intel(0): EDID vendor "AUO", prod id 6516
(II) intel(0): EDID vendor "AUO", prod id 6516
(II) intel(0): Using hsync ranges from config file
(II) intel(0): Using vrefresh ranges from config file
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1280x800"x0.0   68.90  1280 1301 1333 1408  800 804 808 816 -hsync -vsync (48.9 kHz)
(II) intel(0): EDID vendor "AUO", prod id 6516
(II) AIGLX: Suspending AIGLX clients for VT switch
(II) intel(0): xf86UnbindGARTMemory: unbind key 0
(II) Open ACPI successful (/var/run/acpid.socket)
(II) AIGLX: Resuming AIGLX clients after VT switch
(II) intel(0): xf86BindGARTMemory: bind key 0 at 0x0f700000 (pgoffset 63232)
(II) intel(0): Fixed memory allocation layout:
(II) intel(0): 0x00000000-0x00000fff: power context (4 kB)
(II) intel(0): 0x0077f000:            end of stolen memory
(II) intel(0): 0x0077f000-0x0f6fffff: DRI memory manager (245252 kB)
(II) intel(0): 0x0f700000-0x0fffffff: exa offscreen (9216 kB)
(II) intel(0): 0x10000000:            end of aperture
(II) intel(0): BO memory allocation layout:
(II) intel(0): 0x0077f000:            start of memory manager
(II) intel(0): 0x0079f000-0x00a9efff: depth buffer (3072 kB) Y tiled
(II) intel(0): 0x00b9f000-0x00e9efff: back buffer (3072 kB) X tiled
(II) intel(0): 0x00f9f000-0x0139efff: front buffer (4096 kB) X tiled
(II) intel(0): 0x0139f000-0x0139ffff: overlay registers (4 kB)
(II) intel(0): 0x013a0000-0x013a9fff: HW cursors (40 kB)
(II) intel(0): 0x0f700000:            end of memory manager
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
(--) SynPS/2 Synaptics TouchPad touchpad found
(II) AT Translated Set 2 keyboard: Device reopened after 1 attempts.
(II) Video Bus: Device reopened after 1 attempts.
(II) Macintosh mouse button emulation: Device reopened after 1 attempts.
(II) Microsoft Microsoft? 2.4GHz Transceiver V2.0: Device reopened after 1 attempts.
(II) PM Event received: Capability Changed
I830PMEvent: Capability change
(II) intel(0): EDID vendor "AUO", prod id 6516
(II) intel(0): Using hsync ranges from config file
(II) intel(0): Using vrefresh ranges from config file
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1280x800"x0.0   68.90  1280 1301 1333 1408  800 804 808 816 -hsync -vsync (48.9 kHz)
(II) intel(0): EDID vendor "AUO", prod id 6516
(II) AIGLX: Suspending AIGLX clients for VT switch
(II) intel(0): xf86UnbindGARTMemory: unbind key 0
(II) Open ACPI successful (/var/run/acpid.socket)
(II) AIGLX: Resuming AIGLX clients after VT switch
(II) intel(0): xf86BindGARTMemory: bind key 0 at 0x0f700000 (pgoffset 63232)
(II) intel(0): Fixed memory allocation layout:
(II) intel(0): 0x00000000-0x00000fff: power context (4 kB)
(II) intel(0): 0x0077f000:            end of stolen memory
(II) intel(0): 0x0077f000-0x0f6fffff: DRI memory manager (245252 kB)
(II) intel(0): 0x0f700000-0x0fffffff: exa offscreen (9216 kB)
(II) intel(0): 0x10000000:            end of aperture
(II) intel(0): BO memory allocation layout:
(II) intel(0): 0x0077f000:            start of memory manager
(II) intel(0): 0x0079f000-0x00a9efff: depth buffer (3072 kB) Y tiled
(II) intel(0): 0x00b9f000-0x00e9efff: back buffer (3072 kB) X tiled
(II) intel(0): 0x00f9f000-0x0139efff: front buffer (4096 kB) X tiled
(II) intel(0): 0x0139f000-0x0139ffff: overlay registers (4 kB)
(II) intel(0): 0x013a0000-0x013a9fff: HW cursors (40 kB)
(II) intel(0): 0x0f700000:            end of memory manager
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
(--) SynPS/2 Synaptics TouchPad touchpad found
(II) AT Translated Set 2 keyboard: Device reopened after 1 attempts.
(II) Video Bus: Device reopened after 1 attempts.
(II) Macintosh mouse button emulation: Device reopened after 1 attempts.
(II) Microsoft Microsoft? 2.4GHz Transceiver V2.0: Device reopened after 1 attempts.


Any ideas?

ReedMace

---

### Post by ssdt on 2009-05-01
I wouldn't say that if I were you. At first all versions are like that.

---

### Post by dsnettleton on 2009-05-02
I just gave up and reverted to intrepid.

---

### Post by ReedMace on 2009-05-03
There must be a solution to this somewhere?? Anyone?

---

### Post by ReedMace on 2009-05-05
It appears that no-one can offer any further help on this so I have submitted a [**[COLOR="Blue"]_bug report_[/COLOR]**]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/371863"). If anyone else has similar problems perhaps you could add your name to it.

ReedMace

---

### Post by ReedMace on 2009-05-06
For anyone who is interested the following code (supplied by the bug-fix team) solved my immediate issue:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

ReedMace

---

### Post by ischnura on 2009-05-11
> **ReedMace said:**
> For anyone who is interested the following code (supplied by the bug-fix team) solved my immediate issue:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

ReedMace

Thanks ReedMace!

Your solution worked perfectly!

---

### Post by ReedMace on 2009-05-11
> **ischnura said:**
> Thanks ReedMace!

Your solution worked perfectly!

Glad it helped!

ReedMace

---

