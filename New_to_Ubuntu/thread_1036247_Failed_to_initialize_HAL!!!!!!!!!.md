---
title: "Failed to initialize HAL!!!!!!!!!"
date: 2009-01-10
forum: New to Ubuntu
---

### Post by FAMUgolfer on 2009-01-10
I am one dumb noob!!
I tried installing the new 180.22 nvidia driver on my acer 4530 with 9100m nvidia graphics card following the via this website [http://ubuntuforums.org/showthread.php?t=990978&highlight=180](http://ubuntuforums.org/showthread.php?t=990978&highlight=180).  I realized that there was now difference between the 177 and 180.22 so I tried reverting back to the 177 using the Hardware Driver (system>admin>hardware driver) activation section.  But now my laptop goes into a kernel panic.  I can't even return to the desktop because a pop-up reads "Internal Error: Failed to initialize HAL".  My mouse is frozen, causing me to do a manual shutdown.

What should I do now?? Thank You!!

PS I have a dual boot with XP, which is why I am able to address my problem, if that helps any.

---

### Post by FAMUgolfer on 2009-01-10
I've tried "sudo dpkg-reconfigure hal", but that doesn't seem to work either.

---

### Post by Cl0ud9 on 2009-01-10
I would try booting into failsafe mode, remove the nvidia drivers and then reinstall the correct one.

---

