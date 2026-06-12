---
title: "Changing Default Volume name"
date: 2009-11-12
forum: New to Ubuntu
---

### Post by jamil_1 on 2009-11-12
I have two windows partition C: and D:. On ubuntu they appear as "157 GB Filesystem". I want to change that to either C: or D: accordingly. How can I do this ?

---

### Post by coldReactive on 2009-11-12
This thread should shed some light on why you "can't."

[http://ubuntuforums.org/showthread.php?t=33319](http://ubuntuforums.org/showthread.php?t=33319)

---

### Post by sisco311 on 2009-11-12
Change the label of the partitions: [https://help.ubuntu.com/community/RenameUSBDrive]("https://help.ubuntu.com/community/RenameUSBDrive")

In karmic you can use "Palimpsest Disk Utility" is somewhere in the System menu.

---

### Post by coldReactive on 2009-11-12
> **sisco311 said:**
> Change the label of the partitions: [https://help.ubuntu.com/community/RenameUSBDrive]("https://help.ubuntu.com/community/RenameUSBDrive")

In karmic you can use "Palimpsest Disk Utility" is somewhere in the System menu.

It's simply called "Disk Utility."

---

### Post by John Bean on 2009-11-12
> **coldReactive said:**
> This thread should shed some light on why you "can't."

[http://ubuntuforums.org/showthread.php?t=33319](http://ubuntuforums.org/showthread.php?t=33319)
2005???

Things change.

---

### Post by coldReactive on 2009-11-12
> **John Bean said:**
> 2005???

Things change.

Sometimes they don't:

[http://ubuntuforums.org/showthread.php?t=1324580](http://ubuntuforums.org/showthread.php?t=1324580)

and

[https://bugs.launchpad.net/ubuntu/+source/gnome-mount/+bug/81239](https://bugs.launchpad.net/ubuntu/+source/gnome-mount/+bug/81239)

---

### Post by jamil_1 on 2009-11-12
So what should I do ? Any final answer ? Can I rename or not ?

---

### Post by coldReactive on 2009-11-12
> **jamil_1 said:**
> So what should I do ? Any final answer ? Can I rename or not ?

Yes, you can. Use Disk Utility under System > Administration.

---

### Post by sisco311 on 2009-11-12
> **jamil_1 said:**
> So what should I do ? Any final answer ? Can I rename or not ?

Yes you can by changing the partition's label.

Labeled devices will be mounted in the /media directory using their label as the mount point.



Or you may want to mount the partitions at mount time:
[http://psychocats.net/ubuntu/mountwindows]("http://psychocats.net/ubuntu/mountwindows")

---

### Post by jamil_1 on 2009-11-12
I have tried to rename the mount point but it hasnt changed the volume name on Desktop

---

### Post by John Bean on 2009-11-13
> **jamil_1 said:**
> I have tried to rename the mount point but it hasnt changed the volume name on Desktop
Don't try to change the name of the mount point, instead change the disk label using Disk Utility or similar. The disk will show on the desktop as whatever the label says, if it has one.

Despite claims to the contrary this will work correctly and reliably.

---

