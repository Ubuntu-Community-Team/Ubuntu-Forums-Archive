---
title: "old kernels"
date: 2010-10-24
forum: New to Ubuntu
---

### Post by manny43 on 2010-10-24
Hello friends

Do old kernels take a lot of space on the hard drive and is it safe to remove old kernels or
they have to remain in the system?

---

### Post by ArgusVision on 2010-10-24
You can get rid of them safely using synaptic. Search "header" or "linux" or "kernel". Then check to remove and apply.

---

### Post by drs305 on 2010-10-24
The space in the /boot folder is about 20MB. There are files elsewhere but the size of /boot is usually the concern. There was a time when users were told to make a /boot partition as small as 50MB, but as kernel size grew this obviously led to problems.

It's easy to remove older kernels via Ubuntu Tweak. You might want to keep at least one older kernel you know works. Here is a thread on removing older kernels with Ubuntu-Tweak:
[HOWTO: Remove Older Kernels via GUI]("http://ubuntuforums.org/showthread.php?t=1587462")

---

### Post by Sef on 2010-10-24
> You might want to keep at least one older kernel you know works. 

Do keep one older one that works around in case the current one goes bad. That way you have a back up.

---

### Post by ArgusVision on 2010-10-25
+1 for "keep one old one you know works". <- A good piece of advice I neglected to mention.

---

