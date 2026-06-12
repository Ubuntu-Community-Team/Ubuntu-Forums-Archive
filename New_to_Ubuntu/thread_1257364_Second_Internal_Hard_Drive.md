---
title: "Second Internal Hard Drive?"
date: 2009-09-03
forum: New to Ubuntu
---

### Post by ManBearPender on 2009-09-03
So I just recently formatted my C:\ drive, wiped it and installed Ubuntu 9.04. Beforehand though, I placed all the files I thought I'd like to keep on my D:\ drive, figuring I can access it all from Ubuntu. I don't even think Ubuntu is detecting my second internal hard drive though... but I could just be missing something. 

Can someone guide me step-by-step on how to get access to my second hard drive? Thank you!

---

### Post by DFlame on 2009-09-03
Let's have a peep. Open a Terminal window and type:

```
sudo fdisk -l
```

Post the output here :)

---

### Post by ManBearPender on 2009-09-03
Here we go:
```

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xefcc88e2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       38633   310319541   83  Linux
/dev/sda2           38634       38913     2249100    5  Extended
/dev/sda5           38634       38913     2249068+  82  Linux swap / Solaris

```Not looking like it's detecting it...?

---

### Post by DFlame on 2009-09-03
Not at all. Can you confirm that it's connected properly with the correct jumper pin settings (master/slave)?

Is it a SATA or IDE drive (I'm assuming it is internal), and does it show up in the BIOS settings of the computer?

---

### Post by halitech on 2009-09-03
was the D:\ drive actually a drive and not a partition on your 320gig drive? How big was C:\ before you wiped it out?

---

### Post by DFlame on 2009-09-03
> **halitech said:**
> was the D:\ drive actually a drive and not a partition on your 320gig drive? How big was C:\ before you wiped it out?

Good point. I do hope it really is a second drive though :|

---

### Post by halitech on 2009-09-03
> **DFlame said:**
> Good point. I do hope it really is a second drive though :|

so do I but some people assume that each partition is a physical drive, let's hope thats not the case here.

---

### Post by Megatron3000 on 2009-09-03
I did more or less exactly the same as you, coming from windows and not wanting to lose my files. I had three partitions in advance, C,D and F and put all my files on the F partition. When installing Ubuntu, with the manual partitioning tool, i reformatted the remaining space into a formation for my ubuntu root, swap space and /home directory.  
 
so after installation, it looked more or less like this: 
sda1 (ext3 formatted): root partition, 10 GB sda2 (ext3 formatted): swap partition, 2 GB sda3 (ext3 formatted): home partition, 90 GB sda4 (old F partition, NTFS formatted): data, 78 GB 
 
with all that done, i copied all data from the original F to my home partition. Which did show up directly, i think as 'media 78GB' in My computer.  Then, i ran the partitioner (gparted, you may have to install it) in a live disc environment (you can't partition the disk you're working from), and formatted my former F space into another ext3 drive. 
 
after that, you'll want to automatically mount this drive at every startup and keep it at the same location all the time, and you'll have to give your user read and write access to it (i only had read access in the beginning). i don't know exactly which commands i ran for this, but the information is easily found in the howto's 
 
so well, that's how i got it to work. but first you have to find your harddrive of course. did you install with manual partitioning, making sure nothing would happen to your D partition? otherwise the automatic option might have formatted it. And i'm afraid it looks a bit like that from your fdisk list: 
 
 seeing that you have 38913 cylinders, and the first 38633 are all Linux formatted, while the remaining 720 are Linux/swap, it seems like your whole hard disk is linux formatted, and that all previous data is gone. Which would be a whole load of carp. I'm new with all this too though, and i might be completely wrong, i very much hope so.

---

