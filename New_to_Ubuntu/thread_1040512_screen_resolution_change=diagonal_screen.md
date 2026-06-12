---
title: "screen resolution change=diagonal screen"
date: 2009-01-15
forum: New to Ubuntu
---

### Post by UberHank on 2009-01-15
Hey folks.  I just upgraded my wife's computer to 8.10 in the hopes her video card (Radeon 9800) would run as well as mine (Radeon x1950) did when I upgraded.  I get Intrepid installed, activate the restricted drivers, and reboot.  When it comes back up it tells me it is in low graphics mode-- fine.  Resolution after logging in is something ridiculous, 1280x1024 I think.  That won't work with her monitor, way to high, so I changed it to something lower-- don't remember what and cannot see now.

After the pretty login screen, the desktop is slanted: upper left seems in the right place, but the right side is about 1/3rd of the way down the screen and everything else is blurry as heck.  This happened after I tried to change the resolution.  :confused:

I've scoured the forums for a solution but I am not sure what the problem even is!  I've reconfigured my xorg.conf a billion ways (okay, billion is a bit much) but even with a very basic one the screen is still messed up.   ](*,)

Any suggestions?  Thanks.

---

### Post by utnubuuser on 2009-01-16
Remove --purge the driver and re-install?

---

### Post by UberHank on 2009-01-19
Yeah, that is what I thought and tried to do (I think).  If you can give me step by step how to do that, I will try again.  Thank you so much for the suggestion!

Chuck

---

### Post by UberHank on 2009-01-19
Hmm...

Well, I got the graphics to work by replacing my xorg.conf with one called xorg.conf.failsafe.bak.  Interesting... Now it is seemingly working as before.  Thanks!

---

