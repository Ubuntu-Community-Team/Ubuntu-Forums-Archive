---
title: "What is &quot;DATADRIVE&quot;?"
date: 2010-11-14
forum: New to Ubuntu
---

### Post by artificialname on 2010-11-14
APOLOGIES for the absolute beginner-ness of this question:

When I click on PLACES - COMPUTER

a window comes up with a list down the left hand side.

the list is:

myusername - desktop - file system - network - DATADRIVE - floppy disk - trash - documents - music - pictures

1) What is DATADRIVE? A second internal hard disk?
2) What is file system - the same as "c: drive" in windows?

DATADRIVE - when I double click on it, it said - free space 465.5 gb. it it has 4 directories: "recycled - recycler - system volume information - 192e4d12d4b647987bbfqw" 

3) what are these directories? can i delete them?

---

### Post by ubudog on 2010-11-14
1. This may be from your old Windows install (I'm not sure)

2. Yes, the file system is like the C:Drive, it contains the /etc, /bin, and other vital directories that contain the program files, etc.

---

### Post by artificialname on 2010-11-14
> **ubudog said:**
> 1. This may be from your old Windows install (I'm not sure)
 
.
 
 
But what IS IT? a seperate internal hard disk? a partition on my main hard disk?

---

### Post by coffeecat on 2010-11-14
> **artificialname said:**
> But what IS IT? a seperate internal hard disk? a partition on my main hard disk?

It's a partition on your internal hard drive with a partition label of 'DATADRIVE'. This...

> **artificialname said:**
> DATADRIVE - when I double click on it, it said - free space 465.5 gb. it it has 4 directories: "recycled - recycler - system volume information - 192e4d12d4b647987bbfqw" 

... suggests that it is a NTFS partition. It's probably your old but unused D: or E: partition. You have a lot of free space in it. How big is your hard drive altogether?

> **artificialname said:**
>  3) what are these directories? can i delete them?  

You can't delete entries from the Places menu; they are giving you information about your system. But if you have an unused partition of nearly 500GB, let's do some investigation. Open a terminal (Applications > Accessories) and post the output of this command:

```
sudo fdisk -lu
```

---

### Post by artificialname on 2010-11-14
> **coffeecat said:**
> It's a partition on your internal hard drive with a partition label of 'DATADRIVE'....How big is your hard drive altogether?...Open a terminal and post the output of this command:

```
sudo fdisk -lu
```

1) are you sure it is a partition? I suspect I have 2 internal hard drives. Is there any way to check?

2)I am not sure how big they are altogether

3) result of ```
sudo fdisk -lu[/code is:

[code]sudo fdisk -lu
```

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000104b0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   149838254    74919096   83  Linux
/dev/sda2       149838255   156296384     3229065    5  Extended
/dev/sda5       149838318   156296384     3229033+  82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x9d015d38

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   976768064   488384001    c  W95 FAT32 (LBA)

---

### Post by coffeecat on 2010-11-14
> **artificialname said:**
> 1) are you sure it is a partition? I suspect I have 2 internal hard drives. Is there any way to check?

Yes, I am sure it is a partition. Yes, it is a second drive with just one big partition. And, yes, you've already checked with your fdisk output. :)

sda is your first hard drive of 80GB with your Linux partitions. sdb is your second 500GB HD with just one FAT32 partition. I was wrong about it being NTFS. Those folders you can see in Linux would be hidden in Windows. Which means your sdb1 FAT32 partition has the label 'DATADRIVE'. I should have realised it was probably FAT32 from the all-caps label.

---

### Post by Elfy on 2010-11-14
Make sure you have doubleclicked the 'datadrive' then run ```
mount
``` from a terminal and post the result.

---

### Post by nlsthzn on 2010-11-14
Not a lot of people have about 500GB they are not aware of :D

---

### Post by artificialname on 2010-11-14
> **coffeecat said:**
> Yes, I am sure it is a partition. Yes, it is a second drive with just one big partition. And, yes, you've already checked with your fdisk output. :)
 
sda is your first hard drive of 80GB with your Linux partitions. sdb is your second 500GB HD with just one FAT32 partition. I was wrong about it being NTFS. Those folders you can see in Linux would be hidden in Windows. Which means your sdb1 FAT32 partition has the label 'DATADRIVE'. I should have realised it was probably FAT32 from the all-caps label.
 
 
THANKS! Awesome advice!
 
1) if sdb is 500 gb, how come it only shows 465.5gb free space?
2) in sdb, can I delete, "recycled - recycler - system volume information - 192e4d12d4b647987bbfqw" ? are they just windows rubbish?
3) should i just start using it to store media, or should I format it first?
4) How do I format it? should I use Fat32 or Ntfs ?
 
Thanks again!

---

### Post by apollothethird on 2010-11-14
> **artificialname said:**
> 1) are you sure it is a partition? I suspect I have 2 internal hard drives. Is there any way to check?

2)I am not sure how big they are altogether

3) result of ```
sudo fdisk -lu[/code is:

[code]sudo fdisk -lu
```

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000104b0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   149838254    74919096   83  Linux
/dev/sda2       149838255   156296384     3229065    5  Extended
/dev/sda5       149838318   156296384     3229033+  82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x9d015d38

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   976768064   488384001    c  W95 FAT32 (LBA)

You have two hard drives in your computer.  The first line of the first block of your output (sda) is your first drive.  It’s capacity if 80 Gigs.

The second block of your output shows that your 80 Gig hard drive is divided into 3 partitions.

1 partition of 74 Gigs and 2 partitions of 3 gigs.  The 74 Gig partition is the drive with your Linux operating system.  You’re using 3 Gigs (the third partition for you linux swap drive.

The second drive is a 500 Gig hard drive.  When you were running Windows it had originally been setup as an area to store data.  That’s why the person who set it up named it a data drive.  The original post indicate that either it was never used or all the information stored on it was deleted (moved to the recycle bin) before Windows was removed from your system.

It would be safe, if you wanted to, to reformat the large drive for use on your Linux system for storing data, such as backups, video files, etc.  Linux can use the drive in the Windows NTFS format, but having it formatted under Linux would make it faster, more efficient and less in the need of defrag.

By the way, if you’re considering it for use as a backup, I advise you not to use it as your own backup of your important data.  Having a backup of your most important data on a different machine is a good way of protection against lost, in the event of something extraordinary such as theft.

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

### Post by tad1073 on 2010-11-14
> **artificialname said:**
> THANKS! Awesome advice!
 
1) if sdb is 500 gb, how come it only shows 465.5gb free space?
2) in sdb, can I delete, "recycled - recycler - system volume information - 192e4d12d4b647987bbfqw" ? are they just windows rubbish?
3) should i just start using it to store media, or should I format it first?
4) How do I format it? should I use Fat32 or Ntfs ?
 
Thanks again!

1. forgot why
2. if you have no windows installations
3. sure
5. Use gparted to format. ntfs
```
sudo apt-get install gparted
```

---

### Post by coffeecat on 2010-11-14
> **artificialname said:**
> 1) if sdb is 500 gb, how come it only shows 465.5gb free space?

Because if it's telling you 465.5 GB and not 465.5 GiB, then that's a bug. Which is it saying: GB or GiB?

1GB = 1 gigabyte = 1,000,000,000 bytes
1 GiB - 1 gibibyte = 1024x1024x1024 bytes = 1073741824 bytes.

500.1 GB = 465.75 GiB. You've 'lost' about .25GiB to the file allocation table or whatever.

> **artificialname said:**
>  2) in sdb, can I delete, "recycled - recycler - system volume information - 192e4d12d4b647987bbfqw" ? are they just windows rubbish?

Best to leave them. They are part of the function of the filesystem. I am hazy about the details, although the first three might be telling you something from their names. :p

> **artificialname said:**
> 3) should i just start using it to store media, or should I format it first?

You could just use it but FAT32 is an ancient filesystem, unjournalled and not particularly robust. It also has a 4GB file size limit.

> **artificialname said:**
> 4) How do I format it? should I use Fat32 or Ntfs ?

Don't use NTFS unless you have Windows on the same system to fix it when/if something goes wrong with the filesystem. For a Linux only system, it's best to use ext3 or ext4 but you will have permissions problems with it until you doing some chown-ing and chmodding. Post back if you want to do that.

---

### Post by CharlesA on 2010-11-14
The "missing" space is due to the way hard drive manufacturers measure disk space - using base 10, not base 2. Don't worry about it.

EDIT: Ninja'd by coffeecat. :P

---

### Post by apollothethird on 2010-11-14
> **artificialname said:**
> THANKS! Awesome advice!
 
1) if sdb is 500 gb, how come it only shows 465.5gb free space?
2) in sdb, can I delete, "recycled - recycler - system volume information - 192e4d12d4b647987bbfqw" ? are they just windows rubbish?
3) should i just start using it to store media, or should I format it first?
4) How do I format it? should I use Fat32 or Ntfs ?
 
Thanks again!

You can easily reformat it by clicking on System -> Administration -> Disk Utility -> (select the 500 GB Hard disk) -> (click) Format.

As I mentioned previously, your best filesystem would be Linux (ext3 or ext4).  The ext4 would be the best of the later.  When you click on the Format button that should be listed first.

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

### Post by artificialname on 2010-11-14
Thanks Everyone! Awesome advice!
 
I have not been to this forum in a while. Good to see it is the same helpful, friendly place!

---

### Post by ubudog on 2010-11-15
> **artificialname said:**
> Thanks Everyone! Awesome advice!
 
I have not been to this forum in a while. Good to see it is the same helpful, friendly place!

The people here are awesome.

---

