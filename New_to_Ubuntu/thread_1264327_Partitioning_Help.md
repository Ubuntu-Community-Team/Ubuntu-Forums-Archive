---
title: "Partitioning Help"
date: 2009-09-12
forum: New to Ubuntu
---

### Post by stktek on 2009-09-12
I am ready to take the plunge and do a dual boot. What i would like to do is create 3 partitions on my 160gig hhd. 1st one will be 30gig for XP 2nd for Ubuntu 30gig and the remaining for storage of movies, pdf, music and pic which i want access to from both OS's is this possible and what file system should i use.

Aspire One D250 160gig hhd and 1gig ram.

---

### Post by Bucky Ball on 2009-09-12
[http://members.iinet.net/~herman546/index.html]("http://members.iinet.net/%7Eherman546/index.html")

That will help a lot. At least, you need these on your Ubuntu setup:

```
/
/home
/swap
```/ = root
/home = where your data lives
/swap = no more than 2Gb is fine

Install Windows on a partition size you want and make sure the rest of the disk is 'free space'.

Pop the Windows installer out and stick in the Ubuntu one. You will get to a section for partitioning. Choose manual and just don't go near the Windows partition. It will be NTFS so easy to spot. On the free space set up the partitions you want (the ones I provided are defaults in there but you can do whatever). Ubuntu bits are installed into / (root) and whatever else you setup. Good luck with it and post back with any more queries. Hope the transition goes smoothly for you. (Which release are you installing? 8.04 LTS is the most stable and longest supported, 9.04 could work fine too.)

---

### Post by armandh on 2009-09-12
create a 30 gig windows ntsf partition, active, pimary at the front of the drive and install xp. create and format a storage partition at the end of the drive, of a type useable by both OS [ntsf/fat32] using all but 30 gig. install Ubuntu selecting install to largest unpartitioned space [the remaing 30] and it will do the rest, including the swap!

ps if you only have the computer manufacturers xp restore
restore first [whole drive] then resize to 30 gig. and proceed to the storage.

re sizing an existing much fragmented partition is risky, a new restore will most likely succeed in resizing.

my mini-9 dual boots XP and Ubuntu but I use the SD card for storage
the dell ubuntu restore would not work. I needed to use OOTB ubuntu

---

### Post by KIAaze on 2009-09-12
For the shared partition, you can use FAT32, ext2, ext3 or NTFS theoretically.
-FAT32 is the safest, as it will be accessible out of the box from both OSes.
-ext2/ext3 will require one of the following solutions on Windows: [http://www.howtoforge.com/access-linux-partitions-from-windows](http://www.howtoforge.com/access-linux-partitions-from-windows)
Warning: Using the ext2/ext3 driver on Windows (last solution) will give you write access on ext2/ext3 partition, which might compromise the security of your Ubuntu installation.
-NTFS will require the [ntfs-3g]("http://www.ntfs-3g.org/") driver under GNU/Linux systems. I believe it's already installed by default in Ubuntu, since I can read/write to NTFS without problems without installing anything since at least Ubuntu v9.x I think.
Warning: Because NTFS is proprietary, the (reverse-engineered) ntfs-3g driver might not be perfect and lead to errors when writing.

---

### Post by talsemgeest on 2009-09-12
I would suggest you resize your XP partition to 130GB, as NTFS can be read by both OSs. That willo leave you 30GB free space at the end to install Ubuntu onto, which will be done quite easily in the Ubuntu setup ("install onto free space").

---

### Post by LewRockwell on 2009-09-12
you might find this thread interesting:

[http://ubuntuforums.org/showthread.php?t=1222961](http://ubuntuforums.org/showthread.php?t=1222961)

.

---

### Post by oldfred on 2009-09-12
I did something similiar 2-3 years ago and used FAT32 as at that time there were some questions on the NTFS-3g driver (since resolved). I was using that partition to backup my Ubuntu and every time the backup was 4GB which I assumed was correct. When I added a new drive and started updating to ext3 partition my backup was much bigger! Then I understood the find print that says FAT32 has a max file size of ~4GB.

If you are storing movies or large files I suggest the NTFS for a shared partition. I avoid writing a lot of data directly into my windows partition just in case of issues and back up the data partition. I like the idea of data separate from the operating system to make it easier to backup just data.

---

### Post by KIAaze on 2009-09-12
I've always wondered about that. :confused:
Does it mean you can't store more than 4GB?
Or that each file can't exceed 4GB?
Do files bigger than 4GB get split into smaller files or do they just get cut off?
Basically, did your backups on the FAT32 partition become useless or not?

---

### Post by talsemgeest on 2009-09-12
> **KIAaze said:**
> I've always wondered about that. :confused:
Does it mean you can't store more than 4GB?
Or that each file can't exceed 4GB?
Do files bigger than 4GB get split into smaller files or do they just get cut off?
Basically, did your backups on the FAT32 partition become useless or not?
It means that you can't store a single file that is more than 4GB. It is not split, it is simply cut off, so if you try to put a file that is greater than 4GB on a FAT32 partition (like a backup), it becomes useless.

---

### Post by louieb on 2009-09-12
> **stktek said:**
> 1st one will be 30gig for XP 2nd for Ubuntu 30gig and the remaining for storage of movies, pdf, music and pic which i want access to from both OS's is this possible and what file system should i use...

Nice plan - I really like keeping my data  separate from my OS - NTFS will work as well or better that any other file system  for a data partition shared by both OS. 

Only thing I would suggest is a 4th partition for Linux swap. In case you want to hibernate the PC make it a little larger than the amount of ram you have or plan to install in the future.

---

### Post by raymondh on 2009-09-13
> **stktek said:**
> I am ready to take the plunge and do a dual boot. What i would like to do is create 3 partitions on my 160gig hhd. 1st one will be 30gig for XP 2nd for Ubuntu 30gig and the remaining for storage of movies, pdf, music and pic which i want access to from both OS's is this possible and what file system should i use.

Aspire One D250 160gig hhd and 1gig ram.

Good scheme.

Wrap Ubuntu inside an extended (whether you decide to incorporate or separate /home).

Defrag windows (f you're taking space from it to establish your partitions).

---

