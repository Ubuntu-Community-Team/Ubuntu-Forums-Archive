---
title: "Ubuntu 10.04 installation"
date: 2011-07-14
forum: New to Ubuntu
---

### Post by user_linux on 2011-07-14
Hi,
I'm trying to install ubuntu 10.04 thru a CD, however, when I am put my CD and go to Ubuntu interface to install, I don't see my windows partitions in ubuntu installer. My only fear is that if I continue to do so, my windows would be wiped and I will be left w/ just ubuntu. Can anyone help pls?

---

### Post by Rex Bouwense on 2011-07-14
First can you boot into Windows now?
If you can, just pop the CD into your CD drive. Press F2 or F12 or what ever button allows you to get into the BIOS and rearrange the boot order so that the CD drive boots before the hard drive.  A menu comes up which will allow you to try Ubuntu or install it.
First, click try Ubuntu so you can insure that everything will work out of the box.
If you are happy that all works, you can install side by side from there.  Enjoy.

---

### Post by mastablasta on 2011-07-14
> **user_linux said:**
> Hi,
I'm trying to install ubuntu 10.04 thru a CD, however, when I am put my CD and go to Ubuntu interface to install, I don't see my windows partitions in ubuntu installer. My only fear is that if I continue to do so, my windows would be wiped and I will be left w/ just ubuntu. Can anyone help pls?
 
that installer had a few problems. I am not sure why they haven't fixed these yet.
 
Anyway the easiest/safest way is to create an empty partition in windows and then install it there (empty disk space - this means no formating in any kind of filetype). you can install to largest empty disk space.
 
see the manual in my signature. maybe it will help with partioning.
 
 
another way to approach this is to boot into linux and then run gparted (just by typing it in terminal) and see if that one can at leats see your windows partitions.

---

### Post by Mark Phelps on 2011-07-14
You safest bet is to NOT, repeat NOT, allow the Ubuntu installer to shrink your Windows OS partition. If you're running XP, that's not likely to be a problem, but if you're running Win7, that IS likely to be a problem -- because that filesystem is easily corrupted by Linux filesystem utilities.

Also, if you have an optical drive in your PC, BEFORE you do the dual-boot install, use the Win7 Backup feature to create and burn a Win7 Repair CD.  That will come in handy later, should you need to repair the Win7 boot loader after the dual-boot setup.

Also, boot from the Ubuntu, open a terminal, and enter "sudo fdisk -lu" (that's a lowercase L, not a one).  That will list out the partitions on your hard disk.  If it shows the maximum of 4 partitions already allocated, you will have a lot of work to do to install Ubuntu because you can't then create anymore partitions.

---

### Post by mastablasta on 2011-07-14
> **Mark Phelps said:**
>  
Also, boot from the Ubuntu, open a terminal, and enter "sudo fdisk -lu" (that's a lowercase L, not a one). That will list out the partitions on your hard disk. If it shows the maximum of 4 partitions already allocated, you will have a lot of work to do to install Ubuntu because you can't then create anymore partitions.
 
you actually can have more partitions, but only extended one. Primary partitions are indeed limited to 4. and this could really be the cause of the problem here.

---

