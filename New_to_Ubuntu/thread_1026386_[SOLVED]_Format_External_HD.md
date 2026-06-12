---
title: "[SOLVED] Format External HD"
date: 2008-12-31
forum: New to Ubuntu
---

### Post by mayagrafix on 2008-12-31
I have a USB external HD (sdb1) connected to my laptop that I want to use for transferring files. I want to erase and reformat it to free up space. Also delete all the partitions. How do I go about this? with Gparted?

Thanks for your help :)

---

### Post by bumanie on 2008-12-31
Gparted will do it fine. Right click on partitions and choose delete once the whole drive is seen as unallocated space right click and choose to format to whatever filesystem you like. Would suggest ntfs if you have windows as well, so that windows and ubuntu will both be able to access the drive. If no windows, just format to ext3.

---

### Post by Michael.Godawski on 2008-12-31
hi mayagrafix,

gparted is the right tool. You can either use the Live CD or the gparted live cd.

Be sure you select the right drive for deletion, and making a back-up was never a bad idea. But you should be fine. 

And if you have any questions feel free to ask.

---

