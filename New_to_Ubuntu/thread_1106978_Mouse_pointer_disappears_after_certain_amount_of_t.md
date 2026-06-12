---
title: "Mouse pointer disappears after certain amount of time"
date: 2009-03-26
forum: New to Ubuntu
---

### Post by k10chen on 2009-03-26
hi all...

searched the forums but couldnt find anything, when i start ubuntu, the mouse pointer is there and everything is fine, but after leaving it for a few hours, after the screen goes black (not hibernate, i have Wubi right now), the mouse pointer disappears. 

the mouse still works, i just cant see the pointer, it can still right click, and i can use the "press control to see mouse" thing to find out where it is. 

any help?

---

### Post by LowSky on 2009-03-26
Sounds like a Wubi issue, best option is to turn off the screen saver and to turn off power managemnt of turning off the screen.

---

### Post by billgoldberg on 2009-03-26
I found this bug old bug report. It could be related, or it could be Wubi related.

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-nv/+bug/63905https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-nv/+bug/63905](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-nv/+bug/63905https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-nv/+bug/63905)

The bug report says it has something to do with the open source Nvidia driver and xorg.

Are you using the open source driver?

Someone also said that switching to a different terminal and then switching back makes the mouse come back (press ctrl+alt+f1 and then ctrl+alt+f7).

---

### Post by k10chen on 2009-03-26
i will try this tonight, the power management  and the nvidia driver suggestion

thanks guys

i updated the hardware driver last night, so im not sure if that will help.

---

