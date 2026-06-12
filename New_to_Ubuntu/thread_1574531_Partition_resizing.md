---
title: "Partition resizing"
date: 2010-09-14
forum: New to Ubuntu
---

### Post by donescamillo on 2010-09-14
Hi,

I need to do some partition moving/resizing and I need some advice. Here is my configuration:
Ubuntu 10.04, 4 partitions:
1. 100Mb for Win7
2. WIn 7
3. Linux ext3
4. NTFS for data
I dont have a CD ROM, only hard drives and the Internet
I tried to do it under Windows, but:
1. Esaeus free wont work with ext3 partitions
2. PartitionWizardHome had a bug 
3. Paragon Free wont let me move the ext3 around (lack of functionality maybe)
4. Gparted wont let me move the Linux partition as it is where the system is running.

Is there a way to tell GParted what I want and set it run at boot or something like this?

Thanks

---

### Post by TonKi on 2010-09-14
Boot with an Ubuntu LiveCD gParted is afair on there.
Or download and burn a gparted iso from [gparted.sf.net]("http://gparted.sourceforge.net/livecd.php")

---

### Post by perspectoff on 2010-09-14
> **donescamillo said:**
> Hi,

I need to do some partition moving/resizing and I need some advice. Here is my configuration:
Ubuntu 10.04, 4 partitions:
1. 100Mb for Win7
2. WIn 7
3. Linux ext3
4. NTFS for data
I dont have a CD ROM, only hard drives and the Internet
I tried to do it under Windows, but:
1. Esaeus free wont work with ext3 partitions
2. PartitionWizardHome had a bug 
3. Paragon Free wont let me move the ext3 around (lack of functionality maybe)
4. Gparted wont let me move the Linux partition as it is where the system is running.

Is there a way to tell GParted what I want and set it run at boot or something like this?

Thanks

I think you can put the GParted LiveCD on a USB drive and boot from that.

PS, IMO the best partition Manager for Windows is Perfect Disk (paid or trial version), since it works with almost all filesystems and is the only I found that can shrink the Windows 7 partition properly.

---

### Post by Mark Phelps on 2010-09-14
> **donescamillo said:**
> Is there a way to tell GParted what I want and set it run at boot or something like this?

Just make sure you do NOT use GParted to move/shrink your Win7 partition.  Use the Win7 Disk Management utility, or the app referenced in a previous post, to do this.  Using GParted to do this runs the risk of corrupting the filesystem and rendering Win7 unbootable.

---

### Post by drs305 on 2010-09-14
If you want to use Gparted, don't have a CD-ROM and don't want to use or don't have a USB, you can boot to the Gparted ISO via Grub 2. Here is a link on how to do that:
[ISO Booting with Grub 2]("http://ubuntuforums.org/showthread.php?t=1549847")

One of the *menuentry* examples is for Gparted. I'd agree with Mark that using Windows utilities to resize Windows partitions is probably a good idea.

---

### Post by bsalem on 2010-09-14
Probably a good idea to dfrag that Windows Partition BEFORE you resize it unless you know for certain that Win 7 does that automatically.

---

