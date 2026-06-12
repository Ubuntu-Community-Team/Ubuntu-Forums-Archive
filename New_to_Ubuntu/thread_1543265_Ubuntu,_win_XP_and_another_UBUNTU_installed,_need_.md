---
title: "Ubuntu, win XP and another UBUNTU installed, need to delete one! help!"
date: 2010-07-31
forum: New to Ubuntu
---

### Post by Vuk Matic on 2010-07-31
Okay so i had a problem with ubuntu coz after i installed Win XP (dual boot) it would only boot into a white terminal :@ and that pissed me off (no solutions worked) so i reinstalled ubuntu again! Problem is, ubuntu didnt install over the old instalation... like i thought i told it too! and now i have loads of ubuntus that i cant boot into. i can even boot into my old ubuntu but my mouse doesnt work there :( (plug and play mouse works though!) anyways the biggest problem is that the new UBUNTU i installed, installed on a tiny partition of about 4gb in size. Now what i wana ask is if i delete the old partition containing the old ubuntu (76gb) can i use that free space for the NEW ubuntu? im gna try expand the partition now using gparted and see if that does anything!

sorry if i bored you but please give me some support, like am i on the right tracks with GPARTED?


thank you!!

---

### Post by skyjacker on 2010-07-31
Install a NEW ubuntu in the 76 mb partition (select manual for the install choice), and be sure to tell the install program to FORMAT that partition. This should give you a clean install in the 76  mb partition.

---

### Post by joshedmonds on 2010-07-31
If the partitions are physically separate (e.g. Ubuntu1 - Windows - Ubuntu2) then GParted will not be able to 'move' Ubuntu2 to where Ubuntu1 is. You *could* delete Ubuntu1, resize Windows, then resize Ubuntu2, but this will take forever and increase the chances of screwing your Windows install, and probably require you to set up Grub again.

If the partitions are adjacent (e.g. Windows - Ubuntu1 - Ubuntu2) then you can delete Ubuntu1 and resize Ubuntu2. If you have a lot of data stored within the root drive (e.g. storing things in /home without a separate /home partition) then this will also take forever and require a Grub setup.

If the new Ubuntu install is a default one (it seems like you haven't been able to boot into it?) it may be easiest to do a clean install and select the partitions manually. This will ensure your Windows partition is not moved, and will reinstall Grub.

Determine what partition will be used where in the new install (using the names provided by GParted e.g. sda1) and assign the partition you want to install to '/'. If you want the other partitions available specify them as well e.g. /windows /media/STORAGE_DRIVE etc.

EDIT: of course, as noted by skyjacker, mark the install partition for formatting to remove the old install

---

### Post by Vuk Matic on 2010-07-31
well i decided to just "**** it" and i deleted all partitions and made 2 new partitions for win xp and ubuntu! although i think my win xp install messed up, i ll sort it out tomorrow hehe :) but thanks for all your help! im really learning lots about ubuntu!!!

---

### Post by -kg- on 2010-07-31
What it sounds like is that you selected "Install Side By Side" in the partitioning step of the installation.  This will not select the partition you want to install in, but instead will shrink another partition and create another one in the free space.

> if i delete the old partition containing the old ubuntu (76gb) can i use that free space for the NEW ubuntu?

Yes, but you will run into problems.  Linux (and GParted) assigns drive designation in the order of their creation, not the order on the hard drive.  That means that, if you delete the old Ubuntu partition, which was created earlier than your present one, the drive numbers of the partitions created afterward will change.

When you select the menu selection in the GRUB boot loader menu, it looks for the subsequent GRUB stages by partition number.  If you delete the original ubuntu partition, it will change the designations of the following partitions, and the boot loader will not be able to find the subsequent partitions.

If you don't have much data in your original Ubuntu, then I would suggest deleting both the Ubuntu root partitions, the swap partition, and then reinstall using the whole space.  If you have a separate "/home" partition, you can save that and, when you reinstall, use the "Manual Partitioning" selection, mark that partition as "/home" (*_don't_ format it!*), and create your "/" (root) partition in the remaining space and install into it.

Of course, if you've already tried deleting your original root partition and expanding the new one, we'll see you back here when you get Ubuntu totally reinstalled. :p

> well i decided to just "**** it" and i deleted all partitions and made 2 new partitions for win xp and ubuntu! although i think my win xp install messed up, i ll sort it out tomorrow

That would be the best way.  Install XP first, make sure it works, and when you have it working, install Ubuntu and allow Ubuntu to put GRUB into the MBR.

One thing...

After you install XP, be sure to defrag it before installing Ubuntu.  The Windows installer isn't very particular about fragmentation when it installs, and some of the worst fragmentation I've ever seen is just after installation.  This will also make the partition easier to shrink for the installation of Ubuntu.

That is, unless you create your XP partition beforehand to the size you want it.  That is ideal, and you can elect to install in the free space ("Use Largest Contiguous Free Space" selection in the partitioning step of the installer) you left.

---

