---
title: "File format for external hard drive?"
date: 2009-09-01
forum: New to Ubuntu
---

### Post by jpt85 on 2009-09-01
Hi everyone, this is my first post and I am new to the Ubuntu experience.  I come from the Microsoft world, so excuse me for asking such a noobie question.    I bought a new external USB hard drive to use with my Ubuntu laptop. In the Microsoft world, I really enjoyed using the NTFS file system as it was fast, efficient, and had no limitations on file sizes.  I work a lot with very large video files and want to know the best format to use for my new external hard drive.  It must be able to "talk" to both my Windows operation system desktop computer as well as my separate Ubuntu computer, and also have no file size limitations due to the large files I work with.  Because of that, it would seem to eliminate using FAT 32 for the drive. 

So, what file system should I use in this scenario - FAT 32, ext3, or NTFS?  Or something else?

Does ext3 have any file size limitations?

Also, do hard drives have to be defragged in Ubuntu like they did in Windows?

Thanks everyone, this community rocks! :D

---

### Post by k33bz on 2009-09-01
> **jpt85 said:**
> Hi everyone, this is my first post and I am new to the Ubuntu experience.  I come from the Microsoft world, so excuse me for asking such a noobie question.    I bought a new external USB hard drive to use with my Ubuntu laptop. In the Microsoft world, I really enjoyed using the NTFS file system as it was fast, efficient, and had no limitations on file sizes.  I work a lot with very large video files and want to know the best format to use for my new external hard drive.  It must be able to "talk" to both my Windows operation system desktop computer as well as my separate Ubuntu computer, and also have no file size limitations due to the large files I work with.  Because of that, it would seem to eliminate using FAT 32 for the drive. 

So, what file system should I use in this scenario - FAT 32, ext3, or NTFS?  Or something else?

Does ext3 have any file size limitations?

Also, do hard drives have to be defragged in Ubuntu like they did in Windows?

Thanks everyone, this community rocks! :D

I will tackle these questions one at a time for you.

As far as what to format your external HDD, you don't have to even worry about that no more. Maybe in the older days, but now if you install a program onto your computer you can mount NTFS HDDs. Forgive me I do not remember the name of the program, I am sure someone will tell you that one.

I personally am not sure if there is a file size limitations on ext3.

Defragging, no not at all. Linux pretty much does that chore on its own. With out any human commands or clicks to get it started.

---

### Post by achianese on 2009-09-01
Ubuntu reads and writes NTFS very well in my hands. Ext3 is the standard for linux (soon to be ext4), but Windows won't read it natively. I dual boot and keep a third data partition in NTFS that both OSes read.

Don't know about fragmentation though.

---

### Post by achianese on 2009-09-01
p.s. I didn't have to install anything to mount NTFS partitions, so I think it's set up by default, at least in Jaunty.

---

### Post by k33bz on 2009-09-01
> **achianese said:**
> p.s. I didn't have to install anything to mount NTFS partitions, so I think it's set up by default, at least in Jaunty.

awww, then things of that nature have changed, I only run LTS versions, currently that is 8.04 Hardy Heron

---

