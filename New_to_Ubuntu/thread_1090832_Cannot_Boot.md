---
title: "Cannot Boot"
date: 2009-03-08
forum: New to Ubuntu
---

### Post by DucksAndDolphins on 2009-03-08
So one day out of the blue, with really no warning whatsoever, I booted Ubuntu just as I always do and the load progress bar came up and went halfway and then I received the following error message:

Booting 'Ubuntu 8.10, kernel 2.6.27-7-generic'

 Filesystem type is ntfs, partition type 0x07
The current working directory(i.e., the relative path) is /ubuntu/disks
   [Linux-bzImage, setup=0x3000, size=0x220d70]
   [Linux-initrd @ 0x1ee4f000, 0x810733 bytes]
Loading, please wait...
ALERT! /host/ubuntu/disks/root.disk does not exist. Dropping to a shell!

BusyBox v1.10.2 (ubuntu 1:1.10.2-1ubuntu6) built-in-shell (ash)
Enter 'help' for a list of built-in commands.

And then I get a terminal that looks like this:

(initramfs)_

Help??

---

### Post by taurus on 2009-03-08
Did you install it under windows--wubi?

---

### Post by DucksAndDolphins on 2009-03-08
Yes.

---

### Post by DucksAndDolphins on 2009-03-14
[Duplicate]

So one day out of the blue, with really no warning whatsoever, I booted Ubuntu just as I always do and the load progress bar came up and went halfway and then I received the following error message:

Booting 'Ubuntu 8.10, kernel 2.6.27-7-generic'

Filesystem type is ntfs, partition type 0x07
The current working directory(i.e., the relative path) is /ubuntu/disks
[Linux-bzImage, setup=0x3000, size=0x220d70]
[Linux-initrd @ 0x1ee4f000, 0x810733 bytes]
Loading, please wait...
ALERT! /host/ubuntu/disks/root.disk does not exist. Dropping to a shell!

BusyBox v1.10.2 (ubuntu 1:1.10.2-1ubuntu6) built-in-shell (ash)
Enter 'help' for a list of built-in commands.

And then I get a terminal that looks like this:

(initramfs)_

Help??

---

### Post by lisati on 2009-03-14
*bump* on behalf of OP

Maybe the installation didn't work as well as it should. One possibility is to remove the installation via Windows control panel->Add/remove programs, and to try the installation again. Don't forget to take the usuall precautions to protect your data (Backup etc)

---

### Post by abn91c on 2009-03-14
> **DucksAndDolphins said:**
> [Duplicate]

So one day out of the blue, with really no warning whatsoever, I booted Ubuntu just as I always do and the load progress bar came up and went halfway and then I received the following error message:

Booting 'Ubuntu 8.10, kernel 2.6.27-7-generic'

Filesystem type is ntfs, partition type 0x07
The current working directory(i.e., the relative path) is /ubuntu/disks
[Linux-bzImage, setup=0x3000, size=0x220d70]
[Linux-initrd @ 0x1ee4f000, 0x810733 bytes]
Loading, please wait...
ALERT! /host/ubuntu/disks/root.disk does not exist. Dropping to a shell!

BusyBox v1.10.2 (ubuntu 1:1.10.2-1ubuntu6) built-in-shell (ash)
Enter 'help' for a list of built-in commands.

And then I get a terminal that looks like this:

(initramfs)_

Help??if you installed ubuntu with wubi, you need to boot to windows first to "mount" the disks, might as well defrag windows while there then reboot back to Ubuntu

---

### Post by lisati on 2009-03-14
[http://ubuntuforums.org/showthread.php?p=6861908#post6861908](http://ubuntuforums.org/showthread.php?p=6861908#post6861908)

---

### Post by DucksAndDolphins on 2009-03-14
Thank you all!

---

### Post by bapoumba on 2009-03-15
Threads merged.

---

