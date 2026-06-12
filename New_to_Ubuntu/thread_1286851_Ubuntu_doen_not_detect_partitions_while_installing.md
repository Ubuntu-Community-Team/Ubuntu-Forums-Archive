---
title: "Ubuntu doen not detect partitions while installing"
date: 2009-10-09
forum: New to Ubuntu
---

### Post by SACHINVD on 2009-10-09
Hi !

When i boot my pc using ubuntu 9.04 live cd which installing it doen detect any partition on my hd0.
There is only one option available i.e create new partition table.

What is the problem ?

and when click on top panel on places menu then it shows all partition on disk.
I am able to browse all partitions using live cd then what is the problem come while installing ? 

Thank You !!!

---

### Post by Diabolis on 2009-10-09
Maybe you didn't shutdown Windows properly and the drive is flaged as dirty. this happens when you shut it down by holding the power button. Start up Windows and then turn it off properly.

---

### Post by jeremyswalker on 2009-10-09
Out of curiousity, open up Gparted (System > Administration > Partition Editor or Gparted). See if Gparted sees your partitions.

---

### Post by SACHINVD on 2009-10-09
I tried the same 2-3 times on different day.
but the result is same as above.

Gparted does not detect any partition.
It display 80gb unallocated space

and output of "fdisk -l" using live cd is

ubuntu@ubuntu:~$ sudo fdisk -l

Unable to seek on /dev/sda

---

### Post by jeremyswalker on 2009-10-09
You said you can browse the files on the partitions with the command line or file manager? Do you have an OS installed already? If so, does it boot ok?

---

### Post by SACHINVD on 2009-10-09
No,
I don't have linux installed but i can browse partitions when i boot using Live CD
but problem comes while installing

---

### Post by SACHINVD on 2009-10-10
Problem Solved !!!

Thanks to everyone

---

### Post by LewRockwell on 2009-10-10
> **SACHINVD said:**
> Problem Solved !!!

Thanks to everyone

what was the difficulty

.

---

### Post by SACHINVD on 2009-10-10
Partition table was damage

---

### Post by jeremyswalker on 2009-10-10
Glad you figured it out.

---

