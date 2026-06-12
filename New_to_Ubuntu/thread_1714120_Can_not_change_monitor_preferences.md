---
title: "Can not change monitor preferences"
date: 2011-03-24
forum: New to Ubuntu
---

### Post by 604daizi on 2011-03-24
I just upgraded to ubuntu 10.04 from 8 or 9.something.  I may have directed the installation not to save my preferences.

Now, I can not change my monitor resolution or refresh rate, and I can  no longer stream AVI files or Megavideo.  Administration > Hardware  Drivers is empty.  Preferences > Monitors is empty.

My monitor is a Sony Multiscan G200 and my video card is a nvidia nv5.  I  have searched for drivers for both hardware pieces, but have found none  for linux.

I am a total nooby.  Help much appreciated.

---

### Post by 604daizi on 2011-03-25
I have found a bunch of nvidia files on my hard drive.  Maybe, if I can get ubuntu to associate these with the video card, my problem will be solved?

---

### Post by realzippy on 2011-03-25
Open terminal,post output from

```
lspci | grep  VGA
```

so we know which VGA card you are running.

---

### Post by 604daizi on 2011-03-25
nVidia Corporation NV5 [RIVA TNT2/TNT2 Pro] (rev 15)

---

### Post by realzippy on 2011-03-25
..have you formerly run a nvidia graphics driver ?

---

### Post by 604daizi on 2011-03-25
I don't know how to do that.

---

### Post by 604daizi on 2011-03-25
Should I try this: [http://ubuntuguide.net/install-latest-nvidia-graphics-drivers-in-ubuntu-linux](http://ubuntuguide.net/install-latest-nvidia-graphics-drivers-in-ubuntu-linux) ?

As I wrote earlier, I have some nVidia files on my hard drive, but I do not know how to run them.

---

### Post by realzippy on 2011-03-26
No,the new nvidia-driver does not work for your old card.
You need [71.86.xx]("http://ubuntuforums.org/showpost.php?p=8939154&postcount=7") 
Do not know if this driver works under new X server you use since you have upgraded 2 versions ,had to google that.

---

### Post by 604daizi on 2011-03-27
Zippy, thank you for finding this for me.  Unfortunately, I do not understand the installation How To,  I will need step-by-step instructions.

By the way, what about the driver I apparently still have on my hard drive?  Is there a simple way to activate it?  Or is the problem that my old driver is incompatible with my new operating system?

---

### Post by realzippy on 2011-03-27
The problem might not be *how* to install the driver...it might be *not* possible,since the X server version altered during your upgrades.
The card is ancient,the driver isn't supported any more.

if you run

```
ls -l /etc/X11/

```
and watch out for xorg.conf.backup files (if,post their output),so we can get a clue which driver
has been installed -or still is although it might not be possible to run
it anymore.
You could still use the free nouveau driver,but the performance will not be as good as it has been with old ubuntu + nvidia driver.

Edit:

also run 
```
nvidia-settings
```

what happens/output ?
Anyone else has an idea (TNT2 Maverick)?

---

### Post by realzippy on 2011-03-27
After some more googling:

Using the nouveau-driver is the only choice you have,no more nvidia..

---

### Post by 604daizi on 2011-03-27
Code:
ls -l /etc/X11/
Response:

total 84
drwxr-xr-x 2 root root  4096 2011-03-22 20:42 app-defaults
drwxr-xr-x 2 root root  4096 2011-03-22 20:52 cursors
-rw-r--r-- 1 root root    14 2008-04-29 12:19 default-display-manager
drwxr-xr-x 6 root root  4096 2008-04-29 12:12 fonts
-rw-r--r-- 1 root root 17394 2007-11-19 07:15 rgb.txt
lrwxrwxrwx 1 root root    13 2008-04-29 12:03 X -> /usr/bin/Xorg
drwxr-xr-x 3 root root  4096 2011-03-22 20:08 xinit
-rw-r--r-- 1 root root  1721 2011-03-22 21:43 xorg.conf-backup-110322214240
-rw-r--r-- 1 root root  1425 2011-03-22 21:24 xorg.conf.dist-upgrade-201103222124
-rw-r--r-- 1 root root   270 2011-03-27 12:06 xorg.conf.failsafe
-rwxr-xr-x 1 root root   709 2010-04-01 04:19 Xreset
drwxr-xr-x 2 root root  4096 2011-03-22 19:21 Xreset.d
drwxr-xr-x 2 root root  4096 2011-03-22 19:21 Xresources
-rwxr-xr-x 1 root root  3730 2008-03-13 08:10 Xsession
drwxr-xr-x 2 root root  4096 2011-03-24 19:32 Xsession.d
-rw-r--r-- 1 root root   265 2007-11-19 07:15 Xsession.options
-rw-r--r-- 1 root root    13 2007-07-24 02:59 XvMCConfig
-rw------- 1 root root   601 2011-03-22 19:21 Xwrapper.config

Code:
nvidia-settings
Response:
The program 'nvidia-settings' is currently not installed.  You can install it by typing:
sudo apt-get install nvidia-settings

Code:
sudo apt-get install nvidia-settings

Response:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libavutil1d libdc1394-13 libpostproc1d libamrnb3 libavformat1d libamrwb3
  libavcodec1d
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  nvidia-settings
0 upgraded, 1 newly installed, 0 to remove and 1 not upgraded.
Need to get 819kB of archives.
After this operation, 1,921kB of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main nvidia-settings 195.36.08-0ubuntu2 [819kB]
Fetched 819kB in 4s (200kB/s)                          
Selecting previously deselected package nvidia-settings.
(Reading database ... 185392 files and directories currently installed.)
Unpacking nvidia-settings (from .../nvidia-settings_195.36.08-0ubuntu2_i386.deb) ...
Processing triggers for man-db ...
Setting up nvidia-settings (195.36.08-0ubuntu2) ...


I then tried to open Preferences > Monitors.  I got the following this message:

'It appears that your graphics driver does not support the necessary extensions to support this tool.  Do you want to use your graphics driver vendor's tool instead? Yes/No

I closed the pop up window.

What next?

---

### Post by 604daizi on 2011-03-27
Oops!

Zippy, I went ahead and ran ththat code before I realised there was a further message from you.

---

### Post by realzippy on 2011-03-28
As mentioned,the only way for you is the nouveau driver.
Delete relics of the nvidia-driver you had installed:

```
sudo apt-get --purge remove nvidia-glx* nvidia-kernel-common nvidia-settings
```

(re-)install nouveau :

```
sudo apt-get install --reinstall xserver-xorg-video-nouveau
```

Reboot..hopefully you get your resolutions back at least.

---

### Post by 604daizi on 2011-03-29
Doesn't seem to have made any difference.

Thank you for your time, Zippy.

---

### Post by realzippy on 2011-03-30
...can you post your var/log/Xorg.0.log file ?

---

### Post by 604daizi on 2011-03-31
Don't know how to do that.  I assume I enter a command in Terminal.

---

### Post by realzippy on 2011-04-02
```
gedit /var/log/Xorg.0.log
```

---

### Post by 604daizi on 2011-05-24
X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-27-server i686 Ubuntu
Current Operating System: Linux freegeek 2.6.32-31-generic #61-Ubuntu SMP Fri Apr 8 18:24:35 UTC 2011 i686
Kernel command line: root=UUID=35d78d2b-7708-42b5-916d-4f1ec00bd2ac ro quiet splash 
Build Date: 08 March 2011  08:22:50AM
xorg-server 2:1.7.6-2ubuntu7.6 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
Current version of pixman: 0.16.4
    Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Mon May 23 13:48:58 2011
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
(II) Loader magic: 0x81f1e80
(II) Module ABI versions:
    X.Org ANSI C Emulation: 0.4
    X.Org Video Driver: 6.0
    X.Org XInput driver : 7.0
    X.Org Server Extension : 2.0
(--) using VT number 7

(--) PCI:*(0:1:0:0) 10de:0028:10de:0060 nVidia Corporation NV5 [RIVA TNT2/TNT2 Pro] rev 21, Mem @ 0xfd000000/16777216, 0xf8000000/33554432, BIOS @ 0x????????/65536
(II) Open ACPI successful (/var/run/acpid.socket)
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
(==) Matched nouveau as autoconfigured driver 0
(==) Matched nv as autoconfigured driver 1
(==) Matched vesa as autoconfigured driver 2
(==) Matched fbdev as autoconfigured driver 3
(==) Assigned the driver to the xf86ConfigLayout
(II) LoadModule: "nouveau"
(II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
(II) Module nouveau: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 0.0.15
    Module class: X.Org Video Driver
    ABI class: X.Org Video Driver, version 6.0
(II) LoadModule: "nv"
(II) Loading /usr/lib/xorg/modules/drivers/nv_drv.so
(II) Module nv: vendor="X.Org Foundation"
    compiled for 1.7.3.901, module version = 2.1.15
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
(II) NOUVEAU driver Date:   Wed Feb 10 18:43:39 2010 +0100
(II) NOUVEAU driver for NVIDIA chipset families :
    RIVA TNT    (NV04)
    RIVA TNT2   (NV05)
    GeForce 256 (NV10)
    GeForce 2   (NV11, NV15)
    GeForce 4MX (NV17, NV18)
    GeForce 3   (NV20)
    GeForce 4Ti (NV25, NV28)
    GeForce FX  (NV3x)
    GeForce 6   (NV4x)
    GeForce 7   (G7x)
    GeForce 8   (G8x)
(II) NOUVEAU driver Date:   Wed Feb 10 18:43:39 2010 +0100
(II) NOUVEAU driver for NVIDIA chipset families :
    RIVA TNT    (NV04)
    RIVA TNT2   (NV05)
    GeForce 256 (NV10)
    GeForce 2   (NV11, NV15)
    GeForce 4MX (NV17, NV18)
    GeForce 3   (NV20)
    GeForce 4Ti (NV25, NV28)
    GeForce FX  (NV3x)
    GeForce 6   (NV4x)
    GeForce 7   (G7x)
    GeForce 8   (G8x)
(II) VESA: driver for VESA chipsets: vesa
(II) FBDEV: driver for framebuffer: fbdev
(II) Primary Device is: PCI 01@00:00:0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: Searching for BusID pci:0000:01:00.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: drmOpenMinor returns 8
drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
(II) [drm] nouveau interface version: 0.0.15
(WW) Falling back to old probe method for vesa
(WW) Falling back to old probe method for fbdev
(II) Loading sub module "fbdevhw"
(II) LoadModule: "fbdevhw"
(II) Loading /usr/lib/xorg/modules/linux/libfbdevhw.so
(II) Module fbdevhw: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 0.0.2
    ABI class: X.Org Video Driver, version 6.0
(II) Loading sub module "dri"
(II) LoadModule: "dri"
(II) Reloading /usr/lib/xorg/modules/extensions/libdri.so
(II) NOUVEAU(0): Loaded DRI module
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 9, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 9, (OK)
drmOpenByBusid: Searching for BusID pci:0000:01:00.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 9, (OK)
drmOpenByBusid: drmOpenMinor returns 9
drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
(II) [drm] DRM interface version 1.3
(II) [drm] DRM open master succeeded.
(--) NOUVEAU(0): Chipset: "NVIDIA NV05"
(II) NOUVEAU(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
(==) NOUVEAU(0): Depth 24, (--) framebuffer bpp 32
(==) NOUVEAU(0): RGB weight 888
(==) NOUVEAU(0): Default visual is TrueColor
(==) NOUVEAU(0): Using HW cursor
(II) NOUVEAU(0): Output VGA-1 has no monitor section
(II) NOUVEAU(0): EDID for output VGA-1
(II) NOUVEAU(0): Manufacturer: SNY  Model: 1270  Serial#: 7000522
(II) NOUVEAU(0): Year: 1999  Week: 38
(II) NOUVEAU(0): EDID Version: 1.2
(II) NOUVEAU(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) NOUVEAU(0): Sync:  Separate  Composite  SyncOnGreen
(II) NOUVEAU(0): Max Image Size [cm]: horiz.: 33  vert.: 24
(II) NOUVEAU(0): Gamma: 2.50
(II) NOUVEAU(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) NOUVEAU(0): GTF timings supported
(II) NOUVEAU(0): redX: 0.625 redY: 0.340   greenX: 0.280 greenY: 0.605
(II) NOUVEAU(0): blueX: 0.155 blueY: 0.070   whiteX: 0.283 whiteY: 0.298
(II) NOUVEAU(0): Supported established timings:
(II) NOUVEAU(0): 720x400@70Hz
(II) NOUVEAU(0): 720x400@88Hz
(II) NOUVEAU(0): 640x480@60Hz
(II) NOUVEAU(0): 640x480@67Hz
(II) NOUVEAU(0): 640x480@72Hz
(II) NOUVEAU(0): 640x480@75Hz
(II) NOUVEAU(0): 800x600@56Hz
(II) NOUVEAU(0): 800x600@60Hz
(II) NOUVEAU(0): 800x600@72Hz
(II) NOUVEAU(0): 800x600@75Hz
(II) NOUVEAU(0): 832x624@75Hz
(II) NOUVEAU(0): 1024x768@87Hz (interlaced)
(II) NOUVEAU(0): 1024x768@60Hz
(II) NOUVEAU(0): 1024x768@70Hz
(II) NOUVEAU(0): 1024x768@75Hz
(II) NOUVEAU(0): 1280x1024@75Hz
(II) NOUVEAU(0): 1152x864@75Hz
(II) NOUVEAU(0): Manufacturer's mask: 0
(II) NOUVEAU(0): Supported standard timings:
(II) NOUVEAU(0): #0: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) NOUVEAU(0): #1: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) NOUVEAU(0): #2: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) NOUVEAU(0): #3: hsize: 1152  vsize 864  refresh: 85  vid: 22897
(II) NOUVEAU(0): #4: hsize: 1280  vsize 1024  refresh: 85  vid: 39297
(II) NOUVEAU(0): #5: hsize: 1600  vsize 1200  refresh: 75  vid: 20393
(II) NOUVEAU(0): Serial No: 7000522
(II) NOUVEAU(0): Ranges: V min: 48 V max: 120 Hz, H min: 30 H max: 96 kHz, PixClock max 250 MHz
(II) NOUVEAU(0): Monitor name: SONY CPD-G200
(II) NOUVEAU(0): Monitor name:  Trinitron
(II) NOUVEAU(0): EDID (in hex):
(II) NOUVEAU(0):     00ffffffffffff004dd97012cad16a00
(II) NOUVEAU(0):     260901020e211896e90cc9a057479b27
(II) NOUVEAU(0):     12484cffff8031594559615971598199
(II) NOUVEAU(0):     a94f01010101000000ff003730303035
(II) NOUVEAU(0):     32320a2020202020000000fd0030781e
(II) NOUVEAU(0):     6019000a202020202020000000fc0053
(II) NOUVEAU(0):     4f4e59204350442d47323030000000fc
(II) NOUVEAU(0):     00205472696e6974726f6e0a20200026
(II) NOUVEAU(0): EDID vendor "SNY", prod id 4720
(II) NOUVEAU(0): Using EDID range info for horizontal sync
(II) NOUVEAU(0): Using EDID range info for vertical refresh
(II) NOUVEAU(0): Printing DDC gathered Modelines:
(II) NOUVEAU(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) NOUVEAU(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) NOUVEAU(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) NOUVEAU(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) NOUVEAU(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) NOUVEAU(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) NOUVEAU(0): Modeline "720x400"x0.0   35.50  720 738 846 900  400 421 423 449 -hsync -vsync (39.4 kHz)
(II) NOUVEAU(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) NOUVEAU(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) NOUVEAU(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) NOUVEAU(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) NOUVEAU(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) NOUVEAU(0): Modeline "1024x768"x0.0   44.90  1024 1032 1208 1264  768 768 772 817 interlace +hsync +vsync (35.5 kHz)
(II) NOUVEAU(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) NOUVEAU(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) NOUVEAU(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) NOUVEAU(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) NOUVEAU(0): Modeline "640x480"x0.0   36.00  640 696 752 832  480 481 484 509 -hsync -vsync (43.3 kHz)
(II) NOUVEAU(0): Modeline "800x600"x0.0   56.25  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
(II) NOUVEAU(0): Modeline "1024x768"x0.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
(II) NOUVEAU(0): Modeline "1152x864"x85.0  119.65  1152 1224 1352 1552  864 865 868 907 -hsync +vsync (77.1 kHz)
(II) NOUVEAU(0): Modeline "1280x1024"x0.0  157.50  1280 1344 1504 1728  1024 1025 1028 1072 +hsync +vsync (91.1 kHz)
(II) NOUVEAU(0): Modeline "1600x1200"x0.0  202.50  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (93.8 kHz)
(II) NOUVEAU(0): Not using default mode "640x350" (unknown reason)
(II) NOUVEAU(0): Not using default mode "320x175" (unknown reason)
(II) NOUVEAU(0): Not using default mode "640x400" (unknown reason)
(II) NOUVEAU(0): Not using default mode "320x200" (unknown reason)
(II) NOUVEAU(0): Not using default mode "720x400" (unknown reason)
(II) NOUVEAU(0): Not using default mode "360x200" (unknown reason)
(II) NOUVEAU(0): Not using default mode "640x480" (unknown reason)
(II) NOUVEAU(0): Not using default mode "320x240" (unknown reason)
(II) NOUVEAU(0): Not using default mode "640x480" (unknown reason)
(II) NOUVEAU(0): Not using default mode "320x240" (unknown reason)
(II) NOUVEAU(0): Not using default mode "640x480" (unknown reason)
(II) NOUVEAU(0): Not using default mode "320x240" (unknown reason)
(II) NOUVEAU(0): Not using default mode "640x480" (unknown reason)
(II) NOUVEAU(0): Not using default mode "320x240" (unknown reason)
(II) NOUVEAU(0): Not using default mode "800x600" (unknown reason)
(II) NOUVEAU(0): Not using default mode "400x300" (unknown reason)
(II) NOUVEAU(0): Not using default mode "800x600" (unknown reason)
(II) NOUVEAU(0): Not using default mode "400x300" (unknown reason)
(II) NOUVEAU(0): Not using default mode "800x600" (unknown reason)
(II) NOUVEAU(0): Not using default mode "400x300" (unknown reason)
(II) NOUVEAU(0): Not using default mode "800x600" (unknown reason)
(II) NOUVEAU(0): Not using default mode "400x300" (unknown reason)
(II) NOUVEAU(0): Not using default mode "800x600" (unknown reason)
(II) NOUVEAU(0): Not using default mode "400x300" (unknown reason)
(II) NOUVEAU(0): Not using default mode "1024x768" (unknown reason)
(II) NOUVEAU(0): Not using default mode "512x384" (unknown reason)
(II) NOUVEAU(0): Not using default mode "1024x768" (unknown reason)
(II) NOUVEAU(0): Not using default mode "512x384" (unknown reason)
(II) NOUVEAU(0): Not using default mode "1024x768" (unknown reason)
(II) NOUVEAU(0): Not using default mode "512x384" (unknown reason)
(II) NOUVEAU(0): Not using default mode "1024x768" (unknown reason)
(II) NOUVEAU(0): Not using default mode "512x384" (unknown reason)
(II) NOUVEAU(0): Not using default mode "1024x768" (unknown reason)
(II) NOUVEAU(0): Not using default mode "512x384" (unknown reason)
(II) NOUVEAU(0): Not using default mode "1152x864" (unknown reason)
(II) NOUVEAU(0): Not using default mode "576x432" (unknown reason)
(II) NOUVEAU(0): Not using default mode "1280x960" (unknown reason)
(II) NOUVEAU(0): Not using default mode "640x480" (unknown reason)
(II) NOUVEAU(0): Not using default mode "1280x960" (unknown reason)
(II) NOUVEAU(0): Not using default mode "640x480" (unknown reason)
(II) NOUVEAU(0): Not using default mode "1280x1024" (unknown reason)
(II) NOUVEAU(0): Not using default mode "640x512" (unknown reason)
(II) NOUVEAU(0): Not using default mode "1280x1024" (unknown reason)
(II) NOUVEAU(0): Not using default mode "640x512" (unknown reason)
(II) NOUVEAU(0): Not using default mode "1280x1024" (unknown reason)
(II) NOUVEAU(0): Not using default mode "640x512" (unknown reason)
(II) NOUVEAU(0): Not using default mode "1600x1200" (unknown reason)
(II) NOUVEAU(0): Not using default mode "800x600" (unknown reason)
(II) NOUVEAU(0): Not using default mode "1600x1200" (unknown reason)
(II) NOUVEAU(0): Not using default mode "800x600" (unknown reason)
(II) NOUVEAU(0): Not using default mode "1600x1200" (unknown reason)
(II) NOUVEAU(0): Not using default mode "800x600" (unknown reason)
(II) NOUVEAU(0): Not using default mode "1600x1200" (unknown reason)
(II) NOUVEAU(0): Not using default mode "800x600" (unknown reason)
(II) NOUVEAU(0): Not using default mode "1600x1200" (hsync out of range)
(II) NOUVEAU(0): Not using default mode "800x600" (hsync out of range)
(II) NOUVEAU(0): Not using default mode "1792x1344" (unknown reason)
(II) NOUVEAU(0): Not using default mode "896x672" (unknown reason)
(II) NOUVEAU(0): Not using default mode "1792x1344" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "896x672" (hsync out of range)
(II) NOUVEAU(0): Not using default mode "1856x1392" (unknown reason)
(II) NOUVEAU(0): Not using default mode "928x696" (unknown reason)
(II) NOUVEAU(0): Not using default mode "1856x1392" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "928x696" (hsync out of range)
(II) NOUVEAU(0): Not using default mode "1920x1440" (unknown reason)
(II) NOUVEAU(0): Not using default mode "960x720" (unknown reason)
(II) NOUVEAU(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "960x720" (hsync out of range)
(II) NOUVEAU(0): Not using default mode "832x624" (unknown reason)
(II) NOUVEAU(0): Not using default mode "416x312" (unknown reason)
(II) NOUVEAU(0): Not using default mode "1152x864" (unknown reason)
(II) NOUVEAU(0): Not using default mode "576x432" (unknown reason)
(II) NOUVEAU(0): Not using default mode "1152x864" (unknown reason)
(II) NOUVEAU(0): Not using default mode "576x432" (unknown reason)
(II) NOUVEAU(0): Not using default mode "1152x864" (unknown reason)
(II) NOUVEAU(0): Not using default mode "576x432" (unknown reason)
(II) NOUVEAU(0): Not using default mode "1152x864" (unknown reason)
(II) NOUVEAU(0): Not using default mode "576x432" (unknown reason)
(II) NOUVEAU(0): Not using default mode "1152x864" (unknown reason)
(II) NOUVEAU(0): Not using default mode "576x432" (unknown reason)
(II) NOUVEAU(0): Not using default mode "1152x864" (unknown reason)
(II) NOUVEAU(0): Not using default mode "576x432" (unknown reason)
(II) NOUVEAU(0): Not using default mode "1360x768" (monitor doesn't support reduced blanking)
(II) NOUVEAU(0): Not using default mode "680x384" (unknown reason)
(II) NOUVEAU(0): Not using default mode "1360x768" (unknown reason)
(II) NOUVEAU(0): Not using default mode "680x384" (unknown reason)
(II) NOUVEAU(0): Not using default mode "1400x1050" (unknown reason)
(II) NOUVEAU(0): Not using default mode "700x525" (unknown reason)
(II) NOUVEAU(0): Not using default mode "1400x1050" (unknown reason)
(II) NOUVEAU(0): Not using default mode "700x525" (unknown reason)
(II) NOUVEAU(0): Not using default mode "1400x1050" (unknown reason)
(II) NOUVEAU(0): Not using default mode "700x525" (unknown reason)
(II) NOUVEAU(0): Not using default mode "1400x1050" (unknown reason)
(II) NOUVEAU(0): Not using default mode "700x525" (unknown reason)
(II) NOUVEAU(0): Not using default mode "1440x900" (unknown reason)
(II) NOUVEAU(0): Not using default mode "720x450" (unknown reason)
(II) NOUVEAU(0): Not using default mode "1600x1024" (unknown reason)
(II) NOUVEAU(0): Not using default mode "800x512" (unknown reason)
(II) NOUVEAU(0): Not using default mode "1680x1050" (monitor doesn't support reduced blanking)
(II) NOUVEAU(0): Not using default mode "840x525" (unknown reason)
(II) NOUVEAU(0): Not using default mode "1680x1050" (unknown reason)
(II) NOUVEAU(0): Not using default mode "840x525" (unknown reason)
(II) NOUVEAU(0): Not using default mode "1680x1050" (unknown reason)
(II) NOUVEAU(0): Not using default mode "840x525" (unknown reason)
(II) NOUVEAU(0): Not using default mode "1680x1050" (unknown reason)
(II) NOUVEAU(0): Not using default mode "840x525" (unknown reason)
(II) NOUVEAU(0): Not using default mode "1680x1050" (unknown reason)
(II) NOUVEAU(0): Not using default mode "840x525" (unknown reason)
(II) NOUVEAU(0): Not using default mode "1920x1080" (monitor doesn't support reduced blanking)
(II) NOUVEAU(0): Not using default mode "960x540" (unknown reason)
(II) NOUVEAU(0): Not using default mode "1920x1200" (monitor doesn't support reduced blanking)
(II) NOUVEAU(0): Not using default mode "960x600" (unknown reason)
(II) NOUVEAU(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "960x720" (hsync out of range)
(II) NOUVEAU(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "1024x768" (unknown reason)
(II) NOUVEAU(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "1024x768" (hsync out of range)
(II) NOUVEAU(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "1024x768" (hsync out of range)
(II) NOUVEAU(0): Printing probed modes for output VGA-1
(II) NOUVEAU(0): Modeline "1920x1440"x60.0  234.00  1920 2048 2256 2600  1440 1441 1444 1500 -hsync +vsync (90.0 kHz)
(II) NOUVEAU(0): Modeline "1856x1392"x60.0  218.25  1856 1952 2176 2528  1392 1393 1396 1439 -hsync +vsync (86.3 kHz)
(II) NOUVEAU(0): Modeline "1792x1344"x60.0  204.75  1792 1920 2120 2448  1344 1345 1348 1394 -hsync +vsync (83.6 kHz)
(II) NOUVEAU(0): Modeline "1920x1200"x74.9  245.25  1920 2056 2264 2608  1200 1203 1209 1255 -hsync +vsync (94.0 kHz)
(II) NOUVEAU(0): Modeline "1920x1200"x59.9  193.25  1920 2056 2256 2592  1200 1203 1209 1245 -hsync +vsync (74.6 kHz)
(II) NOUVEAU(0): Modeline "1600x1200"x75.0  205.99  1600 1720 1896 2192  1200 1201 1204 1253 -hsync +vsync (94.0 kHz)
(II) NOUVEAU(0): Modeline "1600x1200"x70.0  189.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (87.5 kHz)
(II) NOUVEAU(0): Modeline "1600x1200"x65.0  175.50  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (81.2 kHz)
(II) NOUVEAU(0): Modeline "1600x1200"x60.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz)
(II) NOUVEAU(0): Modeline "1680x1050"x84.9  214.75  1680 1808 1984 2288  1050 1053 1059 1105 -hsync +vsync (93.9 kHz)
(II) NOUVEAU(0): Modeline "1680x1050"x74.9  187.00  1680 1800 1976 2272  1050 1053 1059 1099 -hsync +vsync (82.3 kHz)
(II) NOUVEAU(0): Modeline "1680x1050"x60.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
(II) NOUVEAU(0): Modeline "1400x1050"x85.0  179.50  1400 1504 1656 1912  1050 1053 1057 1105 -hsync +vsync (93.9 kHz)
(II) NOUVEAU(0): Modeline "1400x1050"x74.9  156.00  1400 1504 1648 1896  1050 1053 1057 1099 -hsync +vsync (82.3 kHz)
(II) NOUVEAU(0): Modeline "1400x1050"x60.0  121.75  1400 1488 1632 1864  1050 1053 1057 1089 -hsync +vsync (65.3 kHz)
(II) NOUVEAU(0): Modeline "1280x1024"x85.0  157.50  1280 1344 1504 1728  1024 1025 1028 1072 +hsync +vsync (91.1 kHz)
(II) NOUVEAU(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) NOUVEAU(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) NOUVEAU(0): Modeline "1440x900"x84.8  157.00  1440 1544 1696 1952  900 903 909 948 -hsync +vsync (80.4 kHz)
(II) NOUVEAU(0): Modeline "1440x900"x75.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz)
(II) NOUVEAU(0): Modeline "1440x900"x59.9  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
(II) NOUVEAU(0): Modeline "1280x960"x85.0  148.50  1280 1344 1504 1728  960 961 964 1011 +hsync +vsync (85.9 kHz)
(II) NOUVEAU(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
(II) NOUVEAU(0): Modeline "1360x768"x60.0   85.50  1360 1424 1536 1792  768 771 777 795 +hsync +vsync (47.7 kHz)
(II) NOUVEAU(0): Modeline "1280x800"x84.9  122.50  1280 1360 1496 1712  800 803 809 843 -hsync +vsync (71.6 kHz)
(II) NOUVEAU(0): Modeline "1280x800"x74.9  106.50  1280 1360 1488 1696  800 803 809 838 -hsync +vsync (62.8 kHz)
(II) NOUVEAU(0): Modeline "1280x800"x59.8   83.50  1280 1352 1480 1680  800 803 809 831 +hsync -vsync (49.7 kHz)
(II) NOUVEAU(0): Modeline "1152x864"x85.1  119.74  1152 1224 1352 1552  864 865 868 907 -hsync +vsync (77.2 kHz)
(II) NOUVEAU(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) NOUVEAU(0): Modeline "1280x768"x84.8  117.50  1280 1360 1496 1712  768 771 778 809 -hsync +vsync (68.6 kHz)
(II) NOUVEAU(0): Modeline "1280x768"x74.9  102.25  1280 1360 1488 1696  768 771 778 805 +hsync -vsync (60.3 kHz)
(II) NOUVEAU(0): Modeline "1280x768"x59.9   79.50  1280 1344 1472 1664  768 771 778 798 -hsync +vsync (47.8 kHz)
(II) NOUVEAU(0): Modeline "1024x768"x85.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
(II) NOUVEAU(0): Modeline "1024x768"x75.1   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) NOUVEAU(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) NOUVEAU(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) NOUVEAU(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) NOUVEAU(0): Modeline "1024x768"x87.0   44.90  1024 1032 1208 1264  768 768 772 817 interlace +hsync +vsync (35.5 kHz)
(II) NOUVEAU(0): Modeline "1024x768"x87.0   44.90  1024 1032 1208 1264  768 768 776 817 interlace +hsync +vsync (35.5 kHz)
(II) NOUVEAU(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) NOUVEAU(0): Modeline "800x600"x85.1   56.25  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
(II) NOUVEAU(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) NOUVEAU(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) NOUVEAU(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) NOUVEAU(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) NOUVEAU(0): Modeline "848x480"x60.0   33.75  848 864 976 1088  480 486 494 517 +hsync +vsync (31.0 kHz)
(II) NOUVEAU(0): Modeline "640x480"x85.0   36.00  640 696 752 832  480 481 484 509 -hsync -vsync (43.3 kHz)
(II) NOUVEAU(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) NOUVEAU(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) NOUVEAU(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz)
(II) NOUVEAU(0): Modeline "640x480"x66.7   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) NOUVEAU(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) NOUVEAU(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 489 492 525 -hsync -vsync (31.5 kHz)
(II) NOUVEAU(0): Modeline "720x400"x85.0   35.50  720 756 828 936  400 401 404 446 -hsync +vsync (37.9 kHz)
(II) NOUVEAU(0): Modeline "720x400"x87.8   35.50  720 738 846 900  400 421 423 449 -hsync -vsync (39.4 kHz)
(II) NOUVEAU(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) NOUVEAU(0): Modeline "640x400"x85.1   31.50  640 672 736 832  400 401 404 445 -hsync +vsync (37.9 kHz)
(II) NOUVEAU(0): Modeline "640x350"x85.1   31.50  640 672 736 832  350 382 385 445 +hsync -vsync (37.9 kHz)
(II) NOUVEAU(0): Output VGA-1 connected
(II) NOUVEAU(0): Using exact sizes for initial modes
(II) NOUVEAU(0): Output VGA-1 using initial mode 1920x1440
(II) NOUVEAU(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
(--) NOUVEAU(0): Virtual size is 1920x1440 (pitch 1920)
(**) NOUVEAU(0):  Driver mode "1920x1440": 234.0 MHz (scaled from 0.0 MHz), 90.0 kHz, 60.0 Hz
(II) NOUVEAU(0): Modeline "1920x1440"x60.0  234.00  1920 2048 2256 2600  1440 1441 1444 1500 -hsync +vsync (90.0 kHz)
(**) NOUVEAU(0):  Driver mode "1856x1392": 218.2 MHz (scaled from 0.0 MHz), 86.3 kHz, 60.0 Hz
(II) NOUVEAU(0): Modeline "1856x1392"x60.0  218.25  1856 1952 2176 2528  1392 1393 1396 1439 -hsync +vsync (86.3 kHz)
(**) NOUVEAU(0):  Driver mode "1792x1344": 204.8 MHz (scaled from 0.0 MHz), 83.6 kHz, 60.0 Hz
(II) NOUVEAU(0): Modeline "1792x1344"x60.0  204.75  1792 1920 2120 2448  1344 1345 1348 1394 -hsync +vsync (83.6 kHz)
(**) NOUVEAU(0):  Driver mode "1920x1200": 245.2 MHz (scaled from 0.0 MHz), 94.0 kHz, 74.9 Hz
(II) NOUVEAU(0): Modeline "1920x1200"x74.9  245.25  1920 2056 2264 2608  1200 1203 1209 1255 -hsync +vsync (94.0 kHz)
(**) NOUVEAU(0):  Driver mode "1920x1200": 193.2 MHz (scaled from 0.0 MHz), 74.6 kHz, 59.9 Hz
(II) NOUVEAU(0): Modeline "1920x1200"x59.9  193.25  1920 2056 2256 2592  1200 1203 1209 1245 -hsync +vsync (74.6 kHz)
(**) NOUVEAU(0):  Mode "1600x1200": 206.0 MHz (scaled from 0.0 MHz), 94.0 kHz, 75.0 Hz
(II) NOUVEAU(0): Modeline "1600x1200"x75.0  205.99  1600 1720 1896 2192  1200 1201 1204 1253 -hsync +vsync (94.0 kHz)
(**) NOUVEAU(0):  Driver mode "1600x1200": 189.0 MHz (scaled from 0.0 MHz), 87.5 kHz, 70.0 Hz
(II) NOUVEAU(0): Modeline "1600x1200"x70.0  189.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (87.5 kHz)
(**) NOUVEAU(0):  Driver mode "1600x1200": 175.5 MHz (scaled from 0.0 MHz), 81.2 kHz, 65.0 Hz
(II) NOUVEAU(0): Modeline "1600x1200"x65.0  175.50  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (81.2 kHz)
(**) NOUVEAU(0):  Driver mode "1600x1200": 162.0 MHz (scaled from 0.0 MHz), 75.0 kHz, 60.0 Hz
(II) NOUVEAU(0): Modeline "1600x1200"x60.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz)
(**) NOUVEAU(0):  Driver mode "1680x1050": 214.8 MHz (scaled from 0.0 MHz), 93.9 kHz, 84.9 Hz
(II) NOUVEAU(0): Modeline "1680x1050"x84.9  214.75  1680 1808 1984 2288  1050 1053 1059 1105 -hsync +vsync (93.9 kHz)
(**) NOUVEAU(0):  Driver mode "1680x1050": 187.0 MHz (scaled from 0.0 MHz), 82.3 kHz, 74.9 Hz
(II) NOUVEAU(0): Modeline "1680x1050"x74.9  187.00  1680 1800 1976 2272  1050 1053 1059 1099 -hsync +vsync (82.3 kHz)
(**) NOUVEAU(0):  Driver mode "1680x1050": 146.2 MHz (scaled from 0.0 MHz), 65.3 kHz, 60.0 Hz
(II) NOUVEAU(0): Modeline "1680x1050"x60.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
(**) NOUVEAU(0):  Driver mode "1400x1050": 179.5 MHz (scaled from 0.0 MHz), 93.9 kHz, 85.0 Hz
(II) NOUVEAU(0): Modeline "1400x1050"x85.0  179.50  1400 1504 1656 1912  1050 1053 1057 1105 -hsync +vsync (93.9 kHz)
(**) NOUVEAU(0):  Driver mode "1400x1050": 156.0 MHz (scaled from 0.0 MHz), 82.3 kHz, 74.9 Hz
(II) NOUVEAU(0): Modeline "1400x1050"x74.9  156.00  1400 1504 1648 1896  1050 1053 1057 1099 -hsync +vsync (82.3 kHz)
(**) NOUVEAU(0):  Driver mode "1400x1050": 121.8 MHz (scaled from 0.0 MHz), 65.3 kHz, 60.0 Hz
(II) NOUVEAU(0): Modeline "1400x1050"x60.0  121.75  1400 1488 1632 1864  1050 1053 1057 1089 -hsync +vsync (65.3 kHz)
(**) NOUVEAU(0):  Driver mode "1280x1024": 157.5 MHz (scaled from 0.0 MHz), 91.1 kHz, 85.0 Hz
(II) NOUVEAU(0): Modeline "1280x1024"x85.0  157.50  1280 1344 1504 1728  1024 1025 1028 1072 +hsync +vsync (91.1 kHz)
(**) NOUVEAU(0):  Driver mode "1280x1024": 135.0 MHz (scaled from 0.0 MHz), 80.0 kHz, 75.0 Hz
(II) NOUVEAU(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(**) NOUVEAU(0):  Driver mode "1280x1024": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz
(II) NOUVEAU(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(**) NOUVEAU(0):  Driver mode "1440x900": 157.0 MHz (scaled from 0.0 MHz), 80.4 kHz, 84.8 Hz
(II) NOUVEAU(0): Modeline "1440x900"x84.8  157.00  1440 1544 1696 1952  900 903 909 948 -hsync +vsync (80.4 kHz)
(**) NOUVEAU(0):  Driver mode "1440x900": 136.8 MHz (scaled from 0.0 MHz), 70.6 kHz, 75.0 Hz
(II) NOUVEAU(0): Modeline "1440x900"x75.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz)
(**) NOUVEAU(0):  Driver mode "1440x900": 106.5 MHz (scaled from 0.0 MHz), 55.9 kHz, 59.9 Hz
(II) NOUVEAU(0): Modeline "1440x900"x59.9  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
(**) NOUVEAU(0):  Driver mode "1280x960": 148.5 MHz (scaled from 0.0 MHz), 85.9 kHz, 85.0 Hz
(II) NOUVEAU(0): Modeline "1280x960"x85.0  148.50  1280 1344 1504 1728  960 961 964 1011 +hsync +vsync (85.9 kHz)
(**) NOUVEAU(0):  Driver mode "1280x960": 108.0 MHz (scaled from 0.0 MHz), 60.0 kHz, 60.0 Hz
(II) NOUVEAU(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
(**) NOUVEAU(0):  Driver mode "1360x768": 85.5 MHz (scaled from 0.0 MHz), 47.7 kHz, 60.0 Hz
(II) NOUVEAU(0): Modeline "1360x768"x60.0   85.50  1360 1424 1536 1792  768 771 777 795 +hsync +vsync (47.7 kHz)
(**) NOUVEAU(0):  Driver mode "1280x800": 122.5 MHz (scaled from 0.0 MHz), 71.6 kHz, 84.9 Hz
(II) NOUVEAU(0): Modeline "1280x800"x84.9  122.50  1280 1360 1496 1712  800 803 809 843 -hsync +vsync (71.6 kHz)
(**) NOUVEAU(0):  Driver mode "1280x800": 106.5 MHz (scaled from 0.0 MHz), 62.8 kHz, 74.9 Hz
(II) NOUVEAU(0): Modeline "1280x800"x74.9  106.50  1280 1360 1488 1696  800 803 809 838 -hsync +vsync (62.8 kHz)
(**) NOUVEAU(0):  Driver mode "1280x800": 83.5 MHz (scaled from 0.0 MHz), 49.7 kHz, 59.8 Hz
(II) NOUVEAU(0): Modeline "1280x800"x59.8   83.50  1280 1352 1480 1680  800 803 809 831 +hsync -vsync (49.7 kHz)
(**) NOUVEAU(0):  Mode "1152x864": 119.7 MHz (scaled from 0.0 MHz), 77.2 kHz, 85.1 Hz
(II) NOUVEAU(0): Modeline "1152x864"x85.1  119.74  1152 1224 1352 1552  864 865 868 907 -hsync +vsync (77.2 kHz)
(**) NOUVEAU(0):  Driver mode "1152x864": 108.0 MHz (scaled from 0.0 MHz), 67.5 kHz, 75.0 Hz
(II) NOUVEAU(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(**) NOUVEAU(0):  Driver mode "1280x768": 117.5 MHz (scaled from 0.0 MHz), 68.6 kHz, 84.8 Hz
(II) NOUVEAU(0): Modeline "1280x768"x84.8  117.50  1280 1360 1496 1712  768 771 778 809 -hsync +vsync (68.6 kHz)
(**) NOUVEAU(0):  Driver mode "1280x768": 102.2 MHz (scaled from 0.0 MHz), 60.3 kHz, 74.9 Hz
(II) NOUVEAU(0): Modeline "1280x768"x74.9  102.25  1280 1360 1488 1696  768 771 778 805 +hsync -vsync (60.3 kHz)
(**) NOUVEAU(0):  Driver mode "1280x768": 79.5 MHz (scaled from 0.0 MHz), 47.8 kHz, 59.9 Hz
(II) NOUVEAU(0): Modeline "1280x768"x59.9   79.50  1280 1344 1472 1664  768 771 778 798 -hsync +vsync (47.8 kHz)
(**) NOUVEAU(0):  Driver mode "1024x768": 94.5 MHz (scaled from 0.0 MHz), 68.7 kHz, 85.0 Hz
(II) NOUVEAU(0): Modeline "1024x768"x85.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
(**) NOUVEAU(0):  Driver mode "1024x768": 78.8 MHz (scaled from 0.0 MHz), 60.1 kHz, 75.1 Hz
(II) NOUVEAU(0): Modeline "1024x768"x75.1   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(**) NOUVEAU(0):  Driver mode "1024x768": 78.8 MHz (scaled from 0.0 MHz), 60.0 kHz, 75.0 Hz
(II) NOUVEAU(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(**) NOUVEAU(0):  Driver mode "1024x768": 75.0 MHz (scaled from 0.0 MHz), 56.5 kHz, 70.1 Hz
(II) NOUVEAU(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(**) NOUVEAU(0):  Driver mode "1024x768": 65.0 MHz (scaled from 0.0 MHz), 48.4 kHz, 60.0 Hz
(II) NOUVEAU(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(**) NOUVEAU(0):  Driver mode "1024x768": 44.9 MHz (scaled from 0.0 MHz), 35.5 kHz, 87.0 Hz (I)
(II) NOUVEAU(0): Modeline "1024x768"x87.0   44.90  1024 1032 1208 1264  768 768 772 817 interlace +hsync +vsync (35.5 kHz)
(**) NOUVEAU(0):  Driver mode "1024x768": 44.9 MHz (scaled from 0.0 MHz), 35.5 kHz, 87.0 Hz (I)
(II) NOUVEAU(0): Modeline "1024x768"x87.0   44.90  1024 1032 1208 1264  768 768 776 817 interlace +hsync +vsync (35.5 kHz)
(**) NOUVEAU(0):  Driver mode "832x624": 57.3 MHz (scaled from 0.0 MHz), 49.7 kHz, 74.6 Hz
(II) NOUVEAU(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(**) NOUVEAU(0):  Driver mode "800x600": 56.2 MHz (scaled from 0.0 MHz), 53.7 kHz, 85.1 Hz
(II) NOUVEAU(0): Modeline "800x600"x85.1   56.25  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
(**) NOUVEAU(0):  Driver mode "800x600": 50.0 MHz (scaled from 0.0 MHz), 48.1 kHz, 72.2 Hz
(II) NOUVEAU(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(**) NOUVEAU(0):  Driver mode "800x600": 49.5 MHz (scaled from 0.0 MHz), 46.9 kHz, 75.0 Hz
(II) NOUVEAU(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(**) NOUVEAU(0):  Driver mode "800x600": 40.0 MHz (scaled from 0.0 MHz), 37.9 kHz, 60.3 Hz
(II) NOUVEAU(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(**) NOUVEAU(0):  Driver mode "800x600": 36.0 MHz (scaled from 0.0 MHz), 35.2 kHz, 56.2 Hz
(II) NOUVEAU(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(**) NOUVEAU(0):  Driver mode "848x480": 33.8 MHz (scaled from 0.0 MHz), 31.0 kHz, 60.0 Hz
(II) NOUVEAU(0): Modeline "848x480"x60.0   33.75  848 864 976 1088  480 486 494 517 +hsync +vsync (31.0 kHz)
(**) NOUVEAU(0):  Driver mode "640x480": 36.0 MHz (scaled from 0.0 MHz), 43.3 kHz, 85.0 Hz
(II) NOUVEAU(0): Modeline "640x480"x85.0   36.00  640 696 752 832  480 481 484 509 -hsync -vsync (43.3 kHz)
(**) NOUVEAU(0):  Driver mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.5 kHz, 75.0 Hz
(II) NOUVEAU(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(**) NOUVEAU(0):  Driver mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.9 kHz, 72.8 Hz
(II) NOUVEAU(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(**) NOUVEAU(0):  Driver mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.9 kHz, 72.8 Hz
(II) NOUVEAU(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz)
(**) NOUVEAU(0):  Driver mode "640x480": 30.2 MHz (scaled from 0.0 MHz), 35.0 kHz, 66.7 Hz
(II) NOUVEAU(0): Modeline "640x480"x66.7   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(**) NOUVEAU(0):  Driver mode "640x480": 25.2 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) NOUVEAU(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(**) NOUVEAU(0):  Driver mode "640x480": 25.2 MHz (scaled from 0.0 MHz), 31.5 kHz, 59.9 Hz
(II) NOUVEAU(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 489 492 525 -hsync -vsync (31.5 kHz)
(**) NOUVEAU(0):  Driver mode "720x400": 35.5 MHz (scaled from 0.0 MHz), 37.9 kHz, 85.0 Hz
(II) NOUVEAU(0): Modeline "720x400"x85.0   35.50  720 756 828 936  400 401 404 446 -hsync +vsync (37.9 kHz)
(**) NOUVEAU(0):  Driver mode "720x400": 35.5 MHz (scaled from 0.0 MHz), 39.4 kHz, 87.8 Hz
(II) NOUVEAU(0): Modeline "720x400"x87.8   35.50  720 738 846 900  400 421 423 449 -hsync -vsync (39.4 kHz)
(**) NOUVEAU(0):  Driver mode "720x400": 28.3 MHz (scaled from 0.0 MHz), 31.5 kHz, 70.1 Hz
(II) NOUVEAU(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(**) NOUVEAU(0):  Driver mode "640x400": 31.5 MHz (scaled from 0.0 MHz), 37.9 kHz, 85.1 Hz
(II) NOUVEAU(0): Modeline "640x400"x85.1   31.50  640 672 736 832  400 401 404 445 -hsync +vsync (37.9 kHz)
(**) NOUVEAU(0):  Driver mode "640x350": 31.5 MHz (scaled from 0.0 MHz), 37.9 kHz, 85.1 Hz
(II) NOUVEAU(0): Modeline "640x350"x85.1   31.50  640 672 736 832  350 382 385 445 +hsync -vsync (37.9 kHz)
(**) NOUVEAU(0): Display dimensions: (330, 240) mm
(**) NOUVEAU(0): DPI set to (147, 152)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "exa"
(II) LoadModule: "exa"
(II) Loading /usr/lib/xorg/modules/libexa.so
(II) Module exa: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 2.5.0
    ABI class: X.Org Video Driver, version 6.0
(II) Loading sub module "shadowfb"
(II) LoadModule: "shadowfb"
(II) Loading /usr/lib/xorg/modules/libshadowfb.so
(II) Module shadowfb: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.4
(II) UnloadModule: "nv"
(II) Unloading /usr/lib/xorg/modules/drivers/nv_drv.so
(II) UnloadModule: "vesa"
(II) Unloading /usr/lib/xorg/modules/drivers/vesa_drv.so
(II) UnloadModule: "fbdev"
(II) Unloading /usr/lib/xorg/modules/drivers/fbdev_drv.so
(II) UnloadModule: "fbdevhw"
(II) Unloading /usr/lib/xorg/modules/linux/libfbdevhw.so
(--) Depth 24 pixmap format is 32 bpp
(II) NOUVEAU(0): Opened GPU channel 1
(II) NOUVEAU(0): [DRI2] Setup complete
(EE) NOUVEAU(0): Error allocating scanout buffer: -12

Fatal server error:
AddScreen/ScreenInit failed for driver 0


Please consult the The X.Org Foundation support 
     at [http://wiki.x.org](http://wiki.x.org)
 for help. 
Please also check the log file at "/var/log/Xorg.0.log" for additional information.

 ddxSigGiveUp: Closing log

---

