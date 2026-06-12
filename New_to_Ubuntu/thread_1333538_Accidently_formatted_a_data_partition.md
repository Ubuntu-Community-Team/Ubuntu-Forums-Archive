---
title: "Accidently formatted a data partition"
date: 2009-11-21
forum: New to Ubuntu
---

### Post by zahil on 2009-11-21
Hi,

I was trying to create a ubuntu-windows double-boot. while installing windows i accidently formatted a partition which i use to store my data.The partition was ntfs and it has been formatted to ntfs

now, about 140 gb of my data is lost, and windows has placed 3 files on it which are few hundred kilobytes.

I tried using ntfsundelete and testdisk, both fail to detect any deleted files.

Can somebody please help to restore this partition?

Help is sincerely appreciated.

---

### Post by Baelus on 2009-11-21
This may help:

[https://help.ubuntu.com/community/DataRecovery]("https://help.ubuntu.com/community/DataRecovery")

---

### Post by Puzzled Guy on 2009-11-22
You reformatted the partition?
I think your data is TOAST

Why else do you think I reformat my USB? To wipe it clean! (don't ask why though)

---

### Post by mlentink on 2009-11-22
Is your backup too old? With that much data it seems likely to me that your backup has at least most of your data, albeit not the most up-to-date

---

### Post by lkraemer on 2009-11-22
zahil,
First thing is to ABSOLUTELY not write anything else to that drive.

Use another computer to download the following LiveCD.
Trinity Home Rescue Kit
[http://trinityhome.org/Home/index.php?wpid=1&front_id=12](http://trinityhome.org/Home/index.php?wpid=1&front_id=12)

Then Read, Burn a LiveCD, Play, and come up with a plan of attack for
your drive.  You should be able to recover the data.

Read the section at 2.8 Ntfsundeleteall

You can also check out the UBCD4WIN...it contains about 8 or 9 recovery programs...and 3 of them are designed for recovering files from a format.

PC Inspector
[http://www.pcworld.com/downloads/file/fid,23069-order,1-page,1-c,utilities/description.html](http://www.pcworld.com/downloads/file/fid,23069-order,1-page,1-c,utilities/description.html)
to recover files, it works really well.  

Runtime - GetBackData NTFS/FAT32 is the best and one of the most reliable

[http://www.r-undelete.com/](http://www.r-undelete.com/)

[http://blog.easeus.com/easeus-products/How-to-recover-files-after-format-194.html](http://blog.easeus.com/easeus-products/How-to-recover-files-after-format-194.html)

[http://www.bestshareware.net/howto/recover-files-from-formatted-hard-drives.htm](http://www.bestshareware.net/howto/recover-files-from-formatted-hard-drives.htm)

Good luck.

lk

---

