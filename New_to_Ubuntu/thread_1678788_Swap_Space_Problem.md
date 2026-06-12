---
title: "Swap Space Problem"
date: 2011-01-31
forum: New to Ubuntu
---

### Post by miikedenton on 2011-01-31
I've been looking around for a while, and can't seem to find anything that can work.

When I installed Ubuntu I had one partition of my External harddrive as the OS' and the other was my storage for my windows files and stuff. But when it asked about Swap Space, I click my storage partition as it.
So is there a way I can undo that? I have a lot of files on there that I can't replace, so it would be better if there's a way where i don't have to delete it and re-format it.
Windows isn't picking up the partition because it is a Swap Space partition, and when I try changing it back into NTFS with Disk Utility, it gives me the error:
```
Message did not receive a reply (timeout by message bus)
```and this is in the beginner talk forum because I'm new to linux and not really sure what to do.

---

### Post by mharrison on 2011-01-31
It sounds like when you clicked on your drive when it asked for swap space you gave it permission to use the drive.

Can you paste the results of: ```
sudo fdisk -l
```


Edit:
Instead of saying you gave it permission, it is more like you overwrote your partition to use as swap space.  If this is the case, you will not get your data back as the data partition was deleted to make the swap partition and it was formatted as a swap space partition.  If you could change it back to NTFS you would only have a blank NTFS partition at that point.

---

### Post by mcduck on 2011-01-31
If you haven't actully used Ubutu much this far, you might be able to recover some stuff from the partition with testdisk. But the more you have used Ubuntu, the less likely it is to find anything recoverable, especially since it is a swap partition and thus gets quite a lot of writes when Ubuntu is running....

---

