---
title: "e2label finds no magic - I can't re-label"
date: 2009-03-25
forum: New to Ubuntu
---

### Post by Mark_in_Hollywood on 2009-03-25
Using GParted in LiveCD, I re-formatted a 256 meg memory stick (USB). I gave it an ms-dos label, but selected ext2 as the file format. Works fine.

On re-boot, Intrepid found the device and named it:

**255.0 MB Media**

I tried to use e2label, but got nowhere as I had to know the device by a name I cannot find or can't understand if I do "find" it.

I tried the tricks at this post

RenameUSBDrive
[https://help.ubuntu.com/community/RenameUSBDrive](https://help.ubuntu.com/community/RenameUSBDrive)

but when I:

sudo e2label <device>

and look for the device, I find nothing but confusion. In my /dev/disk
there are 4 more folders:

by-id
by-label
by-path
by-uuid

and I have NO idea of how to complete the command line after e2label /

I want to name it jumpdrive-1 or something I can find in the filesystem so I can use rsync to run backups.

Anybody know how to rename or relabel devices?

---

### Post by nothingspecial on 2009-03-25
```
sudo fdisk -l
``` will tell you. Look for the /dev/sd? that matches the size of your device.

Then unmount it ```
 umount /dev/sd?
```

Then ```
sudo e2label /dev/sd? jumpdrive
```

---

### Post by Mark_in_Hollywood on 2009-03-25
So, Nothing, I did 

mark@Lexington-19:~$ umount /dev/sdd
umount: /dev/sdd is not mounted (according to mtab)


checking my desktop, I found that drive's icon there: 255.0 MB Media

Unmounted it by right-click and then:


mark@Lexington-19:~$ sudo e2label /dev/sdd mp1
e2label: Bad magic number in super-block while trying to open /dev/sdd
Couldn't find valid filesystem superblock.

??? I can move any type of file in/out of this thumbdrive.

---

### Post by nothingspecial on 2009-03-25
2 things to make sure of.

Is it definitely /dev/sdd ?

It should not appear on your desktop if it is not mounted.

Is it definitely ext2 or ext3 ?

Other than that I`m not sure, e2label has always worked for me.

---

### Post by Mark_in_Hollywood on 2009-03-25
> **nothingspecial said:**
> 2 things to make sure of.

Is it definitely /dev/sdd ?

It should not appear on your desktop if it is not mounted.

Is it definitely ext2 or ext3 ?

Other than that I`m not sure, e2label has always worked for me.

YES, it is definitely:

/dev/sdd

and yes, it is

ext2

thanks for your help.

---

### Post by mcduck on 2009-03-25
> **Mark_in_Hollywood said:**
> YES, it is definitely:

/dev/sdd

and yes, it is

ext2

thanks for your help.

Your problem is that you are trying to label the drive, while label is something you give to a partition..

Assuming you only have one partition on that drive, this should work:

```
sudo e2label /dev/sdd1 mp1
```

by the way, one easy way to check the correct device names for your drives  is running "sudo fdisk -l"

---

### Post by nothingspecial on 2009-03-25
That`s it McDuck!!

Nice one

---

### Post by Mark_in_Hollywood on 2009-03-25
> **mcduck said:**
> Your problem is that you are trying to label the drive, while label is something you give to a partition..

Assuming you only have one partition on that drive, this should work:

```
sudo e2label /dev/sdd1 mp1
```

by the way, one easy way to check the correct device names for your drives  is running "sudo fdisk -l"

Since the **sdd1** is a partiton and not a device, will the e2label delete the existing files on the device?

---

### Post by Polygon on 2009-03-25
e2 label doesnt delete anything, it just names the partition. your files are safe.

---

### Post by mcduck on 2009-03-25
> **Mark_in_Hollywood said:**
> Since the **sdd1** is a partiton and not a device, will the e2label delete the existing files on the device?

No, e2label (and tune2fs which could be used for this as well) only change the file system's settings but have no effect on it's contents.

Actually I'm not really sure if you even need to unmount the partition first. If I remember right both tools should work just fine with mounted filesystems.

---

### Post by Mark_in_Hollywood on 2009-03-25
It's times like these that makes me cry: "why me, Lord?"

mark@Lexington-19:~$sudo fdisk -l

[extraneous devices redacted]

Disk /dev/sdd: 257 MB, 257949696 bytes
255 heads, 63 sectors/track, 31 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x417fc429

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1          31      248976    b  W95 FAT32

[B]mark@Lexington-19:~$ sudo umount /dev/sdd
umount: /dev/sdd: not mounted[/B]

[B]mark@Lexington-19:~$ sudo e2label /dev/sdd1 mp1
e2label: Bad magic number in super-block while trying to open /dev/sdd1
Couldn't find valid filesystem superblock.[/B]

and again with the device mounted:
[B]
mark@Lexington-19:~$ sudo e2label /dev/sdd1 mp1
e2label: Bad magic number in super-block while trying to open /dev/sdd1
Couldn't find valid filesystem superblock.[/B]

I am confounded that the fdisk reports the System as W95 FAT32, cause I know I selected ext2 in GParted, but there it is.

---

### Post by nothingspecial on 2009-03-25
> **Mark_in_Hollywood said:**
> It's times like these that makes me cry: "why me, Lord?"

I know exactly how you feel. I suggest trying gparted again.

All the best!

---

### Post by mcduck on 2009-03-26
> **Mark_in_Hollywood said:**
> 
I am confounded that the fdisk reports the System as W95 FAT32, cause I know I selected ext2 in GParted, but there it is.
Base on the fdisk output it does look like FAT32 to me, and the fact that the system also mounts it without problems even when detecting it as FAT32 supports that.

Just like nothingspecial suggested, you'll have to re-format the partition to get it formatted into Ext2.

---

### Post by louieb on 2009-03-26
Kinda sounds like you did not click apply when reformatting the jump drive.  

Just on a side note, versions .0.3.6 and newer of Gparted can label partitions.  I use the [SystemRescueCd]("http://www.sysresccd.org/Main_Page")   when I want to use Gparted.

---

