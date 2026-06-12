---
title: "Partitioning ubuntu HD to install Windows 7"
date: 2011-07-05
forum: New to Ubuntu
---

### Post by nostromo72 on 2011-07-05
I currently have only ubuntu 10.04 on my laptop and want to dual boot with windows 7 (just for games), I've been trying to find a step by step type of guide for installing windows from ubuntu but haven't found anything that really satisfies me. I guess there's not as much a demand for going from straight ubuntu back to windows as there is the other way around. Can anyone help? Also, from what I've seen it looks like I'd lose the GRUB, how do I not?

---

### Post by overdrank on 2011-07-05
Hi and welcome. Moved and bumped to Absolute Beginner Talk

---

### Post by jtarin on 2011-07-05
Can you boot from the Ubuntu Live CD Gparted from the menu take a screenshot of your partitions currently on your drive or alternately you can use the link in my signature to use Boot Info script to give us information about your drive. One more way is the command in a terminal ```
sudo fdisk -l
```For my thinking Gparted would be the best as it will give us a visual of how your partitions can be resized......if at all.

---

### Post by Rex Bouwense on 2011-07-05
Here is a How To for what you are asking for.
[http://ubuntuforums.org/showthread.php?p=10257675](http://ubuntuforums.org/showthread.php?p=10257675) 
I think one of the six scenarios will fit.

---

### Post by Mark Phelps on 2011-07-06
Admittedly, I did not read through the entire Guide that was linked, but basically, you can NOT install Windows 7 from inside Ubuntu; instead, you need to be able to boot from the DVD and install it that way.

BEFORE you do that, you need to boot from an Ubuntu CD and shrink the Ubuntu partition to make room for an NTFS partition for Win7.  Do NOT use the Linux filesystem partitioning tool to create an NTFS partition; instead, let Win7 do that itself as part of the installation.

---

### Post by Rex Bouwense on 2011-07-06
> **Mark Phelps said:**
> Admittedly, I did not read through the entire Guide that was linked, but basically, you can NOT install Windows 7 from inside Ubuntu; instead, you need to be able to boot from the DVD and install it that way.

BEFORE you do that, you need to boot from an Ubuntu CD and shrink the Ubuntu partition to make room for an NTFS partition for Win7.  Do NOT use the Linux filesystem partitioning tool to create an NTFS partition; instead, let Win7 do that itself as part of the installation.

The steps in scenario 4 explain exactly what has to be done to include what you have explained.  It is actually quite good and explains all of the scenarios that could possibly occur.

---

