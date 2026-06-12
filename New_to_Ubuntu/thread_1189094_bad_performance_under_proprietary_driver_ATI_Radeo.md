---
title: "bad performance under proprietary driver ATI Radeon 4350"
date: 2009-06-16
forum: New to Ubuntu
---

### Post by alienkid10 on 2009-06-16
I just got a new graphics card and was hoping to use Blender in Ubuntu again like I did in 8.10, so I boot Ubuntu and "restricted drivers available" so I am like "ok, cool." I click activate reboot and BAM stuck in a small sqaure of my screen at something like 1280x768 screen res with very bad performance. So I thought, "maybe it's Compiz." Compiz wasn't on so that's not it. Next I am like "it reconized my monitor before maybe it's doesn't now." I open "Display" and I was right! So I change my screen res to 1024x786(it didn't change though) and now I am stuck with a very small screen still and horrble permormance! My old card was an Intel card and I was hoping to fix my graphics bugs and beable to use Compiz again. My monitor is a ViewSonic E771 CRT. I am using Wubi to install and was hoping to partition sometime but that's mom's call. So any ideas or fixes? I can post the xorg log file if you want it. My Windows OS works fine BTW. Ubuntu is smooth w/o driver but no 3D so no Blender oe Compiz.

---

### Post by Johan-Steyn on 2009-06-16
Hi alienkid10,

How was your graphics card's performance before installing the ati restricted diver?

I've read on numerous forums that the safest bet would be to stick with the ubuntu default xorg drivers.

Try un-installing the ati restricted drivers from add/remove or synaptic, it ought to restore xorg.

If not, post back.

Regards,

JS

---

### Post by Jazzy_Jeff on 2009-06-16
This is why I recommend using nVidia cards. They seem to just work.

---

### Post by alienkid10 on 2009-06-16
currently removed the restricted drivers and it knows my monitor etc. Same performance as on Intel card except the main piece 3D and compiz(+emerald) support. If the OSS driver had those 2 things I would be fine. But no.

EDIT: [Jazzy_Jeff]("http://ubuntuforums.org/member.php?u=388464"): buy me a new PSU. Yes I am pissed right now.

---

### Post by alienkid10 on 2009-06-16
Bump

---

### Post by alienkid10 on 2009-06-17
Bump

---

### Post by alienkid10 on 2009-06-17
I figured it out! After installing the latest Catayst on a fresh install of wubi and doing aticonfig --initial I think that changed my monitor in the config file. Would someone check it and tell me how to change it back to the ViewSonic E771 CRT VGA monitor?
```

Section "ServerLayout"
    Identifier     "aticonfig Layout"
    Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
EndSection

Section "Monitor"
    Identifier   "aticonfig-Monitor[0]-0"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
EndSection

Section "Device"
    Identifier  "aticonfig-Device[0]-0"
    Driver      "fglrx"
    Option "VideoOverlay" "on"
    Option "OpenGLOverlay" "off"
    BusID       "PCI:1:0:0"
EndSection

Section "Screen"
    Identifier "aticonfig-Screen[0]-0"
    Device     "aticonfig-Device[0]-0"
    Monitor    "aticonfig-Monitor[0]-0"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection

```

---

### Post by lavinog on 2009-06-17
can you post /etc/X11/xorg.conf

---

### Post by alienkid10 on 2009-06-17
look above you post. in the code box.

---

### Post by alienkid10 on 2009-06-19
bump

---

