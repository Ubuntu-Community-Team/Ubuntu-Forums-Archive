---
title: "Windows XP reactivate partition in install"
date: 2010-11-20
forum: New to Ubuntu
---

### Post by flebber on 2010-11-20
I was following this guide as I was having an error with an install.
[http://ubuntuforums.org/showthread.php?t=1367248]("http://ubuntuforums.org/showthread.php?t=1367248")

Now I am trying to install ubuntu onto an internal drive of 500GB size. 380GB is windows xp and 120gb will be ubuntu.

However I am concerned that my xp install is not detected.

When I ran 

sudo apt-get install lilo
 and
sudo lilo -M /dev/sda mbr

then rebooted I got a no partition active, how can I reactivate windows xp partition so ubuntu detects it?

Oh and using 10.10

---

### Post by mapes12 on 2010-11-20
[http://helpdeskgeek.com/how-to/fix-mbr-xp-vista/](http://helpdeskgeek.com/how-to/fix-mbr-xp-vista/)

---

### Post by Rubi1200 on 2010-11-20
I suggest you run the boot info script linked at the bottom of my post and let us see the results back here.

This will give us a much better overview of your setup and ma;e offering solutions easier.

Thanks.

---

