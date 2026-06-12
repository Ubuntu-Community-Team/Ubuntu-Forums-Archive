---
title: "how to install Win XP after ubuntu"
date: 2011-08-16
forum: New to Ubuntu
---

### Post by sallam on 2011-08-16
Greetings
At first I had Windows 7, then I installed ubuntu 11 in a separate partition, and I'm using both in a dual boot.
Now I need to install Windows Xp in a third separate partition, so that I have 3 OS's.
Is it possible? and how please?

Many thanks.

---

### Post by Kellemora on 2011-08-16
Hi Sallam

You might be happier if you install it in Virtual Box!

I have most of my computers triple boot, but after using Windows XP in Virtual Box, I'll be changing to using only that method.

#1 - You don't have to reboot to get from Linux to Windoze!
#2 - Virtual Box can be left open on one of your Desks.
#3 - Windoze opens from cold boot in only seconds IF you close it.
#4 - My favorite feature, you can jump between Linux and the Doze simply by changing which Desk you are on.
#5 - Virtual Box can have other OS's only one click away also!

I wouldn't need Windows at all anymore if it were not for the fact that in all of the worldwide Linux community, no one has assembled a simple programmable autoclicker.

I also still need to use QuickBooksPro and Family Tree Makers FTW program for archived files and both of these work with the Doze in Virtual Box.

TTUL
Gary

---

### Post by coffeecat on 2011-08-16
> **sallam said:**
> Now I need to install Windows Xp in a third separate partition, so that I have 3 OS's.
Is it possible? and how please?

Yes, it is possible, but there are a few things you need to know.

The Windows XP installer will replace the mbr with its own booting code, which means that you will temporarily lose the ability to boot into Ubuntu. This is easily fixed by the use of a live CD, though. After repairing grub, you will then need to run "sudo update-grub" to get Windows XP into your grub menu, otherwise you won't be able to boot Windows XP!

The partition you install XP to needs to be a primary one, not a logical one, otherwise the XP installer will grab the nearest primary partition it can find for its boot files. And that may not be where you want them. Windows 7 will put its own boot files in a Windows XP partition, if it finds one, but what XP does can be quite unpredictable.

Somewhat related to the above, if you have logical partitions present on your drive in certain configurations, the XP installer can do the most crazy things to your partition table without telling you. In particular, it may "convert" a logical partition to a primary one leading to the illegal situation of a primary partition inside an extended partition. It is the presence of Linux filesystems that seems to confuse the XP installer, and it's most likely to be your Ubuntu root partition that will suffer from the XP installer's tender mercies. This does not happen always - it seems to depend on the partition layout - but I have seen enough threads about this to believe it needs bearing in mind, and I have managed to simulate the situation myself.

Post the output terminal output of:

```
sudo fdisk -lu
```

Tell us which partition you intend to put XP on and I may be able to comment some more.

---

