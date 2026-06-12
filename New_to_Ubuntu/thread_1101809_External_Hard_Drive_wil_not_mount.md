---
title: "External Hard Drive wil not mount"
date: 2009-03-20
forum: New to Ubuntu
---

### Post by Pondoro on 2009-03-20
I installed Ubuntu GNU/Linux on an old PC. I have a Seagate external hard drive that plugs in via USB. My windows machines see it but the Linux machine does not. If I plug a USB memory drive containing jpg files into the same USB port the Linux machine picks it right up. 

Any hints? I am a total noob.

---

### Post by cariboo on 2009-03-20
Could you open an Applications-->Accessories-->Terminal and type:

```
dmesg | tail -n10
```

Just after you have plugged the drive in and paste the output in your next post. The above command will print out the last 10 lines of the command dmesg.

Jim

---

### Post by mvalviar on 2009-03-20
Try plugging your external hard drive to your windows machine then "Safely remove hardware", then power down cleanly. Your ubuntu box should now be able to mount your external drive.

---

### Post by kansasnoob on 2009-03-20
Try simply installing pmount from synaptic or go to terminal and:

```
sudo apt-get install pmount
```

Simple description of pmount:

> pmount is a wrapper around the standard mount program which permits normal
users to mount removable devices without a matching /etc/fstab entry. This
provides a robust basis for automounting frameworks like GNOME's Utopia
project and confines the amount of code that runs as root to a minimum.

This package also contains a wrapper "pmount-hal" which reads some
information like device labels and mount options from hal and passes
them to pmount. Install the package "hal" if you want to use this
feature.

If a LUKS capable cryptsetup package is installed, pmount is able to
transparently mount encrypted volumes.

Canonical does not provide updates for pmount. Some updates may be provided by the Ubuntu community.

Restart afterwards!

---

### Post by Pondoro on 2009-03-20
mike@mike-desktop:~$ dmesg | tail -n10
[10280.820782] sd 7:0:0:0: [sdb] Write Protect is off
[10280.820798] sd 7:0:0:0: [sdb] Mode Sense: 10 00 00 00
[10280.820802] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[10280.823614] sd 7:0:0:0: [sdb] 156301488 512-byte hardware sectors (80026 MB)
[10280.825519] sd 7:0:0:0: [sdb] Write Protect is off
[10280.825532] sd 7:0:0:0: [sdb] Mode Sense: 10 00 00 00
[10280.825536] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[10280.827517]  sdb: sdb1
[10280.836180] sd 7:0:0:0: [sdb] Attached SCSI disk
[10280.836678] sd 7:0:0:0: Attached scsi generic sg2 type 0

---

### Post by Pondoro on 2009-03-20
> **mvalviar said:**
> Try plugging your external hard drive to your windows machine then "Safely remove hardware", then power down cleanly. Your ubuntu box should now be able to mount your external drive.

I tried this and it did not help. Was I supposed to power down the computer 1st or the external drive 1st? I did the "Safely Remove Hardware" bit and then shut down the hard drive.

---

### Post by bagle on 2009-03-20
check your external device on a windows machine and check if the file system is fat32 or nfts. if its nfts it is  windows only and you will have to reformat the drive to fat32. if its a fat device use the "force" comand on the comand line while you are mounting it on the command line.it will try to force the device to mount.

---

### Post by Pondoro on 2009-03-21
I checked the hard drive, it is FAT32, so that should not be the problem.

---

