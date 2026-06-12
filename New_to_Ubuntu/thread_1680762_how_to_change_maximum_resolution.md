---
title: "how to change maximum resolution"
date: 2011-02-03
forum: New to Ubuntu
---

### Post by opendevlite on 2011-02-03
in the terminal, when i xrandr, how do i increase the maximum value?

i mean the word maximum

my hardware is on my signature

$ xrandr

```
Screen 0: minimum 320 x 200, current 2000 x 1024, **maximum** 2048 x 2048
VGA connected 1280x1024+720+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1360x768       59.8  
   1152x864       60.0  
   1024x768       60.0  
   800x600        60.3  
   640x480        59.9  
   1280x1024_60.00   59.9* 
LVDS connected 720x400+0+624 (normal left inverted right x axis y axis) 0mm x 0mm
   1024x600       60.1 +
   800x600        85.1     72.2     75.0     60.3     56.2  
   640x480        85.0     72.8     75.0     59.9  
   720x400        85.0* 
   640x400        85.1  
   640x350        85.1  


```

---

### Post by realzippy on 2011-02-03
You have to generate a modeline for your desired resolution,eg with the cvt command,then add the mode to your display,then set the mode.
[http://wiki.debian.org/XStrikeForce/HowToRandR12](http://wiki.debian.org/XStrikeForce/HowToRandR12)
Which display you want at which resolution?

---

### Post by henson.1001p on 2011-02-03
If you don't mind just faking your resolution (I often do it on my netbook, where a dialog box is sometimes out-of-site) then you can type:

xrandr --output WHATEVER --scale 1.2x1.2

Where 1.2 stands 120%, or %20 larger than the standard display. We have to list it twice because we have to specify the change for x and y coordinates.

---

