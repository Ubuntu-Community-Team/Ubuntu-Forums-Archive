---
title: "Visual Effects Grief"
date: 2010-06-25
forum: New to Ubuntu
---

### Post by jess711 on 2010-06-25
Well it all began when I upgraded to ubuntu 10.04. After upgrading my cursor turned into an "X". I was able too fix this by changing the visual effects to normal. The problem is I have to do this every time I start up ubuntu and my compiz settings don't stick either (wobbly windows, Desktop Cube, et al...), can somebody plz help? Thanks in advance for all your help.

---

### Post by sikander3786 on 2010-06-25
> **jess711 said:**
> Well it all began when I upgraded to ubuntu 10.04. After upgrading my cursor turned into an "X". I was able too fix this by changing the visual effects to normal. The problem is I have to do this every time I start up ubuntu and my compiz settings don't stick either (wobbly windows, Desktop Cube, et al...), can somebody plz help? Thanks in advance for all your help.

Hi.

Which graphics card are you using? Have you tried removing and re-installing the drivers after upgrade?

---

### Post by lsutiger on 2010-06-25
I had the ati restricted driver when I was on 9.04. I installed 10.04, while having my /home folder on a separate partition. I noticed there are no restricted drivers available for ati in 10.04.....so, the question is how to remove and reinstall?

---

### Post by dca on 2010-06-25
I've never had an OS upgrade go right for me with any OS.  When distro-hopping w/ my laptop what I normally do is set-up partitions as:
 
sda1 = /boot
sda2 = /
sda3 = /home
sda4 = swap
 
...  not really necessary to set-up this way anymore, dont' really need LVM and such.  Anywho, when I'm ready to switch to newer OS or different Linux distro, I boot up SystemRescueCD, mount /home and delete all '.' files (hidden)and anything else that's not part of what I normally have in my profile, cd.. back to /home and delete the 'lost+found' directory if it's there. What you're left with should be the important bits: Documents, Music, Videos, et al.  Then reboot into new Live/Install CD and have installer format all partitions identical except for /home leaving that one alone and letting OS populate with the normal .local, .gconf, .themes, et al...
 
The last time I tried an in-place update the same type of thing happened to me with graphics on laptop.

---

