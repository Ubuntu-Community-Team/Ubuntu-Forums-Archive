---
title: "Gparted - Fat 32 - Pen Drive"
date: 2009-04-19
forum: New to Ubuntu
---

### Post by brandoncolorado on 2009-04-19
I have a pen drive that I need to bring with me to school.  I have gparted and I used it to format the drive because it was having problems.  Now I have it formatted to ext3, but I can't format it to fat32.  

The only options that aren't "greyed out" in gparted are ext2,3,4 and swap.  Why can I not select fat32?

---

### Post by novafluxx on 2009-04-19
Try deleting the entire partition table on the pendrive and creating a new one, formatting it with ext2 or FAT32.

You probably don't want to use a journalizing file system on a solid state storage device.

Which version of gparted and Ubuntu are you using?

---

### Post by brandoncolorado on 2009-04-19
> **novafluxx said:**
> Try deleting the entire partition table on the pendrive and creating a new one, formatting it with ext2 or FAT32.

You probably don't want to use a journalizing file system on a solid state storage device.

Which version of gparted and Ubuntu are you using?

Thanks for your reply.  I am using 9.04 UNR and the default gparted.  I figured out the problem.  By default a required package is not installed.  In order to be able to format to fat 16 or fat 32 you need to have dosfstools package installed.  Hopefully this will help someone in the future.

---

### Post by DragonlordP on 2009-07-27
It did help, although I use Debian now.
Thanks a lot for posting that!

---

