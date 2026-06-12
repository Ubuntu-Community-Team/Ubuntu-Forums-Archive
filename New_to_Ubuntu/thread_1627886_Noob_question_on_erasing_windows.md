---
title: "Noob question on erasing windows"
date: 2010-11-21
forum: New to Ubuntu
---

### Post by helphelphelp! on 2010-11-21
Okay, well I've decided that i LOVE ubuntu and want to clear windows completely. I currently have it as a duel boot and I have two questions

1) How do I go about erasing Windows? Do I boot from the CD again and erase the disk of everything Ubuntu?

2) If i go that route, will all my progress be okay?? Will I lose all the packages/settings I currently have in Ubuntu now?

---

### Post by helphelphelp! on 2010-11-22
bump

---

### Post by carl4926 on 2010-11-22
Please open a terminal and post the result of this:

```
sudo fdisk -l
```

---

### Post by Bucky Ball on 2010-11-22
Use a live cd, so partitions are unmounted, open Partition Editor, then just try expanding your Ubuntu partition over Windows or removing the partition, then expanding.

One issue here; when you kill windows you may well kill your ability to boot into Ubuntu (boot record). You might need to rewrite some things. Hopefully someone else can chime in with some advice as to what.

---

### Post by carl4926 on 2010-11-22
Lets see the fdisk result first

Chances are, that you don't already know the answer to all this that you are going to struggle with gparted and shifting the partitions.

Grub could be affected, so you should have a current Ub* cd to hand incase you need to do a repair

It's often a messy thing to do what you are asking and if it were my machine I would almost certainly re-install.

---

### Post by amjjawad on 2010-11-22
> **helphelphelp! said:**
> Okay, well I've decided that i LOVE ubuntu and want to clear windows completely. I currently have it as a duel boot and I have two questions

1) How do I go about erasing Windows? Do I boot from the CD again and erase the disk of everything Ubuntu?

2) If i go that route, will all my progress be okay?? Will I lose all the packages/settings I currently have in Ubuntu now?

There are many threads about the same issue in this forum and you could also use Google. I don't have a link at the moment, sorry.

Mainly, there are two scenarios here:
a) Ubuntu's Bootloader is installed in the MBR
b) Windows' Bootloader is installed in the MBR

In case of (a), all what you really need to do is:
1- Delete Windows Partition via GParted. If it's not installed on your machine, use the LiveCD or install it via Synaptic Package Manager.
2- Applications > Accessories > Terminal and run:
```
sudo update-grub

```
3- done.

In case of (b), if you'll remove/delete Windows, you won't be able to boot into Ubuntu anymore. You need then to rewrite GRUB or install it in the MBR.

You might find this [thread]("http://ubuntuforums.org/showthread.php?t=1612851") helpful so please check it out.

Sorry, not so much help.

---

### Post by wilee-nilee on 2010-11-22
**I agree with the sudo fdisk -l as well this could be a wubi install, for all we know. Somebody saying dual boot means nothing to me until I see the proof. Many call a wubi install a dual boot.**

---

### Post by papibe on 2010-11-22
First of all, backup your personal files on both your windows partition and your /home/user on Ubuntu.

I see a few options:

**Using Disk Utilities**

Go to System -> Administration -> Disk Utilities. Select your main disk. You'll see a map of how your disk is partitioned. Select your main ntfs windows partition and press Format Volume. Choose ext3 or ext4 as a format. This would be the easier easy way to recover the space allocated by windows. On the bad side, you'll end up with a new partition separated from your /home. You may mount the new one where you want (like /media/newpartition or /home/user/newpartition)

**Live CD and gparted**

Boot with the installation CD and choose try Ubuntu. Once you get to the desktop run gparted. Delete your ntfs partition and use it to expand your Ubuntu partitions. This option will give you the best use of your hard drive. However, this is more risky since if for some crazy reason the process fail without finishing, you may be loose all your data. Another risk is that it may corrupt grub, and you'll need to recover it by using a more advance solution (see [here]("https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202")).

**Clean Install**

Maybe this is the easiest way if you don't mind the process of backing up your files and then recovering them. You'll need to reinstall all programs you installed after you installed Ubuntu for the first time.

I hope that helps.

---

