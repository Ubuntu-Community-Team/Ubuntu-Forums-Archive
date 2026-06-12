---
title: "DriveImage"
date: 2009-01-27
forum: New to Ubuntu
---

### Post by mesmith on 2009-01-27
Using xubuntu and love it.  However, when a Windows user I frequently used a product called Drive Image.  I backed up my hdd to a second (smaller) hdd by ignoring unused space and using compression.  Over a 12 year period, I did in fact suffer a total hdd failure.  With Drive Image I loaded a boot disk after replacing the bad hdd and DI automatically formatted and partitioned the new hdd proportionally, and then loaded the backup off the small hdd.

I was back on the air in 20 minutes without losing a byte of data, nor having to do any reloading of software or systems mods.

I have never forgotten this experience.  Are there any linux products that can do this type of imaging while ignoring unused space?

---

### Post by handydan918 on 2009-01-27
> **mesmith said:**
> Using xubuntu and love it.  However, when a Windows user I frequently used a product called Drive Image.  I backed up my hdd to a second (smaller) hdd by ignoring unused space and using compression.  Over a 12 year period, I did in fact suffer a total hdd failure.  With Drive Image I loaded a boot disk after replacing the bad hdd and DI automatically formatted and partitioned the new hdd proportionally, and then loaded the backup off the small hdd.

I was back on the air in 20 minutes without losing a byte of data, nor having to do any reloading of software or systems mods.

I have never forgotten this experience.  Are there any linux products that can do this type of imaging while ignoring unused space?

There aren't really many Linux "products" per se. 
But check out rsync. It will do full backups as well as incremental.

---

### Post by kaibob on 2009-01-27
> **mesmith said:**
> ...Are there any linux products that can do this type of imaging while ignoring unused space?

Yes, have a look at:

Clonezillla
[http://www.clonezilla.org/](http://www.clonezilla.org/)

Partimage
[http://www.partimage.org/](http://www.partimage.org/)

Ghost for Linux
[http://sourceforge.net/projects/g4l](http://sourceforge.net/projects/g4l)

Also see this recent thread on the same topic:

[http://ubuntuforums.org/showthread.php?t=1050460&highlight=partimage](http://ubuntuforums.org/showthread.php?t=1050460&highlight=partimage)

I have personally used Clonezilla, and it does what you want, although grub issued error messages after a restore. I have used Acronis True Image for many years, and it does what you want, but you have to pay for it. Also, the just-released version of True Image has many bugs and is not as reliable as previous versions.

---

