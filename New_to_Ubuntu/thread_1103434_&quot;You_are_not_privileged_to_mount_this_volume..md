---
title: "&quot;You are not privileged to mount this volume.&quot;"
date: 2009-03-22
forum: New to Ubuntu
---

### Post by InfectedWithDrew on 2009-03-22
Hi, I was fixing a friend's computer and I wanted to scan my flash drive for viruses before I used it on Windows again.  But when I plugged it into Ubuntu it gave this message:
> "You are not privileged to mount this volume."
Scary, right?  The worst part is that it has NEVER done this before.

What should I do?  I really live off this flash drive.

---

### Post by lisati on 2009-03-22
> **InfectedWithDrew said:**
> Hi, I was fixing a friend's computer and I wanted to scan my flash drive for viruses before I used it on Windows again.  But when I plugged it into Ubuntu it gave this message:

Scary, right?  The worst part is that it has NEVER done this before.

What should I do?  I really live off this flash drive.

My first thought is did you use the "Safely remove hardware" option within Windows?

---

### Post by InfectedWithDrew on 2009-03-22
> **lisati said:**
> My first thought is did you use the "Safely remove hardware" option within Windows?
Shoot!  I always forget to do that... and I can't risk it on this computer.  Is there a way to force it?

---

### Post by lisati on 2009-03-22
> **InfectedWithDrew said:**
> Shoot!  I always forget to do that... and I can't risk it on this computer.  Is there a way to force it?

I'll have to pass on to someone else to answer.....

---

### Post by drs305 on 2009-03-22
If it's an unclean shutdown, either plug it back into a windows machine and unmount it from there, or less preferably:
```

sudo mount /dev/sdXX -t ntfs /media/your.mount.point -o force

```

Change "sdXX" to your device name and the mount point to your mount point.

You can also install ntfsprogs and run "ntfsfix". Read about it after installing it with "man ntfsfix".

---

### Post by InfectedWithDrew on 2009-03-22
> **drs305 said:**
> If it's an unclean shutdown, either plug it back into a windows machine and unmount it from there, or less preferably:
```

sudo mount /dev/sdXX -t ntfs /media/your.mount.point -o force

```

Change "sdXX" to your device name and the mount point to your mount point.

You can also install ntfsprogs and run "ntfsfix". Read about it after installing it with "man ntfsfix".

How would I run ntfsfix on this volume, since it isn't mounted?

---

### Post by drs305 on 2009-03-22
> **InfectedWithDrew said:**
> How would I run ntfsfix on this volume, since it isn't mounted?

After installing ntfsprogs, you simply run ntfsfix as:
```
sudo ntfsfix /dev/sdXX
```
with sdXX replaced with your device's designation.

---

### Post by InfectedWithDrew on 2009-03-22
> **drs305 said:**
> After installing ntfsprogs, you simply run ntfsfix as:
```
sudo ntfsfix /dev/sdXX
```

What command should I use to determine which device this flash drive is?

---

### Post by drs305 on 2009-03-22
> **InfectedWithDrew said:**
> What command should I use to determine which device this flash drive is?

```
sudo fdisk -l
```

---

### Post by InfectedWithDrew on 2009-03-22
```
drew@spider-desktop:~$ sudo ntfsfix /dev/sdd1
Mounting volume... Failed to startup volume: Invalid argument.
FAILED
Attempting to correct errors... FAILED
Failed to startup volume: Invalid argument.
Volume is corrupt. You should run chkdsk.

```
So what should I do, force mount it?  Can't risk it on my PC, I don't have data backups (nowhere to back it up to...).

Oh, shoot!  I think I know what's wrong.  This is a FAT32 drive...

Well maybe I'll just mount it at school, no biggie if their computers get totaled. ;)

---

### Post by drs305 on 2009-03-22
Are you sure this is an ntfs formatting? That is the error you will get if you run it on another file system.

---

### Post by InfectedWithDrew on 2009-03-22
> **drs305 said:**
> Are you sure this is an ntfs formatting? That is the error you will get if you run it on another file system.

Yeah, it's FAT32, as I edited in.

I figured that since I said it was a flash drive, that would be understood, but hey, I'm the one with a problem xD

----------------
Now playing: [Jeremy Camp - Feels Like](http://www.foxytunes.com/artist/jeremy+camp/track/feels+like)

---

### Post by drs305 on 2009-03-22
I have flash drives formatted in all sorts of file system types so I should have known to ask.

---

### Post by InfectedWithDrew on 2009-03-23
So despite taking this drive to school, mounting it, and safely removing it, I get the same errors.

So should I force mount it, or is there another option?  I'd like to preserve the data I have on there, if possible.

---

### Post by drs305 on 2009-03-23
Force mounting won't destroy the data, it just tells the system that there may be errors and to mount it anyway. If it mounts, the first thing I would do is copy the data elsewhere. ;-)

The command to force mount the drive was given previously in another post.

---

### Post by InfectedWithDrew on 2009-03-23
```
drew@spider-desktop:~$ sudo mount /dev/sdd1 -t fat32 /media/sdd1 -o force
[sudo] password for drew: 
mount: unknown filesystem type 'fat32'

```:(

---

### Post by drs305 on 2009-03-23
Change "fat32" to "vfat"

---

### Post by InfectedWithDrew on 2009-03-23
```
drew@spider-desktop:~$ sudo mount /dev/sdd1 -t vfat /media/sdd1 -o force
mount: wrong fs type, bad option, bad superblock on /dev/sdd1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

drew@spider-desktop:~$ sudo mount /dev/sdd1 -t vfat /dev/sde1 -o force
mount: mount point /dev/sde1 does not exist

```Uh-oh.

---

### Post by drs305 on 2009-03-23
Edited: Oh, I see you changed the command but the second one really won't do it. Does /media/sdd1 exist? Try this and then run the command again.

```

sudo mkdir /media/sdd1
sudo mount /dev/sdd1 -t vfat /media/sdd1 -o force

```

---

### Post by InfectedWithDrew on 2009-03-23
```
drew@spider-desktop:~$ sudo mkdir /media/sde1
drew@spider-desktop:~$ sudo mount /dev/sdd1 -t vfat /dev/sde1 -o force
mount: mount point /dev/sde1 does not exist
drew@spider-desktop:~$ sudo mount /dev/sdd1 -t vfat /media/sde1 -o force
mount: wrong fs type, bad option, bad superblock on /dev/sdd1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```I realize that I typed it in wrong back in the last post but I typed it in right this time... so I think my drive is shot?

---

### Post by MikeTheC on 2009-03-23
Just recently had this problem myself. A friend of mine fixed it by killing the line item for the drive in fstab, disconnecting and then reconnecting the drive. It has to do with something in FSTAB being given a bad assignment, or that it thinks the drive is supposed to be NTFS when, in your case as in mine, it is actually FAT32.

---

### Post by InfectedWithDrew on 2009-03-23
> **MikeTheC said:**
> Just recently had this problem myself. A friend of mine fixed it by killing the line item for the drive in fstab, disconnecting and then reconnecting the drive. It has to do with something in FSTAB being given a bad assignment, or that it thinks the drive is supposed to be NTFS when, in your case as in mine, it is actually FAT32.

Any clue how to go about doing this?

---

### Post by drs305 on 2009-03-23
Just to be sure, with the drive inserted, please post the results of:
```
sudo fdisk -l
```

Also, when you went back to your school and tried unmounting it in windows, were you able to see any of the data? 

Sorry, but unless I see something in the fdisk command I've run out of ideas. Testdisk would be the next step but I'm no expert at that app.

---

### Post by InfectedWithDrew on 2009-03-23
```
drew@spider-desktop:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00083952

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19456   156280288+   7  HPFS/NTFS

Disk /dev/sdb: 20.4 GB, 20416757760 bytes
255 heads, 63 sectors/track, 2482 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xea1aa9c7

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        2373    19061091   83  Linux
/dev/sdb2            2374        2482      875542+   5  Extended
/dev/sdb5            2374        2482      875511   82  Linux swap / Solaris

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa4b57300

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       60801   488384001    7  HPFS/NTFS

Disk /dev/sdd: 2055 MB, 2055019520 bytes
16 heads, 63 sectors/track, 3981 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes
Disk identifier: 0x538e19e0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1        3982     2006823+   b  W95 FAT32

```When I put it into a Windows machine, I could see all my data but ClamWin portable did strange things... it couldn't update its database, for instance.  And then the computer BSoD'd but it didn't crash, just hitting Ctrl-alt-del made it return to the desktop as if nothing had happened.

So you see why I'm trying not to put this thing into my Windows partition ;)

EDIT: No, I can't run chkdsk at school, because I lack admin privileges there.

---

### Post by InfectedWithDrew on 2009-03-27
A little update: I still can't mount this drive in Linux though I've mounted it in Windows and ran chkdsk and defragged it.

Furthermore, it seems that I can't mount my mp3 player's drive either (Sansa e280r).  I get the same error.  I suspect something is wrong with my system.

---

### Post by GeeZor on 2009-03-27
To be honest, you can't realy total a machine running Windows.. someone beat you to it :) :) :) :) :)

---

### Post by InfectedWithDrew on 2009-03-27
> **GeeZor said:**
> To be honest, you can't realy total a machine running Windows.. someone beat you to it :) :) :) :) :)This helps me not.

----------------
Now playing: [Nonpoint - Circles](http://www.foxytunes.com/artist/nonpoint/track/circles)

---

### Post by GeeZor on 2009-04-06
fbus-launch nautilius might solve some issues.
i do that when my camera has problems connecting.
(fbus-luanch f-spot in that case)

Hope that will help you out though!

---

### Post by jws957 on 2009-04-18
The USB drive was somehow corrupted. You need to format the USB drive in Linux to be a FAT file system.
First, copy the files off the drive onto a Windows machine.
Then, in the Linux terminal type:
>sudo mkdosfs -F 32 /dev/sdx -I
(This will give you a FAT32 file system, substitute 16 for 32 if you want FAT16)
When that is finished, go back to the Windows machine and copy the files back onto the drive - this should take care of the problem.

---

### Post by jws957 on 2009-04-18
Remember to substitute "x" in "sdx" for your drive location.  If you don't know that, type
>sudo fdisk -l
and you should be able to figure it out.

---

