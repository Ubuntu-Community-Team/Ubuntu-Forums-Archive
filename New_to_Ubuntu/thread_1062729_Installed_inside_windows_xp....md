---
title: "Installed inside windows xp..."
date: 2009-02-07
forum: New to Ubuntu
---

### Post by M03BIUS on 2009-02-07
I installed Ubuntu using the Ubuntu LiveCD autorun menu while I was in Windows XP. I installed it for a 20 GB installation because that's the highest I could choose. Now, I have run out of disc space in Ubuntu... how do I resize the partition to fill up more than 20 GBs?  I initially made a partition in Windows MMC consol to 70GBs but why is it I can only use 20GBs in the Ubuntu installer? If I install Ubuntu from the POST cd boot will it fix this problem? I tried Gparted and Partition Editor but it won't let me resize anything.

---

### Post by Partyboi2 on 2009-02-07
You should be able to resize by following [[COLOR=Blue]this[/COLOR]]("https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20resize%20the%20virtual%20disks?").

---

### Post by M03BIUS on 2009-02-07
So I installed Ubuntu on a Virtual disk using the installer?

---

### Post by M03BIUS on 2009-02-07
I did what that guide said to do and I still only have 1.1GB of free space... I don't know how to do this.

---

### Post by Paqman on 2009-02-07
> **M03BIUS said:**
> I did what that guide said to do and I still only have 1.1GB of free space... I don't know how to do this.

What did you actually do? Install LVPM and use it to resize your virtual disk?

Btw, the installer you used is called Wubi. It installs Ubuntu to a virtual disk which is bascially just a big file on the Windows NTFS partition. It's clever stuff.

If you're unable to resize using LVPM then your next option is create a new partition of the size you want and use LVPM to migrate your install to that partition. Instructions are on the same page as above.

---

### Post by avtolle on 2009-02-07
If you decide to follow Paqman's recommendation, please defrag the HDD before proceeding; you might want to do it more than once, BTW. Good luck.

---

### Post by M03BIUS on 2009-02-07
Ok, the way my system is setup is like this..

1st Partition

70GBs Windows XP


2nd Partition

70GBs Windows Vista


3rd Partition

This is where I installed Ubuntu using that Wubi installing inside of the 1st Partition using Windows XP.


I currently use the "Windows Boot Loader" with this menu selection...

Earlier versions of Windows
Microsoft Windows Vista
Ubuntu



Now when I migrate my Ubuntu it is going to replace my Windows Boot Loader with GRUB correct?  Should I have to anything else besides migrating or will I have to reinstall my Windows as well?  I mean will I still be able to log into my XP and Vista after the migrate?

---

### Post by theozzlives on 2009-02-07
Sounds like you want to do a full install. You have to boot to the Ubuntu CD to do that. That requires modifying your partitions, but you can still keep your Windows... it's called dual boot.

---

### Post by Paqman on 2009-02-07
> **theozzlives said:**
> Sounds like you want to do a full install. You have to boot to the Ubuntu CD to do that. That requires modifying your partitions, but you can still keep your Windows... it's called dual boot.

Actually, no you don't. You can migrate a Wubi install to a partition without reinstalling. Also, Wubi is already technically a dual-boot. It just has an unconventional way of using the disk space.

M03BIUS: Yes, LVPM would install GRUB to replace your current Windows bootloader. It won't touch Windows itself, just the Master Boot Record of your drive. 

Having said that, it's always smart to take a backup before you do any disk partitioning, just in case.

---

### Post by M03BIUS on 2009-02-07
I did a fresh install.. I like the GRUB boot loader better anyway... everything works nice now... I now have a triple booted system... XP,Vista,Ubunut. I actually get better performance now that it's on its own partition.  The virtual drive was kinda laggy for me anyway.  Thanks for your help everyone!

---

