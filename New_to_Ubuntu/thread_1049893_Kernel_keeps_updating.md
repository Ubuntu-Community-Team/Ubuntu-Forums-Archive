---
title: "Kernel keeps updating"
date: 2009-01-25
forum: New to Ubuntu
---

### Post by Nixie Pixel on 2009-01-25
My package manager keeps wanting to upgrade me to linux-image-2.6.27-11-generic (and headers, etc.), even though I have already updated, and when I boot in GRUB it says I'm booting to 2.6.27-11...and uname says the same...

Any idea how to get the update manager to stop trying to update me when I'm already running the correct version of the kernel?

---

### Post by Michael.Godawski on 2009-01-25
hi, 

you could try to lock the package version:

[http://ubunturesources.ub.ohost.de/lockversion.html](http://ubunturesources.ub.ohost.de/lockversion.html)

although I have never locked the linux-image so do not know what consequences this might have.

But if you feel adventurous today you could try. Basically nothing bad should happen, but if a real update is available you will have to unlock the packages again.

---

### Post by sdennie on 2009-01-25
Sometimes kernel updates don't require version number changes because the update is binary compatible with what is on the system.  You may be seeing that here.  I would update and see if it still wants you to update afterwards.

---

### Post by Nixie Pixel on 2009-01-27
> **sdennie said:**
> Sometimes kernel updates don't require version number changes because the update is binary compatible with what is on the system.  You may be seeing that here.  I would update and see if it still wants you to update afterwards.
Hi, it looks like you were correct, and I had a couple of updates that were binary compatible.  I have updated again, rebooted, and now am not being asked to update.

Thanks!

---

