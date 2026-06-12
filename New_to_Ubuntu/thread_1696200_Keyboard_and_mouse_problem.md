---
title: "Keyboard and mouse problem"
date: 2011-02-27
forum: New to Ubuntu
---

### Post by djuturum on 2011-02-27
I have installed Ubuntu 10.10 on my PC. 
After starting Ubuntu, I don’t doing anything special, just start terminal and type something, cursor was changed into empty rectangle and I can not type anything.
After that, I can not activate any tab from desktop main menu (Applicaton, Places, System), can not shutdown or restart PC.
I have the similar problem if I start web browser and typing in text box.

I found out that:
if I hold down backspace button, I can type in terminal or click tab from desktop menu! I have to hold down backspace for every mouse click or typed letter :)

I started updates, it was not helpful. I repeated installation Ubuntu from beginning, the same situation.

I’m using PS2 keyboard and USB mouse!
System information:
Motherborad: ASRock GE Pro-M2
CPU: Intel Celeron 4A 2.3 GHz
Mem: DDR2


I installed the same version from the same live CD, on my laptop and everything works fine. I was searching trough forum, but I couldn't find something similar!

---

### Post by amsterdamharu on 2011-02-27
If you start up your computer you have a menu where you can choose Ubuntu and Ubuntu recovery? If not press the arrow down key a couple of times while starting up.

When you choose recovery there should be a second menu that contains something with X server, I am sorry but can't remember what it was exactly. There are also drop to root shell and dpkg reconfigure options. Could you choose the X server option and when that's finished reboot to see if that solved anything?

---

### Post by djuturum on 2011-02-27
Thanks amsterdamharu for your effort!

I followed your instructions:

After running in recovery mode, I chose
**failsafeX run in failsafe graphic mode**

Message box appeared with message like: *Your graphic card, screen, input device didn&#8217;t configure properly. You need configure it manually*. I pressed OK
In the next form I have chosen option &#8216;Restart X&#8217;

I restarted ubuntu and start normally.  I tried terminal, web browser and everything looked fine. I was overjoyed!!!!!!!

I tried installing some application (google chrome) by Ubuntu Softare Center and during installation process, form for Authentication was appeared but I could not type password. 
After that I didn&#8217;t click anything on my desktop like before.

I repeated procedure with restart X and for now looks good!
Is there some log file to show me status devices (graphic card, keyboard, mouse)???

---

### Post by amsterdamharu on 2011-02-27
The log file is in /var/log/kern.log but since your keyboard stopped working it will be difficult to read it. You might boot off a live CD then mount the partition where Ubuntu is installed and then check that file.

---

### Post by djuturum on 2011-02-27
I definitely still have a problem with typing. If I typing in web browser cursor just stop with blinking and disappear after a few moments, and I just can not type or do anything with my desktop. 

I opened kern.log but as a beginner I cannot see anything strange :D

Only two sentences with words keyboard and mouse are:
 0.496397] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input2

Feb 27 20:41:28 mk kernel: [    4.028645] input: USB Optical Mouse as /devices/pci0000:00/0000:00:03.1/usb3/3-2/3-2:1.0/input/input3

I can not find any word like error or problem in log file!!!!

---

### Post by amsterdamharu on 2011-02-27
I guess there is no kernel panic so your computer didn't crash, it's just the input under X server doesn't work.


Could you post the following file?
```
/etc/X11/xorg.conf
```

You can do so by copying the following command and post the output or open the file with gedit:
```
cat /etc/X11/xorg.conf
```

---

### Post by djuturum on 2011-02-28
I tried with terminal and here is result:

user@mk:~$ sudo cat /etc/X11/xorg.conf
[sudo] password for user: 
cat: /etc/X11/xorg.conf: No such file or directory
user@mk:~$ 

I tries with GUI and at location /etc/X11/ there are a few files and folders, but there is no file xorg.conf.

I found only xorg.conf.failsafe with content:

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"vesa"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

---

### Post by djuturum on 2011-03-01
Here is my Xorg.0.log file. I don't know is it helpful for find something wrong?
There are a few files in folder "/usr/share/X11/xorg.conf.d"


[    22.322] 
X.Org X Server 1.9.0
Release Date: 2010-08-20
[    22.323] X Protocol Version 11, Revision 0
[    22.323] Build Operating System: Linux 2.6.24-28-server i686 Ubuntu
[    22.323] Current Operating System: Linux mk 2.6.35-25-generic #44-Ubuntu SMP Fri Jan 21 17:40:48 UTC 2011 i686
[    22.323] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-25-generic root=UUID=f0766868-6224-4ee4-95a4-0d6e5bbb104e ro quiet splash
[    22.323] Build Date: 09 January 2011  12:14:58PM
[    22.323] xorg-server 2:1.9.0-0ubuntu7.3 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[    22.323] Current version of pixman: 0.18.4
[    22.323] 	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
[    22.329] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    22.329] (==) Log file: "/var/log/Xorg.0.log", Time: Tue Mar  1 06:45:01 2011
[    22.343] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    22.345] (==) No Layout section.  Using the first Screen section.
[    22.345] (==) No screen section available. Using defaults.
[    22.345] (**) |-->Screen "Default Screen Section" (0)
[    22.345] (**) |   |-->Monitor "<default monitor>"
[    22.345] (==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
[    22.345] (==) Automatically adding devices
[    22.346] (==) Automatically enabling devices
[    22.346] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    22.346] 	Entry deleted from font path.
[    22.346] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[    22.346] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    22.346] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    22.347] (II) Loader magic: 0x81f9b00
[    22.347] (II) Module ABI versions:
[    22.347] 	X.Org ANSI C Emulation: 0.4
[    22.347] 	X.Org Video Driver: 8.0
[    22.347] 	X.Org XInput driver : 11.0
[    22.347] 	X.Org Server Extension : 4.0
[    22.353] (--) PCI:*(0:1:0:0) 1039:6325:1849:6325 rev 0, Mem @ 0xd0000000/134217728, 0xdfee0000/131072, I/O @ 0x0000ac00/128
[    22.353] (WW) Open ACPI failed (/var/run/acpid.socket) (No such file or directory)
[    22.354] (II) LoadModule: "extmod"
[    22.369] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    22.369] (II) Module extmod: vendor="X.Org Foundation"
[    22.369] 	compiled for 1.9.0, module version = 1.0.0
[    22.369] 	Module class: X.Org Server Extension
[    22.370] 	ABI class: X.Org Server Extension, version 4.0
[    22.370] (II) Loading extension MIT-SCREEN-SAVER
[    22.370] (II) Loading extension XFree86-VidModeExtension
[    22.370] (II) Loading extension XFree86-DGA
[    22.370] (II) Loading extension DPMS
[    22.370] (II) Loading extension XVideo
[    22.370] (II) Loading extension XVideo-MotionCompensation
[    22.370] (II) Loading extension X-Resource
[    22.370] (II) LoadModule: "dbe"
[    22.371] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    22.371] (II) Module dbe: vendor="X.Org Foundation"
[    22.371] 	compiled for 1.9.0, module version = 1.0.0
[    22.371] 	Module class: X.Org Server Extension
[    22.371] 	ABI class: X.Org Server Extension, version 4.0
[    22.371] (II) Loading extension DOUBLE-BUFFER
[    22.371] (II) LoadModule: "glx"
[    22.374] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    22.374] (II) Module glx: vendor="X.Org Foundation"
[    22.374] 	compiled for 1.9.0, module version = 1.0.0
[    22.375] 	ABI class: X.Org Server Extension, version 4.0
[    22.375] (==) AIGLX enabled
[    22.375] (II) Loading extension GLX
[    22.375] (II) LoadModule: "record"
[    22.380] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    22.380] (II) Module record: vendor="X.Org Foundation"
[    22.380] 	compiled for 1.9.0, module version = 1.13.0
[    22.380] 	Module class: X.Org Server Extension
[    22.380] 	ABI class: X.Org Server Extension, version 4.0
[    22.381] (II) Loading extension RECORD
[    22.381] (II) LoadModule: "dri"
[    22.381] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    22.382] (II) Module dri: vendor="X.Org Foundation"
[    22.382] 	compiled for 1.9.0, module version = 1.0.0
[    22.382] 	ABI class: X.Org Server Extension, version 4.0
[    22.382] (II) Loading extension XFree86-DRI
[    22.382] (II) LoadModule: "dri2"
[    22.383] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    22.393] (II) Module dri2: vendor="X.Org Foundation"
[    22.394] 	compiled for 1.9.0, module version = 1.2.0
[    22.394] 	ABI class: X.Org Server Extension, version 4.0
[    22.394] (II) Loading extension DRI2
[    22.394] (==) Matched sis as autoconfigured driver 0
[    22.394] (==) Matched vesa as autoconfigured driver 1
[    22.394] (==) Matched fbdev as autoconfigured driver 2
[    22.394] (==) Assigned the driver to the xf86ConfigLayout
[    22.394] (II) LoadModule: "sis"
[    22.395] (II) Loading /usr/lib/xorg/modules/drivers/sis_drv.so
[    22.402] (II) Module sis: vendor="X.Org Foundation"
[    22.403] 	compiled for 1.8.99.905, module version = 0.10.3
[    22.403] 	Module class: X.Org Video Driver
[    22.403] 	ABI class: X.Org Video Driver, version 8.0
[    22.403] (II) LoadModule: "vesa"
[    22.404] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    22.404] (II) Module vesa: vendor="X.Org Foundation"
[    22.404] 	compiled for 1.8.99.905, module version = 2.3.0
[    22.405] 	Module class: X.Org Video Driver
[    22.405] 	ABI class: X.Org Video Driver, version 8.0
[    22.405] (II) LoadModule: "fbdev"
[    22.405] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    22.406] (II) Module fbdev: vendor="X.Org Foundation"
[    22.406] 	compiled for 1.8.99.905, module version = 0.4.2
[    22.406] 	ABI class: X.Org Video Driver, version 8.0
[    22.406] (II) SIS: driver for SiS chipsets: SIS5597/5598, SIS530/620,
	SIS6326/AGP/DVD, SIS300/305, SIS630/730, SIS540, SIS315, SIS315H,
	SIS315PRO/E, SIS550, SIS650/M650/651/740, SIS330(Xabre),
	SIS660/[M]661[F|M]X/[M]670/[M]741[GX]/[M]760[GX]/[M]761[GX]/[M]770[GX],
	SIS340
[    22.407] (II) SIS: driver for XGI chipsets: Volari Z7 (XG20),
	Volari V3XT/V5/V8/Duo (XG40)
[    22.407] (II) VESA: driver for VESA chipsets: vesa
[    22.444] (II) FBDEV: driver for framebuffer: fbdev
[    22.444] (++) using VT number 7

[    22.445] (WW) Falling back to old probe method for sis
[    22.445] (--) Assigning device section with no busID to primary device
[    22.446] (--) Chipset SIS650/M650/651/740 found
[    22.446] (WW) Falling back to old probe method for vesa
[    22.446] (WW) Falling back to old probe method for fbdev
[    22.446] (II) Loading sub module "fbdevhw"
[    22.446] (II) LoadModule: "fbdevhw"
[    22.447] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    22.447] (II) Module fbdevhw: vendor="X.Org Foundation"
[    22.447] 	compiled for 1.9.0, module version = 0.0.2
[    22.447] 	ABI class: X.Org Video Driver, version 8.0
[    22.478] (EE) open /dev/fb0: No such file or directory
[    22.479] (II) SIS(0): SiS driver (2005/09/20-1, compiled for X.org 1.8.99.905)
[    22.479] (II) SIS(0): Copyright (C) 2001-2005 Thomas Winischhofer <thomas@winischhofer.net> and others
[    22.479] (II) SIS(0): *** See [http://www.winischhofer.eu/linuxsisvga.shtml](http://www.winischhofer.eu/linuxsisvga.shtml)
[    22.479] (II) SIS(0): *** for documentation and updates.
[    22.479] (--) SIS(0): sisfb not found
[    22.479] (--) SIS(0): Relocated I/O registers at 0xAC00
[    22.481] (II) Loading sub module "ramdac"
[    22.481] (II) LoadModule: "ramdac"
[    22.481] (II) Module "ramdac" already built-in
[    22.481] (II) SIS(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
[    22.482] (==) SIS(0): Depth 24, (--) framebuffer bpp 32
[    22.482] (==) SIS(0): RGB weight 888
[    22.482] (==) SIS(0): Default visual is TrueColor
[    22.482] (--) SIS(0): Video BIOS version "1.11.19" found (old SiS data layout)
[    22.483] (==) SIS(0): Using XAA acceleration architecture
[    22.483] (==) SIS(0): Using HW cursor
[    22.483] (==) SIS(0): Color HW cursor is enabled
[    22.483] (II) SIS(0): Using VRAM command queue, size 512k
[    22.483] (==) SIS(0): Hotkey display switching is enabled
[    22.483] (II) SIS(0): WARNING: Using the Hotkey might freeze your machine, regardless
[    22.483] (II) SIS(0):          whether enabled or disabled. This is no driver bug.
[    22.483] (==) SIS(0): SiSCtrl utility interface is disabled
[    22.483] (II) SIS(0): For information on SiSCtrl, see
		[http://www.winischhofer.eu/linuxsispart1.shtml#sisctrl](http://www.winischhofer.eu/linuxsispart1.shtml#sisctrl)
[    22.483] (==) SIS(0): DRI disabled
[    22.483] (II) SIS(0): Checking OS for SSE support is not supported in this version of X.org
[    22.512] (II) SIS(0): If your OS supports SSE, set the option "UseSSE" to "on".
[    22.513] (--) SIS(0): DIMM0 is DDR SDRAM
[    22.513] (--) SIS(0): DIMM1 is DDR SDRAM
[    22.513] (--) SIS(0): DIMM2 is not installed
[    22.513] (--) SIS(0): DIMM3 is not installed
[    22.513] (--) SIS(0): DRAM type: DDR SDRAM
[    22.513] (--) SIS(0): Memory clock: 332.892 MHz
[    22.513] (--) SIS(0): DRAM bus width: 64 bit
[    22.513] (--) SIS(0): Linear framebuffer at 0xD0000000
[    22.513] (--) SIS(0): MMIO registers at 0xDFEE0000 (size 64K)
[    22.514] (--) SIS(0): VideoRAM: 65536 KB
[    22.514] (II) SIS(0): Using 64960K of framebuffer memory at offset 0K
[    22.514] (--) SIS(0): SiS650 revision ID 90 (M650 A1 AA)
[    22.514] (--) SIS(0): Hardware supports two video overlays
[    22.514] (==) SIS(0): Using gamma correction (1.0, 1.0, 1.0)
[    22.514] (II) SIS(0): Gamma correction is enabled
[    22.514] (II) SIS(0): Separate Xv gamma correction is disabled
[    22.514] (--) SIS(0): Memory bandwidth at 32 bpp is 665.784 MHz
[    22.514] (II) Loading sub module "ddc"
[    22.514] (II) LoadModule: "ddc"
[    22.514] (II) Module "ddc" already built-in
[    22.839] (--) SIS(0): CRT1 DDC supported
[    22.839] (--) SIS(0): CRT1 DDC level: 2 
[    23.313] (--) SIS(0): CRT1 DDC monitor info: *******************************************
[    23.314] (II) SIS(0): Manufacturer: BTE  Model: 7922  Serial#: 5105
[    23.333] (II) SIS(0): Year: 2002  Week: 31
[    23.333] (II) SIS(0): EDID Version: 1.2
[    23.333] (II) SIS(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
[    23.333] (II) SIS(0): Sync:  Separate
[    23.333] (II) SIS(0): Max Image Size [cm]: horiz.: 32  vert.: 24
[    23.333] (II) SIS(0): Gamma: 2.26
[    23.333] (II) SIS(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
[    23.333] (II) SIS(0): First detailed timing is preferred mode
[    23.333] (II) SIS(0): redX: 0.639 redY: 0.323   greenX: 0.275 greenY: 0.597
[    23.334] (II) SIS(0): blueX: 0.143 blueY: 0.062   whiteX: 0.283 whiteY: 0.296
[    23.334] (II) SIS(0): Supported established timings:
[    23.334] (II) SIS(0): 640x480@60Hz
[    23.334] (II) SIS(0): 640x480@75Hz
[    23.334] (II) SIS(0): 800x600@75Hz
[    23.334] (II) SIS(0): 1024x768@60Hz
[    23.334] (II) SIS(0): 1024x768@75Hz
[    23.334] (II) SIS(0): Manufacturer's mask: 0
[    23.334] (II) SIS(0): Supported standard timings:
[    23.334] (II) SIS(0): #0: hsize: 640  vsize 360  refresh: 70  vid: 51761
[    23.334] (II) SIS(0): #1: hsize: 800  vsize 600  refresh: 85  vid: 22853
[    23.334] (II) SIS(0): #2: hsize: 1024  vsize 768  refresh: 85  vid: 22881
[    23.334] (II) SIS(0): #3: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[    23.334] (II) SIS(0): #4: hsize: 640  vsize 480  refresh: 85  vid: 22833
[    23.335] (II) SIS(0): Supported detailed timing:
[    23.335] (II) SIS(0): clock: 94.5 MHz   Image Size:  310 x 230 mm
[    23.335] (II) SIS(0): h_active: 1024  h_sync: 1072  h_sync_end 1168 h_blank_end 1376 h_border: 0
[    23.335] (II) SIS(0): v_active: 768  v_sync: 769  v_sync_end 772 v_blanking: 808 v_border: 0
[    23.376] (II) SIS(0): Monitor name: Bigtide-CM177
[    23.376] (II) SIS(0): Monitor name: 0MK-
[    23.376] (II) SIS(0): Monitor name: 0000005105
[    23.376] (II) SIS(0): EDID (in hex):
[    23.376] (II) SIS(0): 	1c0000005ca21d0864a74800ffffffff
[    23.376] (II) SIS(0): 	549eabbf48ed40008c3a200878667208
[    23.376] (II) SIS(0): 	0400000060ff1e0800000000089eabbf
[    23.376] (II) SIS(0): 	f40f1f089b9eabbf009d400000000000
[    23.376] (II) SIS(0): 	8a2c0c08f40f1f088b9eabbf4c000000
[    23.376] (II) SIS(0): 	169eabbf9d4f3900899eabbf01000000
[    23.377] (II) SIS(0): 	fffffffff3941e08209eabbfb89eabbf
[    23.377] (II) SIS(0): 	6e230e08819eabbf01000000ffffffff
[    23.377] (II) SIS(0): EDID vendor "BTE", prod id 31010
[    23.377] (II) SIS(0): Printing DDC gathered Modelines:
[    23.377] (II) SIS(0): Modeline "1024x768"x0.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
[    23.377] (II) SIS(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    23.377] (II) SIS(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    23.377] (II) SIS(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    23.377] (II) SIS(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    23.377] (II) SIS(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    23.378] (II) SIS(0): Modeline "640x360"x70.0   20.58  640 648 712 784  360 361 364 375 -hsync +vsync (26.2 kHz)
[    23.378] (II) SIS(0): Modeline "800x600"x0.0   56.25  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
[    23.378] (II) SIS(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    23.378] (II) SIS(0): Modeline "640x480"x0.0   36.00  640 696 752 832  480 481 484 509 -hsync -vsync (43.3 kHz)
[    23.378] (--) SIS(0): According to DDC size, CRT1 aspect ratio is 1.33:1 (normal)
[    23.378] (--) SIS(0): End of CRT1 DDC monitor info *************************************
[    23.378] (==) SIS(0): Min pixel clock is 10 MHz
[    23.378] (--) SIS(0): Max pixel clock is 340 MHz
[    23.378] (II) SIS(0): Replaced default mode list with built-in modes
[    23.379] (II) SIS(0): Using fake widescreen modes for CRT1 VGA devices
[    23.379] (II) SIS(0): 	Use option "ForceCRT1VGAAspect" to overrule
[    23.379] (II) SIS(0): "Unknown reason" in the following list means that the mode
[    23.379] (II) SIS(0): is not supported on the chipset/bridge/current output device.
[    23.379] (II) SIS(0): <default monitor>: Using hsync range of 26.25-68.68 kHz
[    23.379] (II) SIS(0): <default monitor>: Using vrefresh range of 59.94-85.06 Hz
[    23.379] (II) SIS(0): Estimated virtual size for aspect ratio 1.3333 is 1024x768
[    23.379] (II) SIS(0): Clock range:  10.00 to 340.00 MHz
[    23.379] (II) SIS(0): Not using driver mode "1280x1024" (width too large for virtual size)
[    23.379] (II) SIS(0): Not using default mode "800x600" (vrefresh out of range)
[    23.384] (II) SIS(0): Not using default mode "800x600" (vrefresh out of range)
[    23.384] (II) SIS(0): Not using default mode "800x600" (hsync out of range)
[    23.384] (II) SIS(0): Not using default mode "800x600" (hsync out of range)
[    23.384] (II) SIS(0): Not using default mode "640x480" (vrefresh out of range)
[    23.384] (II) SIS(0): Not using default mode "640x480" (vrefresh out of range)
[    23.384] (II) SIS(0): Not using default mode "640x480" (hsync out of range)
[    23.384] (II) SIS(0): Not using default mode "640x480" (hsync out of range)
[    23.384] (II) SIS(0): Not using default mode "1024x768" (vrefresh out of range)
[    23.384] (II) SIS(0): Not using default mode "1024x768" (hsync out of range)
[    23.384] (II) SIS(0): Not using default mode "1024x768" (hsync out of range)
[    23.385] (II) SIS(0): Not using default mode "1280x1024" (width too large for virtual size)
[    23.385] (II) SIS(0): Not using default mode "1280x1024" (width too large for virtual size)
[    23.385] (II) SIS(0): Not using default mode "1280x1024" (width too large for virtual size)
[    23.385] (II) SIS(0): Not using default mode "1280x1024" (width too large for virtual size)
[    23.385] (II) SIS(0): Not using default mode "1600x1200" (width too large for virtual size)
[    23.385] (II) SIS(0): Not using default mode "1600x1200" (width too large for virtual size)
[    23.385] (II) SIS(0): Not using default mode "1600x1200" (width too large for virtual size)
[    23.385] (II) SIS(0): Not using default mode "1600x1200" (width too large for virtual size)
[    23.385] (II) SIS(0): Not using default mode "1600x1200" (width too large for virtual size)
[    23.385] (II) SIS(0): Not using default mode "1600x1200" (width too large for virtual size)
[    23.385] (II) SIS(0): Not using default mode "1600x1200" (width too large for virtual size)
[    23.385] (II) SIS(0): Not using default mode "1920x1440" (width too large for virtual size)
[    23.386] (II) SIS(0): Not using default mode "1920x1440" (width too large for virtual size)
[    23.386] (II) SIS(0): Not using default mode "1920x1440" (width too large for virtual size)
[    23.386] (II) SIS(0): Not using default mode "1920x1440" (width too large for virtual size)
[    23.386] (II) SIS(0): Not using default mode "1920x1440" (width too large for virtual size)
[    23.386] (II) SIS(0): Not using default mode "1920x1440" (width too large for virtual size)
[    23.386] (II) SIS(0): Not using default mode "2048x1536" (width too large for virtual size)
[    23.386] (II) SIS(0): Not using default mode "2048x1536" (width too large for virtual size)
[    23.386] (II) SIS(0): Not using default mode "2048x1536" (width too large for virtual size)
[    23.386] (II) SIS(0): Not using default mode "2048x1536" (width too large for virtual size)
[    23.386] (II) SIS(0): Not using default mode "2048x1536" (width too large for virtual size)
[    23.386] (II) SIS(0): Not using default mode "1024x576" (hsync out of range)
[    23.386] (II) SIS(0): Not using default mode "1280x720" (width too large for virtual size)
[    23.386] (II) SIS(0): Not using default mode "1280x720" (width too large for virtual size)
[    23.386] (II) SIS(0): Not using default mode "1280x720" (width too large for virtual size)
[    23.386] (II) SIS(0): Not using default mode "1280x960" (width too large for virtual size)
[    23.387] (II) SIS(0): Not using default mode "1280x960" (width too large for virtual size)
[    23.387] (II) SIS(0): Not using default mode "1280x768" (width too large for virtual size)
[    23.387] (II) SIS(0): Not using default mode "1280x768" (width too large for virtual size)
[    23.387] (II) SIS(0): Not using default mode "1280x768" (width too large for virtual size)
[    23.387] (II) SIS(0): Not using default mode "1400x1050" (width too large for virtual size)
[    23.387] (II) SIS(0): Not using default mode "1400x1050" (width too large for virtual size)
[    23.387] (II) SIS(0): Not using default mode "1152x864" (width too large for virtual size)
[    23.387] (II) SIS(0): Not using default mode "1152x864" (width too large for virtual size)
[    23.387] (II) SIS(0): Not using default mode "1152x864" (width too large for virtual size)
[    23.392] (II) SIS(0): Not using default mode "1360x768" (width too large for virtual size)
[    23.392] (II) SIS(0): Not using default mode "1280x800" (width too large for virtual size)
[    23.392] (II) SIS(0): Not using default mode "1280x800" (width too large for virtual size)
[    23.392] (II) SIS(0): Not using default mode "1280x800" (width too large for virtual size)
[    23.392] (II) SIS(0): Not using default mode "1680x1050" (width too large for virtual size)
[    23.392] (II) SIS(0): Not using default mode "1920x1080" (width too large for virtual size)
[    23.392] (II) SIS(0): Not using default mode "1280x854" (width too large for virtual size)
[    23.392] (II) SIS(0): Not using default mode "1280x854" (width too large for virtual size)
[    23.392] (II) SIS(0): Not using default mode "1280x854" (width too large for virtual size)
[    23.393] (--) SIS(0): Virtual size is 1024x768 (pitch 1024)
[    23.393] (**) SIS(0): *Driver mode "1024x768": 94.5 MHz, 68.7 kHz, 85.0 Hz
[    23.393] (II) SIS(0): Modeline "1024x768"x85.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
[    23.393] (**) SIS(0): *Driver mode "1024x768": 78.8 MHz, 60.0 kHz, 75.0 Hz
[    23.393] (II) SIS(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    23.393] (**) SIS(0): *Driver mode "1024x768": 65.0 MHz, 48.4 kHz, 60.0 Hz
[    23.393] (II) SIS(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    23.393] (**) SIS(0): *Default mode "1024x768": 94.5 MHz, 68.7 kHz, 85.0 Hz
[    23.394] (II) SIS(0): Modeline "1024x768"x85.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
[    23.394] (**) SIS(0): *Default mode "1024x768": 78.7 MHz, 60.0 kHz, 75.0 Hz
[    23.394] (II) SIS(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    23.394] (**) SIS(0): *Default mode "1024x768": 75.2 MHz, 56.6 kHz, 70.2 Hz
[    23.394] (II) SIS(0): Modeline "1024x768"x70.2   75.17  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.6 kHz)
[    23.394] (**) SIS(0): *Default mode "1024x768": 65.1 MHz, 48.5 kHz, 60.1 Hz
[    23.394] (II) SIS(0): Modeline "1024x768"x60.1   65.15  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.5 kHz)
[    23.395] (**) SIS(0): *Default mode "1024x576": 78.7 MHz, 60.0 kHz, 75.0 Hz
[    23.395] (II) SIS(0): Modeline "1024x576"x75.0   78.75  1024 1040 1136 1312  576 686 690 800 +hsync +vsync (60.0 kHz)
[    23.395] (**) SIS(0): *Default mode "1024x576": 65.1 MHz, 48.5 kHz, 60.1 Hz
[    23.395] (II) SIS(0): Modeline "1024x576"x60.1   65.15  1024 1048 1184 1344  576 688 694 806 +hsync +vsync (48.5 kHz)
[    23.395] (**) SIS(0): *Default mode "960x600": 41.5 MHz, 37.1 kHz, 60.0 Hz
[    23.395] (II) SIS(0): Modeline "960x600"x60.0   41.50  960 1008 1088 1120  600 603 609 618 +hsync +vsync (37.1 kHz)
[    23.395] (**) SIS(0): *Default mode "960x540": 37.3 MHz, 33.8 kHz, 60.0 Hz
[    23.395] (II) SIS(0): Modeline "960x540"x60.0   37.29  960 976 1008 1104  540 543 549 563 +hsync +vsync (33.8 kHz)
[    23.395] (**) SIS(0): *Driver mode "800x600": 56.2 MHz, 53.7 kHz, 85.1 Hz
[    23.395] (II) SIS(0): Modeline "800x600"x85.1   56.25  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
[    23.396] (**) SIS(0): *Driver mode "800x600": 49.5 MHz, 46.9 kHz, 75.0 Hz
[    23.396] (II) SIS(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    23.396] (**) SIS(0): *Default mode "800x600": 56.2 MHz, 53.7 kHz, 85.1 Hz
[    23.396] (II) SIS(0): Modeline "800x600"x85.1   56.25  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
[    23.396] (**) SIS(0): *Default mode "800x600": 49.5 MHz, 46.9 kHz, 75.0 Hz
[    23.396] (II) SIS(0): Modeline "800x600"x75.0   49.52  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    23.396] (**) SIS(0): *Default mode "800x600": 50.1 MHz, 48.2 kHz, 72.4 Hz
[    23.396] (II) SIS(0): Modeline "800x600"x72.4   50.11  800 856 976 1040  600 637 643 666 +hsync +vsync (48.2 kHz)
[    23.396] (**) SIS(0): *Default mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
[    23.396] (II) SIS(0): Modeline "800x600"x60.3   39.97  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    23.396] (**) SIS(0): *Default mode "768x576": 35.0 MHz, 35.9 kHz, 60.1 Hz
[    23.397] (II) SIS(0): Modeline "768x576"x60.1   35.00  768 792 872 976  576 578 581 597 +hsync +vsync (35.9 kHz)
[    23.397] (**) SIS(0): *Default mode "720x576": 32.7 MHz, 35.9 kHz, 60.1 Hz
[    23.397] (II) SIS(0): Modeline "720x576"x60.1   32.73  720 744 816 912  576 578 581 597 +hsync +vsync (35.9 kHz)
[    23.397] (**) SIS(0): *Default mode "856x480": 33.9 MHz, 31.7 kHz, 59.8 Hz
[    23.397] (II) SIS(0): Modeline "856x480"x59.8   33.94  856 872 1000 1072  480 492 495 529 -hsync -vsync (31.7 kHz)
[    23.397] (**) SIS(0): *Default mode "856x480": 33.9 MHz, 30.5 kHz, 76.5 Hz (I)
[    23.397] (II) SIS(0): Modeline "856x480"x76.5   33.94  856 904 1048 1112  480 672 680 797 interlace +hsync +vsync (30.5 kHz)
[    23.397] (**) SIS(0): *Default mode "848x480": 33.7 MHz, 31.0 kHz, 60.0 Hz
[    23.397] (II) SIS(0): Modeline "848x480"x60.0   33.75  848 864 976 1088  480 486 494 517 -hsync -vsync (31.0 kHz)
[    23.397] (**) SIS(0): *Default mode "848x480": 33.9 MHz, 30.5 kHz, 76.5 Hz (I)
[    23.398] (II) SIS(0): Modeline "848x480"x76.5   33.94  848 904 1048 1112  480 672 680 797 interlace +hsync +vsync (30.5 kHz)
[    23.398] (**) SIS(0): *Default mode "800x480": 56.2 MHz, 53.7 kHz, 85.2 Hz
[    23.398] (II) SIS(0): Modeline "800x480"x85.2   56.25  800 832 896 1048  480 554 557 630 +hsync +vsync (53.7 kHz)
[    23.398] (**) SIS(0): *Default mode "800x480": 49.5 MHz, 46.9 kHz, 75.1 Hz
[    23.398] (II) SIS(0): Modeline "800x480"x75.1   49.52  800 816 896 1056  480 551 554 624 +hsync +vsync (46.9 kHz)
[    23.398] (**) SIS(0): *Default mode "800x480": 39.8 MHz, 37.7 kHz, 60.0 Hz
[    23.398] (II) SIS(0): Modeline "800x480"x60.0   39.77  800 840 968 1056  480 552 556 628 +hsync +vsync (37.7 kHz)
[    23.398] (**) SIS(0): *Default mode "720x480": 28.3 MHz, 31.6 kHz, 61.0 Hz
[    23.398] (II) SIS(0): Modeline "720x480"x61.0   28.28  720 728 840 896  480 490 492 517 -hsync -vsync (31.6 kHz)
[    23.398] (**) SIS(0): *Driver mode "640x480": 36.0 MHz, 43.3 kHz, 85.0 Hz
[    23.398] (II) SIS(0): Modeline "640x480"x85.0   36.00  640 696 752 832  480 481 484 509 -hsync -vsync (43.3 kHz)
[    23.398] (**) SIS(0): *Driver mode "640x480": 31.5 MHz, 37.5 kHz, 75.0 Hz
[    23.399] (II) SIS(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    23.399] (**) SIS(0): *Driver mode "640x480": 25.2 MHz, 31.5 kHz, 59.9 Hz
[    23.399] (II) SIS(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    23.399] (**) SIS(0): *Default mode "640x480": 36.1 MHz, 43.3 kHz, 85.1 Hz
[    23.399] (II) SIS(0): Modeline "640x480"x85.1   36.06  640 696 752 832  480 481 484 509 -hsync -vsync (43.3 kHz)
[    23.399] (**) SIS(0): *Default mode "640x480": 31.5 MHz, 37.5 kHz, 75.0 Hz
[    23.399] (II) SIS(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    23.399] (**) SIS(0): *Default mode "640x480": 31.5 MHz, 37.9 kHz, 72.8 Hz
[    23.399] (II) SIS(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz)
[    23.399] (**) SIS(0): *Default mode "640x480": 25.1 MHz, 31.3 kHz, 59.7 Hz
[    23.408] (II) SIS(0): Modeline "640x480"x59.7   25.06  640 656 752 800  480 490 492 525 -hsync -vsync (31.3 kHz)
[    23.408] (**) SIS(0): *Default mode "640x400": 25.1 MHz, 31.6 kHz, 71.6 Hz
[    23.408] (II) SIS(0): Modeline "640x400"x71.6   25.06  640 656 752 792  400 413 415 442 -hsync +vsync (31.6 kHz)
[    23.408] (**) SIS(0): *Driver mode "640x360": 20.6 MHz, 26.2 kHz, 70.0 Hz
[    23.408] (II) SIS(0): Modeline "640x360"x70.0   20.58  640 648 712 784  360 361 364 375 -hsync +vsync (26.2 kHz)
[    23.408] (**) SIS(0): *Default mode "512x384": 32.6 MHz, 48.5 kHz, 60.1 Hz (D)
[    23.408] (II) SIS(0): Modeline "512x384"x60.1   32.57  512 528 592 672  384 385 388 403 doublescan -hsync -vsync (48.5 kHz)
[    23.408] (**) SIS(0): *Default mode "400x300": 20.0 MHz, 37.9 kHz, 60.3 Hz (D)
[    23.408] (II) SIS(0): Modeline "400x300"x60.3   19.98  400 416 480 528  300 300 302 314 doublescan +hsync +vsync (37.9 kHz)
[    23.408] (**) SIS(0): *Default mode "320x240": 12.5 MHz, 31.3 kHz, 60.7 Hz (D)
[    23.409] (II) SIS(0): Modeline "320x240"x60.7   12.53  320 328 376 400  240 245 246 258 doublescan -hsync -vsync (31.3 kHz)
[    23.409] (**) SIS(0): *Default mode "320x200": 12.5 MHz, 31.3 kHz, 70.9 Hz (D)
[    23.409] (II) SIS(0): Modeline "320x200"x70.9   12.53  320 328 376 400  200 206 207 221 doublescan -hsync +vsync (31.3 kHz)
[    23.409] (**) SIS(0): Display dimensions: (320, 240) mm
[    23.409] (**) SIS(0): DPI set to (81, 81)
[    23.409] (II) Loading sub module "fb"
[    23.409] (II) LoadModule: "fb"
[    23.410] (II) Loading /usr/lib/xorg/modules/libfb.so
[    23.410] (II) Module fb: vendor="X.Org Foundation"
[    23.410] 	compiled for 1.9.0, module version = 1.0.0
[    23.410] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    23.410] (II) Loading sub module "xaa"
[    23.410] (II) LoadModule: "xaa"
[    23.411] (II) Loading /usr/lib/xorg/modules/libxaa.so
[    23.416] (II) Module xaa: vendor="X.Org Foundation"
[    23.416] 	compiled for 1.9.0, module version = 1.2.1
[    23.416] 	ABI class: X.Org Video Driver, version 8.0
[    23.416] (II) SIS(0): 2D acceleration enabled
[    23.416] (II) UnloadModule: "vesa"
[    23.416] (II) Unloading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    23.416] (II) UnloadModule: "fbdev"
[    23.417] (II) Unloading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    23.417] (II) UnloadModule: "fbdevhw"
[    23.417] (II) Unloading /usr/lib/xorg/modules/libfbdevhw.so
[    23.417] (--) Depth 24 pixmap format is 32 bpp
[    23.417] (II) Loading sub module "vbe"
[    23.417] (II) LoadModule: "vbe"
[    23.418] (II) Loading /usr/lib/xorg/modules/libvbe.so
[    23.418] (II) Module vbe: vendor="X.Org Foundation"
[    23.418] 	compiled for 1.9.0, module version = 1.1.0
[    23.418] 	ABI class: X.Org Video Driver, version 8.0
[    23.418] (II) Loading sub module "int10"
[    23.418] (II) LoadModule: "int10"
[    23.419] (II) Loading /usr/lib/xorg/modules/libint10.so
[    23.424] (II) Module int10: vendor="X.Org Foundation"
[    23.424] 	compiled for 1.9.0, module version = 1.0.0
[    23.424] 	ABI class: X.Org Video Driver, version 8.0
[    23.424] (II) SIS(0): initializing int10
[    23.425] (II) SIS(0): Primary V_BIOS segment is: 0xc000
[    23.426] (II) SIS(0): VESA BIOS detected
[    23.426] (II) SIS(0): VESA VBE Version 3.0
[    23.426] (II) SIS(0): VESA VBE Total Mem: 65472 kB
[    23.426] (II) SIS(0): VESA VBE OEM: SiS
[    23.427] (II) SIS(0): VESA VBE OEM Software Rev: 1.0
[    23.427] (II) SIS(0): VESA VBE OEM Vendor: Silicon Integrated Systems Corp.
[    23.427] (II) SIS(0): VESA VBE OEM Product: 6325
[    23.427] (II) SIS(0): VESA VBE OEM Product Rev: 1.11.19
[    23.488] (II) SIS(0): Setting custom mode 1024x768 on CRT1
[    23.497] (II) SIS(0): Setting custom mode 1024x768 on CRT2
[    23.498] (II) SIS(0): RENDER acceleration enabled
[    23.498] (II) SIS(0): Framebuffer from (0,0) to (1023,16238)
[    23.499] (II) SIS(0): Using XFree86 Acceleration Architecture (XAA)
[    23.499] 	Screen to screen bit blits
[    23.499] 	Solid filled rectangles
[    23.499] 	8x8 mono pattern filled rectangles
[    23.499] 	8x8 color pattern filled rectangles
[    23.499] 	Solid Lines
[    23.499] 	Dashed Lines
[    23.505] 	Setting up tile and stipple cache:
[    23.505] 		32 128x128 slots
[    23.505] 		32 256x256 slots
[    23.505] 		16 512x512 slots
[    23.505] 		32 8x8 color pattern slots
[    23.505] (--) SIS(0): CPU frequency 2375.42Mhz
[    23.512] (II) SIS(0): Benchmarking system RAM to video RAM memory transfer methods:
[    23.529] (--) SIS(0): 	Checked libc memcpy()... 	460.3 MiB/s
[    23.548] (--) SIS(0): 	Checked built-in-1 memcpy()... 	448.7 MiB/s
[    23.622] (--) SIS(0): 	Checked built-in-2 memcpy()... 	48.2 MiB/s
[    23.632] (--) SIS(0): 	Checked MMX memcpy()... 	455.5 MiB/s
[    23.647] (--) SIS(0): 	Checked MMX2 memcpy()... 	486.6 MiB/s
[    23.658] (--) SIS(0): Using MMX2 method for aligned data transfers to video RAM
[    23.659] (--) SIS(0): Using MMX2 method for unaligned data transfers to video RAM
[    23.659] (==) SIS(0): Backing store disabled
[    23.659] (==) SIS(0): Silken mouse enabled
[    23.659] (==) SIS(0): DPMS enabled
[    23.659] (II) SIS(0): Using SiS300/315/330/340 series HW Xv
[    23.660] (II) SIS(0): Default Xv adaptor is Video Overlay
[    23.674] (II) SIS(0): Initialized SISCTRL extension version 0.1
[    23.675] (II) SIS(0): Registered screen 0 with SISCTRL extension version 0.1
[    23.675] (==) RandR enabled
[    23.675] (II) Initializing built-in extension Generic Event Extension
[    23.675] (II) Initializing built-in extension SHAPE
[    23.675] (II) Initializing built-in extension MIT-SHM
[    23.675] (II) Initializing built-in extension XInputExtension
[    23.675] (II) Initializing built-in extension XTEST
[    23.675] (II) Initializing built-in extension BIG-REQUESTS
[    23.675] (II) Initializing built-in extension SYNC
[    23.675] (II) Initializing built-in extension XKEYBOARD
[    23.675] (II) Initializing built-in extension XC-MISC
[    23.675] (II) Initializing built-in extension SECURITY
[    23.675] (II) Initializing built-in extension XINERAMA
[    23.681] (II) Initializing built-in extension XFIXES
[    23.681] (II) Initializing built-in extension RENDER
[    23.681] (II) Initializing built-in extension RANDR
[    23.681] (II) Initializing built-in extension COMPOSITE
[    23.681] (II) Initializing built-in extension DAMAGE
[    23.681] (II) Initializing built-in extension GESTURE
[    23.709] (II) AIGLX: Screen 0 is not DRI2 capable
[    23.709] (II) AIGLX: Screen 0 is not DRI capable
[    23.764] (II) AIGLX: Loaded and initialized /usr/lib/dri/swrast_dri.so
[    23.765] (II) GLX: Initialized DRISWRAST GL provider for screen 0
[    23.888] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    23.916] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    23.916] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    23.916] (II) LoadModule: "evdev"
[    23.917] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    23.918] (II) Module evdev: vendor="X.Org Foundation"
[    23.918] 	compiled for 1.9.0, module version = 2.3.2
[    23.919] 	Module class: X.Org XInput Driver
[    23.919] 	ABI class: X.Org XInput driver, version 11.0
[    23.919] (**) Power Button: always reports core events
[    23.919] (**) Power Button: Device: "/dev/input/event1"
[    23.919] (II) Power Button: Found keys
[    23.919] (II) Power Button: Configuring as keyboard
[    23.919] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    23.919] (**) Option "xkb_rules" "evdev"
[    23.920] (**) Option "xkb_model" "pc105"
[    23.920] (**) Option "xkb_layout" "us"
[    23.924] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    23.924] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    23.925] (**) Power Button: always reports core events
[    23.957] (**) Power Button: Device: "/dev/input/event0"
[    23.957] (II) Power Button: Found keys
[    23.957] (II) Power Button: Configuring as keyboard
[    23.957] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    23.958] (**) Option "xkb_rules" "evdev"
[    23.958] (**) Option "xkb_model" "pc105"
[    23.958] (**) Option "xkb_layout" "us"
[    23.996] (II) config/udev: Adding input device USB Optical Mouse (/dev/input/event3)
[    23.996] (**) USB Optical Mouse: Applying InputClass "evdev pointer catchall"
[    23.996] (**) USB Optical Mouse: always reports core events
[    23.996] (**) USB Optical Mouse: Device: "/dev/input/event3"
[    23.996] (II) USB Optical Mouse: Found 3 mouse buttons
[    23.996] (II) USB Optical Mouse: Found scroll wheel(s)
[    23.997] (II) USB Optical Mouse: Found relative axes
[    23.997] (II) USB Optical Mouse: Found x and y relative axes
[    23.997] (II) USB Optical Mouse: Found absolute axes
[    23.997] (II) evdev-grail: failed to open grail, no gesture support
[    23.997] (II) USB Optical Mouse: Configuring as mouse
[    23.997] (**) USB Optical Mouse: YAxisMapping: buttons 4 and 5
[    23.997] (**) USB Optical Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    23.997] (II) XINPUT: Adding extended input device "USB Optical Mouse" (type: MOUSE)
[    23.998] (II) USB Optical Mouse: initialized for relative axes.
[    23.998] (WW) USB Optical Mouse: ignoring absolute axes.
[    23.999] (II) config/udev: Adding input device USB Optical Mouse (/dev/input/mouse0)
[    24.006] (II) No input driver/identifier specified (ignoring)
[    24.011] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event2)
[    24.015] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    24.016] (**) AT Translated Set 2 keyboard: always reports core events
[    24.016] (**) AT Translated Set 2 keyboard: Device: "/dev/input/event2"
[    24.016] (II) AT Translated Set 2 keyboard: Found keys
[    24.016] (II) AT Translated Set 2 keyboard: Configuring as keyboard
[    24.016] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
[    24.016] (**) Option "xkb_rules" "evdev"
[    24.016] (**) Option "xkb_model" "pc105"
[    24.017] (**) Option "xkb_layout" "us"

---

