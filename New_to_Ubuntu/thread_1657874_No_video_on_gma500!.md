---
title: "No video on gma500!"
date: 2011-01-01
forum: New to Ubuntu
---

### Post by sheepo1 on 2011-01-01
Hi! I've been using ubuntu 10.10 UNE on my Dell Mini 1010 for about a week. I set up the wifi and everything but because of the gma500 chipset I can't play video games or get video playback. My main use is animation (I'm an animator) so I sorta need it. I tried these 2 methods:
[https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo/](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo/)
[http://ubuntuforums.org/showthread.php?t=1229345](http://ubuntuforums.org/showthread.php?t=1229345)
and they worked great but then the computer would refuse to boot up unless it was in failsafe graphics mode.
I'm not sure if there's a solution to this other than install a different but I don't really want to do that because I've had to install it 4 times because of the video drivers.

So... any other ideas? I think it has to do with the xorg file because in failsafe graphics mode I was fooling around and cleared the xorg file and it worked but that took away the video.

Thanks in advance!
:confused:

---

### Post by sheepo1 on 2011-01-01
Just wanted to make clear my specs.....
Dell mini 1010
ubuntu remix 10.10 running in desktop mode (won't work in netbook)
gma500 poulsbo chip

---

### Post by mikewhatever on 2011-01-03
After installing the driver in 10.10, xorg.conf looks like this:

> Section "DRI"
        Mode    0666
EndSection

Section "Device"
        Identifier      "Configured Video Device"
        Driver  "psb"
EndSection


Try putting it back and delete whatever else is there.

---

