---
title: "How to change the volume label (disk name)"
date: 2009-04-01
forum: New to Ubuntu
---

### Post by Paddy Landau on 2009-04-01
Having created a partition and formatted it, how do I give that partition a name?

That's the name that shows up on Windows as the disk name, and on Ubuntu as the mount name (e.g. /media/MyNiceDisk).

On Windows Vista, I'd right-click the drive, select Properties, and fill in the first box under "General".

I've searched and searched for how to do this on Linux, and haven't managed to find the answer yet.

---

### Post by Junkieman on 2009-04-01
Hi Paddy, I assume this is a linux file system type (ext/ext3)? 

Get the device filename:

```
sudo fdisk -l
```

The output will look similiar to this:
```
Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8a020c1c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60801   488384001   83  Linux

```

/dev/sdb1 is my partition, yours will be different. **Make sure you look at the right one!**

Then change your label with this command, substituting sdb1 for YOUR device:

```
sudo e2label /dev/sdb1 "mydiskname"
```

---

### Post by kanikilu on 2009-04-01
You can also do this in gparted, just right-click the partition you want to change and choose "Label".

---

### Post by mcduck on 2009-04-01
What file system are you using on that partition? The tool you need depends on the file system. For Ext2/Ext3 you can use the "e2label" mentioned in previous post but for others you need different tools..

---

### Post by SunnyRabbiera on 2009-04-01
The best way I found is to use pysdm, its not included by default though.
But be careful with it, this can damage your drives if you touch certain settings.

---

### Post by stchman on 2009-04-01
> **Junkieman said:**
> Hi Paddy, I assume this is a linux file system type (ext/ext3)? 

Get the device filename:

```
sudo fdisk -l
```

The output will look similiar to this:
```
Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8a020c1c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60801   488384001   83  Linux

```

/dev/sdb1 is my partition, yours will be different. **Make sure you look at the right one!**

Then change your label with this command, substituting sdb1 for YOUR device:

```
sudo e2label /dev/sdb1 "mydiskname"
```

Will this command work for FAT32 volumes as well?

---

### Post by mcduck on 2009-04-01
> **stchman said:**
> Will this command work for FAT32 volumes as well?

No, it won't. e2label is for Ext2/ext3 only. For FAT partitions the tool to use is "mlabel"

```
sudo mlabel -i /dev/yourpartition ::new-label
```

I don't think mlabel is installed by default, and if I remember right it wasn't available on it's own but instead as part of some bigger package that includes tools for FAT file systems.

edit: mlabel is part of the mtools-package. And here's a guide for labelling different file systems on Ubuntu: [https://help.ubuntu.com/community/RenameUSBDrive]("https://help.ubuntu.com/community/RenameUSBDrive")

---

### Post by kansasnoob on 2009-04-01
I learned to do it differently. Look at meierfra's posts here:

[http://ubuntuforums.org/showthread.php?t=526008](http://ubuntuforums.org/showthread.php?t=526008)

That's not to say anyone else is wrong. That's just the way I've learned to do it.

---

### Post by mcduck on 2009-04-01
> **kansasnoob said:**
> I learned to do it differently. Look at meierfra's posts here:

[http://ubuntuforums.org/showthread.php?t=526008](http://ubuntuforums.org/showthread.php?t=526008)

That's not to say anyone else is wrong. That's just the way I've learned to do it.

That doesn't label the partition. It only changes the name the partition is mounted with on the system where you make the configuration (and thus is useless for removable drives as the setting is only on your computer and has no effect when using the drive on other machines).

But sure, if it's an internal drive and you only access it with Ubuntu then that's just as good way to change it's name as labeling is.

---

### Post by WorldTripping on 2009-04-01
For FAT you need to install mtools

```
sudo apt-get install mtools
```

From [http://www.gnu.org/software/mtools/]("http://www.gnu.org/software/mtools/")

> This directory contains mtools. Mtools is a collection of utilities to access MS-DOS disks from Unix without mounting them. It supports Win'95 style long file names, OS/2 Xdf disks and 2m disks (store up to 1992k on a high density 3 1/2 disk).



---

### Post by WorldTripping on 2009-04-01
> **kansasnoob said:**
> I learned to do it differently. Look at meierfra's posts here:

[http://ubuntuforums.org/showthread.php?t=526008](http://ubuntuforums.org/showthread.php?t=526008)

That's not to say anyone else is wrong. That's just the way I've learned to do it.

It's not wrong, just a different way of doing things.

Personally I never liked messing with fstab :) and I think that mtools is soo much easier.

---

### Post by Junkieman on 2009-04-01
> **stchman said:**
> Will this command work for FAT32 volumes as well?

No, but as the previous posters said you can install mtools. You can also use the 'label' command on a win pc in the command prompt. I think the command, where e: is your drive

```
label e: newlabel
```

---

### Post by Paddy Landau on 2009-04-01
Wow, I didn't realise there were so many ways!

Thank you everyone for answering.

I was curious about both ext3 and NTFS partitions.

I use gparted, so a simple right-click would be, well, simple. I didn't realise that I could do it there.

I don't have access to my computer just now, so I'll test tomorrow. If it can't be done, then no big deal, I'll do it on Windows. I'll let you know what happens.

---

### Post by Paddy Landau on 2009-04-02
> **kanikilu said:**
> You can also do this in gparted, just right-click the partition you want to change and choose "Label".
Unfortunately, I don't see a "Label" on the right-click menu for the partition. I have gparted version 0.3.5 from Synaptic Manager. I see that the latest version is 0.4.3. Perhaps that's the problem for me.

---

### Post by Paddy Landau on 2009-04-02
> **Junkieman said:**
> Then change your label with this command, substituting sdb1 for YOUR device:

```
sudo e2label /dev/sdb1 "mydiskname"
```

That worked great for the ext3 partitions, thank you.

For the NTFS partition, I did it on a Windows machine.

---

### Post by egalvan on 2009-04-02
> **Paddy Landau said:**
>  I don't see a **"Label" on the right-click menu** for the partition. I have gparted version 0.3.5 from Synaptic Manager. I see that the latest version is 0.4.3. Perhaps that's the problem for me.

gparted version 0.3.5 does not have that "right-click" option...
it's under the "Device" tab...

but be careful!

It warns you that the data will be lost...
It WILL erase the partition when you change the label!
I experimented on a fresh install, and the partition WAS emptied.

Later versions don't have this problem.

I use partedmagic, and gparted LiveCD.

---

### Post by egalvan on 2009-04-02
> **mcduck said:**
> That doesn't label the partition. It only changes the name the partition is mounted with on the system where you make the configuration (and thus **is useless for removable drives as the setting is only on your computer **and has no effect when using the drive on other machines).



It's not totally "useless" for removable dirves...
it makes for interesting "customizations"... :)

---

