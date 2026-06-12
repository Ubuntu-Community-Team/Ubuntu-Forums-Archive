---
title: "Partitioned External HD - Can't Read Superblock"
date: 2011-03-21
forum: New to Ubuntu
---

### Post by Jurawks on 2011-03-21
Hi, I'm having a problem mounting my external hard drive. It's partitioned to be able to read both MS-Dos and MAC. However, I've been having problems with mounting my MS-Dos partition. When I plug it in, I get this message: 

Error mounting: mount: /dev/sdb2: can't read superblock

Help, anyone? 

(I'm an epic tech-noob, btw. ^^;)

---

### Post by taseedorf on 2011-03-21
:) We're all noobs, to some degree.

I need a little more info.  Can you tell me what is in /etc/fstab

terminal, type... gedit /etc/fstab and post the output...

Make sure you are specifying the correct partition type when mounting, that is usually the problem....

---

### Post by Jurawks on 2011-03-21
Thanks for taking the time. I really appreciate it. =)

This is what popped out:

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=a8f9b493-a031-48c2-b653-7220443fa88e /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=1c1112f6-b980-4b0d-a973-09ede96500db none            swap    sw              0       0

---

### Post by oldfred on 2011-03-22
I would try running chkdsk from a windows repair Cd.

or from Ubuntu :
You might need dosfstools and ntfsprogs as well.
sudo /sbin/fsck.vfat -V <the fat32 device>

XP CHKDSK
chkdsk drive /p /r
The chkdsk command checks the specified drive and repairs or recovers the drive if the drive requires it. The command also marks any bad sectors and it recovers readable information. Run chkdsk several times, until no more errors are detected.
chkdsk c: /r
You can use the following options:
/p Does an exhaustive check of the drive and corrects any errors.
/r Locates bad sectors and recovers readable information.
Note If you specify the /r option, the /p option is implied. When you specify the chkdsk command without arguments, the command checks the current drive with no options in effect. 
[http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true)

If chkdsk has errors:
[http://support.microsoft.com/kb/247575](http://support.microsoft.com/kb/247575)

---

### Post by Jurawks on 2011-03-22
This is what I got:

dosfsck 3.0.9, 31 Jan 2010, FAT32, LFN
There are differences between boot sector and its backup.
Differences: (offset:original/backup)
  65:01/00
1) Copy original to backup
2) Copy backup to original
3) No action
?

A friend of mine managed to fix my hard drive using some Mac application so that it can be opened. However, the autoplay is gone. Not that I'm complaining. I'm wondering if there's a way to fix it.

---

### Post by Jurawks on 2011-03-23
Oh but all my Word files are rendered read-only. Am I missing something here?

---

### Post by oldfred on 2011-03-23
How are you opening the work files and from Ubuntu, windows, or Mac?

In Ubuntu you have to set ownership & permissions as you mount a FAT or NTFS partition as those windows partitions do not support Linux ownership & permissions. If you copy a file from Ubuntu to FAT & back, it has lost its ownership & permissions. 

In windows, if you copy to a CD you also convert to read only even in windows & usually have to reset it when copying back.

Understanding fstab
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

Ownership and permissions of vfat / ntfs are set at the time of mounting. This is often a source of confusion.
[http://www.psychocats.net/ubuntu/mountwindowsfstab](http://www.psychocats.net/ubuntu/mountwindowsfstab)
HOWTO: Mount NTFS partitions with specific ownership/permissions 
[http://ubuntuforums.org/showthread.php?t=1604251](http://ubuntuforums.org/showthread.php?t=1604251)

---

