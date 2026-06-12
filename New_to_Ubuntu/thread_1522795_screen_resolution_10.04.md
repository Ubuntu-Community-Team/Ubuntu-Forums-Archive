---
title: "screen resolution 10.04"
date: 2010-07-02
forum: New to Ubuntu
---

### Post by rjs1064 on 2010-07-02
I have an nvidia fx5200 video card and have installed the 173.14.22 driver. The monitor is an old crt 17inch which isn't detected so I end up with 800x600 resolution. I used to have jaunty and had to add horizsync and vert refresh values to xorg.conf after which it worked fine at 1280x768. Stupidly I didn't think to keep a copy of xorg.conf when I did a clean install and it is now only a few lines long and I have no idea where to put in any values. I can't remember what I was told to do last time, can anyone help?
 I have tryed dpkg- reconfigure xserver-xorg but get an error, and several other things I tryed left me with no x at all.

---

### Post by ajgreeny on 2010-07-02
Try:-

```
Section "Monitor"
    Identifier    "Configured Monitor"
            HorizSync    30-80
            VertRefresh    50-75

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
with your own figures for sync rates,  resolutions and colour depth.

---

### Post by rjs1064 on 2010-07-04
thanks alot. I needed to add an endsection to monitors and then it worked great. If anyone is having the same trouble check the output of /var/log/xorg.0.log which gives a running comentary on the use of xorg.conf by the computer.

---

