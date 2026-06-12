---
title: "Mounting linux partition in windows?"
date: 2008-12-21
forum: New to Ubuntu
---

### Post by Ussr1943 on 2008-12-21
Hi all,
I'm currently dual booting Ubuntu 8.10 and Windows XP. There a few programs that are windows exclusive that I'm required to use on a daily basis, however I much prefer Ubuntu. Anyways I'd like to be bale to listen to my music that is on my Ubuntu partition while in windows, and I'm not quite sure how to go about it.

I've tried Ext2IFS, but unfortunatly I've yet to get it to work and windows keeps asking me if I want to reformat my Ubuntu partition.

Any help is appreciated.
Thanks,

---

### Post by chrisamiller on 2008-12-21
I've used Ext2IFS for this with no problems in the past.  Can you describe exactly what your problem is with it?  

Other options:  

- Run windows in a virtual machine within Ubuntu (some good tutorials on the web and this forum)

- Create a new FAT32 (or ntfs) partition for your data, music, etc, that can be mounted from both windows and linux

---

### Post by SrEstroncio on 2008-12-24
> **chrisamiller said:**
> I've used Ext2IFS for this with no problems in the past.  Can you describe exactly what your problem is with it?  


I am having the same problem as OP, I installed Ext2IFS and the drives appeared on My Computer in Windows, but whenever I try to explore them a message comes up telling me the partition needs to be formatted before I can open it.

---

### Post by caljohnsmith on 2008-12-24
I think you might be having problems with Ext2IFS because Ubuntu is now formatting its ext3 partitions a little differently; Intrepid uses a file system inode size of 256 bytes vs. previous versions of Ubuntu that used 128 bytes. The last time I checked, Ext2IFS still cannot handle the newer 256 byte inode size ext3 partitions. There's another program though that can handle the newer ext3 partitions:

[http://sourceforge.net/projects/ext2fsd](http://sourceforge.net/projects/ext2fsd)

How about giving that program a try and let me know how it goes.

---

### Post by Gone fishing on 2008-12-24
Ext2 IFS works well - I use it.

However it will not work with the standard format that Intrepid uses.

Apparently Ext2 IFS only allows 128 byte inodes (this is an older standard for ext3) whilst Intrepid uses larger inodes. I solved the problem by creating my formats using gparted then installing intrepid onto the created partitions.

You could back up your data then format your home partition with:

mkfs.ext3 -I 128 /dev/your_device

Then copy the data back onto the home partition

---

