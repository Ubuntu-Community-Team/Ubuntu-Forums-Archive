---
title: "Just installed Ubuntu, can't find Windows"
date: 2009-08-04
forum: New to Ubuntu
---

### Post by nekcmo on 2009-08-04
I'm brand new to this.  I had Windows 7 running on a raid 0.  I partitioned that drive in Windows.  I was then seing three drive while in Windows...The Windows partition, the partition that I had just made, and a back up hard drive (Drive C, D, and E)  When I went to install Ubuntu, it didn't see either C or D drive.  Instead it saw another hard drive that I use to back up files (Drive E).  So I went ahead and let Ubuntu partition that drive and install to it.  Now when I boot my machine it goes straight into Ubuntu, and when I go into the bootloader while it's loading up it doesn't show my Windows install.

When I look at the hard drives (using Ubuntu's verion of Windows Explorer), Ubuntu is only seeing the drive it installed to, and the other partition on that drive.  It's not seeing the raid drive at all.

Looking at another thread asking if he/she was using the 32bit or 64bit version, I looked and I'm using the 32 bit version (I wanted the 64 bit version).  Not sure if that has to do with anything, but thought I'd throw it out there.

How do I get back into Windows?

Thanks! :D

---

### Post by Muscovy on 2009-08-04
You made a partition, did you install to it? There's options to install to a partition, make a new one, and wipe everything else, which is ticked by default.

  Edit: To check that you have Windows, open Places, and hopefully it has X GB Media listed.

---

### Post by halitech on 2009-08-04
open a terminal and post the reuslts of
```
sudo fdisk -l
```thats a lowercase L in case you are typing it in and not copying and pasting.

---

### Post by nekcmo on 2009-08-04
> **halitech said:**
> open a terminal and post the reuslts

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x050ca6e0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       12158    97658111    7  HPFS/NTFS
/dev/sda2           12159       60801   390724897+   5  Extended
/dev/sda5           12159       59578   380901118+  83  Linux
/dev/sda6           59579       60801     9823716   82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4a216b20

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sdb2              13      119052   956181504    7  HPFS/NTFS
/dev/sdb3          119052      121602    20478976    7  HPFS/NTFS

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x04e907e7

Disk /dev/sdc doesn't contain a valid partition table
craig@craig-desktop:~$

---

### Post by nekcmo on 2009-08-04
> **Muscovy said:**
> You made a partition, did you install to it? There's options to install to a partition, make a new one, and wipe everything else, which is ticked by default.

  Edit: To check that you have Windows, open Places, and hopefully it has X GB Media listed.

I did make a new partition and install to it.  It did not wipe the other partition as my backup files are accessable with Ubuntu (music and crap).

When I made that partition it was showing I had 500 gigs to work with.  My raid 0 drive has 1000 gigs, and my backup drive is another 500.  Three drives total, each with 500 gig.    It was only seeing the backup drive, and not the raid drive.

My Windows installation is on the raid drive, but Ubuntu isn't seeing it.

---

### Post by halitech on 2009-08-04
ok, I see 3 drives listed with the secondary slave (if its IDE /dev/sdc) not having any partition tables and Ubuntu being installed on /dev/sda6. You also have /dev/sda1 and /dev/sdb1 both being set as bootable. The Windows Drive E seems to be /dev/sda based on where you say Ubuntu was installed to.

Are the drives IDE or SATA? (just to clarify)

---

### Post by nekcmo on 2009-08-04
> **halitech said:**
> ok, I see 3 drives listed with the secondary slave (if its IDE /dev/sdc) not having any partition tables and Ubuntu being installed on /dev/sda6. You also have /dev/sda1 and /dev/sdb1 both being set as bootable. The Windows Drive E seems to be /dev/sda based on where you say Ubuntu was installed to.

Are the drives IDE or SATA? (just to clarify)

Think I was wrong about the drive letters.  Figured it would just go in order after C.  I wrote down the drive that I wanted to install to...drive F  But there was no drive F :D  Didn't know Ubuntu didn't use the whole C, D, F type system.

The drives are SATA.  I just tried putting in my Windows disk and it didn't see a Windows installation.  But, I need to install the raid driver (such a pain)...I'll do that now and see what it shows me.

Edit:  Not sure I'm going to be able to find the RAID driver I used.  Tons of them to choose from. Still working on it...

---

### Post by nekcmo on 2009-08-04
Wow...this really sucks.  I went into the BIOS to make sure it was still configured for a RAID drive.  So far so good.  Then happened to notice when it scanned the disks that it wasn't showing my RAID.  Entered the RAID setup, and sure enough they are now showing as "non-raid disks".  So, I would have to set them back up, wiping all the data anyway.

Well, I got to say my first time trying Linux, this isn't very encouraging.  Why or how it destoyed my RAID array I'll never know.  Now I have to reinstall Windows and every other program I had.  This is going to take hours.  Half tempted to just stop using a RAID drive altogether.  Tired of having to drag out the old floppy drive whenever there's a problem (last computer burned MOBO's every six months).

Really frustrated right now

---

### Post by nothingspecial on 2009-08-04
See [[COLOR="Magenta"]here[/COLOR]]("https://help.ubuntu.com/community/FakeRaidHowto")

---

