---
title: "trouble reading data disc dvd-r or cd-r"
date: 2010-12-28
forum: New to Ubuntu
---

### Post by henry cow on 2010-12-28
I am setting up several (oldish, re-habbed) computers to run 10.10

I can get them installed from a CD-ISO disc that I burned, but I also have backup files and folders that I want to download from CD-Rs and DVD-Rs, burned on an XP box, mostly using Roxio.

For some reason, Ubuntu fails to recognize the files and folders on the discs at all, I would like to move them into Linux directories of my choice, but can't get them on the hard drives at all. I also get error messages about permissions, but then they do not ask me to log in with my password.

The same process, using a USB flash drive, works perfectly without any other problems.

I cannot tell whether this is a hardware problem, or is somehow tied up in the "permissions" scenario which continues to bewilder me completely after almost a year.....

Posting questions here has helped some, and I have read multiple books on Linux and Ubuntu, but I still just don't "get it"

Anyway, how do I copy these files and folders from my discs, without resorting to an intermediate step moving them on and off of flash drives?

Thank you so much

---

### Post by seawolf167 on 2010-12-28
I'm not sure why you'd be getting a permission error, but does this work?

```
cp -vrf /path/to/cdrom/directory /path/to/destination/directory
```

Since it is a permission error you might need a sudo up there before the cp

---

### Post by mcduck on 2010-12-28
The notorious Roxio Easy Media Creator? It has slightly strange ideas about optical media standards, which makes many discs completely, or partly, unreadable on many CD drives (and Linux as well)...

Anyway, any track-at-once writing methods, standard or not, are not really that great if you want the disk to be compatible with every drive and system. So if you dropped individual files to the discs one at a time, instead of burning the whole disc as one session, then that could very well be the reason for your problem.

What comes to any permission problems, Hit Alt-F2 and run "gksudo nautilus" to open the file manager as root. Be careful with that, though... :D

---

