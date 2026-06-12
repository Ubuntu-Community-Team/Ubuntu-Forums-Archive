---
title: "Installing Linux distros on a pen drive"
date: 2011-06-01
forum: New to Ubuntu
---

### Post by jre6 on 2011-06-01
Is it possible to install a Linux distro like Ubuntu, PCLinuxOS, Linux mint etc on a pen drive? I am not referring to live boot that programs like UNetBootin can do. I want to install it, just like I do it on a hard disk. Is this possible?

---

### Post by HermanAB on 2011-06-01
Yes of course.

Unplug the HDD, plug in the SSDD/USBthingummabob and install as normal.

---

### Post by jre6 on 2011-06-01
Now, how do I unplug the hard disk? Can't I do it without having to muck around with my hard disk?

---

### Post by ajgreeny on 2011-06-01
No need to unplug the hard disk.  Just choose manual partitioning when you get to that page of the install, (called **Something else** in natty), and choose to install to (probably), sdb.  It should be obvious from the disk/partition size.

Just make sure you put the bootloader on the usb drive as well, not on the internal hard drive.  You get that choice at the bottom of the manual partitioning page.

Unplugging the hard drive simply means that you can not possibly put the OS or grub in the wrong place, but it is not absolutely necessary.

---

### Post by jre6 on 2011-06-01
I have three more questions to ask:

[LIST=1]
[*]Should I have to partition the USB drive? I want to access my /home contents in the USB drive without having to boot the USB drive, for example, say, from a Windows installation. How can I do so?
[*]Considering that my USB drive is /dev/sdb, should I put the boot loader on /dev/sdb as well?
[*]If I do this in a 4 GB pen drive (with /home partitioning), will I be left with a decent amount of space (my definition of decent space will be around 1GB)? If not, will removing unnecessary packages be of any help? (Otherwise, I can always get USB drives with more capacity)
[/LIST]

---

### Post by SavageWolf on 2011-06-01
I think 4GB will be a little small for Ubuntu etc, maybe a 16GB or 32GB one would be better.

---

### Post by ajgreeny on 2011-06-01
> **jre6 said:**
> I have three more questions to ask:

[LIST=1]
[*]Should I have to partition the USB drive? I want to access my /home contents in the USB drive without having to boot the USB drive, for example, say, from a Windows installation. How can I do so?
[*]Considering that my USB drive is /dev/sdb, should I put the boot loader on /dev/sdb as well?
[*]If I do this in a 4 GB pen drive (with /home partitioning), will I be left with a decent amount of space (my definition of decent space will be around 1GB)? If not, will removing unnecessary packages be of any help? (Otherwise, I can always get USB drives with more capacity)
[/LIST]

1.  You can set the aprtitions as you install; no need to make them in advance.  You will not be able to access your ubuntu partitions from windows, as windows can not see linux file systems.  You will need to make a separate partition for your data in ntfs file system.
2.  Yes you must put grub on sdb (your usb drive) or you will be unable to boot either OS.
3.  Use a larger drive if you can, as large as possible; 4GB is rather small for a full install, particularly if you want a separate /home and also the /data partition thast I am suggesting.

---

