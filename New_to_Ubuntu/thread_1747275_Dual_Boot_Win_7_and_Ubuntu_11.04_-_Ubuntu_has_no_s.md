---
title: "Dual Boot Win 7 and Ubuntu 11.04 - Ubuntu has no space"
date: 2011-05-02
forum: New to Ubuntu
---

### Post by navweb on 2011-05-02
Hello everyone. 

I recently installed Ubuntu 11.04 alongside my previous installation of Windows 7. The installation seems to go fine, but when I actually load the operating system, it says it has "15 MB" of space left. 

After checking the actual hard drive, I discovered I had 200 GB of unused space. The total hdd size is 500 gb. Apparently, the Filesystem is out of space. I can't even open Firefox and browse the web.

Does anyone know  how to resolve this?

---

### Post by oldfred on 2011-05-02
Post a screenshot from gparted, or click on your windows partition to mount it and run these:

sudo df -H

and 

sudo parted /dev/sda unit s print

---

### Post by corncob on 2011-05-02
> **navweb said:**
> Hello everyone. 

I recently installed Ubuntu 11.04 alongside my previous installation of Windows 7. The installation seems to go fine, but when I actually load the operating system, it says it has "15 MB" of space left. 

After checking the actual hard drive, I discovered I had 200 GB of unused space. The total hdd size is 500 gb. Apparently, the Filesystem is out of space. I can't even open Firefox and browse the web.

Does anyone know  how to resolve this?

I forget exactly but win7 uses 4 primary partitions:  Restore, win7, storage (the largest) and the boot manager (the smallest MB,not GB).  It sounds like you've installed Ubuntu on one of the smaller partitions like the boot manager or the recovery.  Windows might still start if its boot manager was replaced by grub.

---

### Post by Mark Phelps on 2011-05-03
> I forget exactly but win7 uses 4 primary partitions

NO, it generally uses two partitions -- a boot partition and an OS partition.  OEM PC providers often add in two more partitions to get to the maximum of 4 (primary).

Also, with that little space left, I would guess yours was a Wubi install -- and one in which you selected the default minimum size.

To check this, open a terminal and enter "sudo fdisk -lu" (that's a lowercase L, not a one).  That will list out your disk partitions, filesystems, and sizes.

---

### Post by bcbc on 2011-05-03
For wubi: [How do I resize the virtual disks?]("https://wiki.ubuntu.com/WubiGuide#How do I resize the virtual disks?")

But if you just installed, reinstalling is probably the best. If you want a permanent Ubuntu install, consider partitioning and installing direct.

---

