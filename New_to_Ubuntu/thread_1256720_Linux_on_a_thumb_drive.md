---
title: "Linux on a thumb drive"
date: 2009-09-03
forum: New to Ubuntu
---

### Post by XKCD64 on 2009-09-03
So, I learned how to create a bootable thumb drive with Linux on it, but my question is....  how hard would it be to remove Ubuntu from the thumb drive if I decide I don't need it on there?  And I need my space back....

Right now, it would work great for me with just plugging it into a computer to use Linux, but I may need the thumb drive for something else later....  Any idea on how to remove ubuntu from the thumb drive.

---

### Post by HermanAB on 2009-09-03
Simple - you just overwrite the thumb drive with zeros, then reformat it on Windows or on Linux as shown below:

$ dmesg
Plug drive in
$ dmesg
Verify name of drive e.g. /dev/sdb

Erase it:
$ sudo dd if=/dev/zero of=/dev/sdb
Long wait...

Reformat it:
$ sudo fdisk /dev/sdb
(Read the menu and make a primary partition)
$ sudo mkfs.vfat /dev/sdb1

Et voila!

---

### Post by XKCD64 on 2009-09-03
Thanks!!  I am going to install Xubuntu!!  Thank you so much!!  :D

---

