---
title: "How can Ubuntu not use xorg.conf?"
date: 2009-03-31
forum: New to Ubuntu
---

### Post by slughappy1 on 2009-03-31
I am using Ubuntu 8.10 Intrepid Ibex and when I check the file /etc/X11/xorg.conf it is an empty file. Why is that? All the versions of Ubuntu before were full of information.

---

### Post by mcduck on 2009-03-31
Ubuntu now detects your hardware at boot time and automatically creates correct configurations (in RAM). So if you change your video card or monitor and boot the machine everything should still work and the desktop should run on a resolution suitable for the new monitor.

xorg.conf is still used, every setting you put there is respected and overrides the automatic settings.

---

### Post by adult swim on 2009-03-31
since 8.04 Xorg uses hal to do input configuration instead of xorg.conf
you can read more here [https://wiki.ubuntu.com/X/Config/Input#hal](https://wiki.ubuntu.com/X/Config/Input#hal)

---

### Post by slughappy1 on 2009-03-31
Thanks for your quick answers!

---

### Post by Bruce M. on 2009-04-05
> **mcduck said:**
> Ubuntu now detects your hardware at boot time and automatically creates correct configurations (in RAM). So if you change your video card or monitor and boot the machine everything should still work and the desktop should run on a resolution suitable for the new monitor.

xorg.conf is still used, every setting you put there is respected and overrides the automatic settings.

OK, but by stripping out my setting from before how do I know exactly what to put back?

---

