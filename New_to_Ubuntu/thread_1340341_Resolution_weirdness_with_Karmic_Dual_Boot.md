---
title: "Resolution weirdness with Karmic Dual Boot"
date: 2009-11-28
forum: New to Ubuntu
---

### Post by Fjodr on 2009-11-28
There are some issues with Ubuntu defaulting to a 800x600 resolution after a fresh install. I've encountered this everytime since 8.10, and (since I seem to be forgetting how I did it) solved it more than once.

After fixing it, all seems well for some time, only to start acting up again after a windows XP boot. It doesn't happen all the time, and most often a few restarts seem to fix it. Recently, after installing Karmic, this doesn't seem to work anymore. Anyone ever heard of a more permanent solution for this?

---

### Post by bertmanphx on 2009-11-28
Fjodr,
Do you have these problems with your Windows installation?
It sounds like either a bad cable, or monitor.

Either way, the EIDE (hope that's correct) is probably not being sent properly to the operating system upon boot.  With the latest versions of the X.org within Linux distros, the kernel, X, and such detect the hardware and set it up each time it boots.  If something changes, the screen resolution will change as well, to fit the hardware.
This works great, unless you have an older monitor that does not cough up the information at boot.  I've had this happen on a recent install.  I bought a new monitor, and it was perfectly setup each time.
I'm sure that an install of XP will NOT reset the resolution, I'm not sure about Vista or 7.  If you're running XP, it's possible that this problem is actually occurring, but because it's X settings are static, you do not see the effects.

bertmanphx

---

### Post by Fjodr on 2009-11-28
Interesting...
I'm using windows XP, and a rather old CRT monitor. Since Karmic doesn't use xorg.conf anymore it could be more of a problem than before. Still, it happened in other distributions and also didn't happen all the time.
A friend of mine had the same problem, also with a ubuntu/xp dual boot, and that a few restarts usually fixed it.

Would adding a xorg.conf make any difference here? I allready tried tinkering with it without much result, my old configs never seemed to fix the problem completely.

---

### Post by bertmanphx on 2009-11-28
Fjodr,
You can add your own xorg.conf file, and I do believe that X will follow it.  You'll have to do some searching on how to do that.

bermanphx

---

### Post by Fjodr on 2009-11-29
I've had a custom xorg.conf since Hardy, but it didn't allways help. Maybe I didn't configure it right, but I guess the real solution here is finding out why it actually works sometimes, and other times reverts to 800x600 after a windows boot. Something must me providing X with the right info most of the time but gets confused after a windows boot. Could it have something to do with Grub?

---

### Post by bertmanphx on 2009-11-30
Fjodr,
Grub should not have anything to do with your monitor resolution.
That being said, you CAN pass along certain arguments to the Kernel from Grub.  I'm not sure if, or how you can specify a screen resolution though.

bertmanphx

---

### Post by ukripper on 2009-11-30
ok let's start from bottom. can you confirm you have enabled System-->Administration-->hardware drivers there?

If you have then post your xorg.conf here.

and can you also tell us which reoslution you normally prefer running at?

---

