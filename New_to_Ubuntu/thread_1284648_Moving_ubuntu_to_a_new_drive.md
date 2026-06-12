---
title: "Moving ubuntu to a new drive"
date: 2009-10-06
forum: New to Ubuntu
---

### Post by copracr on 2009-10-06
Current setup:
120 gb ide HD with 80gb xp portion and the rest for ubuntu,  extra 40gb ide with nothing on it

Desired setup:
120gb windows HD and 40gb ubuntu hd

Can I do this?

Also,  why can't XP read or even find my ubuntu partitions?  Ubuntu sees XP files,  so i don't know.

---

### Post by nhasian on 2009-10-06
yes, i imagine you can do it a number of ways.  you could use clonezilla to backup the partition and restore it to the spare drive.  you could do a fresh install of ubuntu onto the new drive and copy over your /home directory, etc.

in windows you need to install a driver to see the ext3 filesystem in ubuntu but then you can read/write to it.

[http://www.fs-driver.org/index.html](http://www.fs-driver.org/index.html)

---

### Post by mapes12 on 2009-10-07
[http://members.iinet.net.au/~herman546/index.html](http://members.iinet.net.au/~herman546/index.html)

---

### Post by copracr on 2009-10-12
OK,  I installed Ubuntu on the 40Gb IDE drive, imposted settings/home folder.  Now how do I get rid of the old ubuntu partion and swap partition on the 120Gb drive so XP can use that space?

---

### Post by Schendje on 2009-10-12
Use Add/Remove to install GParted. That'll let you edit/delete/move partitions.

Be careful though! Always use back-ups. (Just saying. :D)

---

### Post by copracr on 2009-10-12
After using gparted I was able to delete the second partition on my 120Gb drive and now it is free space.  However,  It wont allow me to increase the size of my XP partition to fill the disk.  Did I miss something?

---

### Post by falconindy on 2009-10-12
> **copracr said:**
> After using gparted I was able to delete the second partition on my 120Gb drive and now it is free space.  However,  It wont allow me to increase the size of my XP partition to fill the disk.  Did I miss something?
You may need to install the ntfs-3g package in order to modify ntfs partitions.

---

### Post by Schendje on 2009-10-13
And make sure you have that partition unmounted, otherwise it won't let you edit it.

---

### Post by copracr on 2009-10-13
OK,  i installed the ntfs-3g package and open GParted to ensure the space was unallocated.  
   the 80Gb or so that is ntfs has a warning triangle next to it so I double click on that volume to see what the warning is.  At the bottom of that dialog box it states:

Unable to read the contents of this file system!
Because of this some operations may be unavailable.


Can this be corrected?

---

### Post by copracr on 2009-11-06
anyone??  please...

---

