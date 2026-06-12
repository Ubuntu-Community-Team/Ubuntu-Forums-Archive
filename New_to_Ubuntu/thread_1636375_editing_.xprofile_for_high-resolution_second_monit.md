---
title: "editing .xprofile for high-resolution second monitor"
date: 2010-12-03
forum: New to Ubuntu
---

### Post by bdevine on 2010-12-03
Hi,

I just got a new toy!  It's a high-resolution monitor attached to my laptop, but unfortunately, I can't access its full capabilities.

Issuing xrandr shows:
```

Screen 0: minimum 320 x 200, current 2560 x 720, maximum 2560 x 720
VGA-0 connected 1280x720+0+0 (normal left inverted right x axis y axis) 553mm x 311mm
   1280x720       60.0* 
   800x600        60.3  
   640x480        59.9  
   720x400        70.1  
LVDS connected 1280x720+1280+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1280x720       59.9* 
   800x600        60.3     59.9  
   640x480        59.9     59.4  

```

Issuing cvt 1920 1080 yields:
```

# 1920x1080 59.96 Hz (CVT 2.07M9) hsync: 67.16 kHz; pclk: 173.00 MHz
Modeline "1920x1080_60.00"  173.00  1920 2048 2248 2576  1080 1083 1088 1120 -hsync +vsync

```

I would like to modify the instructions found at [http://ubuntuforums.org/showthread.php?t=1474910](http://ubuntuforums.org/showthread.php?t=1474910), (which in turn builds on the wiki, although the discussion in that link claims the wiki is wrong at some points) to create an .xprofile file to accomodate both monitors.  Between the wiki possibly leading me astray and the addition of the second monitor, I'm nervous about tackling this alone.  Has anyone done this?

Any help much appreciated,

Brandon

---

### Post by wojox on 2010-12-03
What graphics card are you using?

---

### Post by bdevine on 2010-12-03
Thanks for responding!

```

$ lspci
....
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility X1400

```

---

