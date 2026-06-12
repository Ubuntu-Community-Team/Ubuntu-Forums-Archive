---
title: "Removing XP. Just keep Ubuntu"
date: 2009-08-01
forum: New to Ubuntu
---

### Post by jacklinux on 2009-08-01
Hi
Erm i was wanting to know how do i remove XP from the hardrive and only keep my Ubuntu installation?
i wish to keep all files on the ubuntu part so Format is not an option, Thanks.

---

### Post by atomizer on 2009-08-01
This can be done if Ubuntu is on a seperate partition (NO WUBI INSTALL)

edit your /boot/grub/menu.lst

Comment the part for xp.


then you can format your xp-partition with ```
sudo mke2fs-j /dev/partition-that-contains-xp
```(make Ext2 filesystem with journalling ,that is what ext3 is) The path is probably /dev/sda1. Make shure the partition is unmounted, else you cannot format.

maybe you have to change your /etc/fstab too to have the partition mounted at boot (but you'll have to google a bit for how to do that, has been too long ago for me)

---

### Post by jacklinux on 2009-08-01
> **atomizer said:**
> This can be done if Ubuntu is on a seperate partition (NO WUBI INSTALL)

edit your /boot/grub/menu.lst

Comment the part for xp.


then you can format your xp-partition with ```
sudo mke2fs-j /dev/partition-that-contains-xp
``` (probably /dev/sda1) make shure the partition is unmounted, else you cannot format.

maybe you have to change your /etc/fstab too to have the partition mounted at boot (but you'll have to google a bit for how to do that, has been too long ago for me)
im not sure how to unmout XP or what partition its in. isn't there just a way to 'delete' it?

---

### Post by Sef on 2009-08-01
Locked.  [Duplicate Thread]("http://ubuntuforums.org/showthread.php?p=7715482#post7715482").

---

