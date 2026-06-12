---
title: "how to partition properly to install windoze?"
date: 2010-01-21
forum: New to Ubuntu
---

### Post by gfunkera on 2010-01-21
i need to do the unspeakable... i have to install a version of windows (im lookin at either vista or xp) on my hard drive... what is the proper method of partitioning and installing it?

i need to run some very specific music production software and run it without using virtualbox (FL Studio is very resource/memory intensive)..
:confused::confused::confused:

---

### Post by Roasted on 2010-01-21
It's really your call. Say you have a 500gb hard drive. How much do you need for Windows? When you're at the partitioner in the Windows installation menu, it'll ask you how you want to set up your drive. Just create a new partition, but set the partition size the way you want it.

AKA - if you have a 500gb drive, and you want 100gb to be Windows, only create a 100gb partition and install Windows on that. Leave the remaining 400gb untouched.

When you install Linux, then you can utilize that 400gb to be used for Linux. So during the Windows installer, only set up what you need with Windows. The remaining (unallocated) space Linux can deal with later when you install it.

---

### Post by howefield on 2010-01-21
You need to create a primary partition formatted to something like NTFS. Then install windows in it.

The problem will be that windows will over write grub with its own bootloader, so you will need to reinstall grub.

Were it mine, I'd probably just wipe the lot, having first backed up anything required. WIndows installed first, followed by Ubuntu, and finish off with a disk image with Clonezilla.

---

### Post by gfunkera on 2010-01-21
wait, i wanna install windows on a smaller partition on my linux machine... so are you guys saying that windows will have to be the first thing on there? i dont wanna loose any of the information on my machine...

can i get a second hard drive, say an external one (or internal, it doesnt matter), and install it there and use it as needed?

---

### Post by howefield on 2010-01-21
It doesn't need to be on the first partition, but it does need a primary one, and installing it after you have already installed linux will give you the problem with grub that you'll need to know how to fix.

---

### Post by Roasted on 2010-01-21
> **gfunkera said:**
> wait, i wanna install windows on a smaller partition on my linux machine... so are you guys saying that windows will have to be the first thing on there? i dont wanna loose any of the information on my machine...

can i get a second hard drive, say an external one (or internal, it doesnt matter), and install it there and use it as needed?

You won't lose anything as long as you don't go format-happy with your partitioning scheme.

If you install Windows on a system that already has Linux on it, the Windows boot loader will over-write Grub (the Linux boot loader). That's why it's always recommended that if you're building a fresh dual boot system, to do Windows first, and Linux second. This is because the Linux boot loader can handle booting Windows, while Windows isn't so friendly.

Put it this way. Windows hates everybody but itself. But Linux at least tolerates it.

You should google how to restore Grub with Ubuntu, because if you install Windows on that system, Ubuntu won't be bootable until you restore Grub. But like I said, once Grub is in place, Windows + Ubuntu will both be available options to boot to.

---

