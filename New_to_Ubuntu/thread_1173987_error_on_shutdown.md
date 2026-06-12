---
title: "error on shutdown?"
date: 2009-05-30
forum: New to Ubuntu
---

### Post by wlraider70 on 2009-05-30
when i shutdown my 9.4 box i get a beep.
it sounds like an error code. its two short beeps as near as i can tell.
it only happens on shutdown and since i upgraded.
it still appears to shut down properly.

---

### Post by spiderbatdad on 2009-05-30
this is normal...unfortunately less than graceful...it is bios beep. it can be disabled in several ways, the easiest:
System>>Preferences>>Sounds>>Sounds uncheck "play alerts" 
You can also edit /etc/modprobe.d/blacklist.conf and add "blacklist pcspkr" to the end of the file. You will have to to logout and back in before you will notice the change.

---

