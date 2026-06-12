---
title: "Weird External USB 2.0 Hard Disk Samba Sharing Problem"
date: 2006-10-08
forum: Networking &amp; Wireless
---

### Post by ernz on 2006-10-08
Hello! :D 

  The problem I have is with Samba. All of the folders I have "Shared" on my desktop or home directory within Ubuntu Dapper work fine, and I can access them from the other windows xp machines over my wired network. Unfortunately I have a lot of portable information that I keep on a 300GB external USB 2.0 hard disk. I can access this info fine through nautilus and have been using the drive for a few weeks now, I have even been allowed by ubuntu to right-click some of the folders on this drive and "share" them over my windows network (like I normally do for desktop items); but when I try and access the external share from a windows machine, or locally though ubuntu's own network explorer I get the error: 

**The folder contents could not be displayed.**
*"Library" couldn't be found. Perhaps it has recently been deleted.*

  The USB drive is mounted, and all shares on my internal hard drive still work fine. I have checked and double-checked the attributes on my config file, and it all checks out. 

Whats happening here? - Any help greatly appreciated,

Thanks,
Ernz

---

### Post by arcticblue on 2006-11-11
Bump

I'm having the same problem in Edgy.  I was really hoping this would be fixed.  Anyone know of a workaround?  I was thinking this might be a /dev/fstab thing, but I can't find anything on the internet...only people asking questions with no answers.

---

### Post by ernz on 2006-11-13
Hi ArcticBlue, I have been looking in to this for a LONG time, ever since I got Dapper installed. I am going to have another look into it today, and see if I can turn up any answers. I will let you know if I find anything of any use.

Ernz

---

### Post by ernz on 2006-11-13
ArcticBlue,

Have done a little bit of looking into this one and have found something that may be of use:

"The tricky part was sharing the external hard disk. First of all you need to format the disk to FAT32 (mine was formatted as NTFS). There is no easy way to do this in Windows so I found a program called FAT32Format here:

[http://www.ridgecrop.demon.co.uk/index.htm?fat32format.htm](http://www.ridgecrop.demon.co.uk/index.htm?fat32format.htm)

Beware You may lose data when converting from NTFS to FAT.

Then you need to mount the hard disk either manually or in your /etc/fstab file. I used the fstab solution:

/dev/sda1 /media/usbdisk auto defaults,umask=000

After that I added these lines at the end of /etc/samba/smb.conf.

[usbdisk]
comment = Ekstern harddisk
path = /media/usbdisk
browseable = yes
read only = no
public = yes

Then restart the Samba server like this:

/etc/init.d/samba restart

After that I was able to detect and write to the hard disk from Windows clients on the network."

This was an extract from [http://www.daimi.au.dk/~kaspar/index.php?sectionId=36](http://www.daimi.au.dk/~kaspar/index.php?sectionId=36)

All of my disks are currently NTFS, and they are staying that way for the moment. If you have any success with this, can you please post back and let me know the results.

Hope this helps,
Ernz

---

