---
title: "Change Partition size?"
date: 2010-07-04
forum: New to Ubuntu
---

### Post by losferwords on 2010-07-04
Okay so I've installed Ubuntu on my netbook alongside the original Windows XP.

The only problem is that when I tried to give the Ubuntu install as much disk space as possible, and thought it would have 70gb (of a possible 76gb hard drive) it has in actual fact partitioned it to have 6gb of space... or so it seems.

Is there any way for me to change the partition size within Ubuntu or will I have to install again?

Although it's confused me more now, because it seems like I can write/save things to the C:\ which I thought would be reserved for Windows and the D:\ for Ubuntu (which has been partitioned as 6gb - all already used with existing documents it imported from Windows).

---

### Post by Saint_ on 2010-07-04
In your terminal, type: sudo gparted
From there you'll be able to resize your partitions accordingly. Also yes, you have access to any and all partitions on the hard drive disk

---

### Post by JC Cheloven on 2010-07-04
I'm affraid Gparted will not be able to resize the partition in use by the system (also gparted don't get installed by default in the hard disk). But you can defragment the ntfs partition and then choose:

1) Boot from live pendrive (the one you used for installing), run system-admin-gparted, shrink the xp partition & apply, extend the ubuntu partition accordingly & apply.
Notes.- a) mark "round to cylinders" in gparted to avoid messing the ntfs filesystem. Even so, problems with the ntfs partiton may occur. Playing with partitions is always risky. b) Moving the ubuntu filesystem may take a long time, comparable to that of reinstalling!

2) Srhink the ntfs partition from within windows. You may have to use provided tools in xp for that, or some third party software (can't remember). Then either expand the ubuntu filesystem as described above, or reinstall.

---

### Post by -kg- on 2010-07-04
> I'm affraid Gparted will not be able to resize the partition in use by the system

+1 - You can't perform partitioning operations on a mounted partition, and if you're using GParted from an installation on the hard drive, the partition cannot be unmounted.

> 2) Srhink the ntfs partition from within windows. You may have to use provided tools in xp for that, or some third party software (can't remember). Then either expand the ubuntu filesystem as described above, or reinstall. 

+1 - You have a tool within XP called Disk Management.  With it, you will be able to shrink your Windows partition (called "Resizing"), the amount depending on how full the partition is.  You'll want to leave sufficient room...say, 20% of the partition in free space.  You will want to defrag your Windows partition before shrinking it.

Since this is a brand new installation, you might want to consider just re-installing it.  It will be a lot easier in the long run.  You'll want to boot onto the Live USB Stick, run GParted from it, and delete the original Ubuntu partitions (unless you have critical information in them, but being brand new...).  Then run the installer again and select "Install using largest contiguous free space" in the partitioning portion of the installation process.

The reason you want to delete the original Ubuntu Partitions is that, unless you select "Manual" partitioning and mark the mount points of those partitions (after expanding them to fill the free space), it will install in new partitions created in the free space, leaving the original partitions in place and wasting space.  Deleting these original partitions will free up the 6 GB they take up and allow the installer to install in the full space you created by shrinking the Windows partition.  Just make sure you only delete the Ubuntu partitions and *not* the Windows partition!

For more information on partitioning operations and consideration, read the pages at the link in my signature block.

---

### Post by -kg- on 2010-07-04
Oops!  Just re-read:

> Although it's confused me more now, because it seems like I can write/save things to the C:\ which I thought would be reserved for Windows and the D:\ for Ubuntu (which has been partitioned as 6gb - all already used with existing documents it imported from Windows).

D:\ drive for Ubuntu?  Is this by any chance a WUBI installation, or are you just using Windows terminology for sda(2/3/4...etc)?

---

### Post by losferwords on 2010-07-05
The netbook I have is a Samsung NC10 with 160GB hard drive (split as C:\ and D:\ with equal size) I was keeping Windows XP and having Ubuntu too rather than commit to Ubuntu and then decide I didn't like it.

Nice to know I can still access all the stuff from Windows through Ubuntu.

I'll reinstall Ubuntu from the USB stick I created, I've done nothing with it yet.

---

### Post by nothingspecial on 2010-07-05
6 gig should be fine for Ubuntu. If you are dual booting why have stuff saved to your Ubuntu Partition that you can`t access from windows?

/dev/sda1             6.8G  4.3G  2.2G  66% /

That`s my Ubuntu partition - 6.8 gigs only 66% used.

---

### Post by losferwords on 2010-07-05
> **nothingspecial said:**
> 6 gig should be fine for Ubuntu. If you are dual booting why have stuff saved to your Ubuntu Partition that you can`t access from windows?

/dev/sda1             6.8G  4.3G  2.2G  66% /

That`s my Ubuntu partition - 6.8 gigs only 66% used.
Good point but in the long run I may need more space for music, files, etc I'm basically owning a netbook with 160GB of space and only having access to about 90GB of it.

---

### Post by nothingspecial on 2010-07-05
Well, if I were you, and bearing in mind I know nothing of windows, I would leave the Ubuntu install as it is, have one small partition for windows and one giant one for data accessible by both systems.

That is how all my computer are set up (except that they dual boot linux distros).

---

### Post by losferwords on 2010-07-05
> **nothingspecial said:**
> Well, if I were you, and bearing in mind I know nothing of windows, I would leave the Ubuntu install as it is, have one small partition for windows and one giant one for data accessible by both systems.

That is how all my computer are set up (except that they dual boot linux distros).
I'll have a go at doing that later then.

It's just when I went into Windows after the Ubuntu install it immediately popped up with a message saying that the D:\ drive was full.

---

### Post by VraiChevalier on 2010-07-05
> **losferwords said:**
> I'll have a go at doing that later then.

It's just when I went into Windows after the Ubuntu install it immediately popped up with a message saying that the D:\ drive was full.

Are you sure the D:\ partition has Ubuntu on it? Do the sizes of the C:\ and D:\ partitions add up to the total capacity of the hard drive? I mention this because the last time I checked Microsoft Windows OS would not recognize a partition formatted for an Ubuntu install. Is the D:\ partition perhaps a "Restore" partition? I would use GParted or a similar tool to check the disk layout. Boot a "Live" cd or usb image and run it. You could also check the contents of the D:\ partition when in Windows.

---

### Post by losferwords on 2010-07-05
> **VraiChevalier said:**
> Are you sure the D:\ partition has Ubuntu on it? Do the sizes of the C:\ and D:\ partitions add up to the total capacity of the hard drive? I mention this because the last time I checked Microsoft Windows OS would not recognize a partition formatted for an Ubuntu install. Is the D:\ partition perhaps a "Restore" partition? I would use GParted or a similar tool to check the disk layout. Boot a "Live" cd or usb image and run it. You could also check the contents of the D:\ partition when in Windows.
The netbook itself was already set up as having C:\ and D:\ as far as I was aware I was putting Ubuntu onto the existing D:\ which got partitioned as 6GB.

So when I went into Windows it realised there was not enough space on it (200mb free) as it went from being 76GB to 6GB and recommended that I free up some space.

When I started Windows up it said it needed to check the status of the disks and made some changes which it did automatically and took about 10 seconds to do.

---

### Post by VraiChevalier on 2010-07-05
> **losferwords said:**
> The netbook itself was already set up as having C:\ and D:\ as far as I was aware I was putting Ubuntu onto the existing D:\ which got partitioned as 6GB.

That D:\ partition sure does look like a Windows "Restore" partition. Again, you could boot into Windows or boot a Live cd (usb) and actually look and see what is on the partition. Also, you could start up MS Windows and check to see exactly which file format the D:\ partition is. As mentioned previously, it sounds like Ubuntu did not actually get installed. I know from personal experience that the Ubuntu installer will take only a minimal amount of disk space for itself. Watch the partitioner closely and increase the partition size to what you want.

---

### Post by losferwords on 2010-07-05
Actually it looks like it had installed it correctly.

Ubuntu shows "file system: 76gb", "file system: 6.7gb" and then just "file system" which shows 50gb of free space.

I guess it's going take a while to get used to Ubuntu lol

---

