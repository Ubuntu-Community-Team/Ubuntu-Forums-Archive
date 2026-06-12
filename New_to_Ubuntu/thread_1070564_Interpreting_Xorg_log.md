---
title: "Interpreting Xorg log"
date: 2009-02-15
forum: New to Ubuntu
---

### Post by HavocXphere on 2009-02-15
Can someone please help me interpret these warnings in Xorg.0.log:

> (--) PCI:*(0@1:0:0) ATI Technologies Inc RV670PRO [Radeon HD 3850] rev 0, Mem @ 0xd0000000/0, 0xfe8e0000/0, I/O @ 0x0000c000/0, BIOS @ 0x????????/131072
...
(WW) Falling back to old probe method for fglrx
...
(WW) This ATI Proprietary Linux Driver does not guarantee support of video driver ABI higher than 2.0
(WW) Video driver ABI version of the X server is 4.1
(--) Assigning device section with no busID to primary device
(WW) fglrx: No matching Device section for instance (BusID PCI:0@1:0:1) found
(--) Chipset Supported AMD Graphics Processor (0x9505) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@1:0:1) found
...
**(WW) fglrx(0): Option "RenderAccel" is not used**
...
(WW) AIGLX: 3D driver claims to not support visual 0x23
(WW) AIGLX: 3D driver claims to not support visual 0x24
(WW) AIGLX: 3D driver claims to not support visual 0x25
(WW) AIGLX: 3D driver claims to not support visual 0x26
(WW) AIGLX: 3D driver claims to not support visual 0x27
(WW) AIGLX: 3D driver claims to not support visual 0x28
(WW) AIGLX: 3D driver claims to not support visual 0x29
(WW) AIGLX: 3D driver claims to not support visual 0x2a
(WW) AIGLX: 3D driver claims to not support visual 0x2b
...


Specifically the bold one. Does it mean desktop acceleration is disabled?:confused: Desktop effects are enabled & using OpenGL. RenderAccel seems to be enabled in xorg.conf.

Thanks

[Kubuntu 8.10]
[Kde 4.1.3]
xorg.conf
> 
Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
	SubSection "Display"
		Depth 24
		Modes "16804x1050"
	EndSubSection
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"fglrx"
	Option	    "VideoOverlay" "off"
	Option	    "OpenGLOverlay" "off"
	Option "TexturedVideo" "off"        
        Option "UseFastTLS" "2"
        Option "RenderAccel" "true"
EndSection


---

### Post by Dies on 2009-02-15
```
Section "Device"
Identifier "Configured Video Device"
Driver "fglrx"
Option "VideoOverlay" "off"
Option "OpenGLOverlay" "off"
Option "TexturedVideo" "off"
Option "UseFastTLS" "2"
BusID  "PCI:1:0:0"
EndSection 
```

Try that, obviously make a backup of your current file before so you can recover easily should it fail.

That should get rid of the warnings that you have control over, the other stuff you shouldn't worry about since you can't do anything about it anyways. ;-)

---

### Post by HavocXphere on 2009-02-16
> **Dies said:**
> Try that, obviously make a backup of your current file before so you can recover easily should it fail.

That should get rid of the warnings that you have control over, the other stuff you shouldn't worry about since you can't do anything about it anyways. ;-)
I'll do so when I get home & report the result.

Thanks

---

### Post by RomeReactor on 2009-02-16
Hi. Just to comment on this, it seems the warning you're getting means that the option (as set in xorg.conf) is not used by the X server. It doesn't necessarily mean that you don't have direct rendering--which you do have, given that desktop effects are enabled on your system.

---

