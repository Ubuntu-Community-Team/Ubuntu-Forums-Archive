---
title: "Having Trouble Setting up and Booting With Partitions"
date: 2011-02-02
forum: New to Ubuntu
---

### Post by marl30 on 2011-02-02
I formatted my entire HDD and is in the process of reinstalling Ubuntu. I have always used different partitions, one for the system and the other for backup. My backup partition was usually NTFS. It had been that way since I deleted Windows and went with Ubuntu.

 I've decided I want my backup to EXT4 just as the system partition. However, whenever I click next during the setup, it says I need to choose a mount point or the partition will not show, so I decided to go with /home.  After the installation completed and I rebooted, Ubuntu did not boot. 

I just figured it had something to do with the option I chose at the mount point. All I want is to be able to have a separate partition with the EXT file system that is able to boot with the system partition without conflict. 

Please help me through this.

---

### Post by ajgreeny on 2011-02-02
If there is nothing important on the disk at the moment, I suggest you start again and install one more time.

Choose manual partitioning at that stage and make an ext4 partition of about 10GB with mount point / (root), a separate partition of about 4Gb formatted as swap, no mount point needed, and all the rest as ext4 with /home as the mount point.

Your problem was that you set /home as the mount point for an ntfs formatted partition, which is not possible as ntfs will not allow enabling of the linux file permissions.

---

### Post by LanguidLegend on 2011-02-02
So I am having a similar issue.

I'm looking at my partition table ("Allocate drive space") and it is arranged:
```

/dev/sda
[INDENT]/dev/sda1 (type:ntfs) (size:12888MB)
/dev/sda2 (type:ntfs) (size:35MB)
/dev/sda3 (type:ntfs) (size:307074MB)
[/INDENT]
```

So the Ubuntu [[COLOR="Blue"]dual-boot installation guide[/COLOR]]("https://help.ubuntu.com/8.04/switching/installing-partitioning.html") is telling me to first resize my Windows partition by right-clicking the /dev/sda3 and selecting Resize, but I don't see that option. Instead, I see Change, Delete, and Revert.
So if I click Change or just double click the /dev/sda3, the "Edit partition" window comes up and I am to enter a value for "New partition size in megabytes", then select something for "Use as" (i.e.:FAT32 file system, ntfs, swap area, do not use the partition).

I have three questions:
1)is the Change option same as the Resize option?,
2)what is the recommended amount of space I should allocate for each new partition? (I tried 10GB for the root partition but I got an error saying "The size entered is too small"), and
3)what do I select for "Use as" for the 3 new partitions (root/swap/home)?

---

### Post by marl30 on 2011-02-02
> **ajgreeny said:**
> If there is nothing important on the disk at the moment, I suggest you start again and install one more time.

Choose manual partitioning at that stage and make an ext4 partition of about 10GB with mount point / (root), a separate partition of about 4Gb formatted as swap, no mount point needed, and all the rest as ext4 with /home as the mount point.

Your problem was that you set /home as the mount point for an ntfs formatted partition, which is not possible as ntfs will not allow enabling of the linux file permissions.

I just followed what you said, and when I boot up the root directory has 5.7gb of free space remaining and I haven't even installed any application as yet. Wouldn't I need a larger root than 10gb?

---

### Post by Bucky Ball on 2011-02-02
> **LanguidLegend said:**
> So I am having a similar issue.

I'm looking at my partition table ("Allocate drive space") and it is arranged:
```

/dev/sda[INDENT]/dev/sda1 (type:ntfs) (size:12888MB)
/dev/sda2 (type:ntfs) (size:35MB)
/dev/sda3 (type:ntfs) (size:307074MB)
[/INDENT]
```So the Ubuntu [[COLOR=Blue]dual-boot installation guide[/COLOR]]("https://help.ubuntu.com/8.04/switching/installing-partitioning.html") is telling me to first resize my Windows partition by right-clicking the /dev/sda3 and selecting Resize, but I don't see that option. Instead, I see Change, Delete, and Revert.
So if I click Change or just double click the /dev/sda3, the "Edit partition" window comes up and I am to enter a value for "New partition size in megabytes", then select something for "Use as" (i.e.:FAT32 file system, ntfs, swap area, do not use the partition).

I have three questions:
1)is the Change option same as the Resize option?,
2)what is the recommended amount of space I should allocate for each new partition? (I tried 10GB for the root partition but I got an error saying "The size entered is too small"), and
3)what do I select for "Use as" for the 3 new partitions (root/swap/home)?

Please post a separate thread with a descriptive thread title and as much detail as you can give. You will get more (and more specific) help. We are trying to resolve other issues here and it is confusing when someone jumps in with a bunch of unrelated questions. ;)

---

### Post by Bucky Ball on 2011-02-02
> **marl30 said:**
> I just followed what you said, and when I boot up the root directory has 5.7gb of free space remaining and I haven't even installed any application as yet. Wouldn't I need a larger root than 10gb?

I would suggest:

/ = 20Gb which is plenty (I generally use 15Gb for /)
/home = big as you like
/swap = 2Gb or the same size as your installed RAM if you are intending to hibernate.

;)

---

### Post by marl30 on 2011-02-02
> **LanguidLegend said:**
> So I am having a similar issue.

I'm looking at my partition table ("Allocate drive space") and it is arranged:
```

/dev/sda[INDENT]/dev/sda1 (type:ntfs) (size:12888MB)
/dev/sda2 (type:ntfs) (size:35MB)
/dev/sda3 (type:ntfs) (size:307074MB)
[/INDENT]
```So the Ubuntu [[COLOR=Blue]dual-boot installation guide[/COLOR]]("https://help.ubuntu.com/8.04/switching/installing-partitioning.html") is telling me to first resize my Windows partition by right-clicking the /dev/sda3 and selecting Resize, but I don't see that option. Instead, I see Change, Delete, and Revert.
So if I click Change or just double click the /dev/sda3, the "Edit partition" window comes up and I am to enter a value for "New partition size in megabytes", then select something for "Use as" (i.e.:FAT32 file system, ntfs, swap area, do not use the partition).

I have three questions:
1)is the Change option same as the Resize option?,
2)what is the recommended amount of space I should allocate for each new partition? (I tried 10GB for the root partition but I got an error saying "The size entered is too small"), and
3)what do I select for "Use as" for the 3 new partitions (root/swap/home)?

in your case, you need to partition your drive according to the space you wish to allocate to Ubuntu. 20GB is not a bad place to start. For swap partition, the rule of thumb is to always make it twice the size of your physical ram. However, in the case where your ram amount is small, going with 1 to 2 GB should be ok.

Swap will create its own mount point. Usually I mount the EXT4 partition to /.

I would like to know the benefit of putting the root and home onto a separate partition?

---

### Post by marl30 on 2011-02-02
> **Bucky Ball said:**
> I would suggest:

/ = 20Gb which is plenty (I generally use 15Gb for /)
/home = big as you like
/swap = 2Gb or the same size as your installed RAM if you are intending to hibernate.

;)

I guess I'll have to reinstall another time. I'm going to use like about 20GB, since I have probably 100 programs that I usually install, including large ones like Rosegarden, and games like Urban Terror. Or maybe there is a way to resize it without reinstalling?

---

### Post by Bucky Ball on 2011-02-02
> **marl30 said:**
> Or maybe there is a way to resize it without reinstalling?

Yes there is. Boot from the LiveCD, System>Admin>Gparted, make sure the partitions you want to resize are unmounted (they should already be as you are running from the CD) by right clicking and 'unmount'. Then right click the partition and 'Resize'. Simple. ;)

---

### Post by marl30 on 2011-02-02
> **Bucky Ball said:**
> Yes there is. Boot from the LiveCD, System>Admin>Gparted, make sure the partitions you want to resize are unmounted (they should already be as you are running from the CD) by right clicking and 'unmount'. Then right click the partition and 'Resize'. Simple. ;)

I'm currently on the LiveCD. I have one question before proceeding. What's the benefit of putting root and home on their own partitions?

---

### Post by YesWeCan on 2011-02-02
> **marl30 said:**
> I'm currently on the LiveCD. I have one question before proceeding. What's the benefit of putting root and home on their own partitions?
I thought you said you want a separate backup partition...but everyone seems to be ignoring you.

If you want a separate backup partition you have to decide how big it needs to be and where it should be mounted in the Ubuntu filesystem. Personally, I prefer "/home/backup". This would be your mount point. You could also use "/mnt/backup" or even "/media/backup" if you want a desktop icon to appear automatically for it.

Whether you have /home in its own partition is not of huge importance. Some people like to protect the OS's disk space from filling up. Some people make a partition for root and then a second, LVM partition which can be easily split into LVM volumes with easier resizing. Don't lose sleep over it. Keep it simple.

Using a Live CD and Gparted, you could start afresh. Erase the disk. Then make a single ext4 partition for your backups, located either at the start or end of the disk. Then do the Ubuntu install into the free space. Either during the install (if you can get your head around the installer) you can specify mounting the backup partition OR ignore it during the install and set up the mounting afterwards. It is quite easy.

---

### Post by marl30 on 2011-02-02
> **YesWeCan said:**
> I thought you said you want a separate backup partition...but everyone seems to be ignoring you.

If you want a separate backup partition you have to decide how big it needs to be and where it should be mounted in the Ubuntu filesystem. Personally, I prefer "/home/backup". This would be your mount point. You could also use "/mnt/backup" or even "/media/backup" if you want a desktop icon to appear automatically for it.

Whether you have /home in its own partition is not of huge importance. Some people like to protect the OS's disk space from filling up. Some people make a partition for root and then a second, LVM partition which can be easily split into LVM volumes with easier resizing. Don't lose sleep over it. Keep it simple.

Using a Live CD and Gparted, you could start afresh. Erase the disk. Then make a single ext4 partition for your backups, located either at the start or end of the disk. Then do the Ubuntu install into the free space. Either during the install (if you can get your head around the installer) you can specify mounting the backup partition OR ignore it during the install and set up the mounting afterwards. It is quite easy.

I was having issues resizing the hard drive, as it was only allowing me to shrink the smaller partition, so I went ahead, reformated and use a larger partition for root.  And yeah, I noticed that the responses were not exactly what I was looking for. Was wondering if I wasn't being clear enough. Anyhow I decided to go with the instructions because I'm only backing up videos and music, since everything else is backup online. Besides, it's easy to place them in the home folder and be able to preserve them even it the system crashed. But thanks for your suggestion. I'll give it a test run in VirtualBox when I have everything set up and the spear time.

---

### Post by Bucky Ball on 2011-02-02
If you screw your OS install all your data is on a separate partition. If worse comes to worse you can reinstall and you personal data and settings are still /home. Also easier for backups. 

It is a no brainer. ;)

---

### Post by srs5694 on 2011-02-02
Another point: Backups on the same physical disk as the originals are not very safe. If the disk breaks physically, or even if certain bad enough software errors or human errors occur, your backups will be wiped out at the same time as the originals. Backups are best placed on a separate physical disk (a removable or external drive, ideally) or on some non-disk medium (DVDs, Blu-Ray discs, tapes, etc.). If you're *really* serious about backups, you'll make multiple copies and store some of them off site.

---

### Post by marl30 on 2011-02-03
> **srs5694 said:**
> Another point: Backups on the same physical disk as the originals are not very safe. If the disk breaks physically, or even if certain bad enough software errors or human errors occur, your backups will be wiped out at the same time as the originals. Backups are best placed on a separate physical disk (a removable or external drive, ideally) or on some non-disk medium (DVDs, Blu-Ray discs, tapes, etc.). If you're *really* serious about backups, you'll make multiple copies and store some of them off site.
Well, these stuff are just what I have ripped from CDs/DVDs. If any thing serious should happen, the files that would give me the most setbacks are saved stored online as well, plus I have other offline copies of them saved on other medias.  Losing those stored on my computer would only cause me the inconvenience of having to once again rip, organize, add album cover, editing, etc.

---

### Post by Bucky Ball on 2011-02-03
> **marl30 said:**
> ...  Losing those stored on my computer would only cause me the inconvenience of having to once again rip, organize, add album cover, editing, etc.

I ain't got that kind of time, but if you have, cool ... ;)

---

