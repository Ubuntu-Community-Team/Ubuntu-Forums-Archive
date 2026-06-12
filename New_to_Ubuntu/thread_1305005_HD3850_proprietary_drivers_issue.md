---
title: "HD3850 proprietary drivers issue"
date: 2009-10-29
forum: New to Ubuntu
---

### Post by Ben Page on 2009-10-29
Hey all, long time since my last post. I have decided to give a new 9.10 a try after 8.10 as my last Ubuntu experience till now. I was unpleasantly surprised with my Koala experience...

I have installed 9.10 with no issues (I know it won't work with coo'n'quiet, so I disabled it before installing), Koala looks great, love the improvements and new built-in software solutions, everything works OTB - great stuff! BUT, my ATI HD3850 has issues! OTB it works with default Ubuntu drivers and everything is fine, but no 3d desktop effects, of course, I downloaded ATI proprietary drivers, rebooted, and got a black screen (in fact it's not even a blacks screen, monitor is turned off), but my TV suddenly switches to it's AV channel and Ubuntu is on TV :D. ATI drivers detect my TV as my primary display and I can't set my monitor as my primary display. I know 3850 has chip set limitations and that it can't display the desktop on both the monitor and the TV (only dual monitor), but I can't make Ubuntu work on my monitor, it works only on TV and in NTSC - while my TV is PAL, so no color either :(
Ubuntu says that it can not apply the selected settings when I set my monitor as my primary display...
Any help? Any hints? I would love to play with Ubuntu again it has come very close to OSX

---

### Post by sandyd on 2009-10-29
> **Ben Page said:**
> Hey all, long time since my last post. I have decided to give a new 9.10 a try after 8.10 as my last Ubuntu experience till now. I was unpleasantly surprised with my Koala experience...

I have installed 9.10 with no issues (I know it won't work with coo'n'quiet, so I disabled it before installing), Koala looks great, love the improvements and new built-in software solutions, everything works OTB - great stuff! BUT, my ATI HD3850 has issues! OTB it works with default Ubuntu drivers and everything is fine, but no 3d desktop effects, of course, I downloaded ATI proprietary drivers, rebooted, and got a black screen (in fact it's not even a blacks screen, monitor is turned off), but my TV suddenly switches to it's AV channel and Ubuntu is on TV :D. ATI drivers detect my TV as my primary display and I can't set my monitor as my primary display. I know 3850 has chip set limitations and that it can't display the desktop on both the monitor and the TV (only dual monitor), but I can't make Ubuntu work on my monitor, it works only on TV and in NTSC - while my TV is PAL, so no color either :(
Ubuntu says that it can not apply the selected settings when I set my monitor as my primary display...
Any help? Any hints? I would love to play with Ubuntu again it has come very close to OSX
i have this problem too, its kinda anoying. (except that mines connected to a 1280x1024)

have you tried running amdcccle and changing the settings there?

---

### Post by Ben Page on 2009-10-29
I have tried to configure drivers through xorg.conf, that is what I did last time to enable TV-Out with my nVidia card, but it does not work with HD3850, when I reboot Ubuntu sends me to "verbose" mode, x11 is not running at all...What is amdcccle, is it like CCC in windows? Do I have to download it additionally?

---

### Post by Ben Page on 2009-10-29
LOL! Found a solution!
It&#347; simple, if you want the desktop to appear on the monitor - unplug the TV :p
Lame display priority by ATI/AMD drivers, now if I want to boot to Ubuntu, I have to unplug my TV, otherwise i&#314;l get TV only output and it&#347; impossible to switch to monitor while the TV is plugged in #-o
Way to go ATI! ](*,)

---

