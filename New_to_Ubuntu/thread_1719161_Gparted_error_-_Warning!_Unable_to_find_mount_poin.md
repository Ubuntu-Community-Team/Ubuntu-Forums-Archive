---
title: "Gparted error - Warning! Unable to find mount point."
date: 2011-04-01
forum: New to Ubuntu
---

### Post by Hellfish03 on 2011-04-01
I have 2 hard drives and there are 3 partitions. One is for the Ubuntu system and the other two are just for data. I noticed in Gparted the data partitions are flagged (see screenshots).

Both drives seem to be working fine. Should I be worried about this?

---

### Post by TeoBigusGeekus on 2011-04-01
Notice the last part of the returned message about the e2fsprogs.
Try to install it
```
sudo apt-get install e2fsprogs
```

---

### Post by Hellfish03 on 2011-04-01
Ok, did that and it came back that I already have the newest version.

---

### Post by TeoBigusGeekus on 2011-04-01
I wouldn't worry too much about it, as it seems to be a gparted thing.
Boot up with a live cd though and fsck your partitions, just to be sure.

---

### Post by Hellfish03 on 2011-04-01
I'm new to linux, how do I fsck my partitions?

---

### Post by leclerc65 on 2011-04-01
You can use Gparted.
Right click on the partition then choose option 'Check'.

---

