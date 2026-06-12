---
title: "Unable to mount hibernated drive E:"
date: 2009-01-05
forum: New to Ubuntu
---

### Post by rahimamiah on 2009-01-05
I have a data drive “drive E:” created by windows xp so that I could mount the drive and share the data when I use ubuntu 8.10. However, when the windows xp drive C: in hibernated mode, I am not able to mount the drive to have access to the data in drive E: from linux.

Do you know how to gain access to drive E: while the drive C: in hibernated mode?

---

### Post by tarps87 on 2009-01-05
You maybe able to for mount it but I wouldn't suggest it. xp is locking the drive, this also can happen if you don't safely unmount an external drive from windows.
I would suggest shutting windows down so it releases the drive or using a network drive.
Someone else maybe able to suggest another solution but your best bet is to shutdown windows

---

### Post by beattyml1 on 2009-01-05
I'm somewhat of a n00b myself but if E: is formatted as ntfs you might try formatting it as fat32, I believe that this should work because of the fact that a ntfs drive must be properly ejected to be used by another operating system while fat32 does not have to be properly ejected.  Fat32 also is often a better option for a shared drive anyway because it is able to be both read from and written to by both operating systems without any additional work.  


if you don't know how to do this it can be done in either windows or ubuntu 
in ubuntu:
you can either use synaptic to install a package called gparted
and then go to system->Administration->Partion Editor
or you can type the following commands into the terminal

```
sudo apt-get install gparted
```
```
sudo gparted
```

find the drive that looks like it is your E: drive and right click, if it is mounted unmount it, otherwise go to 'format to->fat32'
then apply your changes

*Note you probably know this but this will overwrite the data on your E: drive, so make sure to back it up first

---

### Post by bodhi.zazen on 2009-01-05
Linux does not use letters to refer to partitions.

To mount a partition you need to make a mount point and then either manually mount the partition or make an entry in /etc/fstab.

Mounting and permissions depends on the file system:

_Windows:_ [Psychocats Mount windows ]("http://www.psychocats.net/ubuntu/mountwindows")
For read-write: 
[LIST=1]
[*]vfat (FAT) use dmask=027,fmask=137[INDENT]more permissive permissions : dmask=000,fmask=111[/INDENT]
[*]ntfs use [ntfs-3g]("http://ubuntuforums.org/showthread.php?t=217009") and a fstab entry something like this:
```
/dev/hda1  /media/windows  ntfs-3g  defaults  0  0
```
[*]An alternate is ntfs-config. ntfs-config uses ntfs-3g to mount windows partitions via a gui :)[INDENT][http://ubuntuforums.org/showthread.php?t=337970](http://ubuntuforums.org/showthread.php?t=337970)[/INDENT]
[/LIST]

---

### Post by beattyml1 on 2009-01-05
.

---

