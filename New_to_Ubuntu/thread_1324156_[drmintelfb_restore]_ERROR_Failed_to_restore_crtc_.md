---
title: "[drm:intelfb_restore] *ERROR* Failed to restore crtc configuration: -22"
date: 2009-11-12
forum: New to Ubuntu
---

### Post by lusierra77 on 2009-11-12
I use a Samsung Q1 Ultra trying to upgrade a Wubi 
to a 9.10. I am having this problem with a fresh Wubi 9.10 
install, or upgrade from 9.04. After install 9.10, reboot, the screen keeps flashing with
 
[SIZE=2][COLOR=black]**_[drm:intelfb_restore] *ERROR* Failed to restore crtc configuration: -22_**[/COLOR][/SIZE]
 
until inactivity makes the screen go blank.
 
also trying ubuntu remix same problem

---

### Post by border on 2010-05-31
any updates on this?
I also get this error when booting ubuntu 9.10 lpia on the samsung q1 ultra

It also sais: screens found, but none have a usable configuration.

I tried manually adding configurations with this gentoo intel guide
[http://www.gentoo-wiki.info/Intel_GMA#Manual_modesetting](http://www.gentoo-wiki.info/Intel_GMA#Manual_modesetting)
but to no avail

---

### Post by lusierra77 on 2010-05-31
sorry my English is very bad,
 solution to de problem, update to ubuntu 10.04, work out box, and if your Q1 runs perfect recommended kubuntu notebook edition, is awesome, if not then tray ubuntu notebook or lubuntu. only problems is touch screen work outbox but need calibration, non of the old how to works,

---

### Post by border on 2010-06-01
I know that 10.04 works out of the box (only the touchscreen doesn't). But I would really want 9.10 to work. And preferebly the lpia architecture version.

But if it doesn't, how do I calibrate the touchscreen to make it work well in 10.04?
Any suggestions on that matter?

thanks

---

### Post by ulugeyik on 2010-07-06
> **border said:**
> any updates on this?
I also get this error when booting ubuntu 9.10 lpia on the samsung q1 ultra

It also sais: screens found, but none have a usable configuration.

I tried manually adding configurations with this gentoo intel guide
[http://www.gentoo-wiki.info/Intel_GMA#Manual_modesetting](http://www.gentoo-wiki.info/Intel_GMA#Manual_modesetting)
but to no avail

This is an old error. Adding i915.modeset=0 to kernel args solved the problem for me.

---

