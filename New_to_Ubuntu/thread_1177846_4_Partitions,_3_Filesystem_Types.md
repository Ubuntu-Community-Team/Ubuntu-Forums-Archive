---
title: "4 Partitions, 3 Filesystem Types?"
date: 2009-06-03
forum: New to Ubuntu
---

### Post by Xylar Wasterend on 2009-06-03
Today I received a new IDE HDD, and had it planned to use Xubuntu 9.04 minimal and Windows XP, dual-booted. Installed a minimal base-system install of Xubuntu 9.04, but before doing so used an old version of gparted to make 4 partitions off this 80 GB drive, header being msdos:

Partition 1: ubuntu (ext4)
Partition 2: entertainment (ext3), using [http://www.fs-driver.org/](http://www.fs-driver.org/) to access this from XP.
Partition 3: windows xp (ntfs)
Partition 4: windows xp utilities (ntfs) (since above partition is small)

Was going to go with ext3 for the start partition, however upon seeing ext4 decided to use that instead. **Is it that it's a no-no for 3 different filesystems on a single HD that causes the lower 3 partitions to never mount?** Have gnome-mount, xfce-mount, and mount installed, and while gparted (newest version) can change the lesser 3 partitions, error messages always pop up saying unable to mount while it applies said changes.

/newbie.

---

### Post by nhasian on 2009-06-03
there shouldnt be a problem with using different filesystems at once.  Did I understand you correctly saying you bought a new 80 Gig hard disk?  I didnt know they made those anymore.  If you split that up by four partitions you arnt giving yourself much space to work with.  why does XP need two separate partitions?  Also if you used an old version of gparted, does it even have ext4 support? I thought that only came out recently with 9.04

---

### Post by skyjacker on 2009-06-03
> **Xylar Wasterend said:**
> Today I received a new IDE HDD, and had it planned to use Xubuntu 9.04 minimal and Windows XP, dual-booted. Installed a minimal base-system install of Xubuntu 9.04, but before doing so used an old version of gparted to make 4 partitions off this 80 GB drive, header being msdos:

Partition 1: ubuntu (ext4)
Partition 2: entertainment (ext3), using [http://www.fs-driver.org/](http://www.fs-driver.org/) to access this from XP.
Partition 3: windows xp (ntfs)
Partition 4: windows xp utilities (ntfs) (since above partition is small)

Was going to go with ext3 for the start partition, however upon seeing ext4 decided to use that instead. **Is it that it's a no-no for 3 different filesystems on a single HD that causes the lower 3 partitions to never mount?** Have gnome-mount, xfce-mount, and mount installed, and while gparted (newest version) can change the lesser 3 partitions, error messages always pop up saying unable to mount while it applies said changes.

/newbie. I believe you had better install xp first, then partion for ubuntu. I've read that this is the way to go, but have never started out any other way, so can't say for sure.

---

