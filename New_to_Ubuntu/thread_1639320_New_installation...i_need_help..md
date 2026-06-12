---
title: "New installation...i need help."
date: 2010-12-06
forum: New to Ubuntu
---

### Post by grobar87 on 2010-12-06
Hi,
I have laptop with windows xp and fedora 14 dual boot.I want to replace fedora with ubuntu and remove windows xp without losing my files who are on separate partition.
I attach screenshot:

1.first partition - win xp (ntfs)
2.second - important partiton with all my data (ntfs)
3.Fedora 14 (ext4)
4.swap partiton

Thanks for help.

---

### Post by bodhi.zazen on 2010-12-06
> **grobar87 said:**
> Hi,
I have laptop with windows xp and fedora 14 dual boot.I want to replace fedora with ubuntu and remove windows xp without losing my files who are on separate partition.
I attach screenshot:

1.first partition - win xp (ntfs)
2.second - important partiton with all my data (ntfs)
3.Fedora 14 (ext4)
4.swap partiton

Thanks for help.

As long as you store all your important data on the second ntfs partition and not the fedora 14 partition you will be good to go (install Ubuntu into the Fedora partition).

Just make sure you understand linux partition terminology:

[http://ubuntuforums.org/showthread.php?t=282018](http://ubuntuforums.org/showthread.php?t=282018)

---

### Post by rmockler on 2010-12-06
There are probably many ways that you could do this task, but I would suggest the following:
Boot up your Ubuntu Live CD.
Using gparted (in Control Center or System--> Administrator--> Gparted), you can delete the unwanted partitions.
From what you said, the means deleting sda1 (Windows), sda3 (Fedora), and sda4 (Swap).
I notice that your sda2 (data partition) has used >78g and there is only >7g left.  Maybe it would be wise after deleting the other partitions for you to expand sda2 to the left so you would have some additional space.   After deleting sda1,sda3 and sda4 and extending sda2 to the left, you can install Ubuntu and choose the largest unallocated space (which is the rest of the hard drive) to put Ubuntu.  It will create a swap partition at the end.  You can do all of the partition work using Gparted.

---

### Post by grobar87 on 2010-12-06
Thank you very much...i perfectly understand what to do now.
Great forum!:)

---

