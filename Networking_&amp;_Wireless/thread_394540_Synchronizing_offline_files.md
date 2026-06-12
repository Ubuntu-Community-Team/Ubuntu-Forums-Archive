---
title: "Synchronizing offline files"
date: 2007-03-27
forum: Networking &amp; Wireless
---

### Post by ogifell on 2007-03-27
Hello All,

I've been working with Ubuntu for about 2 years, new to the forums... good to be here.

I'm looking for some sort of utility (preferably with gui) to synchronize files on my laptop with those on a network drive.  I've been trying Krusader, but it synchronizes files which are in each directory, rather than updating the network drive to match my laptop directory (ie, if I delete a file/folder on my laptop, while on the road, it will come back when I synchronize, as it is still on the network drive).

many thanks

---

### Post by Mr. C. on 2007-03-27
You are looking to mirror, not synchronize (one way vs. two).

Regardless, rsync is excellent.  If you want a GUI, perhaps you want grsync:

[http://www.debianhelp.co.uk/rsyncweb.htm](http://www.debianhelp.co.uk/rsyncweb.htm)

MrC

---

### Post by jnorris235 on 2007-03-29
I have tried grsync - how on earth do you tell it the address of a NAS to sync to?
Laptop sync to NAS after a sad evening in front of the TV is what I want to do - then I can sync from the desktop to the NAS in the morning.

---

### Post by Mr. C. on 2007-03-29
Spend a few minutes reading the man page for rsync.  The grsync is just a GUI frontend.

You can specify many forms of source and destination addresses, such as remotehost::

MrC

---

