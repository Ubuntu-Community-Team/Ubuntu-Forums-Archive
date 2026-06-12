---
title: "Sharing files between XP and Ubuntu"
date: 2010-09-22
forum: New to Ubuntu
---

### Post by slyJ on 2010-09-22
I'm trying to make it as accessible as possible right now. I know Ubuntu is read-only, so I save my files on a designated folder on my Windows partition (I have a dual-boot). In order to access my shortcut on ubuntu that links to XP, i have to manually click on the windows xp disk drive in places. Is there anyway to automatically have the disk drive open, so i could just click on my shortcut when i login?

I've already tried saving open applications for the bootup, but it's not an application, so yeah.

---

### Post by migs73 on 2010-09-22
Try this; [https://help.ubuntu.com/community/AutomaticallyMountPartitions](https://help.ubuntu.com/community/AutomaticallyMountPartitions)

---

### Post by adit on 2010-09-22
You need to install the package ntfs-config 
_[http://launchpadlibrarian.net/38731593/ntfs-config_1.0.1-3ubuntu5_i386.deb](http://launchpadlibrarian.net/38731593/ntfs-config_1.0.1-3ubuntu5_i386.deb)_

---

### Post by migs73 on 2010-09-22
> **adit said:**
> You need to install the package ntfs-config 
_[http://launchpadlibrarian.net/38731593/ntfs-config_1.0.1-3ubuntu5_i386.deb](http://launchpadlibrarian.net/38731593/ntfs-config_1.0.1-3ubuntu5_i386.deb)_
I think the OP already has this (assuming it allows the ntfs read/write via linux) as they can currently access the files, just require the windows partition to mount on log in.

---

### Post by Mark Phelps on 2010-09-23
My personal experience is that it is a BAD idea to automount MS Windows OS partitions.  I used to do that and started encountering forced CHKDSKs in MS Windows immediately.  They got so bad that it happened on every boot into MS Windows.

Not wanting to risk file system corruption anymore, I removed the entries from fstab and resorted to using Places to mount the MS Windows partitions.  More work, but less problems in the long run.

---

### Post by vbartolotta on 2010-09-23
slyJ,

I have a dual boot laptop Ubuntu 9.10 / Windows 7. Ubuntu mounts the Windows (NTFS) volume on boot up. No problems in months of use.

Here's my fstab:[INDENT]# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=469ba2cb-adec-488e-aa03-cf01b975ae2d /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=8f28162b-03f5-4b87-b48a-26fe305b7316 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
**[COLOR=Blue]/dev/sda3    /media/ACER    ntfs    defaults    0    0[/COLOR]**
[/INDENT]The last line is the one I added to mount the Windows volume.

Hope that helps.

---

