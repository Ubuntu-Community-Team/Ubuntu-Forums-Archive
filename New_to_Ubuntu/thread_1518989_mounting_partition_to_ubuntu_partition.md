---
title: "mounting partition to ubuntu partition"
date: 2010-06-27
forum: New to Ubuntu
---

### Post by evilwonka on 2010-06-27
im about a year in to Linux. i whipped out windows to make the jump and i had 64g left over i mounted it to ext4 with g parted but now i cant do anything with it anytime i try to add something to it it says "you do not have partition"  can someone please help me

---

### Post by Leppie on 2010-06-27
> **evilwonka said:**
> anytime i try to add something to it it says "you do not have partition"
i don't believe i've ever seen this error, did you mean "you do not have permission"?

did you create a fstab entry for this partition? if so, could you post you're fstab?

---

### Post by oldfred on 2010-06-27
Some good resources to help you understand mounting, fstab and permissions:

Understanding fstab
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
Ownership and permissions of vfat / ntfs are set at the time of mounting. This is often a source of confusion.
[http://www.psychocats.net/ubuntu/mountwindowsfstab](http://www.psychocats.net/ubuntu/mountwindowsfstab)

[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

---

### Post by mikewhatever on 2010-06-27
Let's get the terminology right - you mount to a mount point, not to partition or ext4.):P
Try formatting that partition again.

---

### Post by evilwonka on 2010-07-14
Sorry for the late reply and the wrong terminology, the info about fstab that has been posted has  been helpful  but i haven't had a lot of time to sit down and work with it so i will be posting my progress.:p

---

