---
title: "lost+found on external drive"
date: 2009-04-25
forum: New to Ubuntu
---

### Post by eddski on 2009-04-25
I created a partition on an external drive and saw that 400 megs were used. I looked and foun that a lost+found folder was on there, but I did not do anything to put it there. I used gparted to create the partition. Can I get rid of that folder safely? Why is it there? Also there is a fat32 partition on the external drive.

---

### Post by cariboo on 2009-04-25
[Fsck]("http://linux.die.net/man/8/fsck") creates lost+found on every partition, it can safely be removed. Files that were saved during failures are found in lost+found.

---

### Post by eddski on 2009-04-26
thanks cariboo907.

---

