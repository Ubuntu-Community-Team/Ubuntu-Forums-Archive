---
title: "my pc consume all the processor when copying files"
date: 2010-05-21
forum: New to Ubuntu
---

### Post by kiraku on 2010-05-21
hi:
 i have the next problem, when i copy or move files from or to another partition of mi disk (with windows) or to external hard drive or pendrives, the oc consumes all the processor, hardly i can do something else and it takes to long to copy...


any ideas of why does this happeng to me??...


i have to mention that in windows i does not have this issue...

i have ubunto 9.10, dual core de 1.46 GHz processor each one, 1 Gb de ram...

---

### Post by -humanaut- on 2010-05-21
It's probably the difference in filesystems (ext4 vs ntfs) thats causing some of the problem does it happen when copying small files large files or all files?

---

### Post by kiraku on 2010-05-21
yeah, it only happens with large files (>= 200 Mb)...

---

### Post by -humanaut- on 2010-05-21
I think its a the difference between filesystems and how they handle files I have a fat32 partition the eats up a ton of my system resources when I'm copying large files over to my ext4 partition.

---

### Post by kiraku on 2010-05-21
so, there is not improvement in how to do de copying??

---

