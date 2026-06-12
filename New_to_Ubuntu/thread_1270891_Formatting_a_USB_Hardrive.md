---
title: "Formatting a USB Hardrive"
date: 2009-09-20
forum: New to Ubuntu
---

### Post by clive littlewood on 2009-09-20
Hi All

I have just purchased a new WD USB Hardrive and formatted this using a live CD and Gparted to EXT4

I noticed that after format it would not let me access unless i was "root"

If i go into nautilus as root everything is OK.

My question is how do I format so that I can access as a "normal" user ??

Any advice would be gratefully received.

Clive

---

### Post by t0p on 2009-09-20
Okay, first get into nautilus as root  That's hit Alt+F2 and type into the box:

```
gksudo nautilus
```

In the root nautilus window, go to /media.  Right-click on the drive's icon (probably called 'disk' or something similar) and select 'Properties'.

Now go to the 'Permissions' tab, and change 'Owner' to your username, with permission to 'Create and delete files', and change 'Group' to your username group with permission to 'Access files'  (dunno if the last bit with 'Group' is essential, but that's how I always do it).

Further down is a button that says 'Apply permissions to enclosed files'.  If the drive contains files, they've probably all been given ownership to root, so you better click that button so ownership transfers to you.

Now when you click on 'Close', ownership of the drive will have been transferred to your username.

---

### Post by clive littlewood on 2009-09-20
Thanks t0p

That did the trick.

Clive

---

