---
title: "DVD problem"
date: 2009-03-06
forum: New to Ubuntu
---

### Post by suomalainen on 2009-03-06
Ubunteros,

My store bought DVD's are playing back in mplayer and VLC in black and white only.... BUT THEY ARE COLOR MOVIES!!!!

What can I look at to make problem go away?

Thanks!

---

### Post by Xiong Chiamiov on 2009-03-07
Take a look at [this](https://bugs.launchpad.net/ubuntu/+source/totem/+bug/149791) bug report.  There's a solution half-way down the page that might work for you.

---

### Post by suomalainen on 2009-03-08
Xiong Chiamiov,

Actually, I found the following and it solved the problem. Heres's what I did:

Open up a terminal window Applications>Accessories>Terminal

enter the command: gstreamer-properties

Then choose:

Select Video>Output> X Window System (No Xv)

NOTE to Above, there are four options:
1 Auto Detect
2 X Window System (No Xv)
3 X Window System (X11/Shm/Xv)
4 Custom

When I re-inserted a dvd mplayer presented my movie in color! Then when I tried VLC it was still Black & White. I rebooted my PC and VLC then played my DVD in color.

Would you know by any chance what the command listed above modified and/or changed?

Thanks once again!

---

### Post by suomalainen on 2009-03-08
By the way, does anyone know if VLC is suppose to play sound/audio when you are viewing an iso ?????


Thanks!

P.S. I played via VLC a ISO and I saw picture but no sound.

---

