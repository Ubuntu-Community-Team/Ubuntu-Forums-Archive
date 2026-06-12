---
title: "NVIDIA display settings are not maintained"
date: 2010-03-18
forum: New to Ubuntu
---

### Post by dancar22 on 2010-03-18
Each time I turn on my computer, the display resolution settings revert to a 1024 x 760.  I then open the NVIDIA hardware driver and adjust the resolution to 1280 X 1024 which looks perfect.  However, every time I restart the computer, the display has reverted to 1024 x 760.  Is there any way to make the change to 1280 X 1024 permanent?  Thank you for your help.

Dan

---

### Post by patchwork on 2010-03-18
Open the setting manager with

```
gksu nvidia-settings
```

in the terminal and retry.

This will open the settings GUI as superuser, and allow the setting to be saved in the root filesystem.

---

### Post by dancar22 on 2010-03-18
Thank you so much.  I will give it a try.

Dan

---

### Post by dancar22 on 2010-03-18
I logged into the terminal as instructed and changed the settings to 1280 x 1024 but when I restarted the computer, the screen resolution reverted back to 1024 x 780.  Not sure why the setting won't persist when the computer is restarted.

Dan

---

### Post by patchwork on 2010-03-18
Can you post your /var/log/Xorg.0.log ?

---

### Post by dancar22 on 2010-03-18
Not sure how to post the log.  Sorry, I am a newbie.

Dan

---

### Post by e-Gee on 2010-03-18
after you put resolution you want with gksu nvidia-setting you have to save it to xconfig file type in terminal sudo nvidia-xconfig

---

### Post by patchwork on 2010-03-18
```
gedit /var/log/Xorg.0.log
```Copy the log, and paste it into reply dialog box.  Select the text in the dialog box, and click on the # icon on the toolbar for the reply dialog box.  This will put the log into a scrollable code block when you post.



EDIT:    ......yes, x config....I forgot about that!

---

### Post by GSF1200S on 2010-03-18
It angers me that nvidia-settings has STILL not been setup to automatically launch with gksudo..

You must open nvidia-settings as root, and you must always Save to X Configuration File in order for changes to persist.

You shouldnt even have to use nvidia-xconfig if nvidia-settings is opened as root and you specify it to save the changes to X Configuration File (which is /etc/X11/xorg.conf)

---

### Post by dancar22 on 2010-03-18
richardson@richardson:~$ gksu nvidia-settings

VALIDATION ERROR:  Data incomplete in file /etc/X11/xorg.conf.
Undefined Device "(null)" referenced by Screen "Default Screen".

richardson@richardson:~$ gksu nvidia-settings
richardson@richardson:~$ sudo nvidia-xconfig

Using X configuration file: "/etc/X11/xorg.conf".

VALIDATION ERROR: Data incomplete in file /etc/X11/xorg.conf.
                  Undefined Device "(null)" referenced by Screen "Default
                  Screen".

Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'

richardson@richardson:~$ 

Not sure what this all means.

Dan

---

### Post by patchwork on 2010-03-18
Long story short you now have a new configuration file for your x server (GUI).  Restart the x server and see if your settings have been updated.

---

### Post by e-Gee on 2010-03-18
restart your computer and if resolution is not changed try again

---

### Post by dancar22 on 2010-03-18
Still keep reverting back to old setting.  Could it be saving to an improperly designated xconfig file or is their only one?

Dan

---

### Post by e-Gee on 2010-03-18
You can also save it to x config by pressing this button

---

### Post by dancar22 on 2010-03-18
I tried it that way too but it still reverts back to the old settings.

Dan

---

### Post by patchwork on 2010-03-18
The only active x configuration file is /etc/X11/xorg.conf

There will be additional files, such as /etc/X11/xorg.conf.failsafe, and a backup, but only the main xorg.conf is read on startup unless the failsafe is needed.

The x server will choose the 'best' validated mode on startup, but the chosen mode may not always be the highest resolution (may instead be the highest refresh rate).

If you read your /var/log/Xorg.0.log, you will see the decision making process somewhere near the middle of the log, and possibly the reason why the lower resolution was selected.

With the nvidia driver, you can add a line to your xorg.conf containing your preferred mode, which may work if the lower resolution is being selected for no other reason than the x server likes it better.

If you're having trouble finding the problem, please post your log so that we can see it.

---

### Post by dancar22 on 2010-03-18
Sorry, but I have just about taken a sledgehammer to this thing.  When I type in to get the log, it is a complete blank.  When I save the xconfig file, it say it has been saved.  But when I start up the computer it reverts right back to the same settings.  I appreciate all the help, but I really don't understand why it started doing this.  It maintained the 1280 x 1024 settings without fail until about two weeks ago and then just suddenly one day just kept reverting back to the 1024 x 760.  I think I am going to call it a day because I can't even get the log to come up.

Dan

---

### Post by patchwork on 2010-03-18
You can also navigate to the log through 

Places > Computer >Filesystem > var > log

and click on the Xorg.0.log.  This will open the log in your text editor.

---

### Post by dancar22 on 2010-03-18
```
X.Org X Server 1.6.4
Release Date: 2009-9-27
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux richardson 2.6.31-20-generic #57-Ubuntu SMP Mon Feb 8 09:05:19 UTC 2010 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-20-generic root=UUID=c2617d3d-af78-4784-8338-6b7ff44f53fb ro quiet splash
Build Date: 14 November 2009  05:48:26PM
xorg-server 2:1.6.4-2ubuntu4.1 (buildd@) 
    Before reporting problems, check [http://wiki.x.org]("http://wiki.x.org/")
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Thu Mar 18 18:54:11 2010
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Layout0"
(**) |-->Screen "Screen0" (0)
(**) |   |-->Monitor "Monitor0"
(**) |   |-->Device "Device0"
(**) |-->Input Device "Keyboard0"
(**) |-->Input Device "Mouse0"
(**) Option "Xinerama" "0"
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
(WW) AllowEmptyInput is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
(WW) Disabling Keyboard0
(WW) Disabling Mouse0
(II) Loader magic: 0x3bc0
(II) Module ABI versions:
    X.Org ANSI C Emulation: 0.4
    X.Org Video Driver: 5.0
    X.Org XInput driver : 4.0
    X.Org Server Extension : 2.0
(II) Loader running on linux
(++) using VT number 7

(--) PCI:*(0:2:0:0) 10de:01f0:1509:904d nVidia Corporation NV18 [GeForce4 MX - nForce GPU] rev 163, Mem @ 0xea000000/16777216, 0xe0000000/67108864, 0xe4000000/524288, BIOS @ 0x????????/131072
(II) Open ACPI successful (/var/run/acpid.socket)
(II) System resource ranges:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [4] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [5] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
(II) "extmod" will be loaded. This was enabled by default and also specified in the config file.
(II) "dbe" will be loaded. This was enabled by default and also specified in the config file.
(II) "glx" will be loaded. This was enabled by default and also specified in the config file.
(II) "record" will be loaded by default.
(II) "dri" will be loaded by default.
(II) "dri2" will be loaded by default.
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "type1"
(WW) Warning, couldn't open module type1
(II) UnloadModule: "type1"
(EE) Failed to load module "type1" (module does not exist, 0)
(II) LoadModule: "freetype"
(WW) Warning, couldn't open module freetype
(II) UnloadModule: "freetype"
(EE) Failed to load module "freetype" (module does not exist, 0)
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
    compiled for 4.0.2, module version = 1.0.0
    Module class: X.Org Server Extension
(II) NVIDIA GLX Module  96.43.13  Thu Jun 25 18:56:56 PDT 2009
(II) Loading extension GLX
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 1.13.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 1.0.0
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions//libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 1.1.0
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
    compiled for 4.0.2, module version = 1.0.0
    Module class: X.Org Video Driver
(II) NVIDIA dlloader X Driver  96.43.13  Thu Jun 25 18:45:26 PDT 2009
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 02@00:00:0
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(II) resource ranges after probing:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [4] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [5] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "TwinView" "0"
(**) NVIDIA(0): Option "MetaModes" "1280x1024 +0+0; 800x600 +0+0; 640x480 +0+0"
(**) NVIDIA(0): Option "TwinViewXineramaInfoOrder" "CRT-0"
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(II) NVIDIA(0): NVIDIA GPU GeForce4 MX Integrated GPU at PCI:2:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 65536 kBytes
(--) NVIDIA(0): VideoBIOS: 04.1f.00.08.09
(II) NVIDIA(0): Detected AGP rate: 4X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce4 MX Integrated GPU at
(--) NVIDIA(0):     PCI:2:0:0:
(--) NVIDIA(0):     EMA eView 17f3 (CRT-0)
(--) NVIDIA(0): EMA eView 17f3 (CRT-0): 300.0 MHz maximum pixel clock
(II) NVIDIA(0): Assigned Display Device: CRT-0
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "1280x1024+0+0"
(II) NVIDIA(0):     "800x600+0+0"
(II) NVIDIA(0):     "640x480+0+0"
(II) NVIDIA(0): Virtual screen size determined to be 1280 x 1024
(WW) NVIDIA(0): Insufficient memory bandwidth for MetaMode "800x512";
(WW) NVIDIA(0):     discarding.
(WW) NVIDIA(0): No valid modes for "800x512"; removing.
(--) NVIDIA(0): DPI set to (101, 108); computed from "UseEdidDpi" X config
(--) NVIDIA(0):     option
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [4] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [5] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
(II) NVIDIA(0): Initialized GART.
(II) NVIDIA(0): Setting mode "1280x1024+0+0"
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(**) Option "dpms"
(**) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
(==) RandR enabled
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
(II) Initializing extension GLX
(II) config/hal: Adding input device Power Button
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 2.2.5
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 4.0
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event1"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/hal: Adding input device Power Button
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event0"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/hal: Adding input device AT Translated Set 2 keyboard
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event3"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/hal: Adding input device ImExPS/2 Generic Explorer Mouse
(**) ImExPS/2 Generic Explorer Mouse: always reports core events
(**) ImExPS/2 Generic Explorer Mouse: Device: "/dev/input/event4"
(II) ImExPS/2 Generic Explorer Mouse: Found 9 mouse buttons
(II) ImExPS/2 Generic Explorer Mouse: Found x and y relative axes
(II) ImExPS/2 Generic Explorer Mouse: Found scroll wheel(s)
(II) ImExPS/2 Generic Explorer Mouse: Configuring as mouse
(**) ImExPS/2 Generic Explorer Mouse: YAxisMapping: buttons 4 and 5
(**) ImExPS/2 Generic Explorer Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "ImExPS/2 Generic Explorer Mouse" (type: MOUSE)
(**) ImExPS/2 Generic Explorer Mouse: (accel) keeping acceleration scheme 1
(**) ImExPS/2 Generic Explorer Mouse: (accel) filter chain progression: 2.00
(**) ImExPS/2 Generic Explorer Mouse: (accel) filter stage 0: 20.00 ms
(**) ImExPS/2 Generic Explorer Mouse: (accel) set acceleration profile 0
(II) ImExPS/2 Generic Explorer Mouse: initialized for relative axes.
(II) config/hal: Adding input device Macintosh mouse button emulation
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event2"
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
(II) Macintosh mouse button emulation: initialized for relative axes.
(II) NVIDIA(0): Setting mode "nvidia-auto-select"
```

---

### Post by patchwork on 2010-03-18
It seems that the system is prepared to use your 1280x1024 on start-up
> (II) NVIDIA(0): Setting mode "1280x1024+0+0"But is then resorting to the auto-select (lower resolution)
> (II) NVIDIA(0): Setting mode "nvidia-auto-select"
Are you comfortable modifying your configuration file manually with help?

If so, can you please type in the terminal (or copy/paste)
```
gksu gedit /etc/X11/xorg.conf
```and add 

```
Option "PreferredMode" "1280x1024+0+0"
``` to the "Monitor" Section.

EDIT: Optionally, you can add

```
Option "ModeDebug" "True"
``` 
to the "Device" Section.  This will create a more informative log during mode selection.  There isn't a lot to go on error-wise in your log.

---

### Post by Fred the Penguin on 2010-03-18
I also have a problem something like this. Every time I boot up it comes up with a message about how the stored configuration for screens could not be applied. Nothing seems to be wrong, but it is annoying.

---

### Post by shazbut on 2010-03-18
I had this problem the other day, trying to make my dual monitor settings persist after a restart, on nvidia 9500gt.  From memory, what i had to do was:

1. Create a new basic xorg.conf file:
```
sudo nvidia-xconfig
```

2. Fix an error in the xorg.conf file which causes the issue in post #10:
```
gksudo gedit /etc/X11/xorg.conf
```
Add this missing line to the "Screen" section of xorg.conf:
```
Device      "Default Device"
```
Save and exit gedit.

3. Run nvidia-settings as root:
```
gksudo nvidia-settings
```
Apply the settings you need, then press the "Save to X Configuration File" button.


Hopefully that works, I can't remember the exact source of the info, I think I googled "nvidia-xconfig nvidia-settings karmic twinview" or somesuch.

---

### Post by imperius69 on 2010-03-18
i had the same problem.

then i found out this post

[http://ubuntuforums.org/showthread.php?t=1359352](http://ubuntuforums.org/showthread.php?t=1359352)

post 2, do what HappyFeet tells.

worked like a charm for me.

---

### Post by dancar22 on 2010-03-19
I will give it a try.  Thanks everybody for your help with this matter.  It is greatly appreciated!

Dan

---

### Post by Easy Limits on 2010-03-19
I had this problem with my Nvidia card.  I did find a simple solution.  Go to System > Preferences > Display and click on NO instead of YES and set your resolution there.  Works for me!

---

### Post by dancar22 on 2010-03-20
Solved.  I tried a number of the suggested solutions which didn't seem to help.  However, my neighbor who introduced me to Ubuntu suggested unplugging the monitor from the computer, turning off the monitor power, and then reattach everthing.  It worked.  The setting are maintained now but it could have been a combination of unplugging the monitor and reconfiguring the xconfig file.  Thanks everybody for all your help.  I really appreciate it.

Dan

---

### Post by csw840915 on 2010-09-14
Hello everyone. I am writing back in connection with the NVIDIA settings that wont save. Well I found that by simply going to the normal Monitor settings in the System > Administration menu and when it asks to use the NVIDIA manager so no and set the resolution and viola! Change and apply the resolution you want in the normal Ubuntu/Linux Display Manager.

Hope this helps. It solved my dilemma.

Clinton - A Happy Ubuntu User :popcorn:

---

### Post by Elentir on 2010-09-15
I had the same problem with Karmic (9.10). It was either fixed by Lucid (10.4) or a driver update which came soon after that. I have driver version 173.14.22 installed now.

---

### Post by windscryer on 2010-09-18
> **Easy Limits said:**
> I had this problem with my Nvidia card.  I did find a simple solution.  Go to System > Preferences > Display and click on NO instead of YES and set your resolution there.  Works for me!

THANK YOU FOR THIS SUGGESTION. While it bothers my inner übergeek to not be able to figure out a better solution, I'm too frustrated by the issue right now and just happy to have SOMETHING that works.

Everything else I tried--manual driver installs, editing xorg.conf, root-access nvidia-settings, unplugging and replugging, etc. (AD NAUSEUM)--*nothing* worked until I tried this.

I'll come back when I can see something other than the red haze of frustration and try again, but until then THANK YOU. =D>

---

