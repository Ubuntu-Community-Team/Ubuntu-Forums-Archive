---
title: "Swap Size over 21gb."
date: 2009-05-10
forum: New to Ubuntu
---

### Post by gackt on 2009-05-10
Hi all, i bought my laptop with Ubuntu 8.10 installed ( i ask the seller to do so). Recently i just noticed that my swap file is 21gb big. i noticed it via system monitor. How do i reduce it? 21gb swap file is definitely stupid. Thanks

---

### Post by lvleph on 2009-05-10
```
sudo apt-get install gparted
```
Then use that to fix your partitions. You may actually want to use the live cd so that you can resize other partitions.

---

### Post by Bölvaður on 2009-05-10
You need to use a [partition manager]("apt:gparted") (click the link to install).

Click on the swap partition and do a "swapoff" to unmount it. Then make it at desired size.
You do that by "Resize/move" when you right click the partition. Should be easy from there.

If you have laptop and use hibernation then you will want ram at equal size of your ram, or a tiny bit bigger.
If you have a desktop computer you will most likely use 300mb tops, so you can give it 0.5 GiB just to be sure, but you'll never use it all.

---

### Post by gackt on 2009-05-10
Thanks so i need cdlive + gparted? Will this procedure delete all my data? Formatting? Where do i start livecd first or gparted?

---

### Post by Bölvaður on 2009-05-10
> **gackt said:**
> Thanks so i need cdlive + gparted? Will this procedure delete all my data? Formatting? Where do i start livecd first or gparted?

no just follow my instructions. and click my link to install gparted.
you do not need live cd to be run as the live cd also uses the swap file as well as you do right now. You just need to use the swapoff on the swap partition in gparted.

---

### Post by gackt on 2009-05-11
Thanks, I'm trying it right now.

---

### Post by MrWES on 2009-05-11
> **gackt said:**
> Thanks, I'm trying it right now.

You'll need:
```
sudo swapoff
```

---

### Post by gackt on 2009-05-15
okey here is the condition:

I have three major partition:
1.Sda1 =  70 gig
2.sda3 = 21 gig ( this is the swap file)
3.sda2 = 56 gig

I turn off the swap file and resize the swap file to 2gig, my question is where will 19 gig reside? will it become a new drive? or can i append that 19 gig into sda2? Thanks

---

### Post by anaconda on 2009-05-15
You can append that 19GB to your sda1 or sda2.
(depending on your filesystem, but I assume it is the default ext3, which gparted can resize. some filesystems cant be resized.) 
But you will need to do that from a livecd, because you can only resize partitions that aren't mounted, and your "/home" and "/" partitions will be mounted when you use ubuntu from hd..

Your original question was about a swap FILE and that is different than a swap partition (which is what you actually have. and what you got advice for) 
Swap file would have been easier to resize, by deleting the old one and creating a new one....

EDIT. What are the sda1 and sda2 partitions used for? Both of them are unnecessarily big for a root partition!  Good root partition size is about 20-25GB and the rest goes usually to home partition (and swap.) And many many ubuntu users have 10-15GB root partition.

---

### Post by tarps87 on 2009-05-15
Can you post you fstab file please
```
gedit /etc/fstab
```
This will show use what the other partitions are used for. You can resize a home partition with out using the live cd but you will need it for the root partition.

Can you also post the output of
```
sudo blkid
```
Your fstab file will probably using UUID's, this command will help us map the entries to you partition names.

I wonder why he created a 21gb swap partition.

Edit: looking at the other partitions it would appear the seller didn't know what they were doing, they should have just used the auto partitioner

---

### Post by Bölvaður on 2009-05-15
1.
you can create a new partition and install a different distro on there :)

2.
Resize a partition to stretch over the empty space
but note that it might take a very long time shifting all data in place on the partition. Less data = less time.
Also you need to take backup of the partition you want to resize if something goes wrong.

3.
Create a new partition and use as storage.
When you'll do the next fresh install please consider doing the partitions from scratch... and use pen and paper to map them before doing anything, planning is everything.

---

### Post by gackt on 2009-05-16
Hi! Thanks I'll submit something on 2-3 days ahead, I'm currently using Windoze for emergency task. Oh i miss my Ubuntu. Making the new unused space as a different partition (new drive) seems to be safer than appending it to existing drive. I'm thinking reformatting all my drives and put jaunty in it as I'm currently using 8.10. But I Wonder about the graphic as I use x3100(intel) which is blacklisted on 8.10 (took me a week to get the vga running).

---

