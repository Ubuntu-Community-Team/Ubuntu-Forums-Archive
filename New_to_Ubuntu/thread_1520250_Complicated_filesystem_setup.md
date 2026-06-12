---
title: "Complicated filesystem setup"
date: 2010-06-29
forum: New to Ubuntu
---

### Post by gallifrey on 2010-06-29
Hi all, 
        just a question about how to best set up my filesystems. I am currently running Ubuntu Lucid, and using Ext4 on my partitions. However, for work related reasons that I don't really want to go into, I have had to install Win 7 on a dual-boot.

My problem is that all the data I need is on an Ext4 partition, and I do not want to have to copy it over, and sync it everytime it changes, so my question is this:

Can I have ntfs as my /home partition, and if so, how will it affect performance? Will r/w access times be impacted badly? Will video files still play as well as they did?

This really is a last resort, but one I am willing to try if the cost is not too high. 

Any input would be greatly appreciated.

---

### Post by nhasian on 2010-06-29
hmm thats a bit tricky.  linux requires a linux filesystem to run, so you cant run it from NTFS.  

you could have a separate /data partition that is NTFS that would be accessible from both windows as well as ubuntu.

finally there are tools to allow windows to read/write EXT2 and EXT3 partitions but as far as I know, it does not yet work with EXT4.  you would have to downgrade your partition to to EXT3 to use something like [Ext2Fsd]("http://sourceforge.net/projects/ext2fsd/")

---

### Post by gallifrey on 2010-06-29
That's as I expected. Of those options, the separate data partition would be th e most viable... I shall review my partitioning scheme. 

Thank you for your reply :)

---

### Post by warfacegod on 2010-06-29
> **gallifrey said:**
> That's as I expected. Of those options, the separate data partition would be th e most viable... I shall review my partitioning scheme. 

Thank you for your reply :)

I disagree. Converting your current /home to NTFS is probably the best option.

Whatever you decide to do, have a backup of your data handy in case this go amok.

---

