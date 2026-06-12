---
title: "Cannot access windows through Ubuntu (vice versa)"
date: 2010-09-08
forum: New to Ubuntu
---

### Post by Zanderist on 2010-09-08
So I've installed Ubuntu, but unlike the other installed I've done of Ubuntu in the past I am not able to see my windows files.

I did an install within windows so they operate side by side.

What I want to do is restore all my documents and music etc. to a file that both OSs can see and access.
(I managed it in the past by making a  partition for Ubuntu)

The Weird thing  is that, I have a 250GB hard drive (in the laptop). Looking at the Disk Utility, it says I have 250 GB used as NTFS and somehow an extra 20GBs ext4. Both are mounted by Ubuntu.

[SIZE=1]*(Another small issue that has to do with the external hard drive is that I can only use a USB cable and not my preferred fire wire in Ubuntu.)*[/SIZE]

---

### Post by jeight on 2010-09-08
> **Zanderist said:**
> So I've installed Ubuntu, but unlike the other installed I've done of Ubuntu in the past I am not able to see my windows files.

I did an install within windows so they operate side by side.

Did you install Ubuntu in virtual environment within Windows?  Otherwise I guess I don't know what you mean by that statement.

---

### Post by Zanderist on 2010-09-08
> **jeight said:**
> Did you install Ubuntu in virtual environment within Windows?  Otherwise I guess I don't know what you mean by that statement.
I installed while in vista, with WUBI. Then I restarted and was asked to either boot Ubuntu or Vista.


So I booted through Ubuntu to complete the install.

---

### Post by bcbc on 2010-09-08
Your windows files are under the /host directory. 

You can install some utility under windows to view your ubuntu files (I've never used this) but apparently [this]("http://ext2read.blogspot.com/") supports ext4.

The 20GB for ubuntu is a virtual disk (?:\ubuntu\disks\root.disk) under the the windows ntfs file system. So the space is part of that, not in addition to that.

In terms of increasing it later - while it is possible, the way you are using it - keeping data on the /host - probably means you won't have to worry about it.

I have no idea about the firewire thing.

---

