---
title: "Monitor Resolution issues"
date: 2010-08-10
forum: New to Ubuntu
---

### Post by chris88knox on 2010-08-10
Hey there! I am a BEEEGINNNER with both linux and ubuntu...I am finding out that this uses alot of code...that is cool, but I know none of it at all...

Here is my issue.  Hopefully someone can assist.

-------------------------------

My machine is:

OS: Ubuntu 10.04  *I Love it!!*

Intel D945GCL mobo

Intel E1400 2.0 Dual Core 

512 DDR2

Monitor:  Gateway FPD1765  

------------------------------

I am trying to get this monitor to run in 1280x1024, but the highest resolution available is 1024 x 768, because ubuntu does not recognize my monitor... I have read how people do this and make it work for their system, but I am still stumped the terminology and processes are above me.  Again if anyone has the magic answer, I would love for you to share it....thank you!

---

### Post by Ozymandias_117 on 2010-08-10
> **chris88knox said:**
> Hey there! I am a BEEEGINNNER with both linux and ubuntu...I am finding out that this uses alot of code...that is cool, but I know none of it at all...

Here is my issue.  Hopefully someone can assist.

-------------------------------

My machine is:

OS: Ubuntu 10.04  *I Love it!!*

Intel D945GCL mobo

Intel E1400 2.0 Dual Core 

512 DDR2

Monitor:  Gateway FPD1765  

------------------------------

I am trying to get this monitor to run in 1280x1024, but the highest resolution available is 1024 x 768, because ubuntu does not recognize my monitor... I have read how people do this and make it work for their system, but I am still stumped the terminology and processes are above me.  Again if anyone has the magic answer, I would love for you to share it....thank you!

What is your graphics card?

If you're not sure, type this into a terminal:```
lspci | grep VGA
```

---

### Post by chris88knox on 2010-08-10
Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)


Thanks  It should be able to support it, right?

Actually, I know it can support it, because i plugged in a 22" widescreen HP hidef lcd into it and it looked SHARP!!! perfect image... and I know the potential of this monitor, because I have put it on a standard "xp pro" (sorry for the PROfanity)  and it looks crisp.

---

### Post by Ozymandias_117 on 2010-08-10
> **chris88knox said:**
> Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)


Thanks  It should be able to support it, right?

Actually, I know it can support it, because i plugged in a 22" widescreen HP hidef lcd into it and it looked SHARP!!! perfect image... and I know the potential of this monitor, because I have put it on a standard "xp pro" (sorry for the PROfanity)  and it looks crisp.

Yeah, it should. I was just checking, if it was ATI or nVidia I was going to say go download their drivers and install them. But the Kernel Intel drivers are usually really good. Hopefully someone else will be able to resolve this for you!

---

### Post by chris88knox on 2010-08-10
Well thanks for your time!... what kind of graphics card should I get to get improved performance (maybe watching dvds) and it be close to a plugnplay atmosphere.

---

### Post by Ozymandias_117 on 2010-08-10
> **chris88knox said:**
> Well thanks for your time!... what kind of graphics card should I get to get improved performance (maybe watching dvds) and it be close to a plugnplay atmosphere.

Well, usually on-board Intel works fine :D. But for a card, nVidia is the most friendly towards Linux.

---

### Post by JKyleOKC on 2010-08-10
This may help; it's how I solved a similar problem this afternoon after installing Lucid Lynx on a very old box...

1. Restart, pressing the Shift key immediately to get the Grub menu to show.

2. From the menu, select the second item, the one marked (recovery).

3. From the menu that it eventually displays, select "Drop to root prompt." These three steps are to get you to a prompt that does not have the X server (which provides the graphic interface) running.

4. If it asks for login, enter your user name and then your password. You won't see anything echo on the screen when you enter your password but it's going in nevertheless.

5. At the prompt, type "sudo Xorg -config" being certain to have the upper-case X, and hit return. Enter your password when asked. This runs a program that will create a new configuration file for you, but the program refuses to run if the X server is running. That's why all the reboot and change from normal login is needed.

6. You'll get quite a bit of text displayed; the result will be a new file named "xorg.conf.new" in your home directory. This file should have the correct parameters in it for your video card and monitor.

7. Still at the command line, type "ls -l /etc/X11" and search the result for a file named "xorg.conf" (but chances are you will not find one). If you do find one, type "sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.old" to make a backup copy just in case things go wrong.

8. Now type "sudo cp $HOME/xorg.conf.new /etc/X11/xorg.conf" to put the new file in place.

9. Finally, type "sudo reboot now" to restart everything. You should come up normally, and the "display" setting dialog should now offer you more choices for resolution. If it doesn't, post a copy of your /var/log/xorg.0.log file here so we can see what is going wrong.

It might be a good idea to print this message out for reference while you are going through the steps. Hope it helps!

---

### Post by chris88knox on 2010-08-10
It does not ask for a password, it merely says root@chris-desktop

---

### Post by chris88knox on 2010-08-10
I got to the login part.... now it says -config not specified

---

### Post by Ozymandias_117 on 2010-08-10
Try -configure

And when in single user mode (recovery mode) you're Root. You don't need sudo.

---

### Post by chris88knox on 2010-08-10
"cannot move old log file ("/var/log/Xorg.0.log" to "..../Xorg.0.log.old")"

---

### Post by chris88knox on 2010-08-10
How do I find the " /var/log/xorg.0.log file"

---

### Post by chris88knox on 2010-08-10
Here is the copy of the file



X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-27-server i686 Ubuntu
Current Operating System: Linux chris-desktop 2.6.32-24-generic #39-Ubuntu SMP Wed Jul 28 06:07:29 UTC 2010 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-24-generic root=UUID=235b0d9e-10f1-4770-91fa-3c468cbcf1d9 ro quiet splash
Build Date: 16 June 2010  09:31:32AM
xorg-server 2:1.7.6-2ubuntu7.2 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
Current version of pixman: 0.16.4
    Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Tue Aug 10 23:43:46 2010
(==) Using config file: "/etc/X11/xorg.conf"
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"
(==) ServerLayout "X.org Configured"
(**) |-->Screen "Screen0" (0)
(**) |   |-->Monitor "Monitor0"
(**) |   |-->Device "Card0"
(**) |-->Input Device "Mouse0"
(**) |-->Input Device "Keyboard0"
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
    Entry deleted from font path.
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
    Entry deleted from font path.
(**) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/75dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    /usr/share/fonts/X11/75dpi,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins,
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/75dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    /usr/share/fonts/X11/75dpi,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
(**) ModulePath set to "/usr/lib/xorg/modules"
(WW) AllowEmptyInput is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
(WW) Disabling Mouse0
(WW) Disabling Keyboard0
(II) Loader magic: 0x81f0e80
(II) Module ABI versions:
    X.Org ANSI C Emulation: 0.4
    X.Org Video Driver: 6.0
    X.Org XInput driver : 7.0
    X.Org Server Extension : 2.0
(++) using VT number 7

(--) PCI:*(0:0:2:0) 8086:2772:107b:6051 Intel Corporation 82945G/GZ Integrated Graphics Controller rev 2, Mem @ 0x30100000/524288, 0x20000000/268435456, 0x30180000/262144, I/O @ 0x000020e0/8
(WW) Open ACPI failed (/var/run/acpid.socket) (No such file or directory)
(II) "extmod" will be loaded. This was enabled by default and also specified in the config file.
(II) "dbe" will be loaded. This was enabled by default and also specified in the config file.
(II) "glx" will be loaded. This was enabled by default and also specified in the config file.
(II) "record" will be loaded. This was enabled by default and also specified in the config file.
(II) "dri" will be loaded. This was enabled by default and also specified in the config file.
(II) "dri2" will be loaded. This was enabled by default and also specified in the config file.
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
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions/librecord.so
(II) Module record: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.13.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "intel"
(II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
(II) Module intel: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 2.9.1
    Module class: X.Org Video Driver
    ABI class: X.Org Video Driver, version 6.0
(II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
    i810-dc100, i810e, i815, i830M, 845G, 852GM/855GM, 865G, 915G,
    E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
    965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
    4 Series, G45/G43, Q45/Q43, G41, B43, Clarkdale, Arrandale
(II) Primary Device is: PCI 00@00:02:0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: Searching for BusID pci:0000:00:02.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: drmOpenMinor returns 8
drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
(==) intel(0): Depth 24, (--) framebuffer bpp 32
(==) intel(0): RGB weight 888
(==) intel(0): Default visual is TrueColor
(II) intel(0): Integrated Graphics Chipset: Intel(R) 945G
(--) intel(0): Chipset: "945G"
(II) intel(0): Output VGA1 using monitor section Monitor0
(II) intel(0): EDID for output VGA1
(II) intel(0): Not using default mode "640x350" (vrefresh out of range)
(II) intel(0): Not using default mode "320x175" (doublescan mode not supported)
(II) intel(0): Not using default mode "640x400" (vrefresh out of range)
(II) intel(0): Not using default mode "320x200" (doublescan mode not supported)
(II) intel(0): Not using default mode "720x400" (vrefresh out of range)
(II) intel(0): Not using default mode "360x200" (doublescan mode not supported)
(II) intel(0): Not using default mode "320x240" (doublescan mode not supported)
(II) intel(0): Not using default mode "640x480" (vrefresh out of range)
(II) intel(0): Not using default mode "320x240" (doublescan mode not supported)
(II) intel(0): Not using default mode "640x480" (vrefresh out of range)
(II) intel(0): Not using default mode "320x240" (doublescan mode not supported)
(II) intel(0): Not using default mode "640x480" (vrefresh out of range)
(II) intel(0): Not using default mode "320x240" (doublescan mode not supported)
(II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
(II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
(II) intel(0): Not using default mode "800x600" (vrefresh out of range)
(II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
(II) intel(0): Not using default mode "800x600" (vrefresh out of range)
(II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
(II) intel(0): Not using default mode "800x600" (vrefresh out of range)
(II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
(II) intel(0): Not using default mode "1024x768" (interlace mode not supported)
(II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
(II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
(II) intel(0): Not using default mode "1024x768" (vrefresh out of range)
(II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
(II) intel(0): Not using default mode "1024x768" (vrefresh out of range)
(II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
(II) intel(0): Not using default mode "1024x768" (vrefresh out of range)
(II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
(II) intel(0): Not using default mode "1152x864" (vrefresh out of range)
(II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
(II) intel(0): Not using default mode "1280x960" (hsync out of range)
(II) intel(0): Not using default mode "640x480" (doublescan mode not supported)
(II) intel(0): Not using default mode "1280x960" (vrefresh out of range)
(II) intel(0): Not using default mode "640x480" (doublescan mode not supported)
(II) intel(0): Not using default mode "1280x1024" (hsync out of range)
(II) intel(0): Not using default mode "640x512" (doublescan mode not supported)
(II) intel(0): Not using default mode "1280x1024" (vrefresh out of range)
(II) intel(0): Not using default mode "640x512" (doublescan mode not supported)
(II) intel(0): Not using default mode "1280x1024" (vrefresh out of range)
(II) intel(0): Not using default mode "640x512" (doublescan mode not supported)
(II) intel(0): Not using default mode "1600x1200" (hsync out of range)
(II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
(II) intel(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
(II) intel(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
(II) intel(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
(II) intel(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
(II) intel(0): Not using default mode "1792x1344" (hsync out of range)
(II) intel(0): Not using default mode "896x672" (doublescan mode not supported)
(II) intel(0): Not using default mode "1792x1344" (vrefresh out of range)
(II) intel(0): Not using default mode "896x672" (doublescan mode not supported)
(II) intel(0): Not using default mode "1856x1392" (hsync out of range)
(II) intel(0): Not using default mode "928x696" (doublescan mode not supported)
(II) intel(0): Not using default mode "1856x1392" (vrefresh out of range)
(II) intel(0): Not using default mode "928x696" (doublescan mode not supported)
(II) intel(0): Not using default mode "1920x1440" (hsync out of range)
(II) intel(0): Not using default mode "960x720" (doublescan mode not supported)
(II) intel(0): Not using default mode "1920x1440" (vrefresh out of range)
(II) intel(0): Not using default mode "960x720" (doublescan mode not supported)
(II) intel(0): Not using default mode "832x624" (vrefresh out of range)
(II) intel(0): Not using default mode "416x312" (doublescan mode not supported)
(II) intel(0): Not using default mode "1152x864" (hsync out of range)
(II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
(II) intel(0): Not using default mode "1152x864" (vrefresh out of range)
(II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
(II) intel(0): Not using default mode "1152x864" (vrefresh out of range)
(II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
(II) intel(0): Not using default mode "1152x864" (vrefresh out of range)
(II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
(II) intel(0): Not using default mode "1152x864" (vrefresh out of range)
(II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
(II) intel(0): Not using default mode "1152x864" (vrefresh out of range)
(II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
(II) intel(0): Not using default mode "1360x768" (monitor doesn't support reduced blanking)
(II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
(II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
(II) intel(0): Not using default mode "1400x1050" (hsync out of range)
(II) intel(0): Not using default mode "700x525" (doublescan mode not supported)
(II) intel(0): Not using default mode "1400x1050" (vrefresh out of range)
(II) intel(0): Not using default mode "700x525" (doublescan mode not supported)
(II) intel(0): Not using default mode "1400x1050" (vrefresh out of range)
(II) intel(0): Not using default mode "700x525" (doublescan mode not supported)
(II) intel(0): Not using default mode "1400x1050" (vrefresh out of range)
(II) intel(0): Not using default mode "700x525" (doublescan mode not supported)
(II) intel(0): Not using default mode "1440x900" (hsync out of range)
(II) intel(0): Not using default mode "720x450" (doublescan mode not supported)
(II) intel(0): Not using default mode "1600x1024" (hsync out of range)
(II) intel(0): Not using default mode "800x512" (doublescan mode not supported)
(II) intel(0): Not using default mode "1680x1050" (hsync out of range)
(II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
(II) intel(0): Not using default mode "1680x1050" (hsync out of range)
(II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
(II) intel(0): Not using default mode "1680x1050" (vrefresh out of range)
(II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
(II) intel(0): Not using default mode "1680x1050" (vrefresh out of range)
(II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
(II) intel(0): Not using default mode "1680x1050" (vrefresh out of range)
(II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
(II) intel(0): Not using default mode "1920x1080" (hsync out of range)
(II) intel(0): Not using default mode "960x540" (doublescan mode not supported)
(II) intel(0): Not using default mode "1920x1200" (hsync out of range)
(II) intel(0): Not using default mode "960x600" (doublescan mode not supported)
(II) intel(0): Not using default mode "1920x1440" (vrefresh out of range)
(II) intel(0): Not using default mode "960x720" (doublescan mode not supported)
(II) intel(0): Not using default mode "2048x1536" (hsync out of range)
(II) intel(0): Not using default mode "1024x768" (doublescan mode not supported)
(II) intel(0): Not using default mode "2048x1536" (vrefresh out of range)
(II) intel(0): Not using default mode "1024x768" (doublescan mode not supported)
(II) intel(0): Not using default mode "2048x1536" (vrefresh out of range)
(II) intel(0): Not using default mode "1024x768" (doublescan mode not supported)
(II) intel(0): Printing probed modes for output VGA1
(II) intel(0): Modeline "1360x768"x59.8   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync (47.7 kHz)
(II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "848x480"x60.0   33.75  848 864 976 1088  480 486 494 517 +hsync +vsync (31.0 kHz)
(II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 489 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Output VGA1 connected
(II) intel(0): Using fuzzy aspect match for initial modes
(II) intel(0): Output VGA1 using initial mode 1024x768
(II) intel(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
(==) intel(0): video overlay key set to 0x101fe
(==) intel(0): DPI set to (96, 96)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.4
(==) Depth 24 pixmap format is 32 bpp
(II) intel(0): [DRI2] Setup complete
(**) intel(0): Framebuffer compression disabled
(**) intel(0): Tiling enabled
(**) intel(0): SwapBuffers wait enabled
(==) intel(0): VideoRam: 262144 KB
(II) intel(0): Attempting memory allocation with tiled buffers.
(II) intel(0): Tiled allocation successful.
(II) UXA(0): Driver registered support for the following operations:
(II)         solid
(II)         copy
(II)         composite (RENDER acceleration)
(==) intel(0): Backing store disabled
(==) intel(0): Silken mouse enabled
(II) intel(0): Initializing HW Cursor
(II) intel(0): No memory allocations
(II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
(==) intel(0): DPMS enabled
(==) intel(0): Intel XvMC decoder disabled
(II) intel(0): Set up textured video
(II) intel(0): Set up overlay video
(II) intel(0): direct rendering: DRI2 Enabled
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
(II) AIGLX: enabled GLX_MESA_copy_sub_buffer
(II) AIGLX: enabled GLX_SGI_make_current_read
(II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
(II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
(II) AIGLX: Loaded and initialized /usr/lib/dri/i915_dri.so
(II) GLX: Initialized DRI2 GL provider for screen 0
(II) intel(0): Setting screen physical size to 270 x 203
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
(II) config/udev: Adding input device Sleep Button (/dev/input/event0)
(**) Sleep Button: Applying InputClass "evdev keyboard catchall"
(**) Sleep Button: always reports core events
(**) Sleep Button: Device: "/dev/input/event0"
(II) Sleep Button: Found keys
(II) Sleep Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/udev: Adding input device HDA Intel Line In at Ext Rear Jack (/dev/input/event5)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device HDA Intel Mic at Ext Front Jack (/dev/input/event6)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device HDA Intel Mic at Ext Rear Jack (/dev/input/event7)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device HDA Intel Speaker at Ext Rear Jack (/dev/input/event8)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device HDA Intel HP Out at Ext Front Jack (/dev/input/event9)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device Logitech USB-PS/2 Optical Mouse (/dev/input/event4)
(**) Logitech USB-PS/2 Optical Mouse: Applying InputClass "evdev pointer catchall"
(**) Logitech USB-PS/2 Optical Mouse: always reports core events
(**) Logitech USB-PS/2 Optical Mouse: Device: "/dev/input/event4"
(II) Logitech USB-PS/2 Optical Mouse: Found 3 mouse buttons
(II) Logitech USB-PS/2 Optical Mouse: Found scroll wheel(s)
(II) Logitech USB-PS/2 Optical Mouse: Found relative axes
(II) Logitech USB-PS/2 Optical Mouse: Found x and y relative axes
(II) Logitech USB-PS/2 Optical Mouse: Configuring as mouse
(**) Logitech USB-PS/2 Optical Mouse: YAxisMapping: buttons 4 and 5
(**) Logitech USB-PS/2 Optical Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Logitech USB-PS/2 Optical Mouse" (type: MOUSE)
(II) Logitech USB-PS/2 Optical Mouse: initialized for relative axes.
(II) config/udev: Adding input device Logitech USB-PS/2 Optical Mouse (/dev/input/mouse1)
(II) No input driver/identifier specified (ignoring)
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

---

### Post by JKyleOKC on 2010-08-11
That looks as if the 1360x768 resolution is the highest that your system is willing to load at this point. Posting your /etc/X11/xorg.conf would be the next step.

To get up to 1024x768 on that very old system I mentioned earlier, I did have to edit my xorg.conf to use only 15-bit pixels rather than the default 24-bit versions. The log file told me that the ancient ATI card's RAM of just 2 MB wasn't enough to handle anything above 832x648 at 24 bits, but trimming the pixel size let me get 1024x768 with only minor decrease in image quality.

Your log, however, doesn't indicate any memory limit. Instead it's saying that the refresh rates are out of range; it just might be that the Gateway panel isn't totally compatible with your video card driver, or possibly that the configuration routines misidentified something.

The xorg.conf file will show us what the system thinks it's using, and may suggest some workarounds.

EDIT: I forgot to mention that those "WW" warning lines are not critical errors; they're simply for your information. Critical errors get flagged with "EE" and you don't have any of these.

---

### Post by chris88knox on 2010-08-11
Section "ServerLayout"
    Identifier     "X.org Configured"
    Screen      0  "Screen0" 0 0
    InputDevice    "Mouse0" "CorePointer"
    InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
    ModulePath   "/usr/lib/xorg/modules"
    FontPath     "/usr/share/fonts/X11/misc"
    FontPath     "/usr/share/fonts/X11/cyrillic"
    FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath     "/usr/share/fonts/X11/Type1"
    FontPath     "/usr/share/fonts/X11/100dpi"
    FontPath     "/usr/share/fonts/X11/75dpi"
    FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
    FontPath     "built-ins"
EndSection

Section "Module"
    Load  "extmod"
    Load  "dbe"
    Load  "glx"
    Load  "dri"
    Load  "dri2"
    Load  "record"
EndSection

Section "InputDevice"
    Identifier  "Keyboard0"
    Driver      "kbd"
EndSection

Section "InputDevice"
    Identifier  "Mouse0"
    Driver      "mouse"
    Option        "Protocol" "auto"
    Option        "Device" "/dev/input/mice"
    Option        "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
    Identifier   "Monitor0"
    VendorName   "Monitor Vendor"
    ModelName    "Monitor Model"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
        ### [arg]: arg optional
        #Option     "NoAccel"                # [<bool>]
        #Option     "SWcursor"               # [<bool>]
        #Option     "ColorKey"               # <i>
        #Option     "CacheLines"             # <i>
        #Option     "Dac6Bit"                # [<bool>]
        #Option     "DRI"                    # [<bool>]
        #Option     "NoDDC"                  # [<bool>]
        #Option     "ShowCache"              # [<bool>]
        #Option     "XvMCSurfaces"           # <i>
        #Option     "PageFlip"               # [<bool>]
    Identifier  "Card0"
    Driver      "intel"
    VendorName  "Intel Corporation"
    BoardName   "82945G/GZ Integrated Graphics Controller"
    BusID       "PCI:0:2:0"
EndSection

Section "Screen"
    Identifier "Screen0"
    Device     "Card0"
    Monitor    "Monitor0"
    SubSection "Display"
        Viewport   0 0
        Depth     1
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     4
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     8
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     15
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     16
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection

---

### Post by JKyleOKC on 2010-08-11
Okay, this part of your log indicates that it did not detect your Gateway panel at all and is simply working with its assumed default specs -- which are set to be the lowest common denominator!```
Section "Monitor"
    Identifier   "Monitor0"
    VendorName   "Monitor Vendor"
    ModelName    "Monitor Model"
EndSection
```

There are ways to get the needed information so you can manually add it to this section of the xorg.conf file, but I don't remember them well enough to give you the details right now. While I look them up, maybe some of the other forum members will chime in...

Here's the front end of that section in my own file, to show you what needs to be there -- but don't copy it verbatim because having the wrong values in this could possibly cause permanent damage to your monitor!```
Section "Monitor"
	Identifier	"Configured Monitor"
	Vendorname	"Acer"
	Modelname	"Acer X173Wv"
	Horizsync	30.0	-	83.0
	Vertrefresh	55.0	-	75.0
	Gamma	1
```Your "Identifier" line should not be changed, but the Vendorname should be "Gateway" and the Modelname should be whatever it shows as when queried (which is what I'll have to look up how to do). The next two lines have to come from the query response, while the final line about Gamma is okay to set to 1.

I'll be back but it may take a while to find what I need to tell you...

---

### Post by JKyleOKC on 2010-08-11
You can find the horizontal and vertical values for your monitor on page 17 of your user guide for it, and if you've lost the manual, you can download a copy from [http://support.gateway.com/s/MONITOR/7005427/7005427ul.shtml](http://support.gateway.com/s/MONITOR/7005427/7005427ul.shtml) and print it.

To use these values in xorg.conf, find the lowest and highest values for each, and use them in the corresponding lines, following the example I posted earlier from my system. You can change the model value to "Gateway FPD1765" since so far as I know, the X drivers don't actually use this information anyway.

To make these changes you'll have to access /etc/X11/xorg.conf with root privileges. The safest way to do this is to open a terminal window, then type "cd /etc/X11" which should give you a prompt indicating that you're there. Then type "gksudo gedit" which will ask for your password, then open gedit with a red bar and ominous warning that you're on dangerous ground. Use file->open to open xorg.conf, and immediately save it as xorg.conf.works to have a backup if need be, then open it again so that you're working on the main file.

Scroll down to the Monitor section and make the changes. The first word on each line should be exactly as shown in my example since the system does an exact-match lookup for its key words. The values for the two sync ranges should be those you found from the user manual, with space-dash-space separating the low and high for each.

Then save the file and quit the editor. Before leaving the terminal, type "less xorg.conf" to verify that your changes took hold properly. If they did, close the terminal, restart the system, and check the display settings once it's come up and you've logged in.

If this doesn't solve it, post the new log and xorg.conf files and we'll try to figure out what to try next! If it does, let us know and use the "thread tools" link at the top of the page to mark it as "solved" so that others can benefit.

---

### Post by chris88knox on 2010-08-11
Thanks so much for your help...but it came back... I used hori: 63.980 - 79.976    then vert 60.020 - 75.025   it then came back  (after restart and said frequency was out of range.... so i went into recovery---failsafe graphics mode---reset to defaults....just so I could get back on the machine... Then I went to look for the xorg.config file to post it here, and it is GONE.


And I also did not change the name.... or model number I am not sure what to do there...

And what does the "vesa" mean on the spec sheet?

---

### Post by JKyleOKC on 2010-08-11
The failsafe default routines do remove the xorg.conf file, since the default action as of Karmic Koala (9.10) is to not use the conf file but instead depend on automatic detection -- which in this case doesn't work (you're far from alone in it not working -- most of us with machines more than a year old face this problem).

If you did the "save as" to xorg.conf.works that I recommended, you can restore to that version by opening a terminal and entering ```
sudo cp /etc/X11/xorg.conf.works /etc/X11/xorg.conf
``` to copy the previous version back to the main file's name. A restart should then get you back to the point where you were before the most recent attempts.

I'll keep looking for ways to get the information set properly. I recall at one time there was an option that could be set to tell the X server not to use EDID information and that might be what you need. The EDID info is a block of data that the monitor sends to the video driver to tell it the capabilities, but it's not always accurate. In my case, my Acer monitor's EDID block isn't accepted by the driver; this happens because when EDID first came into use, there was no generally accepted standard, so not all monitor makers implemented it the same way. If your monitor's EDID is telling the driver it cannot do things when in fact it actually can, then ignoring EDID and giving the information explicitly in the config file might be the answer.

You can see the EDID block mentioned in the copy of the log that you posted earlier in this thread. Unfortunately I don't know how to translate its content into human terms.

Hopefully others who have fought this problem will chime in and we can get you going!

---

### Post by chris88knox on 2010-08-11
I got it!!!! 

$ gtf 1280_1024 60


xrandr --addmode VGA1 1280x1024_60.00

xrandr --output VGA1 1280x1024_60.00

---

### Post by chris88knox on 2010-08-11
the only problem is that is does not keep it upon reboot... how do I make it save current config?

---

### Post by chris88knox on 2010-08-11
I followed the instructions/script here on this site<[http://www.ubuntugeek.com/how-change-display-resolution-settings-using-xrandr.html](http://www.ubuntugeek.com/how-change-display-resolution-settings-using-xrandr.html)>, and it works, (i used the 1280x1024, and it's accompanying script), but upon restart (even though i followed the instructions for saving and it still does not reboot to the 1280x1024 config...frustrating yes....solvable?>>>I hope.

Any suggestions?

---

### Post by JKyleOKC on 2010-08-11
One of the major efforts in developing Lucid Lynx was to shorten the boot-up time by doing as much as possible at the same time, rather than one task after another. This can lead to some things being attempted before their prerequisites have been met. The developers have done a good job of handling most such things, but it's possible that a few such "race" conditions exist and that might be why adding the xrandr commands to the gdm initialization code as directed in that thread you used isn't working for you.

I did trace back to the earlier thread that was referenced on the last line and it looks as if some folk found that it didn't work even with versions before Lucid.

It may be possible to write a script to run those commands, and include it in your "autostart" collection. I actually use Xubuntu rather than Ubuntu, and the settings files are a bit different -- but someone else ought to chime in and give you the details on how to do it...

---

### Post by realzippy on 2010-08-11
..why no try a modeline ,e.g. this one you get with ```
cvt 1280 1024 60
```
in your xorg.conf monitor section?Like:

Section "Monitor"
Identifier "Monitor0"
VendorName "Monitor Vendor"
ModelName "Monitor Model"
Modeline "1280x1024_60.00"    6.25  1280 1320 1440 1600  60 63 73 76 -hsync +vsync
EndSection

?

---

### Post by chris88knox on 2010-08-11
Thank you both SOOOOOO much!! The last line finalized the instructions on the link I put there.  Awesome information [JKyleOKC]("http://ubuntuforums.org/member.php?u=374258") thank you... Good reccomendation realzippy!  Again THANKS!!! You all saved my eyes!

---

### Post by JKyleOKC on 2010-08-11
Good news! Be sure to use the "Thread Tools" link at the top of the page and mark the thread as "solved" so that others will know it does have the solution to a problem. And welcome to the wonderful world of *buntu!

---

