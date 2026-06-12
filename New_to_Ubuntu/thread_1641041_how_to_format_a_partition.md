---
title: "how to format a partition"
date: 2010-12-08
forum: New to Ubuntu
---

### Post by bj218 on 2010-12-08
How can I reformat a ubuntu partition? I want to do this to get rid of a problem  in one of my partitions!!

---

### Post by metalf8801 on 2010-12-08
You can reformat a partition using Gparted 
Go to 
System > Administration > GParted Partition Editor 
however you cannot format partitions that are mounted and if you can't unmount them you are going to need to a live CD that has Gparted on it. The Ubuntu live CD has Gparted but, if for some reason you don't have a copy you might want to try Parted Magic. You can download Parted Magic for free from here [http://partedmagic.com/download.html](http://partedmagic.com/download.html)

I hope this helps 
Dan

---

### Post by bj218 on 2010-12-09
> **metalf8801 said:**
> You can reformat a partition using Gparted 
Go to 
System > Administration > GParted Partition Editor 
however you cannot format partitions that are mounted and if you can't unmount them you are going to need to a live CD that has Gparted on it. The Ubuntu live CD has Gparted but, if for some reason you don't have a copy you might want to try Parted Magic. You can download Parted Magic for free from here [http://partedmagic.com/download.html](http://partedmagic.com/download.html)

I hope this helps 
Dan

I used my ubuntu cd to format my problem partition ie homeu. But when I went back to my system I still have this folder on my desktop. How do I 
get it off my desktop see attached picture. When I clkd on it the folder is now empty.

---

### Post by coffeecat on 2010-12-09
> **bj218 said:**
> I used my ubuntu cd to format my problem partition ie homeu. But when I went back to my system I still have this folder on my desktop. How do I 
get it off my desktop see attached picture. When I clkd on it the folder is now empty.

I guess you need to remove the line in /etc/fstab that refers to homeu. I presume the reformatted partition is being mounted in fstab to the mountpoint that was used for your original homeu. That's why the folder is now empty.

---

### Post by bodhi.zazen on 2010-12-09
> **metalf8801 said:**
> You can reformat a partition using Gparted 
Go to 
System > Administration > GParted Partition Editor 
however you cannot format partitions that are mounted and if you can't unmount them you are going to need to a live CD that has Gparted on it. The Ubuntu live CD has Gparted but, if for some reason you don't have a copy you might want to try Parted Magic. You can download Parted Magic for free from here [http://partedmagic.com/download.html](http://partedmagic.com/download.html)

I hope this helps 
Dan

From the command line you use mkfs

mkfs.ext2 , mkfs.ext4 , mkfs.vfat , etc ...

Example:

```
mkfs.ext4 /dev/sda3
```

It is IMO faster to run a terminal command then fire up gparted :p

You can specify a partition by /dev or mount point.

[http://linux.die.net/man/8/mkfs](http://linux.die.net/man/8/mkfs)

I use gparted, though, if I have to resize a partition ....

---

### Post by bj218 on 2010-12-09
> **coffeecat said:**
> I guess you need to remove the line in /etc/fstab that refers to homeu. I presume the reformatted partition is being mounted in fstab to the mountpoint that was used for your original homeu. That's why the folder is now empty.

Removing that line in fstab looks like it worked ie homeu is no longer on the desktop. Can I now put the line back in fstab? Through all this I am 
using the same partition ie /dev/sdc6  homeu. I down loaded parted magic THANK you I
think I might use it but want to look at it first.

---

### Post by coffeecat on 2010-12-09
> **bj218 said:**
> Can I now put the line back in fstab? Through all this I am 
using the same partition ie /dev/sdc6  homeu.

Er, yes, but I thought you wanted the icon off the desktop. If you want the partition mounted but not have an icon on the desktop you need to create a mountpoint that's not in /media. Usually, you would use /mnt for this. Just to be clear: partitions mounted in /media give you desktop icons (unless you switch this off in gconf-editor). Partitions mounted in /mnt do not give you a desktop icon.

If you need help with this, post back and someone will help. Probably not myself though as I shall be logging off soon to nurse a bad cold.

---

### Post by bj218 on 2010-12-10
Thanks to all things seem to be working greate at monent.

---

