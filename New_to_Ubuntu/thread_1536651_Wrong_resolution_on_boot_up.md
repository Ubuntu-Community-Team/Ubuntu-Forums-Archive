---
title: "Wrong resolution on boot up"
date: 2010-07-22
forum: New to Ubuntu
---

### Post by mcCuppaT on 2010-07-22
Hey guys,

Since I rebased to lucid I can't get the right resolution on my nvidia ion box. I ask for 1080p & I get 800x600 :(

I feel like I have tried everything now. To make matters even more annoying if I log out I can see the log in screen is 1080p.

Below is my xorg.conf (video part only):

Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Panasonic-TV"
    HorizSync       15.0 - 68.0
    VertRefresh     23.0 - 61.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "ION"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    SubSection "Display"
        Virtual 1920 1080
    EndSubSection
EndSection


These are warnings related in /var/Log/Xorg.0.log too:

(--) Jul 22 18:42:44 NVIDIA(0): Connected display device(s) on ION at PCI:3:0:0:
(--) Jul 22 18:42:44 NVIDIA(0):     Panasonic-TV (DFP-1)
(--) Jul 22 18:42:44 NVIDIA(0): Panasonic-TV (DFP-1): 165.0 MHz maximum pixel clock
(--) Jul 22 18:42:44 NVIDIA(0): Panasonic-TV (DFP-1): Internal Single Link TMDS
(II) Jul 22 18:42:44 NVIDIA(0): Assigned Display Device: DFP-1
(==) Jul 22 18:42:44 NVIDIA(0): 
(==) Jul 22 18:42:44 NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
(==) Jul 22 18:42:44 NVIDIA(0):     will be used as the requested mode.
(==) Jul 22 18:42:44 NVIDIA(0): 
(II) Jul 22 18:42:44 NVIDIA(0): Validated modes:
(II) Jul 22 18:42:44 NVIDIA(0):     "nvidia-auto-select"
(**) Jul 22 18:42:44 NVIDIA(0): Virtual screen size configured to be 1920 x 1080
[B](WW) Jul 22 18:42:44 NVIDIA(0): Panasonic-TV (DFP-1)'s EDID does not contain a maximum image
(WW) Jul 22 18:42:44 NVIDIA(0):     size; cannot compute DPI from Panasonic-TV (DFP-1)'s
(WW) Jul 22 18:42:44 NVIDIA(0):     EDID.
[/B](==) Jul 22 18:42:44 NVIDIA(0): DPI set to (75, 75); computed from built-in default
....
(II) Jul 22 18:42:44 NVIDIA(0): Setting mode "nvidia-auto-select"
....
(II) Jul 22 18:42:54 NVIDIA(0): Setting mode "800x600"



If anyone understands why this suddenly happens in lucid I would greatly appreciate an answer.

Many thanks,
Ryan

---

### Post by mcCuppaT on 2010-07-23
Bump.

Anyone else had this?

---

### Post by Jakiejake on 2010-07-23
> **mcCuppaT said:**
> Bump.

Anyone else had this?

Please do not bump to soon
You should only bump every 24 Hours or more

---

### Post by Jakiejake on 2010-07-23
> **mcCuppaT said:**
> Hey guys,

Since I rebased to lucid I can't get the right resolution on my nvidia ion box. I ask for 1080p & I get 800x600 :(

I feel like I have tried everything now. To make matters even more annoying if I log out I can see the log in screen is 1080p.

Below is my xorg.conf (video part only):

Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Panasonic-TV"
    HorizSync       15.0 - 68.0
    VertRefresh     23.0 - 61.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "ION"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    SubSection "Display"
        Virtual 1920 1080
    EndSubSection
EndSection


These are warnings related in /var/Log/Xorg.0.log too:

(--) Jul 22 18:42:44 NVIDIA(0): Connected display device(s) on ION at PCI:3:0:0:
(--) Jul 22 18:42:44 NVIDIA(0):     Panasonic-TV (DFP-1)
(--) Jul 22 18:42:44 NVIDIA(0): Panasonic-TV (DFP-1): 165.0 MHz maximum pixel clock
(--) Jul 22 18:42:44 NVIDIA(0): Panasonic-TV (DFP-1): Internal Single Link TMDS
(II) Jul 22 18:42:44 NVIDIA(0): Assigned Display Device: DFP-1
(==) Jul 22 18:42:44 NVIDIA(0): 
(==) Jul 22 18:42:44 NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
(==) Jul 22 18:42:44 NVIDIA(0):     will be used as the requested mode.
(==) Jul 22 18:42:44 NVIDIA(0): 
(II) Jul 22 18:42:44 NVIDIA(0): Validated modes:
(II) Jul 22 18:42:44 NVIDIA(0):     "nvidia-auto-select"
(**) Jul 22 18:42:44 NVIDIA(0): Virtual screen size configured to be 1920 x 1080
[B](WW) Jul 22 18:42:44 NVIDIA(0): Panasonic-TV (DFP-1)'s EDID does not contain a maximum image
(WW) Jul 22 18:42:44 NVIDIA(0):     size; cannot compute DPI from Panasonic-TV (DFP-1)'s
(WW) Jul 22 18:42:44 NVIDIA(0):     EDID.
[/B](==) Jul 22 18:42:44 NVIDIA(0): DPI set to (75, 75); computed from built-in default
....
(II) Jul 22 18:42:44 NVIDIA(0): Setting mode "nvidia-auto-select"
....
(II) Jul 22 18:42:54 NVIDIA(0): Setting mode "800x600"



If anyone understands why this suddenly happens in lucid I would greatly appreciate an answer.

Many thanks,
Ryan

Whats The Resolution on your monitor?

---

### Post by mcCuppaT on 2010-07-23
Oops! Sorry.

The resolution on this panasonic tv is 1920x1080

As highlighted below I think there is something wrong in either the xorg.conf setup or my tv.

I have tried tweaking my settings related to EDID but no success.
( [http://ubuntuforums.org/showthread.php?t=83973](http://ubuntuforums.org/showthread.php?t=83973) )

I can't see a workaround for no maximum image size for xorg configuration either.


Any pointers guys?
Thanks

---

### Post by mcCuppaT on 2010-07-26
bump.

Anyone know what I can do if the edid resolution is wrong?
(Note: the login screen however is the correct size?!)

Thanks

---

### Post by Grenage on 2010-07-26
You can try and edit a copy of the EDID file, then refer to that in xorg.conf - or you could just specify the settings explicitly (modelines, et cetera).

I have a [guide]("http://www.grenage.com/xorg.html") here, which 'some' people have found useful.

---

