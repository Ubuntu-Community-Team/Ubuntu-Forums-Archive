---
title: "Problem in installation of Ubuntu. Loads directly into Windows"
date: 2011-05-29
forum: New to Ubuntu
---

### Post by snigam3112 on 2011-05-29
I had Vista installed on my laptop with the following drives: C - windows (approx. 24 GB)
F: Recovery and two other drives D; and E:. One of these had approx. 54 GB . I used a USB install of Ubuntu 11.04.
When the installation started, the Install asked me to decide how much space I wanted to allocate to the Ubuntu Install, by dragging some divider. I dragged it so that Ubuntu installed on something around 10 GB.

During the install, due to my slower internet connection, towards the end I had to "skip" the "downloading packages" phase of the install. 

Then the computer rebooted and directly into Windows. In Windows, I cannot see the 54 GB drive. I can't boot into Ubuntu.

Reading through some other threads, I thought maybe this information might be important:

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0c90a2d8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3142    25236448+   7  HPFS/NTFS
/dev/sda2            3142       10037    55380993    f  W95 Ext'd (LBA)
/dev/sda3           10037       13861    30718976    7  HPFS/NTFS
/dev/sda4           13862       14593     5879790    7  HPFS/NTFS
/dev/sda5            3142        8699    44634256    7  HPFS/NTFS
/dev/sda6            8699        9908     9707520   83  Linux
/dev/sda7            9908       10037     1037312   82  Linux swap / Solaris

Disk /dev/sdb: 4023 MB, 4023385600 bytes
255 heads, 63 sectors/track, 489 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000ca318

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         488     3919841    b  W95 FAT32



 i wrote sudo fdisk -l in the terminal and got the following output:




What went wrong? How do I fix it?

---

### Post by duke.tim on 2011-05-29
It looks like you need to install Grub. What version of Ubuntu are you using?

---

### Post by snigam3112 on 2011-05-29
Installing Ubuntu 11.04 (32-bit)

---

### Post by Miljet on 2011-05-29
> towards the end I had to "skip" the "downloading packages" phase of the install. 

Sounds to me like you interrupted the installation before it was complete.

---

### Post by snigam3112 on 2011-05-29
> **Miljet said:**
> Sounds to me like you interrupted the installation before it was complete.
 So, what do i do about it? How do i first uninstall the existing Ubuntu?

---

### Post by oldfred on 2011-05-29
Since it looks like it already created sda6 & sda7, you want to reuse those partitions.

To use the same partitons you have to use manual install which is now called "Something Else". You choose sda6 and tell it to format it to ext4 and set it to / (root). It will find swap automatically. 

One advantage of manual install is that you can also then select to add a /home partition if you desire.

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:
1. 10-20 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext3(or ext4)
3. 2 GB Mountpoint swap logical

---

### Post by wildmanne39 on 2011-05-29
> **snigam3112 said:**
> So, what do i do about it? How do i first uninstall the existing Ubuntu?

When I installed ubuntu it created 2 swap partitions, one was already there and I set it to use it but it still created another one much larger the same size as my ram 7 gigs.

---

### Post by snigam3112 on 2011-05-30
> **oldfred said:**
> Since it looks like it already created sda6 & sda7, you want to reuse those partitions.

To use the same partitons you have to use manual install which is now called "Something Else". You choose sda6 and tell it to format it to ext4 and set it to / (root). It will find swap automatically. 

One advantage of manual install is that you can also then select to add a /home partition if you desire.

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:
1. 10-20 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext3(or ext4)
3. 2 GB Mountpoint swap logical

i did the formatting to ext4 and setting it to /(root)... it worked!! Thx oldfred.

I didn't entirely understand the /home partition instructions, so i skipped that... what is the use of it anyway?

---

### Post by EGamerHDK on 2011-05-30
Yeah, this was my biggest problem when installing ubuntu onto my laptop. You need to format that certain partition before you can install it. Took me like three tries and it ended up working somehow.

---

### Post by Miljet on 2011-05-30
> I didn't entirely understand the /home partition instructions, so i skipped that... what is the use of it anyway?
Your personal files (pictures, documents, music, etc) are all stored in your /home folders. By putting the /home folder in a seperate partition, they will be preserved if you need, or want, to reinstall the operating system.

---

