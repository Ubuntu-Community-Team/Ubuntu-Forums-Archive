---
title: "how do i install backtrack 4 alongside ubu and win7?"
date: 2010-06-13
forum: New to Ubuntu
---

### Post by bradmayne04 on 2010-06-13
I want to install backtrack 4 alongside ubuntu and win7 (i have karmic and win7 home premium installed right now) can someone tell me how i would go about doing that?  I have a 250 gig hd on this laptop which I think is more than enough room to do this seeing as I only need about 20 gigs or less for the backtrack  4 install.  I am using grub2 version 1.97 (don't know if this makes a difference but figured i should let you know) thanks in advance!!

---

### Post by Diabolis on 2010-06-21
Insert the live cd, boot from it, set up a new partition for backtrack 4 and install it there.

---

### Post by oldfred on 2010-06-21
You will want to keep Ubuntu's grub in the MBR, I do not know if backtrack lets you choose to not install its boot loader to the MBR or can install it to the PBR but if not, just plan on reinstalling grub2 like you have to do after a windows install.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
kansasnoob on grub or grub2 reinstall
[http://ubuntuforums.org/showpost.php?p=9338226&postcount=41](http://ubuntuforums.org/showpost.php?p=9338226&postcount=41)

---

### Post by bradmayne04 on 2010-07-03
hey fred sorry it took me so long to write back on this thread.  i just noticed you posted.  so what your saying is if i have a choice to install grub when installing backtrack 4 i should say "no" to installing grub during the backtrack 4 install?  or should i say yes?  and if i have to reinstall grub how do i do that again?  can i do that from an ubuntu live disk? if so how?  (remember the nightmare I went through about a month ago because of that messed up karmic upgrade? and you and i were pm'ing each other all weekend?  i don't wanna go through that again lol!!

---

### Post by gallifrey on 2010-07-03
I have done this recently quite successfully. Obviously, individual preference is up to you, but I will tell you how I did it.

I installed on a laptop with a 500 GB drive. I used Gparted to create partitions as follows:

100 GB NTFS (primary) for Windows 7
30 GB Ext3 (primary) for Backtrack
60 GB Ext4 (primary) for Ubuntu /

I then created and extended partition, with logical volumes as follows:
4 GB Swap
Whatever was left for Ubuntu /home.

After partitioning, install Windows 7 to first partition. 
Then install Backtrack, dedicating /sda2 to it, and sharing the swap created earlier in the extended partition. 
Once Backtrack is installed, make sure to update it first, as necessary,then go ahead and install Ubuntu, as normal, installing grub2 to the MBR of /sda. Grub2 will detect Backtrack as Ubuntu 8.10, but that is normal, since to all intents and purposes, it is. 

i have avoided any Bootloader updates for backtrack, just in case they mess up Ubuntu's Grub. Otherwise, all works like a charm. 
That is what I did, anyway, and I have had no problems.

---

### Post by oldfred on 2010-07-03
Almost all installs give you a choice on where to install the bootloader. If it is old grub I do like to install to the partition the system is installed into - sda5 for example. It gives an additional option of chainbooting. But grub2 is so good now you do not have to use chainloading and can just update  grub2 in Ubuntu to find other systems.

If you end up with backtracks boot loader in the MBR the links in post #3 have instructions to use the liveCD.

Basically the instructions are, but you need to know which linux partition is Ubuntu and which is backtrack:
Install from LiveCD:
Find linux partition change sda5 if not correct (or even change sda if sdb's MBR wanted):
sudo fdisk -l
sudo mkdir /mnt/sda5
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
sudo grub-install --recheck --root-directory=/mnt /dev/sda

---

