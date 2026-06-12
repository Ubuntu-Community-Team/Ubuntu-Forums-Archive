---
title: "Compiz errors."
date: 2010-06-24
forum: New to Ubuntu
---

### Post by lockalidiot on 2010-06-24
Hi again, it's been a while... To my shame I have to admit that lately I have been using W7 part of my HD more than U10.04 side. (school! I have to learn how to do stuff on Windows for school!) 

Today however I vent back to Ubu side to do updates and tweak some stuff. You know the feeling: "Got to  tweak ubuntu...."
To my utmost distress I noticed that my compiz isn't working! 

Earlier this spring I had to manually install nvidia drivers due the low-graphics issue. It worked fine and everything ran smoothly. Even now the drivers are working, as the desktop resolution is as it should and I can access the nvidia control panel.

After discovering that my compiz has some issues I first checed if the desktop effects are enabled, they are not. I try to enable them through System->Preferences->Appearance->Visual Effects(tab). Doing this gives me error message "Desktop effects could not be enabled."

Ok, Next I try to reinstall compiz to see if there is just some odd "thing" bugging it. I run this command:
```
sudo aptitude reinstall compiz
```
It runs through nicely. After that I run:
```
sudo apt-get update && sudo apt-get upgrade
```
Works fine.
then I try to launch compiz via terminal
```
me@mycpu:~$ compiz
compiz (core) - Fatal: glXCreateContext failed
compiz (core) - Error: Failed to manage screen: 0
compiz (core) - Fatal: No manageable screens found on display :0.0

Launching fallback window manager

```
So, what should I do?

---

### Post by RetchingRabbit on 2010-06-24
You may need to enable a restricted video driver....what kind of video card do you have?

---

### Post by lockalidiot on 2010-06-24
nVidia GeForce 220 Gt, ie. crap... The thing is that earlier everything worked fine. I had my über cool compiz effects and all :p now not so much. Where will I find the option to enable these drivers?


EDIT!!!!: Ok, I just checked the "Hardware Drivers" thingy in the System Menu. It says that I have no propitiatory(?) drivers in use on my system... Which is odd as I just a month ago manually installed one...

---

### Post by Joe of loath on 2010-06-24
> **lockalidiot said:**
> nVidia GeForce 220 Gt, ie. crap... The thing is that earlier everything worked fine. I had my über cool compiz effects and all :p now not so much. Where will I find the option to enable these drivers?


EDIT!!!!: Ok, I just checked the "Hardware Drivers" thingy in the System Menu. It says that I have no propitiatory(?) drivers in use on my system... Which is odd as I just a month ago manually installed one...

XD it's better than all my cards put together... The best graphics card in my house is a radeon 9600!

Anyway, have you tried envyng? I know it's not really useful any more, but it might help in your case.

---

### Post by lockalidiot on 2010-06-24
I tried to use it a long while a go, to no avail... lol. I think I should just try to install the drivers again? I checked my Software sources and I have EVERYTHING enabled, including the restricted stuff, drivers and all...

---

### Post by lockalidiot on 2010-06-24
Update to the situation:

Now I'm running with resolution of mayde 800x600 and getting a major headache...:lolflag:

I installed the nvidia-current:
```
sudo apt-get install nvidia-current
```
It installed and shows in the Hardware Drivers thing.
BUT, it says, that it is active but not currently enabled.
I tried to deactivate it and the activate it again. Then I rebooted, but with no effect. still active but not enabled.
Any tips here?

---

### Post by lockalidiot on 2010-07-05
I'm still having this issue.

A recap here:

I had earlier manually installed nvidia drivers, worked fine. Then I got kernel update and as we know, the drivers didn't work anymore. I have tried manually installing them again, to no avail, and have now installed nvidia-current from the repos. The situation is that I can see the drivers in thew Hardware Drivers thingy and they are activated, but not in use. I have tried to deactivate->activate->reboot, but that doesn't help. I do need some help on this... lol. At the moment I'm stuck with 800x600 resolutions with zero(0) desktop effects and stuff. I miss my cube! It was so pretty.....

---

### Post by lockalidiot on 2010-07-05
I have apparently solved this issue by running command:

```
sudo nvidia-xconfig
```

---

### Post by lockalidiot on 2010-07-05
check that, after coming home from work and firing up the 'puter I got the low graphics issue. I checked my drivers, they are there, but not active. I tried to run the command from the previous post again, but it didn't work.

Any ideas?

---

### Post by lidex on 2010-07-07
What is this output:
```
cat /var/log/Xorg.0.log
cat /etc/X11/xorg.conf
```

---

### Post by lockalidiot on 2010-07-08
I have done a clean install, but graphics issues still seem to bug me.

```
cat /var/log/Xorg.0.log
cat /etc/X11/xorg.conf
```

OUTPUT:
```
bigboss@slave:/$ cat /var/log/Xorg.0.log

X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-27-server x86_64 Ubuntu
Current Operating System: Linux slave 2.6.32-24-generic #38-Ubuntu SMP Mon Jul 5 09:20:59 UTC 2010 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-24-generic root=UUID=447a4b80-d88d-48ca-9fab-c39065b1b657 ro quiet splash
Build Date: 16 June 2010  09:34:29AM
xorg-server 2:1.7.6-2ubuntu7.2 (For technical support please see http://www.ubuntu.com/support) 
Current version of pixman: 0.16.4
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Thu Jul  8 22:24:53 2010
(==) Using config file: "/etc/X11/xorg.conf"
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"
(==) No Layout section.  Using the first Screen section.
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "<default monitor>"
(==) No device specified for screen "Default Screen".
	Using the first device section listed.
(**) |   |-->Device "Default Device"
(==) No monitor specified for screen "Default Screen".
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

(--) PCI:*(0:1:0:0) 10de:0a20:174b:2160 nVidia Corporation GT216 [GeForce GT 220] rev 162, Mem @ 0xfd000000/16777216, 0xd0000000/268435456, 0xce000000/33554432, I/O @ 0x0000d800/128, BIOS @ 0x????????/524288
(II) Open ACPI successful (/var/run/acpid.socket)
(II) "extmod" will be loaded by default.
(II) "dbe" will be loaded by default.
(II) "glx" will be loaded. This was enabled by default and also specified in the config file.
(II) "record" will be loaded by default.
(II) "dri" will be loaded by default.
(II) "dri2" will be loaded by default.
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/extra-modules/libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Server Extension
(II) NVIDIA GLX Module  195.36.24  Thu Apr 22 19:52:00 PDT 2010
(II) Loading extension GLX
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
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/extra-modules/nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Video Driver
(II) NVIDIA dlloader X Driver  195.36.24  Thu Apr 22 19:18:54 PDT 2010
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 01@00:00:0
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "wfb"
(II) LoadModule: "wfb"
(II) Loading /usr/lib/xorg/modules/libwfb.so
(II) Module wfb: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(II) NVIDIA(0): Creating default Display subsection in Screen section
	"Default Screen" for depth/fbbpp 24/32
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "NoLogo" "True"
(**) Jul 08 22:24:53 NVIDIA(0): Enabling RENDER acceleration
(II) Jul 08 22:24:53 NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) Jul 08 22:24:53 NVIDIA(0):     enabled.
(EE) Jul 08 22:24:53 NVIDIA(0): Failed to initialize the NVIDIA kernel module. Please see the
(EE) Jul 08 22:24:53 NVIDIA(0):     system's kernel log for additional error messages and
(EE) Jul 08 22:24:53 NVIDIA(0):     consult the NVIDIA README for details.
(EE) NVIDIA(0):  *** Aborting ***
(II) UnloadModule: "nvidia"
(II) UnloadModule: "wfb"
(II) UnloadModule: "fb"
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found

Please consult the The X.Org Foundation support 
	 at http://wiki.x.org
 for help. 
Please also check the log file at "/var/log/Xorg.0.log" for additional information.

 ddxSigGiveUp: Closing log

bigboss@slave:/$ cat /etc/X11/xorg.conf

Section "Screen"
	Identifier	"Default Screen"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Default Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection

```

What does this magic scribble tell you, o'master... ;)

---

### Post by lidex on 2010-07-08
That doesn't look like an xorg.conf generated by nvidia-xconfig. Here's mine, for example:
```
cat /etc/X11/xorg.conf
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder58)  Thu Apr 22 20:35:23 PDT 2010

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       28.0 - 33.0
    VertRefresh     43.0 - 72.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```

Try this:
```
sudo rm /etc/X11/xorg.conf
sudo nvidia-xconfig
```
Now **Reboot**

---

