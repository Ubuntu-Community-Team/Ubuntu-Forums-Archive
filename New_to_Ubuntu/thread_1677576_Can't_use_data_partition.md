---
title: "Can't use data partition"
date: 2011-01-28
forum: New to Ubuntu
---

### Post by mystmaiden on 2011-01-28
I just tried to set up a data partition in 10.04 LTS using a live cd and gparted. In gparted it shows up as sda3 (ext 3) but under 'Places' it just says 16 GB file system. When I mount it, there's a lost and found file there. I tried moving some files to the partition but it says I do not have permission.

```
mystmaiden@hal:~$ sudo fdisk -l
[sudo] password for mystmaiden: 

Disk /dev/sda: 61.5 GB, 61475807232 bytes
255 heads, 63 sectors/track, 7474 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000bc836

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4533    36410298+  83  Linux
/dev/sda2            7219        7474     2055169    5  Extended
/dev/sda3            4534        6445    15358140   83  Linux
/dev/sda5            7219        7474     2055168   82  Linux swap / Solaris


```

Are the permissions fixable at this point? Does it need to be renamed 'data' rather than sda3 and is the fact that two and three are reversed matter? Lots of questions there - but I want to make sure I understand what I'm doing. I'm a bit nervous when it comes to partitioning.

thank you,

mystmaiden

---

### Post by slooksterpsv on 2011-01-28
Try this, open terminal and navigate to wherever your 16GB Parition is mounted (usually it's mounted by a UID in /media

You can also find out by running: ```
ls /media/
```
So type in: ```
cd /media/*whatever_the_uid_or_name_is*
```

Once in there type:
```

gksudo chown ugo=wrx .

```

NOTE: make sure you're not at /, that you are at /media/blahblahblah or whatever it is ok. Otherwise you make the root of your drive writable (/dev/sda1)

Then try to write to it. It's probably owned by Root. To check permissions before executing anything run:
```

ls -la /media/*whatever_the_uid_or_name_is*

```

Unless someone knows a different way.

---

### Post by srs5694 on 2011-01-29
> **mystmaiden said:**
> Does it need to be renamed 'data' rather than sda3

It doesn't need to be, but if you want a more sensible name to be displayed, you can give the partition a name:

```

sudo tune2fs -L newname /dev/sda3

```

That will give the name "newname" to the ext2/3/4 filesystem in /dev/sda3. If you decide to mount it as /home (as noted below), giving it a name will serve very little purpose.

> is the fact that two and three are reversed matter?

No, except for the user confusion factor when looking at the partitions.

BTW, for a user data partition, I recommend using it as a /home partition. There are various guides that describe how to set this up after installing Ubuntu, such as [this one.](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by mystmaiden on 2011-01-29
Thanks so much for the replies, all good to go now!!

---

