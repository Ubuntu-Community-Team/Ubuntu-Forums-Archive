---
title: "Wubi user, switch to &quot;full&quot; dual-boot?"
date: 2011-03-28
forum: New to Ubuntu
---

### Post by Mikel2495 on 2011-03-28
Hey guys, I'm running Maverick Meerkat on a Samsung netbook (NF310). I was wondering whether to switch from Wubi to a proper dual-boot.

If I should, how would I do this?

---

### Post by Mikel2495 on 2011-03-28
Do you mean on Wubi.exe in Windows?

PS: I already have two partitions on my hard drive, one for my school work and similar, and one for music. Would there be any risk in merging those partitions and creating a new one?

---

### Post by Lateralis on 2011-03-28
My personal advice is to install a proper dual boot with Windows and Ubuntu side-by-side.  Wubi is fine as a trial, but it is far safer to install Ubuntu outside of Windows. 

As for partitioning, my general scheme is the following:

1) Windows System partition
2) Shared 'data' partition
3) Ubuntu /
4) Linux swap

More complicated schemes can be devised, for instance where you install your /home directories into a separate partition as well.  In any case, it is a very sensible idea to separate out your Windows System and Data partitions, because the NTFS support in Linux is adequate but NOT foolproof.  So essentially do not automount your Windows system partition and do not keep anything on that partition which is of high importance.  And keep backups of your Data partition.  (But you know to do that already, right? ;))

As for the actual upgrade, I'm not of aware of any system/method to take your current Wubi and "upgrade" it to a full installation.  Even if there was a way to do that I probably wouldn't recommend it.  The best thing to do is to make a copy of any and all important documents and files you have stored in your Wubi Ubuntu installation and then install a fresh copy of Ubuntu as a dual boot using a LiveCD.  Also, be sure to use the built-in tools within Windows to do that partitioning.  The tools in Ubuntu work for open source file systems but, again, are not foolproof when it comes to NTFS.

---

### Post by Mikel2495 on 2011-03-28
Thanks for the great response.

However, I'm pretty much a complete beginner to Ubuntu and not particularly skilled with Windows 7. Could you give some help on how to repartition my hard drive, step-by-step?

---

### Post by bcbc on 2011-03-28
You can [migrate]("http://ubuntuforums.org/showthread.php?t=1519354") your wubi to a dual boot. You need to create the partitions yourself. This is useful if you have a lot of customization/programs/data you don't want to have to set up again.

If not, it's probably simpler to do a fresh install and let the installer setup the partitions.

What's the output of:
```
sudo fdisk -l  (lower case -L)
```

PS any partitioning carries risks - so you are advised to back up your data.
Also create a windows repair disk beforehand.

---

### Post by Mikel2495 on 2011-03-29
Ok, I have a problem. I uninstalled my Wubi installation of Ubuntu and started to shrink a partition to make room for a new one for Ubuntu, thinking that I would need to manually do it. The thing is, my system messed up while shrinking and now, when I try to install Ubuntu from USB, it does not recognise the partitions. Is there any way to fix it?

---

### Post by bcbc on 2011-03-29
> **Mikel2495 said:**
> Ok, I have a problem. I uninstalled my Wubi installation of Ubuntu and started to shrink a partition to make room for a new one for Ubuntu, thinking that I would need to manually do it. The thing is, my system messed up while shrinking and now, when I try to install Ubuntu from USB, it does not recognise the partitions. Is there any way to fix it?
What's the output of 
```
sudo fdisk -l (lower case -L)
```

---

### Post by Mikel2495 on 2011-03-29
Sorry about that. I've already uninstalled Ubuntu, so is there a way to get the info you need in Windows 7 or would I need to reinstall with Wubi?

---

### Post by bcbc on 2011-03-29
> **Mikel2495 said:**
> Sorry about that. I've already uninstalled Ubuntu, so is there a way to get the info you need in Windows 7 or would I need to reinstall with Wubi?

Boot from the USB, select "Try Ubuntu" (or try without installing). Then you can also run the [bootinfoscript]("http://bootinfoscript.sourceforge.net/") if you like.

You can also use GParted on the live CD to setup your partitions before installing. (And you can kick off the install from the desktop as well).

---

### Post by bcbc on 2011-03-29
Also check this out - maverick's installer has some usability features. [http://ubuntuforums.org/showthread.php?t=1622388](http://ubuntuforums.org/showthread.php?t=1622388)

---

### Post by Mikel2495 on 2011-03-29
When I try to use my LiveUSB to boot from (I'm using a netbook without a CD-drive), it get an error as boots from the USB.

---

### Post by bcbc on 2011-03-29
What's the error?

I'd create a new USB by following the instructions here [http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download) (step 2, click on USB, then "show me how")

---

### Post by Mikel2495 on 2011-03-29
Basically after the screen by Phoenix it shows a little logo at the bottom, then spouts some code. After a second (literally) it freezes after trying to find the partitions.

Anyway, I'm redownloading the .iso and will remount the file.

BTW: Is the Netbook Edition worth it or should I just get the AMD64 Desktop version (I have a dual core 1.5Ghz Atom processor)?

---

### Post by bcbc on 2011-03-29
I don't think that error has anything to do with the partitions. It should boot the live USB without even looking at the hard drive (unless you choose the install option).

regarding 10.10 netbook - I didn't have much luck running it on my hardware - Unity didn't work. If you've tried it with wubi and it worked, then it will work on a proper install. And if you install netbook edition you can still choose to login with the gnome desktop manager if you don't like or can't use Unity (the netbook interface). So basically the only difference is Unity (and the fact that it's 32 bit not 64).

---

### Post by Mikel2495 on 2011-03-30
It freezes up between showing the option to open BIOS and the install/try out screen. That's the problem.

I'm downloading another .iso to make sure it's the computer not the image.

---

### Post by Mikel2495 on 2011-03-30
```
Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xbf4d583f
 
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13       11632    93323264    7  HPFS/NTFS
/dev/sda3           11632       28773   137690112    f  W95 Ext'd (LBA)
/dev/sda4           28773       30402    13079552   27  Unknown
/dev/sda5           11632       28773   137688064    7  HPFS/NTFS
 
Disk /dev/sdb: 4005 MB, 4005560320 bytes
21 heads, 21 sectors/track, 17740 cylinders
Units = cylinders of 441 * 512 = 225792 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc3072e18
 
   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          19       17741     3907648    c  W95 FAT32 (LBA)


```

Ok, this is the output from fdisk. I can run the LiveUSB using AMD64 Desktop but the installer won't get past checking for power, HDD space, etc.

---

### Post by bcbc on 2011-03-30
I can't see anything wrong with that.

It seems rather puzzling - that the live USB works, Wubi works, but the installer doesn't. Did you run the installer from the live USB Desktop?

---

### Post by Mikel2495 on 2011-03-30
I ran the installer from the LiveUSB desktop, and in the meantime ran fdisk. Then after it didn't run properly (stayed on the same screen, same conditions for five minutes) I restarted and am typing this in Windows.

---

### Post by bcbc on 2011-03-30
If you've checked the md5sum of the image you downloaded, then I have no idea why it won't install. Maybe someone else will jump in on this!

---

