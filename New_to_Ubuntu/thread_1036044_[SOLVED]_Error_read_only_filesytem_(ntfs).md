---
title: "[SOLVED] Error: read only filesytem (ntfs)"
date: 2009-01-10
forum: New to Ubuntu
---

### Post by mern1 on 2009-01-10
I have a separate ntfs drive that I recently set up to automount at startup.  This works fine; however, now it seems to be read-only.  Ubuntu won't let me delete or move any files.  I don't think I had this problem before I set up the drive to automount, which makes me think its an error in my fstab file.  Can someone help please?  Thanks

fstab:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=ed815082-ef9c-4e93-90a4-409f4f584987 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda3
UUID=4908b1d5-ef40-4220-bdad-64ef568f9ce3 none            swap    sw              0       0
# /dev/sdb1 
UUID=2C6827E96827B08E /media/Shared   ntfs-3g  ro,auto,user,fmask=0111,dmask=0000 0 0
#CD/DVD Drives:
/dev/sr0       /media/dvdrw1   udf,iso9660 user,noauto,exec,utf8 0       0
#/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
```

---

### Post by JoshuaRL on 2009-01-10
See the line for /dev/sdb1?  After the "ntfs-3g" there is a "ro".  Make that read:
```

rwx,auto,user,fmask=0777,dmask=0000 0 0

```
Make sure you back up your fstab first, but try that out.

The ro means "read only."  Now you have "read, write, execute" instead.  And the fmask changes permissions levels

---

### Post by mern1 on 2009-01-10
Thank you!  It worked except for the fmask=0777 part.  When I had it configured the way you said I could delete files but couldn't read them.  For example, my wallpaper could not be set and I couldn't play any media files.  I set the fmask back to fmask=0111 and everything works perfectly.  What is this setting for anyway.  Will it cause any problems if I leave it this way?  Thanks again!

---

### Post by JoshuaRL on 2009-01-10
Hmm, maybe I have the wrong permission fmask then.  To be honest, I'm just starting to learn about configuring fstab myself.  Haven't needed to mess with it much before.  But I did see the problem there in the read-only arguement.

If you found the solution, you should to to Thread Tools->Mark Thread as Solved on the page.  That way, others with the same problem know how to fix it.

---

### Post by cerealtx on 2009-01-10
um shouldn't it just be 777 not 0777?

---

### Post by JoshuaRL on 2009-01-10
> **cerealtx said:**
> um shouldn't it just be 777 not 0777?

That's it.  I thought something looked a bit off, but I couldn't find where I went wrong.  [If you look here,](http://www.linuxforums.org/security/file_permissions.html) you'll see that 777 allows read/write/execute across the board for everyone.  So if you want that permission level for the drive, that should make sure you don't have any conflicting info in the fstab.

So if you wanted to change permissions on that drive, you could do:
```

sudo chmod -R 777 /path/to/driveorfolder

```

---

