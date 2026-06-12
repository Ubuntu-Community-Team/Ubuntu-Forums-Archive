---
title: "How to mount a ddrescue crashed HD copy on external HD?"
date: 2009-09-23
forum: New to Ubuntu
---

### Post by pognonec on 2009-09-23
Following a HD drive crash, I copied the faulty drive to an empty partition on an external big HD that I formated in 3 large ext3 partition. I can now see my copied crashed HD on the partition 1 of my external HD (even though the ext3 format is gone) with:
$ sudo fdisk -ls /dev/sdb1 (see below).
```

philippe@Ubuntu:~$ sudo fdisk -ls /dev/sdb1
Warning: ignoring extra data in partition table 7
Warning: ignoring extra data in partition table 7
Warning: ignoring extra data in partition table 7
Warning: invalid flag 0x1f10 of partition table 7 will be corrected by w(rite)

Disk /dev/sdb1: 185.8 GB, 185899521024 bytes
255 heads, 63 sectors/track, 22600 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x28000000

     Device Boot      Start         End      Blocks   Id  System
/dev/sdb1p1               1          27      216846   de  Dell Utility
/dev/sdb1p2              28        1333    10485760    7  HPFS/NTFS
/dev/sdb1p3   *        1333        6061    37975586    7  HPFS/NTFS
/dev/sdb1p4            6062       19458   107604011    f  W95 Ext'd (LBA)
/dev/sdb1p5           19131       19458     2620416   dd  Unknown
/dev/sdb1p6            6062       18594   100671291   83  Linux
/dev/sdb1p7   ?      242591      344140   815687134   55  EZ-Drive

Partition table entries are not in disk order

```
But I am unable to mount that sdb1 partition, presumably because the ext3 formating is gone.
How can I access partition 1 of my external HD/recuperate my data?
Thanx in advance for your help!

---

### Post by Bachstelze on 2009-09-23
You want to mount the partitions that /dev/sdb1 contains, not /dev/sdb1 itself.

---

### Post by pognonec on 2009-09-23
> **Bachstelze said:**
> You want to mount the partitions that /dev/sdb1 contains, not /dev/sdb1 itself.

Yes, and no (since it is a copy of a corrupted HD that does not work anymore). And if i enter:
philippe@Ubuntu:~$ sudo mount /dev/sdb1p6
[sudo] password for philippe: 

I get:

mount: can't find /dev/sdb1p6 in /etc/fstab or /etc/mtab

So what should I do??

---

### Post by Bachstelze on 2009-09-23
> **pognonec said:**
> Yes, and no (since it is a copy of a corrupted HD that does not work anymore). And if i enter:
philippe@Ubuntu:~$ sudo mount /dev/sdb1p6
[sudo] password for philippe: 

I get:

mount: can't find /dev/sdb1p6 in /etc/fstab or /etc/mtab

So what should I do??

You must of course specify a mount point, but what do you want to do, exactly?

---

### Post by pognonec on 2009-09-23
> **Bachstelze said:**
> You must of course specify a mount point, but what do you want to do, exactly?

I want to have access to the data that I rescued from my crashed HD (sda, replace since by a new one) onto sdb1. But I am unable to access sdb1, while sdb2 and sdb3 (the 2 other partitions created at the same time as sdb1, but not used during the ddrescue process) are visible and mounted as soon as I turn the external drive on.

---

### Post by LewRockwell on 2009-09-23
> **pognonec said:**
> Yes, and no (since it is a copy of a corrupted HD that does not work anymore). And if i enter:
philippe@Ubuntu:~$ sudo mount /dev/sdb1p6
[sudo] password for philippe: 

I get:

mount: can't find /dev/sdb1p6 in /etc/fstab or /etc/mtab

So what should I do??

we use Puppy Linux LiveCD for most of our quick and dirty data recovery/rescue

[http://puppylinux.org/wikka/Puppy43](http://puppylinux.org/wikka/Puppy43)

[http://www.puppylinux.org/main/index.php?file=Download%20Latest%20Release.htm](http://www.puppylinux.org/main/index.php?file=Download%20Latest%20Release.htm)

as always, your mileage may vary, buyer beware, and buyer be aware

.

---

### Post by Bachstelze on 2009-09-23
> **pognonec said:**
> I want to have access to the data that I rescued from my crashed HD (sda, replace since by a new one) onto sdb1. But I am unable to access sdb1, while sdb2 and sdb3 (the 2 other partitions created at the same time as sdb1, but not used during the ddrescue process) are visible and mounted as soon as I turn the external drive on.

This is because /dev/sdb1 is the image of a *drive*. Therefore, you cannot mount it directly, just like you cannot mount a drive itself. Instead, you mount the *partitions* that drive contains, so it's the same for /dev/sdb1: you must mount the partitions it contains.

---

### Post by pognonec on 2009-09-23
> **Bachstelze said:**
> This is because /dev/sdb1 is the image of a *drive*. Therefore, you cannot mount it directly, just like you cannot mount a drive itself. Instead, you mount the *partitions* that drive contains, so it's the same for /dev/sdb1: you must mount the partitions it contains.

Thank you for your help!
I guess I see the idea. But on this "Absolute Beginner Talk" forum, could you please be a little more specific? What would be the detailed instructions to do just that?

---

### Post by pognonec on 2009-09-26
I opened a parallel thread ([http://ubuntuforums.org/showthread.php?t=1275160](http://ubuntuforums.org/showthread.php?t=1275160)), with apparently a better presentation of my problem. It got solved, thanks to Solitaire, who suggested trying "Testdisk". This Testdisk application is really a very nice and useful piece of software: all ma data is back! Thank you all for your help.
:-)

---

### Post by bigsuccess on 2009-11-30
[edit: didnt see this was solved.. oh well for more info]

Try this:
[https://help.ubuntu.com/community/DataRecovery#Extract%20filesystem%20from%20recovered%20image](https://help.ubuntu.com/community/DataRecovery#Extract%20filesystem%20from%20recovered%20image)

---

