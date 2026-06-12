---
title: "possible Xserver bug"
date: 2009-12-31
forum: New to Ubuntu
---

### Post by clay woodruff on 2009-12-31
i have what i think is an Xserver bug infinite loop. i have the side affect high cpu usage in firefox i'm not totally sure this is the problem but after following some direction from wiki. this is what i came up with.
after running glxinfo everything seemed ok then i ran  /var/log/Xorg.0.log and that seemed ok then i ran /var/log/gdm/*
and got this
(gnome-settings-daemon:1637): GLib-CRITICAL **: g_propagate_error: assertion `src != NULL' failed

(gnome-settings-daemon:1637): GLib-CRITICAL **: g_propagate_error: assertion `src != NULL' failed
Window manager warning: Failed to read saved session file /var/lib/gdm/.config/metacity/sessions/1024754418bf0505e126209860165997000000015920006.ms: Failed to open file '/var/lib/gdm/.config/metacity/sessions/1024754418bf0505e126209860165997000000015920006.ms': No such file or directory
** (process:1656): DEBUG: Greeter session pid=1656 display=:0.0 xauthority=/var/run/gdm/auth-for-gdm-R3QTzY/database
Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x1200027 (Login Wind)
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.
Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x1200027 (Login Wind)
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.
Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x1200027 (Login Wind)
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.
Window manager warning: CurrentTime used to choose focus window; focus window may not be correct.
Window manager warning: Got a request to focus the no_focus_window with a timestamp of 0.  This shouldn't happen!

there are about 4 tabs : o-greeter.log.1.2.3.4 and just a :  o.log

which has this

X.Org X Server 1.6.4
Release Date: 2009-9-27
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux clays-desktop 2.6.31-16-generic #53-Ubuntu SMP Tue Dec 8 04:01:29 UTC 2009 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-16-generic root=UUID=b34dd81e-d7f4-46c5-b53d-86bf926946d1 ro quiet splash
Build Date: 26 October 2009  05:15:02PM
xorg-server 2:1.6.4-2ubuntu4 (buildd@) 
    Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Tue Dec 29 06:56:34 2009
(==) Using config file: "/etc/X11/xorg.conf"
(==) No Layout section.  Using the first Screen section.
(**) |-->Screen "Screen0" (0)
(**) |   |-->Monitor "Monitor0"
(**) |   |-->Device "Videocard0"
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
(++) using VT number 7

(--) PCI:*(0:1:8:0) 10de:0322:196e:01ad nVidia Corporation NV34 [GeForce FX 5200] rev 161, Mem @ 0xfb000000/16777216, 0xd0000000/268435456, BIOS @ 0x????????/131072
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 1.0.0
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 1.0.0
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
    compiled for 4.0.2, module version = 1.0.0
(II) NVIDIA GLX Module  173.14.20  Thu Jun 25 19:49:59 PDT 2009
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 1.13.0
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 1.0.0
(II) Loading /usr/lib/xorg/modules/extensions//libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 1.1.0
(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
    compiled for 4.0.2, module version = 1.0.0
(II) NVIDIA dlloader X Driver  173.14.20  Thu Jun 25 19:28:52 PDT 2009
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 1.0.0
(II) Loading /usr/lib/xorg/modules//libwfb.so
(II) Module wfb: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 1.0.0
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(WW) NVIDIA(GPU-0): Unable to read EDID for display device CRT-0
(II) NVIDIA(0): NVIDIA GPU GeForce FX 5200 (NV34) at PCI:1:8:0 (GPU-0)
(--) NVIDIA(0): Memory: 262144 kBytes
(--) NVIDIA(0): VideoBIOS: 04.34.20.87.51
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce FX 5200 at PCI:1:8:0:
(--) NVIDIA(0):     CRT-0
(--) NVIDIA(0): CRT-0: 350.0 MHz maximum pixel clock
(II) NVIDIA(0): Assigned Display Device: CRT-0
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "1024x768+0+0"
(II) NVIDIA(0):     "800x600+0+0"
(II) NVIDIA(0):     "640x480+0+0"
(II) NVIDIA(0): Virtual screen size determined to be 1024 x 768
(WW) NVIDIA(0): Unable to get display device CRT-0's EDID; cannot compute DPI
(WW) NVIDIA(0):     from CRT-0's EDID.
(==) NVIDIA(0): DPI set to (75, 75); computed from built-in default
(==) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
(--) Depth 24 pixmap format is 32 bpp
(II) NVIDIA(0): Initialized GPU GART.
(II) NVIDIA(0): Setting mode "1024x768+0+0"
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(**) NVIDIA(0): DPMS enabled
(==) RandR enabled
(II) Initializing extension GLX
(II) config/hal: Adding input device AT Translated Set 2 keyboard
(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 2.2.5
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event3"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(II) config/hal: Adding input device Power Button
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event1"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(II) config/hal: Adding input device Power Button
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event0"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
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
(II) config/hal: Adding input device Microsoft Microsoft 5-Button Mouse with IntelliEye(TM)
(**) Microsoft Microsoft 5-Button Mouse with IntelliEye(TM): always reports core events
(**) Microsoft Microsoft 5-Button Mouse with IntelliEye(TM): Device: "/dev/input/event4"
(II) Microsoft Microsoft 5-Button Mouse with IntelliEye(TM): Found 9 mouse buttons
(II) Microsoft Microsoft 5-Button Mouse with IntelliEye(TM): Found x and y relative axes
(II) Microsoft Microsoft 5-Button Mouse with IntelliEye(TM): Found scroll wheel(s)
(II) Microsoft Microsoft 5-Button Mouse with IntelliEye(TM): Configuring as mouse
(**) Microsoft Microsoft 5-Button Mouse with IntelliEye(TM): YAxisMapping: buttons 4 and 5
(**) Microsoft Microsoft 5-Button Mouse with IntelliEye(TM): EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Microsoft Microsoft 5-Button Mouse with IntelliEye(TM)" (type: MOUSE)
(**) Microsoft Microsoft 5-Button Mouse with IntelliEye(TM): (accel) keeping acceleration scheme 1
(**) Microsoft Microsoft 5-Button Mouse with IntelliEye(TM): (accel) filter chain progression: 2.00
(**) Microsoft Microsoft 5-Button Mouse with IntelliEye(TM): (accel) filter stage 0: 20.00 ms
(**) Microsoft Microsoft 5-Button Mouse with IntelliEye(TM): (accel) set acceleration profile 0
(II) Microsoft Microsoft 5-Button Mouse with IntelliEye(TM): initialized for relative axes.
(II) NVIDIA(0): Setting mode "800x600+0+0"
(II) NVIDIA(0): Setting mode "1024x768+0+0"

the other 4 tabs say about the same thing with a few changes to the session #. 
is this Xserver being stuck in loop?

---

