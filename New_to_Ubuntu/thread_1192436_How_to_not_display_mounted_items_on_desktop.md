---
title: "How to not display mounted items on desktop?"
date: 2009-06-20
forum: New to Ubuntu
---

### Post by Gp. on 2009-06-20
I've got a few drives that are mounted that show up on the desktop (see image)

How do I choose to turn showing mounted drives off?

But more importantly, can I choose which ones I don't want to be shown on the desktop, but have things like MMC cards and CD's still show up on desktop when inserted?

---

### Post by MrWES on 2009-06-20
> **Gp. said:**
> I've got a few drives that are mounted that show up on the desktop (see image)

How do I choose to turn showing mounted drives off?

But more importantly, can I choose which ones I don't want to be shown on the desktop, but have things like MMC cards and CD's still show up on desktop when inserted?

Check Applications | System Tools for Configuration Editor. It it's not installed, install it with
```
sudo apt-get install gconf-editor
``` it should now be in Applications | System Tools. Fire it up and navigate to /apps/nautilus/desktop and unmark the icons you don't want to see.

Bill

---

### Post by PureLoneWolf on 2009-06-20
You can turn off all mounted volumes completely or you can mount hard disks under /mnt and then they will be available but hidden and then any discs/usb sticks/ipods etc will all appear on the desktop - this is what I did.

[http://ubuntuforums.org/showthread.php?t=1158881](http://ubuntuforums.org/showthread.php?t=1158881)

EDIT:  The post above refers to Volumes Visible (and the home/trash/network icons).  To allow SD cards etc to be visible but hide permanently mounted hard disks, you need to mount them under /mnt

---

