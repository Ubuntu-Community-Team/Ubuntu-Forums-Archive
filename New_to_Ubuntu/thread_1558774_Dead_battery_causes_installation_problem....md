---
title: "Dead battery causes installation problem..."
date: 2010-08-22
forum: New to Ubuntu
---

### Post by ppk on 2010-08-22
I have an old laptop with a dead battery that I was hoping to rescue from a messed up Vista installation. I re-installed the whole thing with ubuntu 10.04 and it went smoothly. However, after the progress bar reached 100% it went to a black screen where it was apparently completing a couple of tasks before reboot. One of them is 'checking battery state', which it obviously failed because the battery has been dead for years. After spewing out a dozen error messages it locked up on this. What should I do? Can I force it off and restart it without risking damaging the new installation?

---

### Post by davidmohammed on 2010-08-22
Yes - should be OK - I've had this issue on a couple of installs.  The forced shutdown and reboot didnt do any harm.

---

### Post by ppk on 2010-08-22
Well... I forced it to shutdown but now when I boot it up all I get is a black screen and lots of noise from the fans/processor spinning at full speed. What can I do?

---

### Post by davidmohammed on 2010-08-22
black screen issues are usually graphics card issues. The fix depends on the graphics card.


suggest when booting press shift to display your grub.

Press e.  Find the line containing "quiet splash"

add one of the following

nomodeset
i915.modeset=1
i915.modeset=0

immediately before quiet splash

e.g.

... nomodeset quiet splash --

CTRL +X to boot.

---

