---
title: "Access my external ext3 hard drive from winXP"
date: 2007-12-01
forum: Networking &amp; Wireless
---

### Post by airjaw on 2007-12-01
Hello.. not sure if this is the right category in the forum.. so apologize in advance if its not.

I'm trying to access my ext3 external HD from windows XP.. (I have dual-boot.. and currently have most of my files on the external hard drive)

I downloaded a windows program that let me mount my linux drives.
It however, does not work for the external hard drive.  It said it needed to be formatted and asked if I wanted to format it.  Obviously I did not.

I want to be able to plug in my external hard drive to USB and then have it mount automatically...

Is there any way to do this?

thanks.

---

### Post by froy02 on 2007-12-01
Windows would not read ext3 format. Copy all your files first to the ubuntu machine. Then format your external drive as fat32 or ntfs which both ubuntu and windows can read and write to. 
Mount your external drive then copy back all your data back to the newly formatted drive.

---

### Post by numberboy on 2007-12-01
The lastest version of ext2 IFS works perfectly for me (the name says ext2 but it can read/write ext3 fine). Installation is pretty simple, though it's worth noting that there is a very small chance that it could cause file system damage, so be sure to back up anything critical.

You can get it at [http://www.fs-driver.org/](http://www.fs-driver.org/)

---

