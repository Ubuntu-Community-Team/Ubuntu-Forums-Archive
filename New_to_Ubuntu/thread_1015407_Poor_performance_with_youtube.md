---
title: "Poor performance with youtube"
date: 2008-12-18
forum: New to Ubuntu
---

### Post by mancrow on 2008-12-18
I installed all the plugins for flash but the performance with youtube isnt very good at all.. my computer is fast enough and my internet is 16megs so that isnt the problem... is there any fix for this as i use youtube alot but i cant watch any videos...

thanks for the help

---

### Post by Valtiel on 2008-12-18
Did you try the non-free flash plugin?

1- Synaptic
2- Search for "flashplugin-nonfree"
3- Select it
4- Click on "Apply" at the top
5- The installation will take place


This is the plugin I use. The Free version didn't really do it for me. Now I can even wash movies in HULU without any problems.

---

### Post by anjilslaire on 2008-12-18
Better yet, grab Adobe's Flash 10 deb from the Adobe page
[http://get.adobe.com/flashplayer/]("http://get.adobe.com/flashplayer/")

---

### Post by zim2dive on 2008-12-21
> **anjilslaire said:**
> Better yet, grab Adobe's Flash 10 deb from the Adobe page
[http://get.adobe.com/flashplayer/]("http://get.adobe.com/flashplayer/")

I am using the 64-bit plugin from the Adobe site, Shockwave Flash 10.0 d21, and YouTube is good at the default size, but if I expand to full screen, the performance goes in the toilet... any way to fix this?

---

### Post by evilkastel on 2008-12-21
please give your system specs. maybe your graphics card is not good or is *too* good. nvidia linux drivers have isuues with the latest cards.

---

### Post by zim2dive on 2008-12-22
> **evilkastel said:**
> please give your system specs. maybe your graphics card is not good or is *too* good. nvidia linux drivers have isuues with the latest cards.

Acer AX1200, AMD 5200 (dual-core 2.7GHz), nVidia 8200

My 2002 powermac has better Flash performance :(

---

### Post by ken22 on 2008-12-22
Are you using 3D desktop effects? XGL windowing?

These can sometimes cause issues with video playback.

---

### Post by zim2dive on 2008-12-22
> **ken22 said:**
> Are you using 3D desktop effects? XGL windowing?

These can sometimes cause issues with video playback.

I'm not using anything that wasn't default.  Brand new 8.10 install, Flash 10.0 d21 install, and upgrade to nVidia 177.82.

---

### Post by zim2dive on 2008-12-25
Under Ubuntu, System->Preferences->Appearance->Visual Effect, change from the default to None.

This made YouTube watchable for me at full screen.

Unfortunately it is NOT enough to make The Daily Show watchable at full screen, nor hulu.

Edit: this was a 32-bit install of 8.10.  Also credit to this post [http://ubuntuforums.org/showpost.php?p=5381686&postcount=18](http://ubuntuforums.org/showpost.php?p=5381686&postcount=18) where I found the hint.

---

### Post by caeroe on 2008-12-25
Apparently some out there have perfect Flash performance, but never reply back with their setup. I'm curious what Flash version, video card, and browser they are using.

My Flash video performance is also horrible if I go to fullscreen at Youtube or Hulu.  It obviously shouldn't be, considering the PC and connection speed is well beyond sufficient.

Ubuntu 8.10 x64
Flash 10 x64 released 12/16
Nvidia 8800GT 512mb, 180.06 beta drivers (the supported 177 drivers made no difference)
FiOS connection, 10mb downstream

I've tried Opera's v10 beta browser and Firefox 3.0.5.  I also made sure I've tested with a clean install of drivers and plug-ins.

---

### Post by zim2dive on 2008-12-30
I have the 8200.. this seems counter-intuitive, but try rolling back to the 173 driver in the Intrepid Hardware Driver panel.

I now have very speedy (or at least much speedier) full screen flash.

Alas I also have no digital sound out HDMI :(

But at least its a clue.

---

### Post by Steve05TSX on 2008-12-30
noticed this too.  I'm rolling back to 173 as we speak

---

### Post by Steve05TSX on 2008-12-30
not really any better on 1.73 for me (8600 GT)

---

### Post by kansasnoob on 2008-12-30
Read my post #10 here:

[http://ubuntuforums.org/showthread.php?t=1025665](http://ubuntuforums.org/showthread.php?t=1025665)

---

