---
title: "No sound in Ubuntu 9.04"
date: 2009-04-26
forum: New to Ubuntu
---

### Post by umuenzin on 2009-04-26
hi I need help I have no sound with Ubuntu 9.04 it was working fine with 8.10 after the upgrade I have no sound. I use a Laptop HP Pavilion dv6 any one has any solution.

---

### Post by bazdavis on 2009-04-26
your going to have to add an extra line to the etc/modprobe.d file that addreses your laptop off the top of my head it is something like 
options snd-hda-intel model hp

---

### Post by linux_tech on 2009-04-26
try re-installing the alsa sound base
```
 
sudo aptitude --purge reinstall linux-sound-base alsa-base alsa-utils linux-image-`uname -r` linux-ubuntu-modules-`uname -r` libasound2

```

then reboot and try sound again

---

### Post by umuenzin on 2009-04-26
did try that but still no sound

---

### Post by zimmerley on 2009-05-13
Hi There,
I have a dv6 too, I followed the instructions in this thread:
[http://ubuntuforums.org/showthread.php?t=1073090&highlight=no+sound+HP+dv6](http://ubuntuforums.org/showthread.php?t=1073090&highlight=no+sound+HP+dv6)
and it worked immediately.  Good luck!

---

