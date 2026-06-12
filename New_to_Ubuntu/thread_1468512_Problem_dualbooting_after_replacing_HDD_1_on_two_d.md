---
title: "Problem dualbooting after replacing HDD 1 on two drive system with 8.04 on HDD 2"
date: 2010-05-01
forum: New to Ubuntu
---

### Post by defunk on 2010-05-01
Replaced primary HDD and performed a full xp recovery on a dualboot system with Hardy Heron on secondary HDD. Before this, computer booted to grub and gave choices of os's to boot. Now system boots into windows xp and can't even find the Ubuntu HDD.

How do I restore grub to new hard drive?

---

### Post by Sunfist on 2010-05-01
You will need to boot from your Live CD and reinstall from there assuming you know the drive/partition you have Ubuntu on.[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202) this link should help explain it.

---

### Post by oldfred on 2010-05-01
Did you have grub installed on the secondary/Hardy drive. If so you can in BIOS switch boot order and grub will boot. 

Old grub was not as good at finding other operating systems but try sudo update-grub. You may have to manually add a windows entry in menu.lst to your new windows install.

If you do not have grub on the second drive I would still recommend installing it to that drive and leave the windows boot loader in the MBR of the windows drive.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

