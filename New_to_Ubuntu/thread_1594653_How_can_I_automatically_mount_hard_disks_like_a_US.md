---
title: "How can I automatically mount hard disks like a USB drive..."
date: 2010-10-12
forum: New to Ubuntu
---

### Post by MadRush on 2010-10-12
I have a machine with a bunch of removable racks.  Where I am now is, I can automatically mount the disks by UUID to already established folders (e.g. /mnt/sdc1)

I want the system to mount them like it does USB drives; I want a folder to pop up in /media named according to the disk label. 

Reasons why I want to do it this way:
1. I dont want the system to throw a hissy fit because it expects to see a drive which is statically listed in /etc/fstab.  It's a headless system, btw.
2.  I want to be able to 'ls /media' to quickly know what disks are in the system and mounted, rather than 'mount' and go blind looking at lines and lines of ...
'/dev/sdf1 on /mnt/sdf1 type ext3 (rw)'
'/dev/sdf2 on /mnt/sdf2 type ext3 (rw)'
'/dev/sdf5 on /mnt/sdf5 type ext3 (rw)'
'/dev/sdf6 on /mnt/sdf6 type ext3 (rw)'
'/dev/sdf7 on /mnt/sdf7 type ext3 (rw)'
'/dev/sdh1 on /mnt/sdh1 type ext3 (rw)'
..ad nauseam. the machine has four removable racks and two internals disks... you get the idea.

---

### Post by MadRush on 2010-12-04
really? nobody?

---

### Post by The Small Human on 2010-12-04
Try in BIOS! Select the drive to boot first.
Good luck :)

---

### Post by searchfgold6789 on 2010-12-04
I think you may be looking for software called mountall.
It automatically mounts everything at startup when installed.

---

### Post by MadRush on 2011-01-18
mountall is definitely not what I'm looking for.  

What I want is to automatically mount a disk upon boot, but not complain if it's not there.  I have a hunch the nature of fstab doesn't allow this... 

I don't want to have to authenticate myself to access the disk... it's kind of pointless, it should be able to be done 

I think I found the right mount option to use in fstab, though it may not apply because its boot time and it may be governed by other rules...
```
nofail Do not report errors for this device if it does not exist. 
```

---

### Post by MadRush on 2011-01-18
yeah I just tried adding nofail into /etc/fstab to no avail.  i need an expert here... surely this kind of thing isn't a rare problem

---

### Post by j002 on 2011-01-18
Well I have system with IDE drives, and if I disconnect one or both, the system doesn't care whether they are there or not.
The (auto-mount ?) icon just doesn't show on the desktop, and with
fdisk -a

It just doesn't show the unconnected drives.

I have the drives mounted DOS style at:
/media/C
/media/D

---

