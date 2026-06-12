---
title: "format a usb drive"
date: 2009-05-06
forum: New to Ubuntu
---

### Post by saskatchewan on 2009-05-06
How can I reformat a usb drive in ubuntu?

In windows xp there is a function that you just right click.

Is there any command in ubuntu to reformat a usb?

---

### Post by _Purple_ on 2009-05-06
Use gparted
Go to System > Administration > Partition Editor

Then select the USB drive from the dropdown list and format. Make sure that you select the right HDD from the list.

---

### Post by HermanAB on 2009-05-06
Yes, but, if you need to share the drive with Windows then you should use NTFS as the file system.

So you may need to install ntfs3g and ntfs-utils, then format it with 
mkntfs -L volumename /dev/sdX1

and to do that, you first need to run fdisk and create a partition on it.

---

