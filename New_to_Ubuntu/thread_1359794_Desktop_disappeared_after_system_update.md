---
title: "Desktop disappeared after system update"
date: 2009-12-20
forum: New to Ubuntu
---

### Post by poolse_heks on 2009-12-20
I run UNR Koala 9.10 on Dell Mini 10. After some fiddling with drivers I made it run perfectly (I needed Poulsbo drivers to get the screen resolution right and had to play with alsamixer to get the microphone and audio working) - although I confess I am a beginner in the Linux world, so I basically copy-paste stuff I find on fora and Linux troubleshooting websites. 
Anyway, my Koala was running smoothly until yesterday (I think) when I downloaded updates suggested by the update manager (some of them, for Poulsbo were listed as not authorized or sth like this, although I have no clue if it is relevant to my problem) and ever since, when I start my machine, I don't see my desktop. That is, I can see the wallpaper and the top panel, but I can't see any icons that would let me run applications. The Ubuntu sign in the top left corner is inactive. Plus the sound is gone (although it worked perfectly before).
Screen resolution is fine and the system seems to be generally ok, except the lack of the interface that would allow me to use it...
I will appreciate any help and please remember I'm a newbie. Thanks!

Some info about my system: Dell Mini 10
Processor    2x Intel(R) Atom(TM) CPU Z530 @ 1.60GHz
Memory    1017MB 
Operating System    Ubuntu 9.10
Display Resolution    1024x576 pixels
OpenGL Renderer    Unknown
X11 Vendor    The X.Org Foundation
Audio Adapter    HDA-Intel - HDA Intel MID
SCSI Disks
ATA WDC WD1600BEVT-7    
Kernel    Linux 2.6.31-16-generic (i686)
Compiled    #53-Ubuntu SMP Tue Dec 8 04:01:29 UTC 2009
C Library    GNU C Library version 2.10.1 (stable)
Default C Compiler    GNU C Compiler version 4.4.1 (Ubuntu 4.4.1-4ubuntu8)
Distribution    Ubuntu 9.10
Desktop Environment    GNOME 2.28.1

---

### Post by Temposs on 2009-12-20
Something you could do is drop down to a terminal by typing Ctrl-Alt-F1. Login if necessary.

Then, remove your GNOME settings like so:

```
rm -rf .gnome .gnome2 .gconf
```

After that, restart in normal boot mode and see if you get anything working better. When you delete those directories using the above command, Ubuntu automatically generates the default settings for you. If your GNOME settings are the problem(which is my first instinct), this would fix it.

---

### Post by poolse_heks on 2009-12-20
Temposs, thanks for your reply. I followed your advice, as a result I have default background and top panel now but it didn't solve my problem. Still nothing to navigate with...

---

### Post by Temposs on 2009-12-20
Are you able to add things to the panel at all? Can you right click on the top panel and do "Add To Panel"?

If you can, you can add a menu, which will give you the ability to do things in the graphical mode.

---

### Post by poolse_heks on 2009-12-22
No, I can't add anything to the panel.
I operate through AltF2 and then run firefox or nautilus but it is far from convenient...
Well, still no clue what is wrong...

---

