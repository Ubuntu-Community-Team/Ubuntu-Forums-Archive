---
title: "Mounting jfs partitions ?"
date: 2010-01-18
forum: New to Ubuntu
---

### Post by j002 on 2010-01-18
I have a PC and an Ubuntu 6.06 live CD (don't bother telling me to upgrade).

I want to mount some 'jfs' partitions on the live CD so I can transfer the contents to another hard drive because the installation doesn't work.
However, I don't know what the settings/contents for the /etc/fstab file are for partitions of the 'jfs' type, only for ext2 and vfat.
Does anyone know ?

---

### Post by falconindy on 2010-01-18
jfs is type jfs. The rest is pretty much the same as any other FS.

FYI, 'cat /proc/filesystems' will give you a list of valid filesystems. 'man mount' will give you a list of FS specific mounting options.

---

### Post by bodhi.zazen on 2010-01-18
first, you do not need to edit fstab on the live CD, simply use the mount command.

If you want to use fstab, the option for jfs is, well, jfs :twisted:

/dev/sda1 /mnt/tmp jfs defaults 0 0

---

### Post by j002 on 2010-01-19
Yeah well I tried putting in :

/dev/hda2 /media/C jfs defaults 0 0 

(after mkdir /media/C, after "fdisk -l" the partition was on /dev/hda2)

and it won't recognise it (after "mount -a"), it says something starting with :

Wrong FS type or... 


What I have is a Fedora install, which has a small boot partition (ext2 - 200kB) and two other partitions (jfs).  There is no root partition like Ubuntu.
When I run the rescue mode in Fedora it says 'no linux partitions', yet they show on Gparted and "fdisk -l".

It will mount the boot partition, which only has vmlinuz (the boot loader ?) and another compacted file.

My brother set up the PC, and installed a whole lot of things, it was working then.

---

### Post by bodhi.zazen on 2010-01-19
First, change "jfs" to "auto"

Second, if it is Fedora partition, is LVM ?

If all that fails, try fsck

```
fsck -y /dev/hda2
```

---

### Post by j002 on 2010-01-20
Okay I'll try that.

---

### Post by j002 on 2010-01-24
Well after the fsck command, Fedora would load - it's magic !

---

