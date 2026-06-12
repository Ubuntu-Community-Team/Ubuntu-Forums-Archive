---
title: "Screen resolution to 1920x1200 on T61 WSXGA+?"
date: 2010-04-17
forum: New to Ubuntu
---

### Post by robotsari on 2010-04-17
I recently upgraded to Ubuntu 9.10 64 bit and now I can't get at the 1920x1200 resolution that I used to have under 9.04 and 8.10. I've tried a billion fixes, including making & updating xorg.conf. I've tried solutions posted in these threads:

[http://ubuntuforums.org/showthread.php?t=83973](http://ubuntuforums.org/showthread.php?t=83973) - borked my computer, had to insert install disk, mount my FS and delete the xorg.conf.
[http://ubuntuforums.org/showthread.php?t=1433827](http://ubuntuforums.org/showthread.php?t=1433827) - did nothing
[http://www.ubuntugeek.com/how-change-display-resolution-settings-using-xrandr.html](http://www.ubuntugeek.com/how-change-display-resolution-settings-using-xrandr.html) - doesn't work:


```

~$ xrandr
Screen 0: minimum 320 x 200, current 1680 x 1050, maximum 8192 x 8192
VGA1 disconnected (normal left inverted right x axis y axis)
LVDS1 connected 1680x1050+0+0 (normal left inverted right x axis y axis) 331mm x 207mm
   1680x1050      60.1*+   84.9     74.9     69.9     60.0     50.1  
   1600x1024      60.2  
   1400x1050      85.0     74.8     70.0     60.0  
   1280x1024      85.0     75.0     60.0  
   1440x900       59.9  
   1280x960       85.0     60.0  
   1360x768       59.8  
   1152x864      100.0     85.1     85.0     75.0     75.0     70.0     60.0  
   1024x768       85.0     75.0     70.1     60.0  
   832x624        74.6  
   800x600        85.1     72.2     75.0     60.3     56.2  
   640x480        85.0     72.8     75.0     59.9  
   720x400        85.0  
   640x400        85.1  
   640x350        85.1  
DVI1 disconnected (normal left inverted right x axis y axis)
~$ cvt 1920 1200
# 1920x1200 59.88 Hz (CVT 2.30MA) hsync: 74.56 kHz; pclk: 193.25 MHz
Modeline "1920x1200_60.00"  193.25  1920 2056 2256 2592  1200 1203 1209 1245 -hsync +vsync
~$ xrandr --newmode "1920x1200_60.00"  193.25  1920 2056 2256 2592  1200 1203 1209 1245 -hsync +vsync
~$ xrandr --addmode LVDS1 1920x1200_60.00
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  149 (RANDR)
  Minor opcode of failed request:  18 (RRAddOutputMode)
  Serial number of failed request:  25
  Current serial number in output stream:  26

```

And when I display xrandr again the new added mode isn't in the right section; rather it's below the DVI1 statement as shown above:

```

DVI1 disconnected (normal left inverted right x axis y axis)
  1920x1200_60.00 (0x13c)  193.2MHz
        h: width  1920 start 2056 end 2256 total 2592 skew    0 clock   74.6KHz
        v: height 1200 start 1203 end 1209 total 1245           clock   59.9Hz

```

I don't really know exactly what graphics card i have (how do I find out?) but the specs on my computer are these: [http://www.thinkwiki.org/wiki/Category:T61](http://www.thinkwiki.org/wiki/Category:T61)

This is real frustrating because it was working fine in 9.04 and 8.10; I know how to edit xorg.conf since I had done it many times on other linux installs, but the edits just simply aren't working. Attached is the xorg.conf that I thought should work but does nothing to help (when I reboot, the 1920x1200 resolution still doesn't appear in System > Preferences > Display)

Thank you so much. I hate using Eclipse without 1900x1200 resolution, and I need to use it a lot this weekend :-\

---

### Post by drascus on 2010-04-18
well not knowing what your graphics card is and what might have happend to your drivers on upgrade here are two things to do. 

type: lspci in terminal one of the things that should pop up is your graphics card. post that here.

check System->Administration->Hardware Drivers and see if you have the latest driver installed for your card. if not install it. If you do reinstall it. then restart. 

Also when you know what graphics card you have search in launchpad bug reports and see if anyone has already reported a bug to that affect: [https://bugs.launchpad.net/ubuntu](https://bugs.launchpad.net/ubuntu)

please post any solutions to your problem back into this post for later use.

---

