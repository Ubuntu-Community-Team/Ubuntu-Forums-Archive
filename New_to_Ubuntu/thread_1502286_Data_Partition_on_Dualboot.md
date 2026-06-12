---
title: "Data Partition on Dualboot?"
date: 2010-06-05
forum: New to Ubuntu
---

### Post by kamitsukai on 2010-06-05
So I've just replaced the Hard drive in my Dell Inspiron 1525 with a Nice beefy 640gb drive and would like to dual-boot with Ubuntu and Windows 7

I've dual-booted before but I've never got a partition setup I've liked xD

Basically I want to have 3 partitions one for Windows and one for Ubuntu and then a 3rd huge data partition that both Ubuntu and Windows can read which I can store all my music and video.

How would I set this up from the Ubuntu installer?

what file system should I use? Fat? Fat32? NTFS? There's a good possibility that I'd like to store files larger then 4gb on the data partition so fat/fat32 would be a problem...

---

### Post by admiralspark on 2010-06-05
NTFS is readable from both Ubuntu and Windows. I suppose you could use that without problems, just set it to mount automatically each time ubuntu is booted up. I'm not sure ATM how one goes about that, since I always have to authenticate mounting my windows partition manually.

---

### Post by Penguin Guy on 2010-06-05
I've attached a screenshot my setup: Windows XP (NTFS), Shared Linux Partition (ext4), [Ubuntu 9.10 (ext4), Ubuntu 10.04 (ext4), Arch Linux (ext4)].

Do something similar, but format the shared partition as something readable by Windows and Linux. The screenshot is of [GParted]("apt:gparted") (included on the liveCD) - you'll probably find it easier to format your partitions with that, rather than the installation tool.

As for what to format the partition as, I don't have a clue.

---

### Post by alexismyname on 2010-06-05
What you should do is create and install the windows 7 o.s. partition first, leaving the rest of the disc alone for now.  after you install windows 7, use the disc manager to create your shared partition, leaving some space on the disc for ubuntu.  Ubuntu will read ntfs and if you install windows first you shouldn't have any boot issues with ubuntu.  I would think this is your best bet.  Its funny because I was considering doing something similiar with my harddrive... But I have a 750g external that I boot a copy of ubuntu off of with a separate ntfs partition to share data between windows and ubuntu...

hope this works for you

---

### Post by Jeanke on 2010-06-05
I had a same kind of setup for long time (untill I kicked Windows out for good) and I agree with Alexis, that way it worked perfectly for me.

---

### Post by oldfred on 2010-06-05
I originally had just root, swap and a shared FAT partition with XP as 3 years ago the NTFS driver was not as good. Now it is considered reliable.
I have since converted the FAT to NTFS but now use XP so little most of my data is going into a ext3 /data partition. I still have my photos, firefox and thunderbird in the NTFS partition so I have the same data in both.

Partitioning basics with some info on /data
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition](http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition)
Mount, hide & link windows partition
[http://ubuntuforums.org/showthread.php?t=1397508](http://ubuntuforums.org/showthread.php?t=1397508)
Share Windows partition:
[http://lifehacker.com/348858/use-a-single-data-store-when-dual-booting](http://lifehacker.com/348858/use-a-single-data-store-when-dual-booting)

---

