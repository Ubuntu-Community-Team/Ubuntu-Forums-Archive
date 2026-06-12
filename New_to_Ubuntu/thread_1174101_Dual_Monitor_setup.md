---
title: "Dual Monitor setup"
date: 2009-05-30
forum: New to Ubuntu
---

### Post by MrChainBlueLightnin on 2009-05-30
I have a Dell 1082L CRT with Voodoo3 and a Gateway VX700 CRT with a Matrox millennium video card.  I am not sure what to add to xorg to allow both to be hooked up.
Here is xorg screenshot.

Section "Device"
    Identifier    "Configured Video Device"
    Option        "UseFBDev"        "true"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
    HorizSync    30-69
    VertRefresh    50-120
EndSection

Section "Monitor"
    Identifier    "Configured Monitor 2"
    HorizSync    30-86
    VertRefresh    50-130
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection

---

### Post by Paddy Landau on 2009-05-30
I hassled for a long time with xorg when I first set up dual monitor...

... Only to find out, later, that xorg is not something you necessarily need to worry about.

I reset my xorg to the original, and used xrandr instead; it's much easier. Also, xorg is deprecated, according to what I've read.

Here's the link to start you off:

[http://www.thinkwiki.org/wiki/Xorg_RandR_1.2](http://www.thinkwiki.org/wiki/Xorg_RandR_1.2)

You can reset your xorg.conf by typing the following in a terminal (remember to back you your xorg.conf first!):
```
sudo dpkg-reconfigure -phigh xserver-xorg
```The only change that I had to make to xorg.conf was to add the virtual desktop size. Here is the section with my changes; all I did was add the three lines starting with *SubSection*.
```
Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
    SubSection    "Display"
        Virtual    2560 1024
    EndSubSection
EndSection
```I understand that the later versions of Ubuntu (I still use 8.04) have better screen handling; you may get some luck with System -> Preferences -> Screen Resolution.

Another hint: Ubuntu seems to prefer your main screen on the left (don't ask me why!). If you put it on the right, it's a bit more hassle.

Good luck.

---

### Post by MrChainBlueLightnin on 2009-05-31
I have both CRT's connected to PCI cards.  Only the Dell with voodoo shows up when i run x randr.

---

### Post by Paddy Landau on 2009-05-31
> **MrChainBlueLightnin said:**
> I have both CRT's connected to PCI cards.  Only the Dell with voodoo shows up when i run x randr.
Sorry, I don't know what you can do there. Let's hope someone with more knowledge sees this thread.

Have you searched the other forums?

---

