---
title: "Mounting my 2nd HD at startup"
date: 2011-07-12
forum: New to Ubuntu
---

### Post by jermza on 2011-07-12
I have two drives.  Instead of manually clicking on the drive in Nautilus to mount it, I'd like to automatically mount it at startup.  (It has music and other media on it.)  I have installed Mount Manager, which apparently makes this sort of thing easier to do.

But I'm a little confused.

I've clicked on the 2nd drive and selected "mount" from the menu.  It's now asking for a mount point.  (See attached.)

I'm not sure what that should be.  Any advice?

---

### Post by linuxman94 on 2011-07-12
I haven't heard of mount manager, but from the looks of it, it isn't very user friendly.  I would use pysdm, it is much more polished.  Just click [here]("apt:pysdm") and to install it.

---

### Post by lmarmisa on 2011-07-12
Try to create a directory for mount point.

Open a terminal and type:

```

sudo mkdir /media/MyMusic

```

---

### Post by Psyco430404 on 2011-07-12
another good utility if you cant get that one to work is

disk manager

```

sudo aptitude install disk-manager

```

---

