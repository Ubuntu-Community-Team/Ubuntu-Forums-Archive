---
title: "screeeeen"
date: 2009-10-18
forum: New to Ubuntu
---

### Post by desmane on 2009-10-18
Hi, 

I have a laptop, docking and external monitor. I'd like to create a shortcut and need some help with the terminal command. In words, it should do something like this: 

*Disable internal Monitor, enable external with 1680x1050, switch off mirror screen*


```
~$ xrandr
Screen 0: minimum 320 x 200, current 2960 x 1050, maximum 8192 x 8192
VGA1 disconnected (normal left inverted right x axis y axis)
LVDS1 connected (normal left inverted right x axis y axis)
   1280x800       60.0 +   50.0  
   1024x768       85.0     75.0     70.1     60.0  
   832x624        74.6  
   800x600        85.1     72.2     75.0     60.3     56.2  
   640x480        85.0     72.8     75.0     59.9  
   720x400        85.0  
   640x400        85.1  
   640x350        85.1  
HDMI1 disconnected (normal left inverted right x axis y axis)
DP1 disconnected (normal left inverted right x axis y axis)
HDMI2 connected 1680x1050+1280+0 (normal left inverted right x axis y axis) 473mm x 296mm
   1680x1050      60.0*+
   1280x1024      75.0  
   1024x768       75.1     70.1     60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3     56.2  
   640x480        72.8     75.0     66.7     60.0  
   720x400        70.1  
DP2 disconnected (normal left inverted right x axis y axis)
DP3 disconnected (normal left inverted right x axis y axis)

```


Not really important - but it would be extremely awesome if ubuntu would detect the docking station and do this automatically, on remove it hops back to the internal. I never use extended screen or - of course - lower resolution! (Fn+F7 cycles through a lot of possible confs)
But, dont worry about it no need to get lazy. If you could help me with xrandr, I'd be happy!!!!!

---

### Post by desmane on 2009-10-18
well.. sometimes it helps to just write the question down .......... maybe someone needs it, check also [http://ubuntuforums.org/showthread.php?t=1086384](http://ubuntuforums.org/showthread.php?t=1086384)

```
#!/bin/bash
export season=`xrandr | grep LVDS1 | cut -c18-21`
echo " * The season is" $season
if [ "$season" == 'norm' ]; then
        xrandr --output LVDS1 --mode 1280x800
	xrandr --output HDMI2 --off
else
        xrandr --output HDMI2 --mode 1680x1050
	xrandr --output LVDS1 --off
fi
```

is there an event i can put it, when I put my laptop on the dock or the external monitor is plugged?

---

