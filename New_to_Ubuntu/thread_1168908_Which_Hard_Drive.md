---
title: "Which Hard Drive"
date: 2009-05-24
forum: New to Ubuntu
---

### Post by daniell59 on 2009-05-24
I have two hard drives. How can I determine which one Ubuntu was installed on?

Thanks

---

### Post by NHArticleTen on 2009-05-24
> **daniell59 said:**
> I have two hard drives. How can I determine which one Ubuntu was installed on?

Thanks

from terminal:

fdisk -l

---

### Post by taurus on 2009-05-24
You need to include sudo in front of the command.

```
sudo fdisk -**[COLOR="Blue"]l[/COLOR]**
```
And that is a lower case letter L, not number 1.

---

### Post by daniell59 on 2009-05-24
> **NHArticleTen said:**
> from terminal:

fdisk -l

I did as you instructed, and nothing happened.

---

### Post by louieb on 2009-05-24
As taurus pointed out its 

```
**sudo** fdisk -l
```

Post the output if you have more questions.
BTW this command list your hard drive(s) and shows their partition table

---

### Post by daniell59 on 2009-05-25
daniel@daniel-desktop:~$ sudo fdisk -l
[sudo] password for daniel: 

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8511808c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30402   244196352    7  HPFS/NTFS

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xead89d04

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       12749   102400000    7  HPFS/NTFS
/dev/sdb2           12750       19457    53882010    5  Extended
/dev/sdb5           12750       19177    51632878+  83  Linux
/dev/sdb6           19178       19457     2249068+  82  Linux swap / Solaris
daniel@daniel-desktop:~$ 


Please help me understand this. Does this mean that Ubuntu is on my second hard drive?

Thanks

---

### Post by taurus on 2009-05-25
Yes, Ubuntu is installed on the first logical partition, /dev/sdb5, of the second harddrive.  Your windows is on the first harddrive and you have a ntfs partition on the first primary of the second harddrive, /dev/sdb1.

---

### Post by daniell59 on 2009-05-25
> **taurus said:**
> Yes, Ubuntu is installed on the first logical partition, /dev/sdb5, of the second harddrive.  Your windows is on the first harddrive and you have a ntfs partition on the first primary of the second harddrive, /dev/sdb1.

Thanks
Everything is where I want it, though I did not know what I was doing when I installed Ubuntu.

---

