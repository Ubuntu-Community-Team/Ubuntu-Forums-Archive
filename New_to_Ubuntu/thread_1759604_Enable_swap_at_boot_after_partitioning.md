---
title: "Enable swap at boot after partitioning?"
date: 2011-05-15
forum: New to Ubuntu
---

### Post by MrTiKi on 2011-05-15
Hello all, Complete linux noob here. Been using 10.04 netbook remix for about 2 weeks now.
Anyways I had to partion my drive to add swap space and now swap doesn't autoenable at boot. I've read various threads on here and tried all of them with no luck. The latest one  I tried is this [http://ubuntuforums.org/showthread.php?t=589586th](http://ubuntuforums.org/showthread.php?t=589586th) 

I get command not found , I input the command to match my swap partition
 Anyhelp would be great

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       12922   103794941    7  HPFS/NTFS
/dev/sda2           30265       30401     1100452+  82  Linux swap / Solaris
/dev/sda3           13055       15013    15728640    f  W95 Ext'd (LBA)
/dev/sda4           15013       30264   122508316   83  Linux
/dev/sda5           13055       15013    15728608+  1b  Hidden W95 FAT32


# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda3       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda4 during installation
UUID=2b2ff8a4-5450-41fb-8884-58f4d6f72dab none            swap    sw              0       0

---

### Post by jtarin on 2011-05-15
> **MrTiKi said:**
> Hello all, Complete linux noob here. Been using 10.04 netbook remix for about 2 weeks now.
Anyways I had to partion my drive to add swap space and now swap doesn't autoenable at boot. I've read various threads on here and tried all of them with no luck. The latest one  I tried is this [http://ubuntuforums.org/showthread.php?t=589586th](http://ubuntuforums.org/showthread.php?t=589586th) 

I get command not found , I input the command to match my swap partition
 Anyhelp would be great

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       12922   103794941    7  HPFS/NTFS
/dev/sda2           30265       30401     1100452+  82  Linux swap / Solaris
/dev/sda3           13055       15013    15728640    f  W95 Ext'd (LBA)
/dev/sda4           15013       30264   122508316   83  Linux
/dev/sda5           13055       15013    15728608+  1b  Hidden W95 FAT32


# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda3       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda4 during installation
UUID=2b2ff8a4-5450-41fb-8884-58f4d6f72dab none            swap    sw              0       0

Read what you posted:
```
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
``````
# swap was on /dev/sda4 during installation
UUID=2b2ff8a4-5450-41fb-8884-58f4d6f72dab none            swap    sw              0       0
```You have swap listed as```
/dev/sda2           30265       30401     1100452+  82  Linux swap / Solaris
```

---

### Post by MrTiKi on 2011-05-16
I've only been on ubuntu/linux for 2 weeks. I have no idea of what you are trying to tell me.

---

### Post by oldfred on 2011-05-16
Use this to see the UUID of sda2.

```
sudo blkid
```

That should give you the UUID of sda2 which is now your swap and you need to replace the UUID in your fstab with the correct UUID for sda2 not sda4. Only replace UUID, copy & paste.

```
cp /etc/fstab /etc/fstab.backup
gksudo gedit /etc/fstab

```

Once changed run this to make sure you have not made an editing error as you may not be able to reboot if fstab has errors.

```
sudo mount -a
```

---

