---
title: "Missing space on ext4"
date: 2011-03-31
forum: New to Ubuntu
---

### Post by MarkTrent on 2011-03-31
Hello,

I formatted a 2TB hard drive using ext4, and disabled both the journal and block reservation at creation to maximise my storage space. This worked great and after formatting, my hdd had only 64mb used by the filesystem (half as much as if I'd formatted it as NTFS).

I then copied 1.3TB of data from a 2TB NTFS hard drive onto the fresh drive. After completion I've checked my drive and the ext4 drive has 33.7GB less space available than the NTFS drive, both containing the exact same files (apart from the lost+found directory). I dismissed myself and ran the commands to disable journaling and set the reserved blocks to 0% again, thinking I must've forgotten to do this originally, but it turns out I had indeed done this when I first formatted the drive.

Unfortunately I rebooted after the transfer before I checked the disk spaces, so I can't be sure wether the space was missing directly after the transfer, or if it occurred after the restart. Does anyone know where the space has gone?

I'm quite new to Linux, and I just want a file system that gives me the low space overheads of NTFS, but with good speed on Linux. Is there a better filesystem I should be using? It's used as a media storage drive. (Coming from Windows, I originally formatted the new drive as NTFS but found it had slow transfer speeds so switched to ext4; went from 15mb/s --> 115 mb/s)

Thanks for any info,
Mark

---

### Post by seawolf167 on 2011-04-01
ext format saves 5% as system overhead during formatting. You can turn it off but its been too long and I can't remember the command, hopefully someone else will chime in that knows it.

EDIT: [here]("http://www.lisnichenko.com/articles/ext3-file-system-overhead-disclosed-part-1.html") is a good explanation + the commands

---

### Post by MarkTrent on 2011-04-02
Thanks for the reply, but I already set the reserved space to 0% when formatting, and once afterwards as well to make sure, so I know that's not the problem.

---

### Post by oldfred on 2011-04-02
It can make a difference if you have large files or lots of small files on which system is "best". I think ext4 is overall better but see this:

Large HDD/SSD Linux 2.6.38 File-System Comparison: EXT3, EXT4, Btrfs, XFS, JFS, ReiserFS, NILFS2
[http://www.phoronix.com/scan.php?page=article&item=linux_2638_large&num=1](http://www.phoronix.com/scan.php?page=article&item=linux_2638_large&num=1)

---

