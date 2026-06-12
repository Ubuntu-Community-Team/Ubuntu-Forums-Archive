---
title: "Mounting Corrupted NTFS Partition"
date: 2011-03-02
forum: New to Ubuntu
---

### Post by arnold.pietersen on 2011-03-02
Hi

I am trying to help a friend whose NTFS partition has been corrupted in one way or another.

I have booted up his laptop with an Ubuntu Live CD. The following appears when I type: fdisk -l

/dev/sda1            HPFS/NTFS
/dev/sda2            HPFS/NTFS
/dev/sda3            HPFS/NTFS

When I click on the hard drive in Places, the following message comes up:

Unable to mount 93 GB Filesystem
DBus error org.gtk.Private.RemoteVolumeMonitor.Failed: An operation is already pending

How do I mount the partition?

Any help will be appreciated.

ARNOLD

---

### Post by gerowen on 2011-03-02
```
sudo mount -t ntfs-3g   /dev/source_partition   /path_to/mount_point
```

---

### Post by anglican on 2011-03-02
> **arnold.pietersen said:**
> Hi

I am trying to help a friend whose NTFS partition has been corrupted in one way or another.

I have booted up his laptop with an Ubuntu Live CD. The following appears when I type: fdisk -l

/dev/sda1            HPFS/NTFS
/dev/sda2            HPFS/NTFS
/dev/sda3            HPFS/NTFS

When I click on the hard drive in Places, the following message comes up:

Unable to mount 93 GB Filesystem
DBus error org.gtk.Private.RemoteVolumeMonitor.Failed: An operation is already pending

How do I mount the partition?

Any help will be appreciated.

ARNOLDDepending on what's gone wrong, ntfsfix might help, it's in the ntfsprogs package - which may or may not be installed by default, if not then ```
sudo apt-get install ntfsprogs
``` will get it. You can then try
```
sudo ntfsfix /dev/sda[1-3]
```which might help. (Obviously check the partitions one at a time). Do this if mounting still doesn't work.

H

---

### Post by Mark Phelps on 2011-03-02
While ntfsfix might fix the problem, it's more likely that it won't. The ntfsfix app is NOT a Linux version of MS Windows CHKDSK; instead, it can only repair some very minor problems.

IF, as you say, the partition is corrupted, your best best is to try to fix that using CHKDSK on an MS Windows PC.

---

### Post by srs5694 on 2011-03-02
> **Mark Phelps said:**
> IF, as you say, the partition is corrupted, your best best is to try to fix that using CHKDSK on an MS Windows PC.

+1

Linux lacks good NTFS repair tools. If you lack the ability to boot into Windows, check [here](http://neosmart.net/blog/2009/windows-7-system-repair-discs/) for some downloadable Windows 7 repair discs. Of course, if the disk is from a Windows computer, you should be able to use Windows' "safe mode" to run these checks, although that doesn't always work.

If by chance your friend is using NTFS on a non-Windows computer, I advise migrating away from NTFS, for the reasons that should be apparent now: You can't fix NTFS errors without Windows! Of course, you'll need to fix the errors this once before you can back up or move the data for such a conversion.

---

### Post by anglican on 2011-03-02
> **Mark Phelps said:**
> While ntfsfix might fix the problem, it's more likely that it won't. The ntfsfix app is NOT a Linux version of MS Windows CHKDSK; instead, it can only repair some very minor problems.

IF, as you say, the partition is corrupted, your best best is to try to fix that using CHKDSK on an MS Windows PC.Yes that's all quite right, but if you look at the original post the computer won't boot and he's used a live CD. ntfsfix is **very** limited, but it's better than nothing. I agree his best bet is to use MS tools to try and rectify the problem, but being a linux user (which I came to from "real" unix) I can't advise him how. Are there Windows live CD's for this sort of occasion?

H

---

### Post by lkraemer on 2011-03-02
Are you sure it isn't a MBR Problem or a Windows Registry Problem, that looks as if it is a NTFS Problem?  Read all the References below before
you do anything to the NTFS Partition.......

Why not start with a Windows UBCD and go from there?
[http://www.ubcd4win.com/](http://www.ubcd4win.com/)

Also Ref:
[http://ubuntuforums.org/showthread.php?t=622828](http://ubuntuforums.org/showthread.php?t=622828)
[http://ubuntuforums.org/showthread.php?t=624943](http://ubuntuforums.org/showthread.php?t=624943)
[http://tech.icrontic.com/articles/repair_windows_xp/](http://tech.icrontic.com/articles/repair_windows_xp/)
[http://michaelstevenstech.com/XPrepairinstall.htm](http://michaelstevenstech.com/XPrepairinstall.htm)
[http://forums.majorgeeks.com/showthread.php?t=35407](http://forums.majorgeeks.com/showthread.php?t=35407)
[http://aumha.org/a/stop.htm](http://aumha.org/a/stop.htm)

These should help determine what the problem is.....

lk

---

### Post by jeremyjjbrown on 2011-03-02
I sounds like the "in use" marker was left checked in the NTFS filesystem so linux thinks the drive still mounted in another system. This is a common problem, I've seen it many times.

The first thing you should do is mount the disk in windows and properly eject the drive or shutdown the computer. If that is the issue when you remount to linux the drive will work.

Always apply the simplest solution first ;)

---

### Post by Mark Phelps on 2011-03-03
> **anglican said:**
> Are there Windows live CD's for this sort of occasion? 

Sorry, no.  MS doesn't want folks walking around with "portable" versions of their OS's.

However, that said, there is the Hiren's Boot CD.  You need to Google for it, download and burn it to CD, and then boot from it. It contains a lot of MS Windows disk utilities.  There's bound to be something on there that can repair the NTFS problem.

---

