---
title: "out of great curiousity for filesystem"
date: 2009-03-18
forum: New to Ubuntu
---

### Post by sazan on 2009-03-18
Hi
I am a new learner about file system and trying to figure out what happens when a file system is created in a disk. 

I know few concepts behind it but eager to learn everything possible.

I created ext3 filesystem on a 2 GB disk and got following results.

---

### Post by sazan on 2009-03-18
```

# mkfs.ext3 /dev/sde

mke2fs 1.39 (29-May-2006)
/dev/sde is entire device, not just one partition!
Proceed anyway? (y,n) y

Filesystem label=
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
262144 inodes, 524288 blocks
26214 blocks (5.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=536870912
16 block groups
32768 blocks per group, 32768 fragments per group
16384 inodes per group
Superblock backups stored on blocks: 
        32768, 98304, 163840, 229376, 294912

Writing inode tables: done                            
Creating journal (16384 blocks): done
Writing superblocks and filesystem accounting information: done

This filesystem will be automatically checked every 23 mounts or
180 days, whichever comes first.  Use tune2fs -c or -i to override.


```

---

### Post by sazan on 2009-03-18
Now here I am curious about everything it shows and the logics behind it like -

what is fragment size, what it does ? how are the no. of groups(block,fragment) determined, what is the use of 5% memory to superuser...?

Above all how does a filesystem determine that how many backups it should create for a superblock, for greater size disks (500 GB) its much more . 

Can anyone put a light on all these basic concepts...????:o:o

---

### Post by TheLions on 2009-03-18
> **sazan said:**
> Now here I am curious about everything it shows and the logics behind it like -

what is fragment size, what it does ? how are the no. of groups(block,fragment) determined, what is the use of 5% memory to superuser...?

Above all how does a filesystem determine that how many backups it should create for a superblock, for greater size disks (500 GB) its much more . 

Can anyone put a light on all these basic concepts...????:o:o

wikipedia IS your friend:

[http://en.wikipedia.org/wiki/Unix_File_System](http://en.wikipedia.org/wiki/Unix_File_System)

---

### Post by sazan on 2009-03-18
went through wikipedia and few books, but didn't find the internal details ....

---

### Post by snova on 2009-03-18
> **sazan said:**
> what is fragment size, what it does ?

Hmm, no idea.

> how are the no. of groups(block,fragment) determined,

By the block size and the partition size.

> what is the use of 5% memory to superuser...?

The idea is that if the disk gets *really* full, there will always be a little space left over for the administrator.

> Above all how does a filesystem determine that how many backups it should create for a superblock, for greater size disks (500 GB) its much more .

One per block group.

---

### Post by LowSky on 2009-03-18
This will answer most of your questions

[http://olstrans.sourceforge.net/release/OLS2000-ext3/OLS2000-ext3.html](http://olstrans.sourceforge.net/release/OLS2000-ext3/OLS2000-ext3.html)
[http://en.wikipedia.org/wiki/Ext3](http://en.wikipedia.org/wiki/Ext3)

Note EXT4 will be the new standard shortly

[http://en.wikipedia.org/wiki/Ext4](http://en.wikipedia.org/wiki/Ext4)

---

### Post by sazan on 2009-03-19
@lowsky 

Thanks for the links... I had gone through them before I posted in this forum because it was not giving me the internal details of the operation. 
But anywayz thanks for the info. Even if ext4 comes, it is nothing but a checksum added to ext3, so it will definitely use similar concept of filesystem creation 

@snova

thanks for your input, was really helpful.

Additional query to your reply, that there is one superblock per group, that will make a lot of superblock backups, don't you think so , I know how the superblock backups are made according to the block size 
1 KB -> at 8 KB (+1 th) sector 
2 KB -> at 16 KB (+1 th) secor and so on 

Bu I think filesystem does know how many backups to make, but how does it decide that ?

---

### Post by TheUnderTaker on 2009-03-19
Try this site

[http://sunsite.nus.sg/LDP/LDP/tlk/node95.html]("http://sunsite.nus.sg/LDP/LDP/tlk/node95.html")

---

### Post by TheUnderTaker on 2009-03-19
Ext3 is exactly like ext2 except it has a journal.

---

### Post by TheUnderTaker on 2009-03-19
Oh here is one more site i found

[http://www.nongnu.org/ext2-doc/ext2.html]("http://www.nongnu.org/ext2-doc/ext2.html")

---

