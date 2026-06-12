---
title: "I accidently deleted windows...whoops..need it back"
date: 2011-02-21
forum: New to Ubuntu
---

### Post by ghosticmp19 on 2011-02-21
So I had originally had my computer dual booted with windows and Ubuntu, but the Ubuntu partition just stopped working all of a sudden. So I ran the new Ubuntu boot cd and accidentally allocated Ubuntu to my whole hard drive. Doh! Its no big loss I've been meaning to do a full restore anyways.I'm not familiar with partitioning and reinstalling windows within Ubuntu...usually I do it the other way around. I have the windows cd and the key . Please help :)

---

### Post by deconstrained on 2011-02-21
Nope.

Some of the data might still be intact, in 1's and 0's on the surface of the disk, but the partition table/superblock/filesystem is set up to completely ignore it, and for all you know the installation of Ubuntu wrote over at least some of it. Thus, you'd need some kind of professional data recovery tool to get it back.

The cardinal rule of repartitioning a hard drive and installing something new on it is: back up the data first.

If you want to reinstall, however, and didn't really value any of the documents/data on the old Windows installation...You have the Windows restore disk, so that shouldn't be too difficult.

Edit: you cannot install Windows within Ubuntu, unless you mean running a virtual machine inside Linux.

To dual-boot what you can do is this:
1. Install windows first, using some of the disk space
2. Install Ubuntu on the rest of the hard drive
That way grub will be installed to the MBR after windows does its thing, and you won't have to boot to the live disk a second time to re-install grub.

---

### Post by ghosticmp19 on 2011-02-21
Yes thanks I don't need the data back I need windows back. I just need to reinstall a windows partition from ubuntu. All the files and stuff I know are lost. I just ussually install windows and then the ubuntu cd lets me partition. Windows doesn't have a partitioner on the cd so how do I partition my hard drive and install windows from ubuntu without having to uninstall ubuntu again and reinstall windows and then reinstall ubuntu and partition...sounds like a lot of unnecessary steps.

---

### Post by deconstrained on 2011-02-21
Windows should have a partitioner! Maybe selecting "advanced" during the installation will eventually lead you to the option of selecting how much hard drive space you want to use, and that's where you do it.

Believe me, it'll be easier to install Windows first, because once you have Windows set up, Ubuntu's installer will recognize the preexisting OS installation and auto-configure grub to add an entry for it so that you will have the option of starting either operating system when you power on your computer.

If you're at your wits' end and can't find out how to use less than the full hard drive for Windows, you can still install Windows first, and use gparted on an Ubuntu live disk to non-destructively resize the Windows partition. And hopefully, the live disk includes ntfsprogs...

---

### Post by ghosticmp19 on 2011-02-21
Ok I guess I should stop being so lazy and just do it that way haha. Thanks for the tips.:D

---

### Post by Sef on 2011-02-21
If you want to get Windows back, check out [Test Disk]("http://www.cgsecurity.org/wiki/TestDisk").

From the site:

> TestDisk is powerful free data recovery software! It was primarily designed to help recover lost partitions and/or make non-booting disks bootable again when these symptoms are caused by faulty software, certain types of viruses or human error (such as accidentally deleting a Partition Table). Partition table recovery using TestDisk is really easy.


---

