---
title: "Dual boot - Windows 7 + Ubuntu"
date: 2009-11-23
forum: New to Ubuntu
---

### Post by evo3logy on 2009-11-23
Hey everyone!

I'm kinda new, so hello!

Anyway, i installed ubuntu a while back on my main notebook. Due to some programs that heavily require a Windows 7 platform, i installed Windows 7 on my 2nd partition (1st partition of 50gb is alloc for ubuntu while 2nd partition of 50gb is alloc for windows 7).

As predicted after reading a few articles, the ubuntu platform is ignored upon start-up and immediately it starts at Windows 7.

My question is if from this point can i make my ubuntu recognisable at start-up and how to, or do i have to reinstall ubuntu from scratch with the GRUB thing?

Thanks!

PS: My unrecognised ubuntu is of 9.04 :)

---

### Post by danill2008 on 2009-11-23
Hi, I quickly searched for a simple solution. [Here]("http://ubuntuforums.org/showthread.php?t=224351") is one. Good Luck!

---

### Post by fancypiper on 2009-11-23
Do you know which version of grub you were using? Windows "fixes" the MBR, so you just need to re-install grub.

Basically, you boot with a live CD, open a terminal, make mount point(s) for your system, chroot to the system with bash, then install grub.

sudo bash # DANGEROUS! ENTER COMMANDS EXACTLY!
mount /dev/sda1 /mnt #<--Change to your root partition, fdisk -l will give disk partition info
mount /dev/sda2 /mnt/boot #<--Only if you have a separate /boot partition
mount -o bind /proc /mnt/proc
mount -o bind /dev /mnt/dev
chroot /mnt bash
update-grub
grub-install /dev/sda #<--Change to your hard drive
exit
exit

[How to restore Grub from a live Ubuntu cd](http://ubuntuforums.org/showthread.php?t=224351)

I have heard that Windows has a boot.ini file that you **might** be able to boot Linux from, but I haven't used Windows since I quit helping a friend that ran Windows 2000 and I had to edit that file to speed up his boot up time.

---

