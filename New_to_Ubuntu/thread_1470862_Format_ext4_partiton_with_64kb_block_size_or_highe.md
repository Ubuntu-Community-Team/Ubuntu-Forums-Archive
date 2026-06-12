---
title: "Format ext4 partiton with 64kb block size or higher"
date: 2010-05-03
forum: New to Ubuntu
---

### Post by sonnet on 2010-05-03
When I installed ubuntu 10.04 64bit I didn't find any option to format ,neither with the installer or gparted, some of the partions on my hard drives (using ext4) with a block size different from the default one.
With Windows operating system and ntfs fs is possible format partition with block size up to 64kb.
I would like to know 
1-it it's possible to do the same with ext4 or eventually other fs like jfs,
2-what's eventually the higher block size limit (64kb or higher?)   
3-and how to do that (in the simplest way).

---

### Post by clhsharky on 2010-05-03
HI sonnet

I don,t know, good question though.
Reading here leads you to believe it can, but nothing on how.

[http://lwn.net/Articles/266274/](http://lwn.net/Articles/266274/)

Sharky

---

### Post by srs5694 on 2010-05-03
Advanced options like that often require going to command-line tools. In this case, that would be mke2fs. Type "man mke2fs" in a shell to read up on all the options. The relevant option is -b; however, the man page description indicates that the legal options are 1024, 2048, and 4096 (bytes per block), so unless the man page is out of date, it doesn't go up to 64KB.

This begs the question: Why do you want to create a filesystem with a 64KB block size? Chances are you're trying to achieve some specific goal that can be achieved this way with NTFS; however, your true goal may be better achieved in some other way with Linux. (I don't know enough about NTFS to guess what your true goal may be.) If you could say what you hope to accomplish, perhaps somebody can give you pointers for a way to do it in Linux.

---

### Post by sonnet on 2010-05-03
> **srs5694 said:**
> Advanced options like that often require going to command-line tools. In this case, that would be mke2fs. Type "man mke2fs" in a shell to read up on all the options. The relevant option is -b; however, the man page description indicates that the legal options are 1024, 2048, and 4096 (bytes per block), so unless the man page is out of date, it doesn't go up to 64KB.

This begs the question: Why do you want to create a filesystem with a 64KB block size? Chances are you're trying to achieve some specific goal that can be achieved this way with NTFS; however, your true goal may be better achieved in some other way with Linux. (I don't know enough about NTFS to guess what your true goal may be.) If you could say what you hope to accomplish, perhaps somebody can give you pointers for a way to do it in Linux.
I have 4 partitions, which I want use for large media files (of several mb) and for .vdi file (for virtualbox vm) of several GB.
As increased block size on the FS for such large files would increase the throughput, I was looking to increase to do that on my new ext4 partition as I used to do with ntfs partition.

---

### Post by srs5694 on 2010-05-03
It's possible that a mount option will do what you want, but I'm not positive of that. Type "man mount" to read the relevant man page. (You'll need to scroll down a way for the ext2/ext3/ext4 mount options.) The "stripe" option looks promising, but the man page description isn't clear enough to me to be sure it does what you want. Perhaps a Web search will turn up better information.

I know from personal experience that the "allocsize" option does the job for XFS, if using XFS rather than ext4fs is acceptable to you. I use "allocsize=512m" on my MythTV box's media partition, and this slightly improves performance vs. using the defaults. (The effect isn't dramatic, but it can be measured.)

---

