---
title: "Installing Ubuntu on Seagate Freeagent Go"
date: 2009-06-27
forum: New to Ubuntu
---

### Post by Redorb1790 on 2009-06-27
I just purchased a FreeAgent Go and I was wondering if anyone could point me to a tutorial that explains how to install Ubuntu on the FA while being able to keep it's ability to be accessed through Windows and Linux.
Thanks in advance.

---

### Post by mikewhatever on 2009-06-27
The brand shouldn't really matter, what does is the type of connection, usb,sata,etc. Can you elaborate on that.

---

### Post by durand on 2009-06-27
It looks like an external usb hard drive. Are you sure you don't want to install it on your computer hard drive instead?

To make a live usb session, you need to partition your drive with the partition editor on the live cd (System > Administration > Partition Editor), adding a FAT32 partition for ubuntu to be on. *Be careful about your data!*

Then go to System > Administration > USB Startup Disk Creator and install it to your newly created partition.

---

### Post by Redorb1790 on 2009-06-28
Yeah it's USB and thanks for the info. The issue with installing it to the actual hard drive is the lack of space and how much I go through. I normally fill up a hundred gigs or so every few weeks.

---

