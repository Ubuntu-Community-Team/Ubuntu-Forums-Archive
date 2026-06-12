---
title: "Asus eeepc 900 multitouchpad problem"
date: 2009-04-24
forum: New to Ubuntu
---

### Post by billgoldberg on 2009-04-24
Ubuntu Jaunty runs greats on my eee pc 900 (well haven't tested/or really care for the webcam) except the touchpad.

Well, the touchpad works, but not the mutlitouch part of it.

I can't drag windows, highlight text, ...

Does anyone know how to get it working?

---

### Post by JohnFH on 2009-04-24
[https://wiki.ubuntu.com/X/Config/Input]("https://wiki.ubuntu.com/X/Config/Input")

Read the section "Input Configuration with HAL".  The touchpad is configured in one of the hal fdi files.  Either under /etc/hal/fdi/policy/ or /usr/share/hal/fdi/policy

Also check that the touchpad device is being recognised.  Check the output of 'lshal'.

---

