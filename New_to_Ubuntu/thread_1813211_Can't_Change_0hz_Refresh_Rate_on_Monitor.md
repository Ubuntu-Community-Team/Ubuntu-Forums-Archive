---
title: "Can't Change 0hz Refresh Rate on Monitor"
date: 2011-07-27
forum: New to Ubuntu
---

### Post by CastleD on 2011-07-27
When I go into display settings for my monitor the only option I have is 0 hz. The screen is slightly blurry, the optimal is supposed to be 75hz.  Otherwise it's at 1024x768 resolution which is correct.

I've searched around and it seems you have to edit xconf.org or do something with xandr. Not sure how to do that though. I have 82845G Intel integrated graphics (which I saw that other people had problems with), and I know all the specs of my Dell e772c Monitor.

How do I change the refresh rate?

---

### Post by mikewhatever on 2011-07-27
Try **xrandr --rate 75**. If that doesn't work, see the wiki on how to edit xorg.conf.
[https://wiki.ubuntu.com/X/Config/Resolution#Setting_resolution_changes_in_xorg.conf](https://wiki.ubuntu.com/X/Config/Resolution#Setting_resolution_changes_in_xorg.conf)

---

### Post by CastleD on 2011-07-28
I ended up fixing this problem, or so I thought. I followed the instructions on this page: [http://www.grenage.com/xorg.html](http://www.grenage.com/xorg.html) and this thread: [http://ubuntuforums.org/showthread.php?t=1611769&highlight=skatergirl&page=3](http://ubuntuforums.org/showthread.php?t=1611769&highlight=skatergirl&page=3)

I did:

```
gksu gedit /etc/X11/xorg.conf
```and edited in a new config. This:

```
Section "Monitor"
    Identifier "Monitor0"
    VendorName "DELL"
    ModelName "E772c"
    HorizSync 30 - 70
    VertRefresh 50 - 160
Modeline "1024x768_60.00"   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync
EndSection

Section "Device"
    Identifier "Device0"
    Driver "intel"
    VendorName "Intel 82845G"
EndSection

Section "Screen"
    Identifier "Screen0"
    Device "Device0"
    Monitor "Monitor0"
    DefaultDepth 24
    SubSection "Display"
        Depth 24
        Modes "1024x768"
    EndSubSection
EndSection
```I got my modeline with:

```
cvt 1024 768
```The only thing I wasn't sure about was the 24 bit depth. I probably should have changed it to 32. After I restarted my pc I went to display and it was 75hz and I had more hz and resolution choices. Success? Should be, 1024x768 at 75hz is optimal for me. That's what I had it on XP. 

No, first, my display was still kinda blurry. Then I had graphical glitches and Xubuntu kept freezing. Thankfully I erased the xorg.conf with $ sudo rm /etc/X11xorg.conf and was back to normal. Not sure what to do now. I thought that was going to work. I have a feeling this can't be fixed and Ubuntu is blurry with my set-up for whatever reason. I realize I have shitty integrated graphics but it was sharp under XP. I probably have no choice but to switch back. Oh well.

edit: maybe I screwed up my modeline. I think I put $ cvt 1024 768 75. Now I don't remember. Damn. I'll try it again.

---

### Post by Wim Sturkenboom on 2011-07-28
I don't think that you need that modeline.

Did you check the 75 Hz on the monitor (go into the menu and it should show it somewhere) or in the computer software? The monitor is the only thing that I trust to see which refresh rate is actually used; the computer software does not have a blooming idea.

---

