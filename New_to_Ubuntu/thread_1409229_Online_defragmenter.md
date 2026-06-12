---
title: "Online defragmenter ?"
date: 2010-02-17
forum: New to Ubuntu
---

### Post by ex-wirecutter on 2010-02-17
Does anyone know where I can get this ?

Online defragmentation

Although ext4 incorporates features to reduce fragmentation within the file system (extents for sequential block allocation), some amount of fragmentation is impossible to avoid when a file system exists for a long period of time. For this reason, an online defragmentation tool exists to defragment both the file system and individual files for improved performance. The online defragmenter is a simple tool that copies files into a new ext4 inode that refers to contiguous extents.

The other aspect of online defragmentation is the reduced time required for a file system check (fsck). Ext4 marks unused groups of blocks within the inode table to allow the fsck process to skip them entirely to speed the check process. When the operating system decides to validate the file system because of internal corruption (which is inevitable as file systems increase in size and distribution), ext4's overall design means improved overall reliability. 
Thanks

---

### Post by chewearn on 2010-02-18
[http://ubuntuforums.org/showthread.php?t=169551](http://ubuntuforums.org/showthread.php?t=169551)
[http://www.webupd8.org/2009/10/defra...lesystems.html]("http://www.webupd8.org/2009/10/defragmenting-linux-ext3-filesystems.html")

I have never used any of the software in these links, so it's your own risk.

---

### Post by ex-wirecutter on 2010-02-18
Humm...looks a bit complicated ( and risky ) to me , think I will leave well alone.
Thanks for the link .

---

### Post by linux18 on 2010-07-08
A little online defragging command i made ( with help from [www.commandlinefu.com](www.commandlinefu.com) ):

 find ~ -maxdepth 20 -type f -size -16M -print > t; for ((i=$(wc -l  < t); i>0; i--)) do a=$(sed -n ${i}p < t); mv "$a" /dev/shm/d;  mv /dev/shm/d "$a"; echo $i; done; echo DONE; rm t

 for external hard drives, replace the "~"  in "find  ~ -maxdepth" with the location of the drive. 

example:

find /dev/sdb1 -maxdepth 20 -type f -size -16M -print > t; for  ((i=$(wc -l < t); i>0; i--)) do a=$(sed -n ${i}p < t); mv "$a"  /dev/shm/d; mv /dev/shm/d "$a"; echo $i; done; echo DONE; rm t
   
this works in most cases. the script basically re-copies most data under  16 mb from the drive back to the drive. it works because most  filesystems (including fat 32 ) will always try to keep new data  contiguous when it is saved. 

but really, linux very rarely needs defragmenting

---

