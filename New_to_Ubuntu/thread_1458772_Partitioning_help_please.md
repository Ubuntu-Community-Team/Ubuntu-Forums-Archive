---
title: "Partitioning help please"
date: 2010-04-20
forum: New to Ubuntu
---

### Post by mesmith on 2010-04-20
I was using xubuntu 8.10 in a primary partition, and a swap file.

I installed xubuntu 10.04 Beta 2 into some unallocated space.  It created an extended partition and its own swap file.

Xubuntu Beta 2 works perfectly. I moved all my data across and I am pleased as punch.

Now, I want to reformat the original primary partition that contained 8.10 in order to use it for data storage, and delete its swap file.  My problem is that the system currently is multi-boot.  How do I tell grub that it should just boot 10.04 without asking?

Thanks.

---

### Post by Paqman on 2010-04-20
Boot up into 10.04 and if you don't already have Gparted installed, do so. Then start it up and delete the old 8.10 partitions (you may need to right click on the swap and "swapoff") and reformat the space as your new storage partition. Then issue the following command in a terminal:
```
sudo update-grub
```

Grub will scan the drive for operating systems, and when it sees that you've only got 10.04 installed that will be the only entry it puts into the list. IIRC if you've only got one system it actually hides the list at boot up, so don't freak if you don't see Grub when you boot.

---

### Post by mesmith on 2010-04-20
I did as you suggested, and all seems to work well except that when (after reboot) I use Gparted to check results it informs me that the partition that I reformated cannot be mounted as "enclosing drive is locked".

Any thoughts?

---

### Post by garvinrick4 on 2010-04-20
> **mesmith said:**
> I did as you suggested, and all seems to work well except that when (after reboot) I use Gparted to check results it informs me that the partition that I reformated cannot be mounted as "enclosing drive is locked".

Any thoughts?
Put your Ubuntu CD in tray and reboot. Right click on extended partition  and pick resize or move and then make it cover the old primary partition where 8.04 resided. If there was a picture of your drive posted here it would be easier to discuss. Is it a dual boot or just Linux? I do that when I want to make my / smaller and my /home bigger and it will resize or move nicely in gparted. Must use your CD and gparted.

---

### Post by mesmith on 2010-04-20
Took a look with gparted on sysrescue disk.  The original primary partition has not moved and is the same size as original.  Just reformated to ext4 (as I desired).

Is there some linux command that will unlock this partition?

---

### Post by mesmith on 2010-04-20
Solved.

I didn't have a mount directory, nor was there an entry in fstab.

Thank you.

---

