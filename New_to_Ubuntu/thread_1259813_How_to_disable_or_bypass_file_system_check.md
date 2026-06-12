---
title: "How to disable or bypass file system check?"
date: 2009-09-06
forum: New to Ubuntu
---

### Post by palmboy5 on 2009-09-06
Ubuntu refuses to boot after I swapped a storage HDD with another HDD. It says the file system check failed. Of course it will fail given the circumstances, but how do I get the system to ignore the failure and continue booting? It's just a storage HDD, nothing to halt the whole OS for!! :(

---

### Post by lswb on 2009-09-06
Usually a filesystem check failure won't stop booting unless the filesystem contains files necessary for the system to run. Are you sure that no part of you system was installed on a partition of the disk you replaced? 

I would try booting into recovery mode, or using a live CD if recovery mode won't start, and editing /etc/fstab to remove references to any partitions on the disk you replaced.

---

### Post by palmboy5 on 2009-09-06
I'm sorry, I should have read the error output more carefully. It said to press Ctrl + D to resume the boot. :-\"

---

### Post by palmboy5 on 2009-09-06
Actually, to ask ahead of time... When the file system check fails like it did for me, what do I do to update it to the new configuration?

---

### Post by lswb on 2009-09-06
Well, that depends on how you had it configured with the old disk of course. How did you access the old disk? was there a directory (mountpoint) that pointed to the files on the old disk? 

Probably you just need to change the line in /etc/fstab that referenced the uuid of the old disk to use the uuid and filesystem type of the new one. Has the new disk been had a filesystem installed or formatted? Post this info and we can help you out:

Contents of /etc/fstab
from a terminal, output of "sudo fdisk -l"
from a terminal, output of "sudo blkid"

---

### Post by palmboy5 on 2009-09-08
I don't know what got into me before. I usually ask about a problem after I fail a few tries towards fixing it, but both of my questions in this thread were asked before I tried to do anything myself. Embarassing. The PC didn't bother me again after a reboot with the new HDD configuration so there was no problem, sorry for wasting your time.

---

### Post by egalvan on 2009-09-08
> **palmboy5 said:**
> ... I usually ask about a problem after I fail a few tries towards fixing it, but both of my questions in this thread were asked before I tried to do anything myself. Embarassing. The PC didn't bother me again after a reboot with the new HDD configuration so there was no problem, **sorry for wasting your time**.

Well, you learned something, so it wasn't a total loss of time... :lolflag:

---

