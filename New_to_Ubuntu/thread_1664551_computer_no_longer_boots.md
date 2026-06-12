---
title: "computer no longer boots"
date: 2011-01-11
forum: New to Ubuntu
---

### Post by barrykgerdes on 2011-01-11
I have a major problem
I tried to install Ubuntu 10.4 on a clean partition on a secondary disk where the main operating system is windows XP SP3
I got to it installed and started to run the updates. These down loaded OK. I installed the updates and the program said it needed to reboot. I answered yes.

Now the computer wont start.
It attemps a restart but comes up with
error:no such device: b2fc66a8-a6cf-4bb0-99a6-d625be1f347b
grub rescue >

I can boot from a cd OK and look at the HDD and see all the old programs but I just can't boot to any system.
I supect it is a grub problem but I have no idea on how to fix it

barry

---

### Post by pedrobelo on 2011-01-11
Hi Barry
Check out this thread [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by SoFl W on 2011-01-11
Others have had the same problem, [try here]("http://www.google.com/search?q=error%3Ano+such+device&sitesearch=ubuntuforums.org").

---

### Post by Rubi1200 on 2011-01-11
If this is a Wubi install, see here:
[http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)
problem #1, solution #1 or #2

If in doubt, post the results of the boot info script from the LiveCD.

---

### Post by barrykgerdes on 2011-01-12
I have read pages and pages on this problem but cannot find a way to get my hard disk back. I don't want linux or any reference to it. I just want to put the HDD in another computer, make it bootable and put some programs on it. 

No matter what I do I cannot get the HDD to do anything but display Error: (string)
grub rescue

I imagine the mbr has been modified but FDISK etc does not get rid of it I can edit the mbr if I know what the problem is.

Surely tghere is a program to generate a generic mbr

barry

---

### Post by barrykgerdes on 2011-01-12
got around the problem. erased the mbr and installed a generic version woth norton under dos

barry

---

### Post by Rubi1200 on 2011-01-13
Glad you got it sorted out.

Good luck!

---

### Post by barrykgerdes on 2011-01-13
I understand the problem now but if someone had told me earlier what the problem was caused by instead of directing me to other replies it would have been resolved easier.

 Here is what I see is the problem:
When Linux is installed it modifies the  primary mbr sector to direct the boot operation to the grub.config. This contains the location of the bootstrap loaders. If the Linux installation is removed or damaged in any way the grub configure is not available and that error message appears.

There are two ways to correct the problem
1. Reinstall Linux from the installation disk. This will fix the mbr for most.

2. However if you wish to use the HDD for a non linux installation the problem arises that the normal fdisk, format arrangements do not modify the mbr and the disk becomes useless. The only way I found to do it was to use a disk editor (Norton diskedit)  and erase the mbr. Then if you run NDD it will find the error and correct it by writing a new generic mbr that uses the standard dos bootstrap loader.

barry

---

### Post by mastablasta on 2011-01-13
you can also fix reload/grub via linux live CD.

---

