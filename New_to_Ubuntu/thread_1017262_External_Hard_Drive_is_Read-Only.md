---
title: "External Hard Drive is Read-Only"
date: 2008-12-20
forum: New to Ubuntu
---

### Post by NukeLuke on 2008-12-20
how do i fix that, dear liza?

---

### Post by handydan918 on 2008-12-20
> **NukeLuke said:**
> how do i fix that, dear liza?

There's a hole in the fstab, Dear liza. 

Post the output of ```
cat /etc/fstab
```
and we can take a crack at it.

---

### Post by NukeLuke on 2008-12-20
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=3c05a4ab-ce8b-45a4-8a77-526ab797d970 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=4b0a6d01-8f89-4811-a907-2c5ce3cfb815 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

---

### Post by albinootje on 2008-12-20
Is it NTFS formatted or FAT32 ?

---

### Post by NukeLuke on 2008-12-20
NTFS, i believe.
i was running it on a Mac. ( I know nothing to the third power, so bear with me)

---

### Post by albinootje on 2008-12-20
> **NukeLuke said:**
> NTFS, i believe.
i was running it on a Mac. ( I know nothing to the third power, so bear with me)

Please connect the usb-disk, and install ntfs-config and ntfsprogs.
```

sudo apt-get install ntfs-config ntfsprogs
sudo fdisk -l

```

---

### Post by NukeLuke on 2008-12-20
It's connected on firewire, will that be an issue?

---

### Post by handydan918 on 2008-12-20
It appears the better command would be ```
mount
```

This should show all mounted filesystems.


If the drive was used on a mac, it may have been formatted to hpfs....

---

### Post by NukeLuke on 2008-12-20
apparently not:
Disk /dev/sda: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x30000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           7       56196   de  Dell Utility
/dev/sda2               8        1313    10485760    7  HPFS/NTFS
/dev/sda3   *        1313       16717   123730469    7  HPFS/NTFS
/dev/sda4           16718       30394   109860502+   5  Extended
/dev/sda5           16718       29833   105354238+  83  Linux
/dev/sda6           29834       30394     4506201   82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table

---

### Post by handydan918 on 2008-12-20
Have you installed the ntfs utilities as another poster recommended?
If you have, then I hope you didn't have anything on that drive. It's either corrupted, or perhaps it's indeed an hfs file system.

---

### Post by NukeLuke on 2008-12-20
it must be hfs, cuz i installed that and it's still working fine, it just insists that it's read-only.
i'm able to burn stuff off of it, but not erase the stuff after i'm done with it.

---

### Post by albinootje on 2008-12-20
> **NukeLuke said:**
> NTFS, i believe.
i was running it on a Mac. ( I know nothing to the third power, so bear with me)

Any chance to try it again in that Mac ?

---

### Post by NukeLuke on 2008-12-20
sure, but it has always worked fine on the Mac.
anything i should do when i get it on the Mac?

---

### Post by albinootje on 2008-12-20
> **NukeLuke said:**
> sure, but it has always worked fine on the Mac.
anything i should do when i get it on the Mac?

I don't remember whether Linux can read/write HFS and HFS+
Can it ?
But the output from fdisk is .. weird :(

---

### Post by NukeLuke on 2008-12-20
could it have something to do with the fact that i started loading a 2nd version of Ubuntu on my main drive but stopped it in the middle?:(

---

### Post by handydan918 on 2008-12-20
> **albinootje said:**
> I don't remember whether Linux can read/write HFS and HFS+
Can it ?
But the output from fdisk is .. weird :(

[This post]("http://www.linuxquestions.org/questions/linux-software-2/mounting-hfs-volumes-under-linux-521189/") seems to cover it pretty well.

There does seem to be a beta driver available [here]("http://www.ardistech.com/hfsplus/hfsplus-20040216.tar.gz").

---

### Post by NukeLuke on 2008-12-20
ok, so can some one walk me through (real slow, as i am a dunderhead) how to use this "+" feature?
PS: the system says the drive is mounted, it just won't write to it...

---

### Post by albinootje on 2008-12-20
> **NukeLuke said:**
> ok, so can some one walk me through (real slow, as i am a dunderhead) how to use this "+" feature?
PS: the system says the drive is mounted, it just won't write to it...

A poster in the linked page (by handydan918) reads :

> 
I've had RWX support on HFS+ in Fedora 6-8, Slackware 10.2-12, Debian 4.0, and Ubuntu 6.06. I do remember that it refused to write to HFS+ when Journaling was enabled. So, I had to use a mac to disable journaling in the iPod.

So.. apparently you have to disable the journal on that disk in a Mac to be able to read/write mount it in Ubuntu as a first requirement.

---

### Post by handydan918 on 2008-12-20
Keeping firmly in mind that all this is BETA. If you break your system, the warranty department will let you keep the pieces.

---

### Post by ruru on 2008-12-24
If this is an HFS+ volume, simply use the Disk Utility under OSX to switch off journalling. Linux can handle HFS fine, but with journalling the volumes will mount read-only.

I suspect this will solve your problem...

---

### Post by mapes12 on 2008-12-24
> **NukeLuke said:**
> apparently not:
Disk /dev/sda: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x30000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           7       56196   de  Dell Utility
/dev/sda2               8        1313    10485760    7  HPFS/NTFS
/dev/sda3   *        1313       16717   123730469    7  HPFS/NTFS
/dev/sda4           16718       30394   109860502+   5  Extended
/dev/sda5           16718       29833   105354238+  83  Linux
/dev/sda6           29834       30394     4506201   82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table

Now you have plugged it in Ubu has detected it (it's the one called **sdb** in the above output) but it does not have a valid partition on it that Linux recognises. On the basis that the external HDD does not contain any data that you need to keep then it will need to be formatted. You can install Gparted from Synaptic to do the formatting. Select your drive from the **Devices** menu in Gparted then set up the partition(s) however you want them. 

When the drive has been formatted then it will be usable but you may have to "mount" it so that you can access it. If need need any help with mounting then post a separate thread. But it's easy to do.

---

