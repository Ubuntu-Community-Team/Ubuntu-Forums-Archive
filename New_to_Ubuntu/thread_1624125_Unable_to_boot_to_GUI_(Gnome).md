---
title: "Unable to boot to GUI (Gnome)"
date: 2010-11-17
forum: New to Ubuntu
---

### Post by search66 on 2010-11-17
Running 10.10 64-bit with no problems until today.  Today, I did a system update; and it appeared that one of my sources updated the NVIDIA drivers... now when I rebooted; I go straight to command line and unable to get into Gnome... I'll get these error(s).

API Mismatch: the nvidia kernel module has version 260.19.12 but this nvidia driver component had version 260.19.21

Failed to initialize the nvidia kernel module

xinit: no such file or directory

So... I'm sure there's a problem with the nvidia driver/kernel; Im just clueless on how to revert the kernel and/or driver... 

Edit: The source that updated the driver was x-swat
Thanks for your help!

---

### Post by TeoBigusGeekus on 2010-11-17
Either [update your kernel]("http://www.cyberciti.biz/faq/linux-kernel-upgrade-howto/") or [downgrade the nvidia driver.]("http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1556399")

---

