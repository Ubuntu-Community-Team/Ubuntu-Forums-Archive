---
title: "adding a partition in 9.10"
date: 2009-12-09
forum: New to Ubuntu
---

### Post by dagarshali on 2009-12-09
Hi,
I had vista and ubuntu installed on my sytem. I just upgraded vista to windows 7 and I repaired the grub loader. I also freed some space from windows and its shows as 45 gb unallocated. I have downloaded Gparted in ubuntu. I can select that partition and I have the the option of picking ext4. All other partitions are ext4. But the create as Primary is available too. But, I dont see the mount point. I am not sure if this the way to do that.

Any help?

Regards,
Vishwa

---

### Post by bodhi.zazen on 2009-12-09
Well, I think you need to make a mount point manually.

The live CD may well manually mount it, but when running from teh hard drive you need to make a directory and add an entry in fstab.

```
sudo mkdir /media/foo
```

"foo" can be any name you wish.

List your partitions by uuid

```
sudo blkid
```

Add an entry in fstab :

[How to fstab - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?&t=283131")

---

