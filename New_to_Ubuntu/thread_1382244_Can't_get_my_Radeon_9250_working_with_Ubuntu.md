---
title: "Can't get my Radeon 9250 working with Ubuntu"
date: 2010-01-15
forum: New to Ubuntu
---

### Post by rimshot4 on 2010-01-15
I just installed Ubuntu on my IBM in a dual-boot configuration. My ATI Radeon 9250 is "working," which is to say my monitor's plugged into it, but I can only get resolutions up to 1024x764 and "Extra Visual Effects" won't work.

Ideas?

---

### Post by ajgreeny on 2010-01-15
This is a problem of karmic and the open source ati/radeon driver, I'm afraid.  The only way to get the desktop effects is either to run at a lower res, as you found, or to use 16 bit colour, though you will still probably get some artifacts show in movies and some other applications.  I had hoped this problem would be overcome by updates, but it has not been so far and does not look likely.

Here is my /etc/X11/xorg.conf to show you how I did it in karmic.
```
Section "Device"
    Identifier    "Configured Video Device"
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

---

### Post by rimshot4 on 2010-01-21
After messing with it and messing with it, I finally tried other distros, including OpenSuSe and Mandviva. (Neither one was nearly as fast or stable on my machines as Ubuntu, BTW.) But graphics still sucked. 

Video started getting choppy even in windows. Then, it up and died. No output. Good riddance. 

So O guess I'll never know what I can chalk up to poor support from ATI and what I can chalk up to premature hardware failure.

I switched on the onboard Intel and now run Compiz with a moderate level of effects (including the Cube) and video the same or better as what I got under Windows with the ATI card. 

Problem: ATI 9250. Solution: Chuck it!

I'll be getting a new card in a month or so. It won't be ATI. :D

---

### Post by clhsharky on 2010-01-21
HI

ATI9250 is now 6 generations old, what do you mean premature?
You still have warranty!

---

### Post by rimshot4 on 2010-01-21
> **clhsharky said:**
> HI

ATI9250 is now 6 generations old, what do you mean premature?
You still have warranty!

My hardware should last forever, just because it's mine. :P

---

### Post by Mark Phelps on 2010-01-21
> **rimshot4 said:**
> My hardware should last forever, just because it's mine. :P

Your hardware does last "forever" -- it's just that the hardware vendors stop writing new drivers for older hardware after a while.

---

### Post by rimshot4 on 2010-01-22
> **Mark Phelps said:**
> Your hardware does last "forever" -- it's just that the hardware vendors stop writing new drivers for older hardware after a while.

Actually my video card didn't last forever. It's definitely fried. For Windows too.

---

