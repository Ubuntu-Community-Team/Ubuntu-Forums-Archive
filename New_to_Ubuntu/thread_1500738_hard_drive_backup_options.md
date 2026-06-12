---
title: "hard drive backup options"
date: 2010-06-03
forum: New to Ubuntu
---

### Post by zetharx on 2010-06-03
I want to backup my hard drive data, but not just the files.  I want to backup the complete integrity of my file system (note that my file system ONLY consists of one partition originated at / ).

After the backup executes, I want to be able to shutdown, unplug my main hard drive and boot from the backup drive with everything the exact same.

I have used rsync to backup specific directories in the past, but I doubt that rsync can do what I am trying to do.  Is it possible to backup the partition on which I am currently running?  Or do I need to boot into a live cd in order to get an exact replica of it?  thanks in advance.

---

### Post by tmette on 2010-06-03
> **zetharx said:**
> I want to backup my hard drive data, but not just the files.  I want to backup the complete integrity of my file system (note that my file system ONLY consists of one partition originated at / ).

After the backup executes, I want to be able to shutdown, unplug my main hard drive and boot from the backup drive with everything the exact same.

I have used rsync to backup specific directories in the past, but I doubt that rsync can do what I am trying to do.  Is it possible to backup the partition on which I am currently running?  Or do I need to boot into a live cd in order to get an exact replica of it?  thanks in advance.

I'm curious to being able to do this as well.  I used to use a Mac and used an application calld SuperDuper! to make bootable back-ups of my HDD to an external drive.  All I had to do then was hold down the Option key and choose the external drive to boot to, if anything happened to my main HDD.

---

### Post by nhasian on 2010-06-03
it sounds like you want [Clonezilla]("http://clonezilla.org/").

---

### Post by zetharx on 2010-06-03
> **nhasian said:**
> it sounds like you want [Clonezilla]("http://clonezilla.org/").

This may be as good as I can get.  This requires I shutdown though.  Is there anyway to do it while still running off the partition which is to be copied?

---

### Post by robert shearer on 2010-06-03
> **zetharx said:**
> This may be as good as I can get.  This requires I shutdown though.  Is there anyway to do it while still running off the partition which is to be copied?

a) not that I am aware of,
and
b) Why ?

---

### Post by lindsay7 on 2010-06-03
Take a look at Acronis True Image, Pc Backup & Recovery.  You have to buy it but it should do what you want.  It works with Windows and Ubuntu partitions separately or with a dual boot.

---

### Post by Mark Phelps on 2010-06-04
Take a CLOSE look at ATI Home 2010 -- same product as PC Backup and Recovery, just different name.  

From what I read in their forums, it does not handle Ext4 filesystems -- but that could have been corrected by now.

---

