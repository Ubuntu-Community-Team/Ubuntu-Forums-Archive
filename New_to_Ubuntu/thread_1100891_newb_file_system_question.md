---
title: "newb file system question"
date: 2009-03-19
forum: New to Ubuntu
---

### Post by arthritisankle on 2009-03-19
I formatted an external hard drive to FAT32 so that I might use it with both Ubuntu and windows.  Now I find out that the maximum file size is 4gb and I am hoping to stream HD video content from this drive.

I really don't care about accessing the drive with windows (just thought it would be nice) so what filesystem should I format the drive to?  ext2? 3?  

Thanks

---

### Post by cmnorton on 2009-03-19
ext3 is journalled and more easily recovered.

---

### Post by Nxion on 2009-03-19
> **cmnorton said:**
> ext3 is journalled and more easily recovered.

+1 on that...

---

### Post by arthritisankle on 2009-03-19
Thanks!

---

### Post by DGortze380 on 2009-03-19
ext3

if you change your mind and want to access in Windows too then NTFS (and NTFS-3G driver in ubuntu for read/write access). But you'll need to defrag NTFS occasionally.

---

### Post by jlochhead on 2009-03-19
I had a similar problem.

I formatted mine NTFS. It can easily be used with both Windows and Ubuntu.

Ext3 is a good option. I hear you can even get ext drivers for Windows if you want.

---

### Post by DGortze380 on 2009-03-19
> **jlochhead said:**
> I hear you can ever get ext drivers for Windows if you want.

true, I forgot about that.

---

### Post by dacorr on 2009-03-19
i use ext3 and ReiserFS still, from windows i installed this

[http://www.fs-driver.org/faq.html](http://www.fs-driver.org/faq.html)

to mount the partitions in windows,

this for reiserfs

[http://yareg.akucom.de/](http://yareg.akucom.de/)

Dac

---

### Post by arthritisankle on 2009-03-19
I don't have a windows box or plan on getting one.  I just picked it because I thought it added functionality without drawbacks.  Live and learn.

Also, I'm scared NTFS will bother the ushare server I use it for.  It's picky sometimes.

Thanks for the heads up about the windows driver for ext3.  It's nice to know I can get to it from a Windows box if I have to.

---

