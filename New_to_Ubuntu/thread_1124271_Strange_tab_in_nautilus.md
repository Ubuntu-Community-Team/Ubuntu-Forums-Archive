---
title: "Strange tab in nautilus"
date: 2009-04-13
forum: New to Ubuntu
---

### Post by Kosimo on 2009-04-13
Hello guys, 
Now every time I open nautilus it appears a tab that says:

These files are on a picture CD   with a link to (Open Disk Copier)...

Always, no matter where I am..  Guys there is any way to disable this?

---

### Post by rushmobius on 2009-04-13
While I don't know how to disable it, it appeared on my system for anything mounted under /media.

As a quick fix, I added my data drives to mount via fstab under /mnt instead.

It seems Nautilus thinks anything under /media must be a removable device. If it sees any pictures, it must assume it is a photo cd.

---

### Post by Kosimo on 2009-04-13
> **rushmobius said:**
> While I don't know how to disable it, it appeared on my system for anything mounted under /media.

As a quick fix, I added my data drives to mount via fstab under /mnt instead.

It seems Nautilus thinks anything under /media must be a removable device. If it sees any pictures, it must assume it is a photo cd.

Thanks for answer.
Nice to know that I'm not the only one with this issue. And yes, my drives are mounted in /media as well. Will try to mount somewhere else.

---

### Post by Kosimo on 2009-04-13
Should this be consider a bug?

Cuz if it is, I can may open a bug in launchpad

---

### Post by Kosimo on 2009-04-13
It has been already notified.


[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/258936](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/258936)

(and confirmed)
So is just a matter of time 'till it gets fixed.

---

