---
title: "Second drive not shared over the network"
date: 2014-03-08
forum: Networking &amp; Wireless
---

### Post by peyre on 2014-03-08
My desktop has an SSD for the system, and a mechanical drive for data storage.  I've shared my home folder and can access it over the network, either from my Xubutu laptop or from my wife's XP machine.  But I can't from the second drive.  I've tried sharing the whole drive or some of its top-level folders, but (depeding on the share permissions) it either just fails outright or it challenges me for my credentials.  I enter my user name and password (they're the same on my laptop and desktop), and it rejects my credentials!!  What gives?

---

### Post by Morbius1 on 2014-03-08
Before anyone answers this question is this topic connected to this topic: [Partitions not mounting automatically on startup ]("http://ubuntuforums.org/showthread.php?t=2210013")

I suspect once the partition is mounted at /data and away from /media/username/something this problem will go away.

---

### Post by peyre on 2014-03-08
Not exactly, though I expect that mounting it under my home folder (which is shared) would probably get around the issue.  (I haven't tried this out yet on the desktop, which has the shares.)

---

### Post by peyre on 2014-03-09
Yes, the solution in my topic above (Partitions not mounting automatically on startup) did the job.  I hesitate to call this "solved" because it's more in the nature of a workaround than a solution, but it does work.

---

