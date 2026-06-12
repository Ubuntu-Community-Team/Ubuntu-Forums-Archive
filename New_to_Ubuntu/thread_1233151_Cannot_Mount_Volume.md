---
title: "Cannot Mount Volume"
date: 2009-08-06
forum: New to Ubuntu
---

### Post by Tremlett on 2009-08-06
Newbie here. Dumbed down talk is much appreciated...
My external hard drive has mysteriously become unmountable.
The error message reads in the title line (cannot mount volume)
In the details of the error prompt, it gives a few command that are of no avail, such as mount -t ntfs-3g/dev/sdb1/media/New Volume -o force

Any ideas are appreciated

---

### Post by ptn107 on 2009-08-06
```
mount -t ntfs-3g/dev/sdb1/media/New Volume -o force
```
I think there needs to be a space between the filesystem type and mount point. Lets rearrange the command options too (the correct format for 'mount' is: **mount [-fnrsvw] [-t vfstype] [-o options] device dir**).  Also since your volume name contains a space you need an escape character '\' so the shell doesn't try to interpret it as something else.  Be sure that **/media/New\ Volume** exists beforehand too (**sudo mkdir -p /media/New\ Volume**):
```
mount -t ntfs-3g -o force /dev/sdb1 /media/New\ Volume
```

---

### Post by Tremlett on 2009-08-06
Happy day! It worked! Thanks ptn.
I first had to figure out the root user stuff and logging in under the su temp. root user command made the difference. But, it was your command sequence that worked. 
Cheers

---

### Post by Tremlett on 2009-08-06
[color="red"]**[solved**[/color] :)

---

