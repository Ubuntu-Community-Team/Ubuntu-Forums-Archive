---
title: "transfer speed ?"
date: 2011-06-09
forum: New to Ubuntu
---

### Post by neil_1 on 2011-06-09
when i used windows some time back , to transfer large amt of data (~200GB) to HDD's it used to be faster (transfer rate ~30 Mbps) 
but now when i use ubuntu , its ~20Mbps and gets slower sometimes ?
is something wrong ?

---

### Post by birkopf on 2011-06-09
> **neil_1 said:**
> when i used windows some time back , to transfer large amt of data (~200GB) to HDD's it used to be faster (transfer rate ~30 Mbps) 
but now when i use ubuntu , its ~20Mbps and gets slower sometimes ?
is something wrong ?

Pls write more about your system. Did you changed anything in the system settings ? 

What exactly do you mean by transferring data to HDD ? From HDD to HDD, from laptop, from external disk ? 

Last question - did you made any adjustments to fstab? What file system you are running ?

---

### Post by neil_1 on 2011-06-10
> **birkopf said:**
> Pls write more about your system. Did you changed anything in the system settings ? 
 
What exactly do you mean by transferring data to HDD ? From HDD to HDD, from laptop, from external disk ? 
 
Last question - did you made any adjustments to fstab? What file system you are running ?
didnt change anything in system
i meant moving movies / music/tv from laptop to external HDD
didnt make any adjustments to fstab

---

### Post by jtarin on 2011-06-10
Post the output of the terminal command "fdisk -l"

---

### Post by 3rdalbum on 2011-06-10
> **neil_1 said:**
> when i used windows some time back , to transfer large amt of data (~200GB) to HDD's it used to be faster (transfer rate ~30 Mbps) 
but now when i use ubuntu , its ~20Mbps and gets slower sometimes ?
is something wrong ?

Writing to NTFS filesystems is quicker in Windows than it is in Ubuntu. Because it's a non-native filesystem, writing to NTFS is CPU-bound (meaning that it only operates as fast as your CPU does).

There's no solution to this - the reverse problem is true as well (Windows writes to Ext2 slowly when it has an Ext2 driver). If your hard disk will not be used with Windows, format it as Ext4 instead. Or if you will not be copying files that are 4 GiB or greater, and you want to transfer them to Windows, then use the Fat32 filesystem instead.

---

### Post by RoyLongbottom on 2011-06-10
> **neil_1 said:**
> when i used windows some time back , to transfer large amt of data (~200GB) to HDD's it used to be faster (transfer rate ~30 Mbps) 
but now when i use ubuntu , its ~20Mbps and gets slower sometimes ?
is something wro
ng ?
 
[FONT=Verdana][SIZE=2]Data transfer speed of disk drives varies over the surface, typically with twice as much data on outer tracks compared with inner ones. So, transfer speed becomes slower as you fill up the disk (or cause it to be fragmented) . Get a new disk and you should see >100 MB/second.[/SIZE][/FONT]
[SIZE=2] [/SIZE]
[SIZE=2]Roy[/SIZE]

---

### Post by neil_1 on 2011-06-12
> **jtarin said:**
> Post the output of the terminal command "fdisk -l"
here
```

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x502f7f5a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13       20073   161132948+   7  HPFS/NTFS
/dev/sda3           20074       33269   105996839+   5  Extended
/dev/sda4           33270       60802   221151232    7  HPFS/NTFS
Partition 4 does not end on cylinder boundary.
/dev/sda5           20074       22686    20988891   83  Linux
/dev/sda6           22687       23208     4192933+  82  Linux swap / Solaris
/dev/sda7           23209       33269    80814951   83  Linux

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x3a83267b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       29018   233079808    7  HPFS/NTFS
/dev/sdb2           29018       30401    11114496    7  HPFS/NTFS
```
sdb1 is the windows partition
sdb2 is the recovery partition
i dont wanna trash original windows :P
> **3rdalbum said:**
>  If your hard disk will not be used with Windows, format it as Ext4 instead. Or if you will not be copying files that are 4 GiB or greater, and you want to transfer them to Windows, then use the Fat32 filesystem instead.
i've dual booted and want both OS's to see the partition , i have files greatr than 4 GB
> **RoyLongbottom said:**
> [FONT=Verdana][SIZE=2]Data transfer speed of disk drives varies over the surface, typically with twice as much data on outer tracks compared with inner ones. So, transfer speed becomes slower as you fill up the disk (or cause it to be fragmented) . Get a new disk and you should see >100 MB/second.[/SIZE][/FONT]

[SIZE=2]Roy[/SIZE]
so i'll defragment it and it will be a bit faster ?

---

### Post by jtarin on 2011-06-12
```
Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
**_[COLOR="Red"]Partition 1 does not end on cylinder boundary.[/COLOR]_**
/dev/sda2              13       20073   161132948+   7  HPFS/NTFS
/dev/sda3           20074       33269   105996839+   5  Extended
/dev/sda4           33270       60802   221151232    7  HPFS/NTFS
**_[COLOR="Red"]Partition 4 does not end on cylinder boundary.[/COLOR]_**
/dev/sda5           20074       22686    20988891   83  Linux
/dev/sda6           22687       23208     4192933+  82  Linux swap / Solaris
/dev/sda7           23209       33269    80814951   83  Linux
```
While there is nothing terribly wrong with that...it does add to the mix. You might think about your swap space,

---

### Post by VOT Productions on 2011-06-12
About the cylinder boundary error, you used Mb's and not cylinders. There is nothing really wrong, since mine does the same thing. Also, your swap partition is 4GB. You just only need a small 1GB one. Finally, ext4 to NTFS or vice versa is slower because you are using ntfs-3g. Boot to Windows to see "improvements."

---

### Post by neil_1 on 2011-06-12
whats the cylindar boundary thing  mean ?
and how do i correct it ?

---

### Post by VOT Productions on 2011-06-12
Don't worry about it. It is not a problem.

---

### Post by neil_1 on 2011-06-12
> **VOT Productions said:**
> Don't worry about it. It is not a problem.
alright :)

---

### Post by neil_1 on 2011-06-13
> **VOT Productions said:**
> About the cylinder boundary error, you used Mb's and not cylinders. There is nothing really wrong, since mine does the same thing. Also, your swap partition is 4GB. You just only need a small 1GB one. Finally, ext4 to NTFS or vice versa is slower because you are using ntfs-3g. Boot to Windows to see "improvements."
really ? only 1 gb swap ?
i have 4 gb ram 
but in this thread [http://ubuntuforums.org/showpost.php?p=10342308&postcount=3](http://ubuntuforums.org/showpost.php?p=10342308&postcount=3)
bucky ball said i need 2-4 gb swap  :/

---

### Post by jtarin on 2011-06-13
You've got 4GB's of ram......do your applications need more? 1GB is sufficient, 2 GB's....have you got the free space to give away?

---

### Post by neil_1 on 2011-06-13
> **jtarin said:**
> You've got 4GB's of ram......do your applications need more? 1GB is sufficient, 2 GB's....have you got the free space to give away?
ok so i'll resixze it to 1gb ?

---

### Post by jtarin on 2011-06-13
> **neil_1 said:**
> ok so i'll resixze it to 1gb ?Everybody has a different take on this and there are many theories.Most will agree 2GB's and I'm not saying that that is not what you need......try. Try one....if it doesn't seem enought then go bigger. You can always delete the extra space and combine it with your OS partition.

---

### Post by neil_1 on 2011-06-13
> **jtarin said:**
> Everybody has a different take on this and there are many theories.Most will agree 2GB's and I'm not saying that that is not what you need......try. Try one....if it doesn't seem enought then go bigger. You can always delete the extra space and combine it with your OS partition.
but what exactly is swap needed for ?
whenever i check in system monitor ,its never in use

---

### Post by jtarin on 2011-06-13
> **neil_1 said:**
> but what exactly is swap needed for ?
whenever i check in system monitor ,its never in use
You questions will be forever until you [read a]("http://www.linux.com/news/software/applications/8208-all-about-linux-swap-space")bout swap space.This only one of many articles about swap space. You'll have to make your own opinion.

---

