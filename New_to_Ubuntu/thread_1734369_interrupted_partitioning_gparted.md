---
title: "interrupted partitioning gparted"
date: 2011-04-20
forum: New to Ubuntu
---

### Post by shahmish on 2011-04-20
I was running gparted, editing my partitions when my laptop crashed because of a known hardware issue.

 Now, whenever I start gparted, it gives an error message, saying that it can't read the partition tables on the drive and that I will only have limited access to the partitions. I cannot resize the partitions I was working on, but I can format them to any file system.

However, I haven't lost any files though and I can still access all of the partitions through the file manager. SO everything is and isn't fine at the same time O_o.
I don't care about losing any data - the drive is backed up. 


The question is, how can I regain control over these partitions?

---

### Post by PhillyPhil on 2011-04-20
Have you tried booting from a LiveCD and using gparted from there?

---

### Post by bodhi.zazen on 2011-04-20
Boot with a live CD and try tools such as fsck and testdisk

[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

testdisk is in the repos, you will need to install it when running the live CD.

---

