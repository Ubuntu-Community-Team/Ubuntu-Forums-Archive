---
title: "Access Vista with Ubuntu booted?"
date: 2008-12-28
forum: New to Ubuntu
---

### Post by crollino on 2008-12-28
I booted Linux Ubuntu 8.10 on my laptop which had Windows Vista but I don't know if I partitioned the hard drive the right way. I might have let Ubuntu use the whole hard drive, but I'm not sure.
Are all my documents from Vista lost? I can't find them through Ubuntu.
How can I get back into Vista?
Would removing Ubuntu or using a Vista recovery disc recover my documents?
I just want my school work to be safe. Thanks!!!!!!!

---

### Post by northern lights on 2008-12-28
Can you please post the output of ```
sudo fdisk -l
```(Open a Terminal from Applications > Accessories > Terminal, type or copy/paste the above, hit Enter, copy/past the result here, use code tags - hash/pound/# sign)

Thank you.

The output will yield detailed information on how many drives/partitions you have.

If Windows is not mentioned in GRUB, I fear you wiped it though.

Should you have indeed overwritten it, no Windows Recovery CD in the world will help you.
Had you just deleted the data, you'd have a chance by immediately seizing to write anything to the hdd and using a data recovery tool, but should have chosen to use the entire disk during the ubuntu install, you'd have formatted the hdd with a completely new filesystem. In that case you will not recover a thing.

---

### Post by teh_yodeler on 2008-12-28
^^^^^^ What he said.

---

### Post by crollino on 2008-12-28
Here's what it said:

charles@charles-laptop:~$ sudo fdisk -l

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf99b3d64

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       23614   189679423+  83  Linux
/dev/sda2           23615       24321     5678977+   5  Extended
/dev/sda5           23615       24321     5678946   82  Linux swap / Solaris
charles@charles-laptop:~$ 

Thanks for helping!

---

### Post by northern lights on 2008-12-28
> **crollino said:**
> Disk [COLOR="DarkOrchid"]/dev/sda: 200.0 GB[/COLOR], 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf99b3d64

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       23614   189679423+  83  [COLOR="Red"]Linux[/COLOR]
/dev/sda2           23615       24321     5678977+   5  [COLOR="Orange"]Extended[/COLOR]
/dev/sda5           23615       24321     5678946   82  [COLOR="RoyalBlue"]Linux swap / Solaris[/COLOR]


[COLOR="DarkOrchid"]This is your harddrive.[/COLOR]
Below you see the partition table.
[COLOR="Red"]This is Ubuntu on a primary partition.[/COLOR]
[COLOR="Orange"]This the extended partition which encompasses all logical partitions.[/COLOR]
[COLOR="RoyalBlue"]This is the swapspace (virtual memory, equivalent to pagefile.sys in Windows). Logical partition.[/COLOR]

Long story short: You wiped everything. And thoroughly reformatted with a new filesystem (ntfs to ext3). Data lost forever. I can feel your pain.

Only thing you can do now is look towards the future.

Do you want Windows back, even without the data?

If so, install it first. Create a Vista partition (ntfs) and a separate data one (ntfs or FAT32), which can be accessed from both opearating systems. Then install Ubuntu anew, choosing manual partitioning, and create an Ubuntu partition, a swapspace and possibly (I'd do so) a separate home.

Linux can handle ntfs and FAT32, while Windows needs third party software to read ext3. Here's an exemplary partition table that should suit your needs:

```
Use........filesystem..Size(GB)..Win ID..Linux ID....Mountpoint...Type

Vista......ntfs........50........C:\...../dev/sda1/..----------...Primary
Ubuntu.....ext3........15........------../dev/sda2/../............Primary
Extended...----------..135.......------../dev/sda3/..----------...Extended (You don't have to create this)
Data.......ntfs........116.......D:\...../dev/sda5/../media/Data..Logical
Home.......ext3........15........------../dev/sda6/../home........Logical
Swapspace..swap........4.........------../dev/sda7/..swap.........Logical
```

---

