---
title: "how do I delete an upgraded ubuntu 10.04 and clean install it?"
date: 2010-07-28
forum: New to Ubuntu
---

### Post by grf7291 on 2010-07-28
Okay, first off I'm a newbie with Ubuntu but i already love it!! I'm running an HP Laptop with a single 500gb HDD with the following partitions as described in GParted:

sda1 ntfs Windows7 430gb
sda3 extended 25gb (Ubuntu 10.04 64-bit by the way)
    sda5 ext4 24gb
    sda6 linux-swap 1gb
sda2 ntfs Vista factory recovery parition 10gb

now my question: i had 9.04 Jaunty but upgraded to 10.04 Lucid recently since i hadn't used Ubuntu is such a long time and was finally ready to get serious with it and try it out. So i upgraded and did some tweaks and played around with it a lot to get the feel for it. now heres what i want to do: i dont want this upgraded 10.04 Lucid version, I want to wipe off everything and start a fresh&clean 10.04 Lucid version on my extended 25gb partition without disturbing my Vista recovery and windows7 partitions

can i do this?

---

### Post by dcollier on 2010-07-28
If you load the CD and start the installation you will have an option to format your partition. "the sda3 or sda4, which ever one you have ubuntu installed on."  This will give you a clean install of the distro.  Make sure you backup your home partition if you have data that you need.  This will give you a clean install.

---

### Post by grf7291 on 2010-07-28
okay thanks, i'm burning the .iso to a disc right now

so i will boot my laptop using the live CD and install it that way, correct?

will this affect my GRUB or anything like that?

---

### Post by dcollier on 2010-07-28
You would go through the same steps as you did with the dual boot process.  As a tip i would create a seperate partion for boot, "/", swap, and home, so that if you want to reinstall the distro all you have to do is format the "/" partion and everything else would still be intact.

---

### Post by grf7291 on 2010-07-29
> **dcollier said:**
> You would go through the same steps as you did with the dual boot process.  As a tip i would create a seperate partion for boot, "/", swap, and home, so that if you want to reinstall the distro all you have to do is format the "/" partion and everything else would still be intact.

okay so what you are saying is when i run the install cd to select "specify partitions (advanced)" and to create a partition with ext4 journaling system and select it as...which one: "/" or "/boot" or "/home"???

---

### Post by dcollier on 2010-07-29
all of them, you can create a seperate partiton for each.  Here is a link below, it gives you more than just root, swap, home, boot, but thess are the ones that I choose to create a partition for. Here is the link [http://tldp.org/LDP/lame/LAME/linux-admin-made-easy/install-partitioning.html](http://tldp.org/LDP/lame/LAME/linux-admin-made-easy/install-partitioning.html)

---

### Post by oldfred on 2010-07-29
You do not need a /boot for a newer desktop system, adding a separate /home is a good idea.

Separately, if you are going to share a lot of data with your windows you may want to create a share partition by shrinking windows and putting your data into that share partition. Many windows users also suggest a separate "data" partition for windows so when you reinstall windows system your data is not lost, just like a separate /home. I also do not like writing into another system partition, windows can be particular. I regularly read my windows system partition, but only write if I have to do repairs.

I also like moving my firefox profile to the shared partition as then I have exactly the same bootmarks and history in both.

Mount, hide & link windows partition
[http://ubuntuforums.org/showthread.php?t=1397508](http://ubuntuforums.org/showthread.php?t=1397508)
Share Windows partition:
[http://lifehacker.com/348858/use-a-single-data-store-when-dual-booting](http://lifehacker.com/348858/use-a-single-data-store-when-dual-booting)
Link XP my docs
[http://www.techsupportalert.com/how_to_move_my_documents.htm](http://www.techsupportalert.com/how_to_move_my_documents.htm)

---

### Post by -kg- on 2010-07-29
Personally, I seriously don't like the idea of a separate "/boot" partition.  It just makes things overly complicated and there's no real reason for it unless you're installing Fedora in an ext4 partition.  Fedora's GRUB bootloader still will not recognize boot files in an ext4 partition. (They *still* haven't fixed that, that I know of!).

Plus, it will cause you additional work when you get several kernels (they're installed in the /boot partition).  You'll have to delete older kernels, depending on the amount of space you give the /boot partition.  I know...I've tried it.


The most you will need is a "/" (root) partition, a "/home" partition (if you want it...I'm ambivalent about the idea, though I still do it), and of course, a swap partition.  If you already have a swap partition, leave it as is.

> sda1 ntfs Windows7 430gb
sda3 extended 25gb (Ubuntu 10.04 64-bit by the way)
sda5 ext4 24gb
sda6 linux-swap 1gb
sda2 ntfs Vista factory recovery parition 10gb

I'm assuming that what you have given Ubuntu to work with is all you're willing to give it.  It's a fair amount.  I would delete the 24 GB sda5 partition, then, if you want a separate "/home" partition (I'm ambivalent about it personally), I would create around a 10 GB "/" (root) partition, then use the remaining space for your "/home" partition.  Both should be formatted as ext4 (default for Lucid), or ext3 if stability is particularly important (I've never had any problem with ext4, myself).

You can do all the above in the installer, or you can boot to the Live CD desktop and do some or all of it with GParted, if you prefer.  Just be sure, when going through the Manual partitioning option in the installer, to mark the mount points of any partition you create with the installer or otherwise.  The mount point for swap doesn't have to be marked.

Alternatively, if you decide you don't need a separate "/home" partition, it simplifies things.  Go to the Live CD desktop, launch GParted, delete both sda5 *_and_* sda6, close GParted, then start the installation.  When you get to the disk partitioning screen, select "Install to largest contiguous free space," and it will automatically create the partitions in the free space within the Extended partition.

If you use this method, it's important to delete the original swap partition as well, since another one will automatically be created.  If you don't delete the original, you'll end up with two and will have to go back and delete one, then expand your root directory to take up the rest of the space.

---

