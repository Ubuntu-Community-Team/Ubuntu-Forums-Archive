---
title: "using gparted"
date: 2011-06-06
forum: New to Ubuntu
---

### Post by scorpious on 2011-06-06
I recently copied all my data from a 1TB drive onto my new 2TB drive using DD. 

I have a partition called storage that I use in both Ubuntu and windows and I want to extend this one. I installed gparted but it wont let me extend my partition.

Infact the only partition it will let me extend is /dev/sda1

Does anyone know why?

cheers

---

### Post by wildmanne39 on 2011-06-06
> **scorpious said:**
> I recently copied all my data from a 1TB drive onto my new 2TB drive using DD. 

I have a partition called storage that I use in both Ubuntu and windows and I want to extend this one. I installed gparted but it wont let me extend my partition.

Infact the only partition it will let me extend is /dev/sda1

Does anyone know why?

cheers

Hi, it could be because they are mounted, if so you have to unmount them to extend them, also the partition could be in the wrong place  which means to extend it you would have to move it first then extend it, and if it is on the drive with grub it will make it unbootable and you will have to reinstall grub. Here is a link to explain.
[http://ubuntuforums.org/showthread.php?t=1219270](http://ubuntuforums.org/showthread.php?t=1219270) Also it is a good idea to back up the data on the partition you want to resize and is better to use gparted from the livecd.

---

### Post by Irihapeti on 2011-06-06
Firstly, the partition you want to edit is mounted - hence the key icon.

Secondly, it's inside an extended partition (/dev/sda4), so you'll need to increase the size of the extended partition as well. To do that, you'll need to unmount the swap partition.

You should be able to unmount the storage partition and the swap area by selecting the partitions and right-clicking on them.

If for some reason that doesn't work, it means that your system is set up not to allow you to unmount the partitions. In that case, you can boot from a gparted or parted magic liveCD.

---

### Post by scorpious on 2011-06-07
thanks for the quick replies.

unmounting and resizing my extended partition did the trick.

cheers

---

### Post by wildmanne39 on 2011-06-07
> **scorpious said:**
> thanks for the quick replies.

unmounting and resizing my extended partition did the trick.

cheers
Your welcome.

---

