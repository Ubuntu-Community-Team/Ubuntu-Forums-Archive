---
title: "Xorg.config problems"
date: 2009-05-14
forum: New to Ubuntu
---

### Post by Drokles on 2009-05-14
```
Section "Monitor"
    Identifier     "SCT17-8BS"
    HorizSync        30 - 81
    VertRefresh    55 - 80
    Modeline "1280x1024" 151.83  1280 1360 1544 1888  1024 1024 1027 1072
EndSection

Section "Device"
    Identifier     "GeForce 7900 GT/GTO"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "GeForce 7900 GT/GTO"
    Monitor        "SCT17-8BS"
    DefaultDepth    24
    Option         "AddARGBGLXVisuals" "True"
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024_75.00"
    EndSubSection
EndSection

```My problem here is that regardless of all this I still reboot into a lower resolution for some reason. I'm not sure where I went wrong. Any ideas?

At least now though I can "system > Preferences > Nvidia X server settings" to change the resolution to 1280x1024_75 after booting. This option was unavailable to me before.

I should prehaps mention that I use the 185.18.08 Nvidia driver.

Thanks!

~ Drokles

---

### Post by Zimmer on 2009-06-14
Modeline "1280x1024" 151.83  1280 1360 1544 1888  1024 1024 1027 1072

Creates a mode called "1280x1024"
The line
        Modes      "1280x1024_75.00"

looks for a mode called "1280x1024_75.00"   

See what the xorg.log has to say .....

[http://us.download.nvidia.com/XFree86/Linux-x86/185.18.14/README/index.html](http://us.download.nvidia.com/XFree86/Linux-x86/185.18.14/README/index.html)

---

