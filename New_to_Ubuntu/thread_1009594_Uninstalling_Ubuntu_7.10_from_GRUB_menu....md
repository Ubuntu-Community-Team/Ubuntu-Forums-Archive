---
title: "Uninstalling Ubuntu 7.10 from GRUB menu...?"
date: 2008-12-12
forum: New to Ubuntu
---

### Post by Austin_Duffy on 2008-12-12
I managed to cram 8.10 into my laptop now how do I remove the former version of 7.10 I had..?

On the other hand I am enjoying 8.10 alot better now.

---

### Post by adult swim on 2008-12-12
EDIT:  my first suggestion didnt work like i thought it would
you can erase the old grub entries off of your menu.lst if you press alt+f2 and enter in ```
gksudo gedit /boot/grub/menu.lst
```
then scroll to the bottom and you can delete the ubuntu 7.10 entries you dont want anymore.  then save and close the file and you should be all set.

---

### Post by Austin_Duffy on 2008-12-12
> **adult swim said:**
> an easy way to do this is first open a terminal and run ```
uname -r
``` take note of the kernel it returns.
then go to synaptic package manager and search for linux-headers.  the ones that have a green box next to them are the ones that are installed.  you can click on the ones that were the old kernels you were using and mark them for removal.  DO NOT remove the one you are currently using, which is what the uname -r command returned.

2.6.27-7-generic

---

### Post by halitech on 2008-12-12
> **adult swim said:**
> EDIT:  my first suggestion didnt work like i thought it would
you can erase the old grub entries off of your menu.lst if you press alt+f2 and enter in ```
gksudo gedit /boot/grub/menu.lst
```
then scroll to the bottom and you can delete the ubuntu 7.10 entries you dont want anymore.  then save and close the file and you should be all set.

instead of deleting them, commenting them out might be a better idea so if there is an issue with 8.10 they can fall back to 7.10 to get help if needed.

---

### Post by thomas228 on 2008-12-12
> **Austin_Duffy said:**
> I managed to cram 8.10 into my laptop now how do I remove the former version of 7.10 I had..?

On the other hand I am enjoying 8.10 alot better now.

Hi 

adult swim gave you a means of altering your grub however I get the impression from your post you want more room for 8.10 which might require you remove some of 7.10.

If that's the case maybe someone more experienced than I can help you remove some of 7.10 edit: Like post#3

Good luck :lolflag:

Tom

---

### Post by adult swim on 2008-12-12
> **Austin_Duffy said:**
> 2.6.27-7-generic

sorry about that, in my original post i said to search for linux-headers in synaptic package manager, that was an error.  if you would like to remove the old ubuntu 7.10 kernels from your computer and your grub menu then you can search for linux-image from synaptic package manager.  then you can mark for removal all of the linux-image files installed but do not remove the one that ends in 2.6.27-7, or linux-image-generic because that is the one that you are using.  once you select the kernels you want to remove, click apply.  that will remove them from your computer and from the grub menu.  if you want to keep the old kernels but not have them show up in grub, you can edit the grub menu by running ```
gksudo gedit /boot/grub/menu.lst
``` and then deleting the blocks that say ubuntu 7.10 in them.

---

### Post by Austin_Duffy on 2008-12-12
> **thomas228 said:**
> Hi 

adult swim gave you a means of altering your grub however I get the impression from your post you want more room for 8.10 which might require you remove some of 7.10.

If that's the case maybe someone more experienced than I can help you remove some of 7.10 edit: Like post#3

Good luck :lolflag:

Tom

Yes I need to remove it to make room for apps I want to use, I don't even know how I crammed 8.10 into this labtop. 

I would like to remove all essences of 7.10 (Including WINE ect)

---

### Post by halitech on 2008-12-12
when you did the install, did you do manual partitioning or guided?

---

### Post by caljohnsmith on 2008-12-12
How about posting:
```
sudo fdisk -l
```
So we can see your setup, and also please identify your partitions.

---

### Post by Austin_Duffy on 2008-12-12
> **caljohnsmith said:**
> How about posting:
```
sudo fdisk -l
```
So we can see your setup, and also please identify your partitions.

[[IMG]http://img95.imageshack.us/img95/2971/screenshotbenbenlaptopuz6.png[/IMG]](http://imageshack.us)
[[IMG]http://img95.imageshack.us/img95/screenshotbenbenlaptopuz6.png/1/w657.png[/IMG]](http://g.imageshack.us/img95/screenshotbenbenlaptopuz6.png/1/)
 

Thanks for being patent btw, I'm multitasking

---

### Post by caljohnsmith on 2008-12-12
So which partition is 7.10? Is it sda1? If so, you could delete sda1 and expand sda6 into that space, but first you would have to expand the extended partition sda2 to take up that space. Also, you don't need two swap partitions, and having 9 GB worth of swap space is a bit of an overkill I think. Even if you have 4 GB of RAM, having a 4 GB swap partition should be adequate. I would delete one of those swap partitions and also shrink the other one to 4 GB, and then let sda6 take the rest of the space. I would recommend copying down the original UUIDs of the partitions you plan on keeping, because doing the repartitioning will change the UUIDs; after you are done with the partition changes, you can change the UUIDs back to their original values and save a lot of hassle of not reconfiguring any system files. To get the UUIDs you would do:
```
sudo blkid
```
And the other detail is you will most likely have to reinstall Grub to the MBR so that it points to the correct partition for the menu.lst. I can help with that if you want after you are done with all the partition changes.

---

### Post by Austin_Duffy on 2008-12-13
> **caljohnsmith said:**
> So which partition is 7.10? Is it sda1? If so, you could delete sda1 and expand sda6 into that space, but first you would have to expand the extended partition sda2 to take up that space. Also, you don't need two swap partitions, and having 9 GB worth of swap space is a bit of an overkill I think. Even if you have 4 GB of RAM, having a 4 GB swap partition should be adequate. I would delete one of those swap partitions and also shrink the other one to 4 GB, and then let sda6 take the rest of the space. I would recommend copying down the original UUIDs of the partitions you plan on keeping, because doing the repartitioning will change the UUIDs; after you are done with the partition changes, you can change the UUIDs back to their original values and save a lot of hassle of not reconfiguring any system files. To get the UUIDs you would do:
```
sudo blkid
```
And the other detail is you will most likely have to reinstall Grub to the MBR so that it points to the correct partition for the menu.lst. I can help with that if you want after you are done with all the partition changes.

[[IMG]http://img528.imageshack.us/img528/3269/screenshotbenbenlaptop1fz0.png[/IMG]](http://imageshack.us)



And 7.10 holds the sd1

---

### Post by caljohnsmith on 2008-12-13
I would first make a backup of all your important data in your sda6 Ubuntu partition, and then from the Live CD run System > Admin > Partition Editor to make the changes that I described in my previous post. When you first run the partition editor though, right-click your swap partitions and choose "swapoff" if it has that option enabled. Then you should be able to make whatever partition changes you need to; keep in mind that the partition editor doesn't actually make any changes until you press the "apply" button, so that is your only insurance against mistakes.

---

