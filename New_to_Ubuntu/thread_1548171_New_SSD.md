---
title: "New SSD"
date: 2010-08-07
forum: New to Ubuntu
---

### Post by Lazy-buntu on 2010-08-07
Hey everyone, I bought a 60GB SSD today, and I'm trying to think of how I'm going to live with such a small drive. If you're concerned about Ubuntu related questions only, go ahead and skip to #2 :)

I dual boot Windows 7 and Ubuntu 9.04, so my goal is to at least have Windows 7 on the SSD. I've got a couple of questions though:

1. (Non-ubuntu related): For the most part, would it be ok to install non-critical software to my HDDs?

2. I'm planning on installing Windows 7 to the SSD, but I do want to keep Ubuntu. Windows 7 will be a fresh install on the SSD. Is it possible to leave Ubuntu on the HDD and make both the SSD and HDD bootable? Therefore, do I need to install GRUB to the SSD or what?

3. If I installed Ubuntu to the SSD, what are the recommended tweaks for Ubuntu if you have any?

---

### Post by ubunterooster on 2010-08-07
1. I stick program files on the SSD and pics, documents... on a separate drive

2. Just have The drive with Ubuntu set up in the motherboard to be the first booted from and then run ```
sudo update-grub
```

3.At this point it would just be best to not do any extra tweaks but I recommend Ext4 over Ext3 due to performance of Ext4

---

### Post by Lazy-buntu on 2010-08-08
So I could delete the Windows 7 partition from my HDD, install Windows 7 to the SSD, set the HDD as the boot drive, update GRUB, and GRUB would pass it over to the SSD if I wanted to boot into Windows?

Would that slow down my boot times on the SSD?

---

### Post by QLee on 2010-08-08
[QUOTE=Lazy-buntu]...
Would that slow down my boot times on the SSD?[/QUOTE]

Strictly speaking, yes, if the SSD is faster than the HDD, however, will it be enough to be noticeable, probably not enough to matter. If your quest is to have a system that is optimised for booting Windows as you have described, then use a separate boot partition on the SSD for GRUB (if GRUB is the bootloader you choose to use). If it was my system, I think I would choose to have both Windows and Ubuntu on the SSD and my swap file, paging disk, and data files on the HDD. [I would probably put log files, mail stores, and temp files in separate partitions on the HDD too but this is becoming more complicated than what is generally asked in the absolute beginner topics forum and the wiki about partitioning should be consulted].

Hope this gave you some topics to research.

---

### Post by ikt on 2010-08-08
> **Lazy-buntu said:**
> 3. If I installed Ubuntu to the SSD, what are the recommended tweaks for Ubuntu if you have any?

As far as I know ubuntu has trim support all built in, so there isn't anything to do.

---

