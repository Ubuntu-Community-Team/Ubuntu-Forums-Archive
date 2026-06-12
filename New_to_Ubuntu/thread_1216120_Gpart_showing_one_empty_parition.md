---
title: "Gpart showing one empty parition"
date: 2009-07-17
forum: New to Ubuntu
---

### Post by bluemarble on 2009-07-17
Hi there peps, 

It has been a while since I have been here which i guess is a good thing (thing have been working). 

Unfortunately when grub updated I lost access to my windows partition. This might be related to Gpart showing one big empty partition.

My partition table seems to be fine (see fdisk -l below)

Any ideas on whats wrong with my system?

Cheers B

bluemarble@flyingBumble:~$ sudo fdisk -l
omitting empty partition (5)

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe796e796

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3187    25599546    7  HPFS/NTFS
/dev/sda2            3188       15633    99972495    b  W95 FAT32
/dev/sda3           15634       19457    30716280    5  Extended
/dev/sda4           17546       18820    10241406   83  Linux
/dev/sda5           15634       17545    15358077   83  Linux
/dev/sda6           18821       19457     5116671   82  Linux swap / Solaris

---

### Post by cariboo on 2009-07-17
Can you access /dev/sda1 from Ubuntu? Give this [thread=224351]howto[/thread] a try.

---

### Post by esalnoj on 2009-07-17
Have you checked any posts by meifrera?
He has a guide for setting partition tables to work.

The last time I had a letter as partition id, the install process had gone gone buggy.

Ubuntu also has not recognized windows in a partition behind a FAT32 on me before.

---

### Post by bluemarble on 2009-07-18
> **cariboo907 said:**
> Can you access /dev/sda1 from Ubuntu? Give this [thread=224351]howto[/thread] a try.

I cannot access /dev/sda1 from ubuntu and I tried the link you provided but nothing changed.

I still get the grub menu (as before) but with no option for the windows partition.


I cannot find any post by meifrera

I should mention that I tried a reinstall (windows and ubuntu) and the problem is still here. Maybe I should format /home as well.

---

### Post by Tman5293 on 2009-07-18
No I believe your problem lies with GRUB itself. I think your problem might a faulty MBR (Master Boot Record). If this is the case you need to wipe your hard drive and start over.

---

### Post by bluemarble on 2009-07-18
If that be the case could just wipe ubuntu or would I need to wipe then entire drive?

---

### Post by LewRockwell on 2009-07-18
surely you didn't wipe your drive before trying out SuperGrubDisk

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

.

---

### Post by louieb on 2009-07-18
> **bluemarble said:**
> 

```
bluemarble@flyingBumble:~$ sudo fdisk -l
omitting empty partition (5)

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe796e796

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3187    25599546    7  HPFS/NTFS
/dev/sda2            3188       15633    99972495    b  W95 FAT32
/dev/sda3 [COLOR=Red]          15634       19457 [/COLOR]   30716280    5  Extended
/dev/sda4 [COLOR=Red]          17546       18820[/COLOR]    10241406   83  Linux
/dev/sda5           15634       17545    15358077   83  Linux
/dev/sda6           18821       19457     5116671   82  Linux swap / Solaris
```

Did you do a reinstall of windows?  Sometime that will leave you with a non-standard partition table.

In your case primary partition sda4 is inside of extended partition sda3. Gparted sees that and treats the drive as blank. 

It can be fixed. 1st follow the [Boot Info Script Instructions]("http://ubuntuforums.org/showpost.php?p=6725571&postcount=3")  and put the results.txt  in your next post. (either attach it or be sure to wrap code tags around it. 

sfdisk is what to use to fix

---

### Post by esalnoj on 2009-07-18
Sorry bluemarble, my syntax error.

Here is the link to where meirefra explains how he fixes partition tables: [http://ubuntuforums.org/showthread.php?t=1126190&page=3](http://ubuntuforums.org/showthread.php?t=1126190&page=3)

Especially post 30. Page 1 of the thread says where to insert the PT.txt.

---

### Post by bluemarble on 2009-07-19
> **louieb said:**
> [/CODE]

Did you do a reinstall of windows?  Sometime that will leave you with a non-standard partition table.

In your case primary partition sda4 is inside of extended partition sda3. Gparted sees that and treats the drive as blank. 

It can be fixed. 1st follow the [Boot Info Script Instructions]("http://ubuntuforums.org/showpost.php?p=6725571&postcount=3")  and put the results.txt  in your next post. (either attach it or be sure to wrap code tags around it. 

sfdisk is what to use to fix

Hi,

I followed the instructions in the link and they are below. It does not make much sense to me but there appears to be some problems in there.

Do you know if it is fixable?

bluemarble

---

### Post by sandyd on 2009-07-19
```
**/dev/sda3 overlaps with /dev/sda4**
```
your hard disk partitions are suffering from something called overlapping partitions.
Its a sign of hard disk failure/problems (i had the ssame thing and turns out my hard disk was damaged )

When you get an overlapping partition, its best to reinstall.

P.S. this also happened when i reinstalled windows in a ubuntu/windows dual boot, not sure why)

---

### Post by louieb on 2009-07-20
> **bluemarble said:**
> ...It does not make much sense to me but there appears to be some problems in there. Do you know if it is fixable?

Yes it can be fixed without stating over. Need the output of one more command. This will give the start and end points in sectors instead of cylinders. 

```
sudo sfdisk -d /dev/sda 
```

In case your wondering  there are two ways to fix one is to change sda4 into a logical partition. The other is to move the start point of sda3 to just after the end of sda4. After seeing the output of above will be able to tell if one is better than the other. 

more about sfdisk and how to use it. [sfdisk to fix partition table problems]("http://ubuntuforums.org/showthread.php?t=1192598") 
off to work now - back in about 14 hours.

---

### Post by bluemarble on 2009-07-20
ummmmm..... I think I broke it!

ubuntu@ubuntu:~$ sudo sfdisk -l

Disk /dev/sda: 19457 cylinders, 255 heads, 63 sectors/track
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sda1          0       -       0          0    0  Empty
/dev/sda2          0       -       0          0    0  Empty
/dev/sda3          0       -       0          0    0  Empty
/dev/sda4          0       -       0          0    0  Empty
ubuntu@ubuntu:~$ 

Lucky I have everything backed up.... well except my windows partition.... All I did was try booting from Ubuntu 9.04 on USB and it destroyed GRUB completely. Now just get an GRUB error 15 or 7 or something! Running from live CD now :(

---

### Post by sandyd on 2009-07-20
that doesn't look good....

---

### Post by louieb on 2009-07-20
Its broke. some how the partition table got wiped out. Do see how booting from a USB version of Ubuntu could have cleared the partition table. 
Do you remember doing anything else?  

Anyway if you had the output from 
```
sudo sfdisk -d /dev/sda
```

you could restore the partition table to like it was before. Still non standard but at least you data could be accessed.

Time to break out **testdisk**. It finds lost and missing partitions
Get the latest version on the [SystemRescueCd]("http://www.sysresccd.org/Main_Page")  and go through the tutorial at [TestDisk - CGSecurity]("http://www.cgsecurity.org/wiki/TestDisk")  . Depending on what wiped the partition table I'm pretty sure testdisk can get things back in working order.

---

### Post by bluemarble on 2009-07-26
Everything is now reinstalled and running smoothly..... for now :)

Thanks for the help!

B

---

