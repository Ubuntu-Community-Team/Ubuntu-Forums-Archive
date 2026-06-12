---
title: "Touchpad not functioning correctly"
date: 2009-08-05
forum: New to Ubuntu
---

### Post by Sonic Alpha on 2009-08-05
Hi all,

I've just installed Ubuntu 9.04 on my laptop, and everything is working perfectly with the exception of the touchpad.

I can move the mouse pointer around, left click, right click, and scroll pages just fine. However, the tap to click functionality of the pad seems a little hit and miss (sometimes it works, other times I have to double tap).

I've read a few forum threads already, and have tried to use gsynaptics to cure the problem. However, it's complaining that I need to "set 'SHMConfig' to 'true' in xorg.conf or XF86Config to use GSynaptics." That option is not part of my xorg.conf file.

xorg.conf: -

```

Section "Device"
        Identifier      "Configured Video Device"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection

```

Any advice you can give, would be greatly appreciated.

Thanks :)

---

### Post by Sonic Alpha on 2009-08-05
Solved the problem myself, with a little help from [this page]("https://help.ubuntu.com/community/SynapticsTouchpad").

---

