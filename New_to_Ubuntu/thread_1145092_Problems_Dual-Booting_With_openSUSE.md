---
title: "Problems Dual-Booting With openSUSE"
date: 2009-05-01
forum: New to Ubuntu
---

### Post by Azhtabak on 2009-05-01
Hi. I recently installed openSUSE on my system alongside an existing Kubuntu 9.04, and am having problems - the bootloader (?) for openSUSE doesn't give me an option for Kubuntu - it doesn't seem to see it. It's still there, and I can see the partition for it in dolphin, but unfortunately, my ext3 openSUSE can't access my ext4 kubuntu :(

Anyone got any ideas on how I can fix this?

---

### Post by jbrown96 on 2009-05-01
Here's what Mandriva generated for my Kubuntu installation. 
> title Ubuntu 9.04
root (hd0,0)

Paste this at the end of your /boot/grub/menu.lst

You will want double check the partitions with ```
sudo fdisk -l
``` you may have to use su then ```
fdisk -l
``` I'm not sure if OpenSUSE comes with sudo installed.

You will get some listings. Find your Kubuntu partition. It will be something like /dev/sda1. You need the final letter and number. A == 0, B == 1, C ==2, etc. The confusing part is the partition number. Just subtract one from it 1 ---> 0, 2 ---> 1, etc. Then change this line > root (hd0,0) to match what you just found out. The first 0 is for the letter (converted to a number) and the second is for the number (don't forget to subtract 1 from it). 

You should now be able to boot into Kubuntu.

Here are some examples

/dev/sda1 ---> (hd0,0)
/dev/sda2 ---> (hd0,1)
/dev/sdb1 ---> (hd1,0)
/dev/sdb3 ---> (hd1,2)

---

