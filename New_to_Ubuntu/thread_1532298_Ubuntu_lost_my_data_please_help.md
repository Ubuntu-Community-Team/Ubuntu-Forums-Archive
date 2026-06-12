---
title: "Ubuntu lost my data please help"
date: 2010-07-16
forum: New to Ubuntu
---

### Post by drsuave on 2010-07-16
Lo all

I am a Computer Tech and have been for a few years now, working with Windows. Last week I tried Ubuntu 10.04 on my machine, to see if it was any good. Eventually, due to Windows rotting my brain, I made the switch back to XP, only to discover that all my data is gone and my HDD is less than half the size it used to be. Below contains exactly what I did, step by step. Any help would be much appreciated.

I have a 36gb WD Raptor Hdd and a 320gb WD drive for storage of data. I had XP installed on the Raptor. I did a clean install of Ubuntu onto the Raptor with a format and all.

After booting into ubuntu, I discovered that the Ubuntu installer had formatted my Raptor but installed itself onto the 320gb HDD. Wierd but ok, I can deal with that. From 'Computer' in Ubuntu I can access all my data on my 320gb HDD, and it says its 320gb too. Cool.

After using Ubuntu for a bit I decided I wanted XP back, so used XP setup to format the Raptor and install to that, with the 320gb drive unplugged.

After booting into XP with the 320gb HDD connected, it reports that the drive is now a 133gb drive, with an unknown unformatted partition, and would I like to format now.

Oh ****.

I shut down and unplugged both hard drives, and installed Ubuntu again to an old 40gb HDD I had lying around. After plugging the 320gb HDD back in, I can access the current Ubuntu system and the old ubuntu file system on what is reported as a 320gb HDD in 'Computer'. All my data is gonskies and I am at a loss as to what to do next. Even Partition Magic reports the 320gb HDD as being a 133gb volume with a 'BAD' partition.

Any help would be much appreciated, as the data that has been lost is priceless and irreplaceable.

---

### Post by nothingspecial on 2010-07-16
Boot up the live cd and mount all the partitions on all the drives.

Can you see any data?

What file systems is the partition that had the data on it now.

It sounds like you have formatted over your data during one of the windows or ubuntu installations

Sorry and no offence, but important data should be backed up. Priceless and irreplaceable data should be backed up twice, and no where near a computer you are installing operating systems on.

You may have some luck with testdisk

Edit  Sorry meant to put a link for testdisk, here it is 

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

and whatever you do, do not try to write anything to the partition your data was on

---

### Post by digitalcitizenx on 2010-07-16
:roll:

---

### Post by restorator on 2010-07-16
You said you reinstalled XP and reformatted. If your XP install disk is not at least Service Pack 2 it will only "see" and use 120gb of disk space (which reads as your 133), no matter how big the drive is. You can safely install XP, then upgrade to SP2 and 3 and the 320 should read as a 320 again. But you may not be able to read the linux filesystem you installed with Ubuntu on the 320 without a utility. 

> I did a clean install of Ubuntu onto the Raptor with a **format** and all.

> I decided I wanted XP back, s**o used XP setup to format** the Raptor and install to that, with the 320gb drive unplugged.
Oh and yes all your data is gone on the raptor of course as you did a few formats. As mentioned above you *may* be able to salvage some data with testdisk or other utilities if you are looking for data there.

---

### Post by eriktheblu on 2010-07-16
Sounds to me like you might have done a side by side install on your 320GB disk. This is one of the default install options in Ubuntu.

Basically what it would have done is resize the NTFS (typical XP file system) partition (likely the entire 320 GB) and created by default EXT4 and swap for Ubuntu. Linux does not really like NTFS so it would not install on the same partition.

Windows does not recognize EXT4 partitions, which is why it is reported as unformatted.

Chances are, your files are still there (on the 320; the 36 as has been mentioned is likely done for), just the partition is smaller.

For a good visual of what your hard drives are doing, boot from the Ubuntu live (install) CD and open Gparted (system>> administration I believe)

You can use the live CD to move any files from your home folder in the Ubuntu partitions to your Windows partitions if needed.

If you're done with Ubuntu, you may use Gparted again to delete the EXT* and swap partitions, and also expand the NTFS partition as needed.

---

### Post by Rubi1200 on 2010-07-16
If you can, use the LiveCD and go into GParted; then take a screenshot and post it here so we can "see" what is going on.

I agree with eriktheblu that you have probably done a side-by-side install.

Next time, you should try asking BEFORE installing.

Even if you are > a Computer Tech and have been for a few years now you could have saved yourself a lot of time and headaches by asking people here on the forums for some advice.

I have seen plenty of posts from people who asked FIRST; they are not the ones who then usually come back and say "oops, I think I may have messed things up."

---

### Post by digitalcitizenx on 2010-07-16
Download and burn a copy of gparted live CD

[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

and use that to partition, discover where your drives are and what's on them, then when you are finished reinstall your OS of choice.

As for recovering deleted data, the best bet would be to take the drives to a professional and see if they can determine if there is any way to save the data.

Consider this a learning experience. The money you spend will be a "Learning Tax".

---

### Post by llawwehttam on 2010-07-16
XP sp1 has trouble with larger HDD sizes. You need sp2 or 3 to be able to see the full disk. Personally I would say you have completely lost the data on both disks. It may be partially recoverable but unlikely you will get much back.

For the future, if you install an OS on one drive and use the other for data, I tend to unplug all drives except the one I am installing on just to make sure. I have had windows muck up installs because of that in the past.

---

