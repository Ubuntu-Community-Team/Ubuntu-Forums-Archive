---
title: "How do you remove sub paritions?"
date: 2009-08-05
forum: New to Ubuntu
---

### Post by lems on 2009-08-05
For some reason I have a partition within another partition...

for example on gparted I see /dev/sda3 and an expand button that lists all the sub partitions of /dev/sda3. When I press expand I see that /dev/sda5 is listed. How do I get rid of /dev/sda5 and just have dev/sda3?

dev/sda5 contains my ubuntu installation btw :( so maybe a better solution would be to move /dev/sda5 out of /dev/sda3 and delete /dev/sda3

help?

---

### Post by lisati on 2009-08-05
Part of the reason for the way the partitions on your system are organized is likely to be limitations on the number of *primary* partitions that you can have on a disk. Some of these limitations are for historical reasons. Although it might be possible to do what you suggest, I'd advise against it, because it would make it difficult to add more partitions later should the need arise.

For more information have a look at [http://en.wikipedia.org/wiki/Disk_partitioning](http://en.wikipedia.org/wiki/Disk_partitioning)

---

### Post by bodhi.zazen on 2009-08-05
Or this link as well : [HowTo: Partitioning Basics - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=282018&highlight=partitioning")

---

