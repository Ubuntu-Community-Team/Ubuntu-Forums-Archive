---
title: "Help! Display Driver Problem"
date: 2009-02-18
forum: New to Ubuntu
---

### Post by psychx on 2009-02-18
New install of Ubuntu 8.10

Downloaded the newest NVIDIA display drivers from their website.

Follow these instructions EXACTLY: [Ubuntuforums.org Thread]("http://ubuntuforums.org/showpost.php?p=4105735&postcount=4")

After reboot, it took slightly longer to load, then came to the login screen (but not the gnome screen, the actual text-based screen). Then without typing anything in, it proceeded to look like it was booting up the GUI, when I then got an error saying that it found displays but is not configured for them. I was able to boot using limit display settings for just this session. If you need other information, I will gladly give it to you. Thanks!

---

### Post by alexandari on 2009-02-18
Well,I also had a problem like that...sometime ago with the newest drivers of ATI
so,the thing I`m going to recommand is for you to install your video drivers using ENVY. It`s located in your package manager,it`s very easy to use. It downloads and installs your latest video drivers :)

kinda out of the topic:

A while back when I was using Fedora Core 6,I had this...problem with Nvidia,I couldnt start the X without removing .X0-lock from /tmp (strange)
Maybe you can try it if you don`t get your problem solved with ENVY :}  gl mate

---

### Post by psychx on 2009-02-18
envy-core ? or envy-qt ?

I installed core, but where do I find it?

---

### Post by Immolatus on 2009-02-18
Your best bet are the nvidia 177 drivers right in the repos (in synaptic). their identical to the download and already binary. They installed for me no problem and came with a configuration utility. Also , these drivers work for the majority of nvidia cards.

---

### Post by psychx on 2009-02-18
I just installed the 177 drivers from Synaptic, then restarted. When I booted back up, I got an error again saying something about the configuration being wrong. I told it to use generic configuration, then tried to boot in. I believe I am still running in low graphics mode. I am going to re-activate the driver one more time and reboot.

---

### Post by psychx on 2009-02-18
I am still unable to boot using the new drivers. I am currently in Limited Graphics Mode. I have tried using the old configuration, I have tried using a new configuration, and I have tried using a generic configuration. I was able to obtain 2 logs of what is happening, the first being my Startup Errors Log, and the second being the xorg log file.

Startups Errors:
```
5293 4989
xinit /etc/gdm/failsafeXinit /etc/X11/xorg.conf.failsafe with-gdm -- /usr/bin/X :0 -auth /var/lib/gdm/:0.Xauth -nolisten tcp vt9 -br -once -config /etc/X11/xorg.conf.failsafe -logfile /var/log/Xorg.failsafe.log

X.Org X Server 1.5.2
Release Date: 10 October 2008
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-19-server i686 Ubuntu
Current Operating System: Linux mike-linux 2.6.27-11-generic #1 SMP Thu Jan 29 19:24:39 UTC 2009 i686
Build Date: 24 October 2008  08:00:16AM
xorg-server 2:1.5.2-2ubuntu3 (buildd@rothera.buildd) 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(++) Log file: "/var/log/Xorg.failsafe.log", Time: Wed Feb 18 16:57:26 2009
(++) Using config file: "/etc/X11/xorg.conf.failsafe"

(EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)
5293 4989
cp: cannot stat `/etc/X11/xorg_conf': No such file or directory
```

Xorg log file:
```

X.Org X Server 1.5.2
Release Date: 10 October 2008
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-19-server i686 Ubuntu
Current Operating System: Linux mike-linux 2.6.27-11-generic #1 SMP Thu Jan 29 19:24:39 UTC 2009 i686
Build Date: 24 October 2008  08:00:16AM
xorg-server 2:1.5.2-2ubuntu3 (buildd@rothera.buildd) 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Wed Feb 18 16:57:20 2009
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

(--) PCI:*(0@1:0:0) nVidia Corporation NV43 [GeForce 6600 GT] rev 162, Mem @ 0xfc000000/0, 0xe0000000/0, 0xfb000000/0, BIOS @ 0x????????/131072
(II) System resource ranges:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) "extmod" will be loaded by default.
(II) "dbe" will be loaded by default.
(II) "glx" will be loaded. This was enabled by default and also specified in the config file.
(II) "freetype" will be loaded by default.
(II) "record" will be loaded by default.
(II) "dri" will be loaded by default.
(II) LoadModule: "glx"

(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Server Extension
(II) NVIDIA GLX Module  177.82  Tue Nov  4 14:03:48 PST 2008
(II) Loading extension GLX
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
(II) LoadModule: "nvidia"

(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Video Driver
(II) NVIDIA dlloader X Driver  177.82  Tue Nov  4 13:42:45 PST 2008
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 01@00:00:0
(II) Loading sub module "fb"
(II) LoadModule: "fb"

(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "wfb"
(II) LoadModule: "wfb"

(II) Loading /usr/lib/xorg/modules//libwfb.so
(II) Module wfb: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
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
(II) NVIDIA(0): Creating default Display subsection in Screen section
	"Default Screen" for depth/fbbpp 24/32
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "NoLogo" "True"
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(II) NVIDIA(0): NVIDIA GPU GeForce 6600 GT (NV43) at PCI:1:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 131072 kBytes
(--) NVIDIA(0): VideoBIOS: 05.43.02.39.51
(II) NVIDIA(0): Detected AGP rate: 4X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce 6600 GT at PCI:1:0:0:
(--) NVIDIA(0):     NEC FE950+ (CRT-1)
(--) NVIDIA(0): NEC FE950+ (CRT-1): 400.0 MHz maximum pixel clock
(II) NVIDIA(0): Assigned Display Device: CRT-1
(==) NVIDIA(0): 
(==) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
(==) NVIDIA(0):     will be used as the requested mode.
(==) NVIDIA(0): 
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "nvidia-auto-select"
(II) NVIDIA(0): Virtual screen size determined to be 1280 x 1024
(--) NVIDIA(0): DPI set to (87, 92); computed from "UseEdidDpi" X config
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
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(II) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
(II) Loading extension XINERAMA
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
(II) Initializing extension GLX

Backtrace:
```

---

### Post by Immolatus on 2009-02-18
Can you please give us your system specs? I also noticed that you are running the server version, is this a machine in fact a server? The reason I ask is that to my knowledge you have to install the desktop after the fact. You might want to try the standard edition.

---

### Post by psychx on 2009-02-18
Pentium 4 2Ghz
NVIDIA GeForce 6600GT
1GB pc3200
-----------
I didn't know that I was running the server version, but what server version? Of Ubuntu or of Xorg?

---

### Post by psychx on 2009-02-19
I'm really not sure what to do, I don't want to have to reinstall, but I can if I have to..

---

### Post by psychx on 2009-02-19
Can anybody help me? If I can't fix this within the next 2 hours I will reinstall Ubuntu.

---

### Post by Immolatus on 2009-02-19
Ok. I think it might be the best idea to start fresh at this point. I think what might have happened here was that you messed with your xorg.conf and not backed it up, or it's just all a jumble at this point (don't feel bad it happened to me twice in a row and now I'm running the beast through a 19 inch Bravia at ridiculous resolution.). 

I assumed that you were running the server version from the out put in your fourth post here. In your Xorg log it said build version "Linux 2.6.x-server ubuntu", so thats where that came from. I thought that might cause a funk with Xorg.

I would download the standard version for sure this time and reinstall--> install the 177 drivers from the repos with the nvidia config utility that is provided there (just search the list if its not obvious, its a short list.) and then have a look at this thread:

[http://ubuntuforums.org/showthread.php?t=965398](http://ubuntuforums.org/showthread.php?t=965398)

What you're looking for here is what "Loomsen" says about xorg.conf, this thread fixed my problem.

I'll check back within the hour, good luck!

---

### Post by psychx on 2009-02-20
I have reformatted and am on a new installation of Ubuntu 8.10 -- Now, which driver am I downloading from Synaptic? nvidia-glx-177 ?

---

### Post by overdrank on 2009-02-20
[Duplicate here]("http://ubuntuforums.org/showthread.php?p=6768530#post6768530") Thread closed.

---

