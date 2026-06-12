---
title: "No Background"
date: 2010-11-20
forum: New to Ubuntu
---

### Post by bvpainter on 2010-11-20
My background has changed to all black. I've tried changing it, and my choice shows for a few minutes and then disappears and I'm back to a black screen again. My icons all show, but it is rather disappointing not to get a background.

Can anyone help me get my background back.

---

### Post by ajgreeny on 2010-11-20
I imagine you have compiz running and a resolution above 1024x768 and have an ATI graphic card using the default /ati/radeon driver that came with the install.

You can workaround the problem by either turning of compiz (Alt+F2 and type metacity --replace in the box) or by running at a lower resolution, or by using 16 bit colour, which is what I did.

The easiest is obviously to not use compiz, but I still found that graphics were slow on my ATI 9200SE card unless I used the 16 bit colour option.

here's the config part of /etc/X11/xorg.conf that I used in my machine.  Try an edit to your hardware resolution etc etc and see if it works for you.
```
Section "Device"
    Identifier     "Configured Video Device"
    Driver         "ati"
    Option         "AccelMethod" "UXA"
EndSection 

Section "Monitor"
    Identifier    "Configured Monitor"
            HorizSync    30-80
            VertRefresh    50-75
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
    DefaultDepth    16
    SubSection "Display"
        Modes        "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
EndSection

```

Things are better in 10.04 and even better in 10.10, but there are possible other problems there depending on hardware.  For me, 10.04 is the best yet, once I have the xorg.conf sorted properly.

---

### Post by bvpainter on 2010-11-20
> **ajgreeny said:**
> I imagine you have compiz running and a resolution above 1024x768 and have an ATI graphic card using the default /ati/radeon driver that came with the install.

You can workaround the problem by either turning of compiz (Alt+F2 and type metacity --replace in the box) or by running at a lower resolution, or by using 16 bit colour, which is what I did.

The easiest is obviously to not use compiz, but I still found that graphics were slow on my ATI 9200SE card unless I used the 16 bit colour option.

here's the config part of /etc/X11/xorg.conf that I used in my machine.  Try an edit to your hardware resolution etc etc and see if it works for you.
```
Section "Device"
    Identifier     "Configured Video Device"
    Driver         "ati"
    Option         "AccelMethod" "UXA"
EndSection 

Section "Monitor"
    Identifier    "Configured Monitor"
            HorizSync    30-80
            VertRefresh    50-75
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
    DefaultDepth    16
    SubSection "Display"
        Modes        "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
EndSection

```

Things are better in 10.04 and even better in 10.10, but there are possible other problems there depending on hardware.  For me, 10.04 is the best yet, once I have the xorg.conf sorted properly.
I do have an ATI Card but I only run at 1024 x 768. How do I change my screen to 16 bit resolution.

Incidentally try Ubuntu 10 from a DVD I had no problem with background. I expect the obvious thing is to upgrade.

---

### Post by matt_symes on 2010-11-20
Hi

> How do I change my screen to 16 bit resolution.

```
Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
    **DefaultDepth**    **16**
    SubSection "Display"
        Modes        "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
EndSection
```

Kind regards

---

### Post by Miyavix3 on 2010-11-20
Try this:

Press Alt+F2, and type in gconf-editor (or run from the terminal)

Look at my screen shot, and navigate to that subfolder
[ desktop > gnome > background ]

Check to see if draw_background is checked.

If  not, check it.

---

### Post by bvpainter on 2010-11-21
Checked and was ticked.

---

