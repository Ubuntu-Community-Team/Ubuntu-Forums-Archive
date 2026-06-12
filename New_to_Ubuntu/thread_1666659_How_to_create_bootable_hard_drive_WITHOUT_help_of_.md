---
title: "How to create bootable hard drive WITHOUT help of Ubuntu Live CD?"
date: 2011-01-14
forum: New to Ubuntu
---

### Post by Fanatico on 2011-01-14
I have Ubuntu 10 running on my computer, USB to SATA adapter and new Hard Disk.

My question is how can I make bootable hard drive WITHOUT help of Ubuntu Live CD?

What I did so far:
1. With help of GParted created 3 partitions on new Hard Drive:
Boot(Ext3 with Boot flag set, primary partitions), Linux (Ext3, primary partitions) and Swap.

2. Copied content of my Ubuntu /boot directory to root of new boot partition

3. Copied contend of entire disk (cp -aPR * /media/Linux) to root of Linux partitions

4. Trying to reboot with new hard disk. Obviously it doesn't boot because I assume the MBR is not created

How can I create proper MBR manually?

Thanks

---

### Post by C.S.Cameron on 2011-01-14
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

---

### Post by oldfred on 2011-01-14
All the instructions for using liveCd assume you do not have a bootable system. But if you have a bootable system, you can install grub from that, just like you would from a liveCD. Just mount the partition with the new install and install grub.

Just run this from your working system:
#Comments are anything after the #, enter commands in terminal session
#Install MBR from LiveCD, Ubuntu install on sda5 and want grub2 in drive sda's MBR:
#Find linux partition, change sda5 if not correct:
sudo fdisk -l
#confirm that linux is sda5
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda
#If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt/ /dev/sda
# After rebooting into working system
sudo update-grub

---

