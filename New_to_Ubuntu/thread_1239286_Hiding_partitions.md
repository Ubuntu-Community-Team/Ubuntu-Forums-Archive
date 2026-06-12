---
title: "Hiding partitions"
date: 2009-08-13
forum: New to Ubuntu
---

### Post by MAJcrew35 on 2009-08-13
Hello all, 

I just set up an XP / Jaunty dual-boot, and consequently have a rather complex set of partitions. Several of these partitions should never be accessed by Ubuntu (e.g. the XP recovery partition, or the partition containing the Windows OS itself). I have figured out how to change permissions so that I don't accidentally edit anything in those partitions, but I would like to remove them from my list of places - they are just clutter at the moment. Is there any way to basically make these partitions hidden from Ubuntu, or at the very least prevent them from being displayed in Nautilus etc?

Thanks!

---

### Post by eldragon on 2009-08-13
im not sure this is something a begginer could accomplish, but a way to do this is with udev rules. still not sure how gnome-volume-manager will handle it.

those partitions are most likely listed under fstab. removing (coment out the line with a # at the beggining of the entry) their entries from fstab could do it too.. not sure though.

---

### Post by wizard10000 on 2009-08-13
> **MAJcrew35 said:**
> Hello all, 

I just set up an XP / Jaunty dual-boot, and consequently have a rather complex set of partitions. Several of these partitions should never be accessed by Ubuntu (e.g. the XP recovery partition, or the partition containing the Windows OS itself). I have figured out how to change permissions so that I don't accidentally edit anything in those partitions, but I would like to remove them from my list of places - they are just clutter at the moment. Is there any way to basically make these partitions hidden from Ubuntu, or at the very least prevent them from being displayed in Nautilus etc?

Thanks!

I'm on a Windows machine and can't test this right now but can't you just comment out the fstab entries as eldragon mentioned and delete the bookmarks in Nautilus?

---

### Post by MAJcrew35 on 2009-08-13
Ok, thanks for that info. Does anyone else have any other ideas, or if not, perhaps a more detailed explanation of the above proposal?

---

### Post by coldReactive on 2009-08-13
install gparted (gnome partition manager.)

---

### Post by MAJcrew35 on 2009-08-13
> **coldReactive said:**
> install gparted (gnome partition manager.)


You rock. Thanks!

---

