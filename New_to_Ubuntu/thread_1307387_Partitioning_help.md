---
title: "Partitioning help"
date: 2009-10-31
forum: New to Ubuntu
---

### Post by TironN on 2009-10-31
Hey guys,

I was just wondering if there was anyway to make sure a partition remained around in all circumstances.
I have just moved over from windows and have a big partition with my music and videos. Now its name keeps moving around from disk/disk-1 so I keep having to re-import my music library in songbird. If there anyway I can keep it still?

Thanks

---

### Post by quanumphaze on 2009-10-31
You have to make an entry in /etc/fstab for it.

All drives/partitions have a Universally Unique Identifier (UUID). Fstab can use this to always mount a partition to the same mount point with the same options.

I won't spoil all the fun:
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
[https://help.ubuntu.com/community/UsingUUID](https://help.ubuntu.com/community/UsingUUID)

---

### Post by TironN on 2009-10-31
Hey thanks. I'll look into it tonight!

---

### Post by louieb on 2009-10-31
An /etc/fstab entry is the best way in the long run. And the only way to get it to mount automatically at boot [How to fstab - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=283131")

Another way is to use Gparted and assign a label to the partition. If you do that then when the partition get mounted it will mount on /media/<label> .

---

### Post by TironN on 2009-10-31
Ok so I've read the guide on Fstab and have added this to the end of it:
```
/dev/sd2    /media/meddsk  vfat  defaults,user 0 0
```That's all.
As I am the only person who uses the computer I didn't see a need for file permissions.
I have restarted the computer and isn't mounting automatically and once I do still comes up as disk in media. Where have I gone wrong?

Edit:
Ok I worked out part of it. I hadn't made the directory in media. I made it and it was saying the drive didn't exist but if you look at the code above I wrote /dev/sd2 not /sda2! so all works now!

---

