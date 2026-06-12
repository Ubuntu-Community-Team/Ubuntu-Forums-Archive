---
title: "uninstalling ubuntu from an external hard drive"
date: 2010-03-12
forum: New to Ubuntu
---

### Post by PhatScurl on 2010-03-12
okay so i seem to have royally messed up my computer and i need some help. I downloaded ubuntu, and have quite enjoyed it except that early this morning i found GRUB wasn't functioning properly. I eventually fiddled around and managed my way around this, and was in the process of moving files from vista into ubuntu.

Now i have ubuntu on an external hard drive that originally had no operating system. While in the process of moving files my external hard drive became disconnected, causing the operating system to freeze. Now when i try to load ubuntu goes on the fritz and tells me that it needs to run a maintenance shell and press ctrl+d (i don't know, forgive me it was a lot of stuff). Honestly with the problems i had i'd just like to start from scratch and i was hoping somebody could tell me how to remove ubuntu from my external hard drive and restore its to original size and also how i can get my computer to stop looking for GRUB when it first turns on (at least until i can figure stuff out)

Thanks a lot!

---

### Post by labinnsw on 2010-03-13
Using Windows, you can format the external hard drive.
Using Ubuntu live CD, you can use Gparted to delete any partitions on the drive or to format the drive.

---

### Post by Overcast32 on 2010-03-13
> **labinnsw said:**
> Using Windows, you can format the external hard drive.
Using Ubuntu live CD, you can use Gparted to delete any partitions on the drive or to format the drive.

Think he might have the boot partition on his regular fixed disk? Does the grub loader come up if the external drive isn't plugged in?

---

