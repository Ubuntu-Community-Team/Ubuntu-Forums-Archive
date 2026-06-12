---
title: "Ubuntu card reader mounting issues"
date: 2009-06-22
forum: New to Ubuntu
---

### Post by Gp. on 2009-06-22
It used to work fine.
I used to stick in my MMC card, it would come up right away, when I removed it, it would unmount.
When I put it in now, sometimes it doesn't mount at all or it takes forever.
When I remove it, it like...caches the mounted media so I can still go into it even when it's no longer inserted into my PC.
Ofcorse when I actually try to open something from it, it gives the access error because the card has been taken out.

I dunno, the MMC mounting and unmounting and usage in general has become crap.

ideas?

---

### Post by jenkinbr on 2009-06-22
Try renameing the .gnome2 folder in your home directory:

Open a terminal (Applications >> Accesories >> Terminal) and run the code below (copy and paste)

```
mv ~/.gnome2 ~/.gnome2_backup
```

Now see if that helps any.  You should get a default instance of nautilus, your settings from before are now under the new location (~/.gnome2_backup

---

