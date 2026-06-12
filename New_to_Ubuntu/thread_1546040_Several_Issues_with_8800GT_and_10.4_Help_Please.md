---
title: "Several Issues with 8800GT and 10.4 Help Please"
date: 2010-08-04
forum: New to Ubuntu
---

### Post by XorgFailure on 2010-08-04
Where do i start? Switched over from WinXP. Last time i used Ubuntu was 2 years ago. 
I'm not a complete noob. But these issues are driving me up the wall.

1. Thanks to my Vizio 42 Monitor EDID none of the hard coded values for modeset work properly. Half the time after rebooting after changing the xorg.conf Ubuntu stops at initial loading screen. So i am forced to reinstall. Ive done that about 50 times over the last 14 hours. I searched the boards and found several solutions, none have worked so far. 
2. In addition to the wonderful world of EDID failures my screen expands beyond the monitor or LCD TV range of viewing, which makes it difficult to see the menus. I finally got Twinview working so now i can actually read text on the screens. I used a 19 in Dell Monitor to setup the initial video, then added my LCD as a second monitor.  When i first started I tried to use my LCD via DVI to HDMI, yea, lets just say im glad i live alone. Lots of profanity.
3. And lastly, my FPS is blindingly slow. On WinXP my framerate gaming was 50fps at the highest res. On 10.4 is barely makes 16fps in 1280x720. I've tried hard coding values generated using CVT to no avail. That usually lets to resinstalling Ubuntu. I know how to get into "safe mode" or low rez but after modifying modesets it wouldnt allow me to enter safe mode. Below is my info. Let me know if theres something else you need or I need to do. Running low on Blue Moon, this could get ugly.

```
lpcis -vv for nvidia
01:00.0 VGA compatible controller: nVidia Corporation G92 [GeForce 8800 GT] (rev a2)
    Subsystem: Device 196e:053c
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin A routed to IRQ 16
    Region 0: Memory at d2000000 (32-bit, non-prefetchable) [size=16M]
    Region 1: Memory at c0000000 (64-bit, prefetchable) [size=256M]
    Region 3: Memory at d0000000 (64-bit, non-prefetchable) [size=32M]
    Region 5: I/O ports at 2000 [size=128]
    Capabilities: [60] Power Management version 3
        Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
        Status: D0 PME-Enable- DSel=0 DScale=0 PME-
    Capabilities: [68] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
        Address: 0000000000000000  Data: 0000
    Capabilities: [78] Express (v2) Endpoint, MSI 00
        DevCap:    MaxPayload 128 bytes, PhantFunc 0, Latency L0s <512ns, L1 <4us
            ExtTag+ AttnBtn- AttnInd- PwrInd- RBE+ FLReset-
        DevCtl:    Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
            RlxdOrd+ ExtTag+ PhantFunc- AuxPwr- NoSnoop+
            MaxPayload 128 bytes, MaxReadReq 512 bytes
        DevSta:    CorrErr- UncorrErr- FatalErr- UnsuppReq- AuxPwr- TransPend-
        LnkCap:    Port #0, Speed 2.5GT/s, Width x16, ASPM L0s L1, Latency L0 <512ns, L1 <1us
            ClockPM- Suprise- LLActRep- BwNot-
        LnkCtl:    ASPM Disabled; RCB 128 bytes Disabled- Retrain- CommClk+
            ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
        LnkSta:    Speed 2.5GT/s, Width x16, TrErr- Train- SlotClk+ DLActive- BWMgmt- ABWMgmt-
    Capabilities: [100] Virtual Channel <?>
    Capabilities: [128] Power Budgeting <?>
    Capabilities: [600] Vendor Specific Information <?>
    Kernel driver in use: nvidia
    Kernel modules: nvidia-current, nvidiafb, nouveau
```

```
Logs Xorg.0.log

X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-25-server i686 Ubuntu
Current Operating System: Linux doctor-desktop 2.6.32-21-generic #32-Ubuntu SMP Fri Apr 16 08:10:02 UTC 2010 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-21-generic root=UUID=f7087f90-7b08-43b2-bb96-deb0679ca575 ro quiet splash
Build Date: 23 April 2010  05:11:50PM
xorg-server 2:1.7.6-2ubuntu7 (Bryce Harrington <bryce@ubuntu.com>) 
Current version of pixman: 0.16.4
    Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Wed Aug  4 15:40:32 2010
(==) Using config file: "/etc/X11/xorg.conf"
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"
(==) ServerLayout "Layout0"
(**) |-->Screen "Screen0" (0)
(**) |   |-->Monitor "Monitor0"
(**) |   |-->Device "Device0"
(**) |-->Screen "Screen1" (1)
(**) |   |-->Monitor "Monitor1"
(**) |   |-->Device "Device1"
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
(==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
(WW) AllowEmptyInput is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
(WW) Disabling Keyboard0
(WW) Disabling Mouse0
(II) Loader magic: 0x81f0e80
(II) Module ABI versions:
    X.Org ANSI C Emulation: 0.4
    X.Org Video Driver: 6.0
    X.Org XInput driver : 7.0
    X.Org Server Extension : 2.0
(++) using VT number 7

(--) PCI:*(0:1:0:0) 10de:0611:196e:053c nVidia Corporation G92 [GeForce 8800 GT] rev 162, Mem @ 0xd2000000/16777216, 0xc0000000/268435456, 0xd0000000/33554432, I/O @ 0x00002000/128
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
(II) Loading /usr/lib/xorg/extra-modules/libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
    compiled for 4.0.2, module version = 1.0.0
    Module class: X.Org Server Extension
(II) NVIDIA GLX Module  195.36.24  Thu Apr 22 10:38:29 PDT 2010
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
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/extra-modules/nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
    compiled for 4.0.2, module version = 1.0.0
    Module class: X.Org Video Driver
(II) NVIDIA dlloader X Driver  195.36.24  Thu Apr 22 09:34:29 PDT 2010
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
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "TwinView" "0"
(**) NVIDIA(0): Option "MetaModes" "CRT: 1024x768_75 +0+0"
(**) NVIDIA(0): Option "TwinViewXineramaInfoOrder" "CRT-0"
(**) Aug 04 15:40:33 NVIDIA(0): Enabling RENDER acceleration
(II) Aug 04 15:40:33 NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) Aug 04 15:40:33 NVIDIA(0):     enabled.
(WW) Aug 04 15:40:35 NVIDIA(GPU-0): Unable to read EDID for display device CRT-0
(II) Aug 04 15:40:35 NVIDIA(0): NVIDIA GPU GeForce 8800 GT (G92) at PCI:1:0:0 (GPU-0)
(--) Aug 04 15:40:35 NVIDIA(0): Memory: 524288 kBytes
(--) Aug 04 15:40:35 NVIDIA(0): VideoBIOS: 62.92.23.00.51
(II) Aug 04 15:40:35 NVIDIA(0): Detected PCI Express Link width: 16X
(--) Aug 04 15:40:35 NVIDIA(0): Interlaced video modes are supported on this GPU
(--) Aug 04 15:40:35 NVIDIA(0): Connected display device(s) on GeForce 8800 GT at PCI:1:0:0:
(--) Aug 04 15:40:35 NVIDIA(0):     CRT-0
(--) Aug 04 15:40:35 NVIDIA(0):     VIZ VX42L HDTV10A (DFP-1)
(--) Aug 04 15:40:35 NVIDIA(0): CRT-0: 400.0 MHz maximum pixel clock
(--) Aug 04 15:40:35 NVIDIA(0): VIZ VX42L HDTV10A (DFP-1): 330.0 MHz maximum pixel clock
(--) Aug 04 15:40:35 NVIDIA(0): VIZ VX42L HDTV10A (DFP-1): Internal Dual Link TMDS
(II) Aug 04 15:40:35 NVIDIA(0): Display Device found referenced in MetaMode: CRT-0
(II) Aug 04 15:40:35 NVIDIA(0): Assigned Display Device: CRT-0
(II) Aug 04 15:40:35 NVIDIA(0): Validated modes:
(II) Aug 04 15:40:35 NVIDIA(0):     "CRT:1024x768_75+0+0"
(II) Aug 04 15:40:35 NVIDIA(0): Virtual screen size determined to be 1024 x 768
(WW) Aug 04 15:40:35 NVIDIA(0): Unable to get display device CRT-0's EDID; cannot compute DPI
(WW) Aug 04 15:40:35 NVIDIA(0):     from CRT-0's EDID.
(==) Aug 04 15:40:35 NVIDIA(0): DPI set to (75, 75); computed from built-in default
(==) Aug 04 15:40:35 NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
(**) NVIDIA(1): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(1): RGB weight 888
(==) NVIDIA(1): Default visual is TrueColor
(==) NVIDIA(1): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(1): Option "TwinView" "0"
(**) NVIDIA(1): Option "MetaModes" "DFP: nvidia-auto-select +0+0"
(**) Aug 04 15:40:35 NVIDIA(1): Enabling RENDER acceleration
(II) Aug 04 15:40:35 NVIDIA(1): NVIDIA GPU GeForce 8800 GT (G92) at PCI:1:0:0 (GPU-0)
(--) Aug 04 15:40:35 NVIDIA(1): Memory: 524288 kBytes
(--) Aug 04 15:40:35 NVIDIA(1): VideoBIOS: 62.92.23.00.51
(II) Aug 04 15:40:35 NVIDIA(1): Detected PCI Express Link width: 16X
(--) Aug 04 15:40:35 NVIDIA(1): Interlaced video modes are supported on this GPU
(--) Aug 04 15:40:35 NVIDIA(1): Connected display device(s) on GeForce 8800 GT at PCI:1:0:0:
(--) Aug 04 15:40:35 NVIDIA(1):     CRT-0
(--) Aug 04 15:40:35 NVIDIA(1):     VIZ VX42L HDTV10A (DFP-1)
(--) Aug 04 15:40:35 NVIDIA(1): CRT-0: 400.0 MHz maximum pixel clock
(--) Aug 04 15:40:35 NVIDIA(1): VIZ VX42L HDTV10A (DFP-1): 330.0 MHz maximum pixel clock
(--) Aug 04 15:40:35 NVIDIA(1): VIZ VX42L HDTV10A (DFP-1): Internal Dual Link TMDS
(II) Aug 04 15:40:35 NVIDIA(1): Display Device found referenced in MetaMode: DFP-1
(WW) Aug 04 15:40:35 NVIDIA(1): The EDID for VIZ VX42L HDTV10A (DFP-1) contradicts itself:
(WW) Aug 04 15:40:35 NVIDIA(1):     mode "1920x1080" is specified in the EDID; however, the
(WW) Aug 04 15:40:35 NVIDIA(1):     EDID's valid HorizSync range (31.000-70.000 kHz) would
(WW) Aug 04 15:40:35 NVIDIA(1):     exclude this mode's HorizSync (28.1 kHz); ignoring
(WW) Aug 04 15:40:35 NVIDIA(1):     HorizSync check for mode "1920x1080".
(WW) Aug 04 15:40:35 NVIDIA(1): The EDID for VIZ VX42L HDTV10A (DFP-1) contradicts itself:
(WW) Aug 04 15:40:35 NVIDIA(1):     mode "720x576" is specified in the EDID; however, the
(WW) Aug 04 15:40:35 NVIDIA(1):     EDID's valid HorizSync range (31.000-70.000 kHz) would
(WW) Aug 04 15:40:35 NVIDIA(1):     exclude this mode's HorizSync (15.6 kHz); ignoring
(WW) Aug 04 15:40:35 NVIDIA(1):     HorizSync check for mode "720x576".
(WW) Aug 04 15:40:35 NVIDIA(1): The EDID for VIZ VX42L HDTV10A (DFP-1) contradicts itself:
(WW) Aug 04 15:40:35 NVIDIA(1):     mode "1920x1080" is specified in the EDID; however, the
(WW) Aug 04 15:40:35 NVIDIA(1):     EDID's valid HorizSync range (31.000-70.000 kHz) would
(WW) Aug 04 15:40:35 NVIDIA(1):     exclude this mode's HorizSync (28.1 kHz); ignoring
(WW) Aug 04 15:40:35 NVIDIA(1):     HorizSync check for mode "1920x1080".
(WW) Aug 04 15:40:35 NVIDIA(1): The EDID for VIZ VX42L HDTV10A (DFP-1) contradicts itself:
(WW) Aug 04 15:40:35 NVIDIA(1):     mode "1920x1080" is specified in the EDID; however, the
(WW) Aug 04 15:40:35 NVIDIA(1):     EDID's valid HorizSync range (31.000-70.000 kHz) would
(WW) Aug 04 15:40:35 NVIDIA(1):     exclude this mode's HorizSync (28.1 kHz); ignoring
(WW) Aug 04 15:40:35 NVIDIA(1):     HorizSync check for mode "1920x1080".
(WW) Aug 04 15:40:35 NVIDIA(1): The EDID for VIZ VX42L HDTV10A (DFP-1) contradicts itself:
(WW) Aug 04 15:40:35 NVIDIA(1):     mode "720x576" is specified in the EDID; however, the
(WW) Aug 04 15:40:35 NVIDIA(1):     EDID's valid HorizSync range (31.000-70.000 kHz) would
(WW) Aug 04 15:40:35 NVIDIA(1):     exclude this mode's HorizSync (15.6 kHz); ignoring
(WW) Aug 04 15:40:35 NVIDIA(1):     HorizSync check for mode "720x576".
(WW) Aug 04 15:40:35 NVIDIA(1): The EDID for VIZ VX42L HDTV10A (DFP-1) contradicts itself:
(WW) Aug 04 15:40:35 NVIDIA(1):     mode "1920x1080" is specified in the EDID; however, the
(WW) Aug 04 15:40:35 NVIDIA(1):     EDID's valid HorizSync range (31.000-70.000 kHz) would
(WW) Aug 04 15:40:35 NVIDIA(1):     exclude this mode's HorizSync (28.1 kHz); ignoring
(WW) Aug 04 15:40:35 NVIDIA(1):     HorizSync check for mode "1920x1080".
(II) Aug 04 15:40:35 NVIDIA(1): Assigned Display Device: DFP-1
(II) Aug 04 15:40:35 NVIDIA(1): Validated modes:
(II) Aug 04 15:40:35 NVIDIA(1):     "DFP:nvidia-auto-select+0+0"
(II) Aug 04 15:40:35 NVIDIA(1): Virtual screen size determined to be 1280 x 720
(--) Aug 04 15:40:35 NVIDIA(1): DPI set to (34, 35); computed from "UseEdidDpi" X config
(--) Aug 04 15:40:35 NVIDIA(1):     option
(==) Aug 04 15:40:35 NVIDIA(1): Enabling 32-bit ARGB GLX visuals.
(--) Depth 24 pixmap format is 32 bpp
(II) Aug 04 15:40:35 NVIDIA: Using 768.00 MB of virtual memory for indirect memory access.
(II) Aug 04 15:40:35 NVIDIA(0): Initialized GPU GART.
(II) Aug 04 15:40:35 NVIDIA(0): Setting mode "CRT:1024x768_75+0+0"
(II) Loading extension NV-GLX
(II) Aug 04 15:40:35 NVIDIA(0): Initialized OpenGL Acceleration
(==) NVIDIA(0): Disabling shared memory pixmaps
(II) Aug 04 15:40:35 NVIDIA(0): Initialized X Rendering Acceleration
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(**) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
(II) Loading extension XINERAMA
(==) RandR enabled
(II) Aug 04 15:40:35 NVIDIA(1): Initialized GPU GART.
(II) Aug 04 15:40:35 NVIDIA(1): Setting mode "DFP:nvidia-auto-select+0+0"
(II) Aug 04 15:40:35 NVIDIA(1): Initialized OpenGL Acceleration
(==) NVIDIA(1): Disabling shared memory pixmaps
(II) Aug 04 15:40:35 NVIDIA(1): Initialized X Rendering Acceleration
(==) NVIDIA(1): Backing store disabled
(==) NVIDIA(1): Silken mouse enabled
(**) NVIDIA(1): DPMS enabled
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
(II) config/udev: Adding input device HDA Digital PCBeep (/dev/input/event6)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device HDA Intel Line Out at Ext Rear Jack (/dev/input/event10)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device HDA Intel Line Out at Ext Rear Jack (/dev/input/event11)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device HDA Intel Line Out at Ext Rear Jack (/dev/input/event12)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device HDA Intel Line Out at Ext Rear Jack (/dev/input/event13)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device HDA Intel HP Out at Ext Front Jack (/dev/input/event14)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device HDA Intel Line In at Ext Rear Jack (/dev/input/event7)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device HDA Intel Mic at Ext Front Jack (/dev/input/event8)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device HDA Intel Mic at Ext Rear Jack (/dev/input/event9)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device Creative HS-1200 Headset Creative HS-1200 Headset (/dev/input/event3)
(**) Creative HS-1200 Headset Creative HS-1200 Headset: Applying InputClass "evdev keyboard catchall"
(**) Creative HS-1200 Headset Creative HS-1200 Headset: always reports core events
(**) Creative HS-1200 Headset Creative HS-1200 Headset: Device: "/dev/input/event3"
(II) Creative HS-1200 Headset Creative HS-1200 Headset: Found 1 mouse buttons
(II) Creative HS-1200 Headset Creative HS-1200 Headset: Found scroll wheel(s)
(II) Creative HS-1200 Headset Creative HS-1200 Headset: Found relative axes
(II) Creative HS-1200 Headset Creative HS-1200 Headset: Found absolute axes
(II) Creative HS-1200 Headset Creative HS-1200 Headset: Found keys
(II) Creative HS-1200 Headset Creative HS-1200 Headset: Configuring as mouse
(II) Creative HS-1200 Headset Creative HS-1200 Headset: Configuring as keyboard
(**) Creative HS-1200 Headset Creative HS-1200 Headset: YAxisMapping: buttons 4 and 5
(**) Creative HS-1200 Headset Creative HS-1200 Headset: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Creative HS-1200 Headset Creative HS-1200 Headset" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(EE) Creative HS-1200 Headset Creative HS-1200 Headset: failed to initialize for relative axes.
(II) Creative HS-1200 Headset Creative HS-1200 Headset: initialized for absolute axes.
(II) config/udev: Adding input device Logitech USB Receiver (/dev/input/event4)
(**) Logitech USB Receiver: Applying InputClass "evdev keyboard catchall"
(**) Logitech USB Receiver: always reports core events
(**) Logitech USB Receiver: Device: "/dev/input/event4"
(II) Logitech USB Receiver: Found keys
(II) Logitech USB Receiver: Configuring as keyboard
(II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/udev: Adding input device Logitech USB Receiver (/dev/input/event5)
(**) Logitech USB Receiver: Applying InputClass "evdev pointer catchall"
(**) Logitech USB Receiver: Applying InputClass "evdev keyboard catchall"
(**) Logitech USB Receiver: always reports core events
(**) Logitech USB Receiver: Device: "/dev/input/event5"
(II) Logitech USB Receiver: Found 12 mouse buttons
(II) Logitech USB Receiver: Found scroll wheel(s)
(II) Logitech USB Receiver: Found relative axes
(II) Logitech USB Receiver: Found x and y relative axes
(II) Logitech USB Receiver: Found absolute axes
(II) Logitech USB Receiver: Found keys
(II) Logitech USB Receiver: Configuring as mouse
(II) Logitech USB Receiver: Configuring as keyboard
(**) Logitech USB Receiver: YAxisMapping: buttons 4 and 5
(**) Logitech USB Receiver: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) Logitech USB Receiver: initialized for relative axes.
(WW) Logitech USB Receiver: ignoring absolute axes.
(II) config/udev: Adding input device Logitech USB Receiver (/dev/input/mouse1)
(II) No input driver/identifier specified (ignoring)
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
(II) Aug 04 15:40:40 NVIDIA(1): Setting mode "DFP:nvidia-auto-select+0+0"
```

```
xorg.conf 
# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildd@palmer)  Fri Apr  9 10:35:18 UTC 2010

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    Screen      1  "Screen1" RightOf "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    Option         "Xinerama" "0"
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
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "DELL  M991"
    HorizSync       30.0 - 96.0
    VertRefresh     50.0 - 160.0
    Option         "DPMS"
EndSection

Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "VIZ VX42L HDTV10A"
    HorizSync       31.0 - 70.0
    VertRefresh     50.0 - 85.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8800 GT"
    BusID          "PCI:1:0:0"
    Screen          0
EndSection

Section "Device"
    Identifier     "Device1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8800 GT"
    BusID          "PCI:1:0:0"
    Screen          1
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "CRT: 1024x768_75 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Device1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "DFP: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection
```


Help me Obi-wan Kenobi your my only hope. Now what do I press?

---

### Post by XorgFailure on 2010-08-04
Also per Ubuntu I removed Nouveau.

Tried to initially install using Nomodeset from the install screen also.

---

### Post by clhsharky on 2010-08-04
Please wrap your c/p with quotes or code, thread is now hard to follow.

> And lastly, my FPS is blindingly slow. On WinXP my framerate gaming was 50fps at the highest res. On 10.4 is barely makes 16fps in 1280x720. 
Apples and oranges, is that a native Linux game?
If you want performance with window apps, use windows, why do you think users duel boot.

Sharky

---

### Post by XorgFailure on 2010-08-04
2 years ago I was using Ubuntu with an older nvidia card and was gaming. My frame rate was well over 50fps in max res. I know its faster. I play WoW via Wine.

---

### Post by corrytonapple on 2010-08-04
Your title says Ubuntu 10.4. That is in beta. Do you mean 10.04, which is not in beta?

---

### Post by XorgFailure on 2010-08-04
Oh thanks, it is 10.04.

---

### Post by cariboo on 2010-08-04
The nouveau drivers don't have any 3d acceleration, that's why your frame rate is so slow.

I would suggest you remove the nouveau drivers, delete your /etc/X11/xorg.conf and start all over.

Install the restricted drives from the repositories, and before you reboot, open a terminal and type:

```
sudo nvidia-xconfig
```

Make sure both the monitor and the TV are connected. Check to see if the TV was detected, then reboot.

I have a 32" Samsung connected through VGA, the native size when connected to VGA is 1360X768. My TV has adjustments in the TV menu to set the picture size, whether it is off center or over-scanning. I can do the settings manually, or just select automatic, it takes less than 5 seconds for the TV to do it's thing.

---

### Post by XorgFailure on 2010-08-04
By the way I switched to Ubuntu because I am sick of the Windows BS extra services that usurp memory and processor power. I know how to setup dual boot. I need help with this so please stop trying to direct me back to windows. Windows is evil. I also trimmed my services in windows for performance and there is still services that Services Packs enable that munch on system resources.

Btw, is *1368x768_60*.[I]00 a supported resolution of Ubuntu 10.04? i can't seem to find any indication that it isn't or is.
[/I]

---

### Post by sandyd on 2010-08-04
> **XorgFailure said:**
> By the way I switched to Ubuntu because I am sick of the Windows BS extra services that usurp memory and processor power. I know how to setup dual boot. I need help with this so please stop trying to direct me back to windows. Windows is evil. I also trimmed my services in windows for performance and there is still services that Services Packs enable that munch on system resources.

Btw, is *1368x768_60*.[I]00 a supported resolution of Ubuntu 10.04? i can't seem to find any indication that it isn't or is.
[/I]
yeah, it is.
if your having trouble getting to the hardware drivers window, press shift while booting, and then press "e" after you see the grub menu.

on the "kernel" line, add "nomodeset" (without the quotes) at the end of the line.

---

### Post by clhsharky on 2010-08-05
> By the way I switched to Ubuntu because I am sick of the Windows BS extra services that usurp memory and processor power. I know how to setup dual boot. I need help with this so please stop trying to direct me back to windows. Windows is evil. I also trimmed my services in windows for performance and there is still services that Services Packs enable that munch on system resources
I'm not trying to make any one do anything.
I'm a firm believer in using the right tool for the job.

Good Luck

Sharky

---

### Post by XorgFailure on 2010-08-05
> **XorgFailure said:**
> Also per Ubuntu I removed Nouveau.

Tried to initially install using Nomodeset from the install screen also.


Will boot into grub then use nomodeset after I delete my xorg.conf. Does that sound correct. I appreciate all the help.:D

Also I do already have the restricted drivers installed. I think the issue is with my xorg. I will do as you instructed.

Thanks again.

---

### Post by XorgFailure on 2010-08-06
Held shift down like you suggested. It never brought up the GRUB screen. :(

---

### Post by LowSky on 2010-08-06
> **XorgFailure said:**
> Held shift down like you suggested. It never brought up the GRUB screen. :(

ESCape should so it, not shift


doing this should get everything working correctly

```
sudo apt-get install nvidia-current
```
```
sudo update-alternatives --config gl_conf
```
```
sudo ldconfig
```
```
sudo nvidia-xconfig
```
```
sudo reboot 
```

[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia#NVIDIA%20driver%20activated%20but%20not%20currently%20in%20use%20in%20ubuntu%2010.04](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia#NVIDIA%20driver%20activated%20but%20not%20currently%20in%20use%20in%20ubuntu%2010.04)

---

### Post by XorgFailure on 2010-08-06
Boot Info Script 0.55    dated February 15th, 2010             $

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in
    partition #1 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________
    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:

=========================== Drive/Partition Info: =============================

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   607,006,719   607,004,672  83 Linux
/dev/sda2         607,008,766   625,141,759    18,132,994   5 Extended
/dev/sda5         607,008,768   625,141,759    18,132,992  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL        

/dev/sda1        f7087f90-7b08-43b2-bb96-deb0679ca575   ext4                    
/dev/sda2: PTTYPE="dos"
/dev/sda5        7adcd317-32bf-47e6-a6d6-8cf96a3d33ff   swap
/dev/sda: PTTYPE="dos"
error: /dev/sdb: No medium found
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found

============================ "mount | grep ^/dev  output: ===========================

/dev/sda1        /                        ext4       (rw,errors=remount-ro)


=========================== sda1/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ext2
set root='(hd0,1)'
search --no-floppy --fs-uuid --set f7087f90-7b08-43b2-bb96-deb0679ca575
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ext2
set root='(hd0,1)'
search --no-floppy --fs-uuid --set f7087f90-7b08-43b2-bb96-deb0679ca575
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
        recordfail
        insmod ext2
        set root='(hd0,1)'
        search --no-floppy --fs-uuid --set f7087f90-7b08-43b2-bb96-deb0679ca575
        linux   /boot/vmlinuz-2.6.32-21-generic root=UUID=f7087f90-7b08-43b2-bb96-deb0679ca575 ro   quiet spl$
        initrd  /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu$
        recordfail
        insmod ext2
        set root='(hd0,1)'
        search --no-floppy --fs-uuid --set f7087f90-7b08-43b2-bb96-deb0679ca575
        echo    'Loading Linux 2.6.32-21-generic ...'
        linux   /boot/vmlinuz-2.6.32-21-generic root=UUID=f7087f90-7b08-43b2-bb96-deb0679ca575 ro single
        echo    'Loading initial ramdisk ...'
        initrd  /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
        insmod ext2
        set root='(hd0,1)'
        search --no-floppy --fs-uuid --set f7087f90-7b08-43b2-bb96-deb0679ca575
        linux16 /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
        insmod ext2
        set root='(hd0,1)'
        search --no-floppy --fs-uuid --set f7087f90-7b08-43b2-bb96-deb0679ca575
        linux16 /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ ${timeout} != -1 ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
### END /etc/grub.d/30_os-prober ###
### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=f7087f90-7b08-43b2-bb96-deb0679ca575 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=7adcd317-32bf-47e6-a6d6-8cf96a3d33ff none            swap    sw              0       0

=================== sda1: Location of files loaded by Grub: ===================


  32.3GB: boot/grub/core.img
 221.5GB: boot/grub/grub.cfg
  32.3GB: boot/initrd.img-2.6.32-21-generic
    .1GB: boot/vmlinuz-2.6.32-21-generic
  32.3GB: initrd.img
    .1GB: vmlinuz
=======Devices which don't seem to have a corresponding hard drive==============

sdb sdc sdd sde


Hope this helps

---

### Post by XorgFailure on 2010-08-06
Still can get into GRUB using ESC.

I tried Holding it down at POST, BIOS, after BIOS, nothing works. :(

---

### Post by XorgFailure on 2010-08-06
I did the steps you suggested, nothing happened. Screen still over stretched and resolution still can't do native resolution of LCD.:(

---

### Post by jtarin on 2010-08-06
[Xrandr]("http://newtoubuntu.wordpress.com/2010/07/17/ubuntu-10-04-fixing-the-monitor-resolution-with-xrandr/")

---

### Post by XorgFailure on 2010-08-06
According to Xrandr I am in 1368x768. But the screen is still overstretched. I still cant see the menus or the bottom bar.

And when take my mouse to the left and right of the screen it moves. I don't understand what is going on, please help.

And inside the Nvidia Config gui it still says the native resolution is 1280x720. I have to use Panning to get it to 1368x768.

---

### Post by XorgFailure on 2010-08-06
Removed the spanning setting. Turned off Forced GPU scaling. Used EDID. When i went to save new config i received this message "Unable to open X config file '/etc/X11/xorg.conf' for writing."

---

### Post by XorgFailure on 2010-08-06
I went and manually copied the new config file into the xorg.conf. Here it is below:

# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildd@palmer)  Fri Apr  9 10:35:18 UTC 2010

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder75)  Thu Apr 22 11:44:23 PDT 2010

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    Option         "Xinerama" "0"
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
    ModelName      "VIZ VX42L HDTV10A"
    HorizSync       31.0 - 70.0
    VertRefresh     50.0 - 85.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8800 GT"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "nvidia-auto-select @1368x768 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

---

### Post by XorgFailure on 2010-08-06
Also tried sudo rm /etc/X11/xorg.conf, sudo nvidia-xconfig. gksudo nvidia-settings  and saved them. Then rebooted no change. I still can do left right up  and down and the screen still shifts.

---

### Post by jtarin on 2010-08-06
> **XorgFailure said:**
> According to Xrandr I am in 1368x768. But the screen is still overstretched. I still cant see the menus or the bottom bar.

And when take my mouse to the left and right of the screen it moves. I don't understand what is going on, please help.

And inside the Nvidia Config gui it still says the native resolution is 1280x720. I have to use Panning to get it to 1368x768.I'm sorry if English is not your native language and apologize and should have explained my link fully or linked to a version translated in your language.
> 2. You will get an output of the display(s) connected to your computer and the _supported resolutions_.Nowhere does it say these are _enabled_ resolutions. You must set this up yourself.

---

### Post by XorgFailure on 2010-08-06
FIXED IT!!!!! 

[http://ubuntuforums.org/showthread.php?t=83973](http://ubuntuforums.org/showthread.php?t=83973)

All it was changed vendor name from nvidia to nv:D

Also the stretching was cause by the monitor over scanning. So i adjusted the  Overscanning compensation in the Nvidia Control Panel.

Thanks for all the help.

---

### Post by jtarin on 2010-08-07
> **XorgFailure said:**
> FIXED IT!!!!! 

[http://ubuntuforums.org/showthread.php?t=83973](http://ubuntuforums.org/showthread.php?t=83973)

All it was changed vendor name from nvidia to nv:D

Also the stretching was cause by the monitor over scanning. So i adjusted the  Overscanning compensation in the Nvidia Control Panel.

Thanks for all the help.(FacePalm) I completely missed that. Installing Nvidia always does that to xorg.conf when it should be 'nv'. Good catch.

---

