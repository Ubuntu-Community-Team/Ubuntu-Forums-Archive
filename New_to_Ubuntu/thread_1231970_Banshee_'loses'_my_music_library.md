---
title: "Banshee 'loses' my music library"
date: 2009-08-05
forum: New to Ubuntu
---

### Post by Trinity1976 on 2009-08-05
Hi,
 
I am a totally novice with Ubuntu. I have three hard-drives. One is a 20GB which has two partitions, one for Windows, one for Ubuntu. I also have a 80GB and a 160GB hard-drive.
 
I downloaded Banshee yesterday and spent several hours importing and messing about with my music, which is on the 80GB hard-drive.
 
This morning I started up the machine and opened up Banshee. All my songs are still listed in the library, but none of them play. When I try to play one it gets a little orange disc with a white cross in it next to the song. In order to get the songs to play I have to re-import them.
 
I assume that this is because Banshee can't find where the songs are located, even though I have previously mounted the local drive.
 
I experimented by putting some of my music into my home folder and importing into Banshee. Banshee plays these just fine after a restart. Does that mean that Banshee will only see songs if they are on the same drive as Ubuntu? I can't move my songs as the drive I have Ubuntu installed on is very tiny.
 
Is there a way round this?

---

### Post by nothingspecial on 2009-08-05
As you have 2 external drives it could be that they are automounting in different places when you boot the computer.

Eg your music hard drive gets mounted /media/disk/ and your other one /media/disk-1. So you import your music library from /media/disk and next time you boot it get`s mounted /media/disk-1.

2 solutions

Difficult - [[COLOR="Red"]edit /etc/fstab[/COLOR]]("https://help.ubuntu.com/community/Fstab")

Easy - [[COLOR="Lime"]label your drives[/COLOR]]("https://help.ubuntu.com/community/RenameUSBDrive")

---

### Post by Trinity1976 on 2009-08-05
Sorry, tried renaming the disks as described in the 'easy' option, but when I follow the instructions and right-click the 'Label' option is greyed out.

The difficult option is just gobbledegook to me I'm afraid.

---

### Post by nothingspecial on 2009-08-05
Did you unmount the drives first?

---

### Post by Trinity1976 on 2009-08-05
Yes, followed the instructions exactly as stated. When I unmount the drives an exclamation mark appears next to the drive which when I double-click it tells me:

Warning! Unable to read the contents of this file system. Because of this some operations may be unavailable.

---

### Post by Trinity1976 on 2009-08-05
I have fiddled around and confirmed your earlier theory by looking at the Track Information. Basically one of the drives is being mounted as Local Drive and the other as Local Drive_. Because it's random each time the drives are mounted, the only way to get round it other than renaming the drives is to have all my music on both drives. However, that would be silly.

I could get rid of one of the drives but obviously I would prefer to rename them. Is it because they are NTFS?

---

### Post by nothingspecial on 2009-08-05
What file systems do the drives use.

Also type ```
sudo fdisk -l
```, with the drives mounted and copy and paste the output here.

---

### Post by Trinity1976 on 2009-08-05
OK, here goes:

Disk /dev/sda: 20.4 GB, 20496236544 bytes
255 heads, 63 sectors/track, 2491 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x03af03ae

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1276    10243219+   7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2            1276        2492     9767520    f  W95 Ext'd (LBA)
Partition 2 does not end on cylinder boundary.
/dev/sda5            1276        2492     9767047+   7  HPFS/NTFS

Disk /dev/sdb: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3e663e65

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        9963    80027766    7  HPFS/NTFS

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf0c92ce1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       19457   156288321    7  HPFS/NTFS

---

### Post by nothingspecial on 2009-08-05
```
sudo apt-get install ntfsprogs
```

Unmount the drives


```

 sudo ntfslabel /dev/sdb1 [COLOR="Red"]tunes[/COLOR]
```

```
 sudo ntfslabel /dev/sdc1 [COLOR="Red"]other_drive[/COLOR]
```

Of course you can change the names (in red) to whatever you like.

This assumes that the 80gig drive is your music one.

Unmount them and then unplug them (unplugging them is important) then plug them back in again.

---

### Post by Trinity1976 on 2009-08-05
It worked on the larger drive (not the one with the music) but I got the following error with the smaller drive:

Failed to empty $FILE_LogFile/$DATA: Input/output error.
Failed to mount '/dev/sdb1': Input/output error.
NTFS is inconsistent. Run chkdsk /f on Windows then reboot it TWICE!
The usage of the /f parameter is very IMPORTANT! No modification was
made to NTFS by this software.

However, it has effectively solved my problem since the two drives now have different names.

Thanks for your help.

---

### Post by nothingspecial on 2009-08-06
Try
```

sudo ntfsfix /dev/sdb1
```

This assumes that your music drive is still sdb1, run sudo fdisk -l again and check

Here is your output from before

```
Disk [COLOR="Red"]/dev/sdb[/COLOR]: [COLOR="Red"]81.9 GB[/COLOR], 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3e663e65

Device Boot Start End Blocks Id System
[COLOR="Red"]/dev/sdb1[/COLOR] * 1 9963 80027766 7 [COLOR="Red"]HPFS/NTFS[/COLOR]
```
lots of clues.

Then try again

 ```
sudo ntfslabel /dev/sdb1 tunes
```

Again please make sure the drive has the same /dev/sd?? before you do, otherwise change the commands accordingly.

---

### Post by Trinity1976 on 2009-08-06
Tried ntfsfix got following output:

Mounting volume... Failed to empty $FILE_LogFile/$DATA: Input/output error.
FAILED
Attempting to correct errors... 
Processing $MFT and $MFTMirr...
Reading $MFT... OK
Reading $MFTMirr... OK
Comparing $MFTMirr to $MFT... OK
Processing of $MFT and $MFTMirr completed successfully.
Setting required flags on partition... OK
Going to empty the journal ($LogFile)... Failed to empty $FILE_LogFile/$DATA: Input/output error.
FAILED
Failed to reset $LogFile: Input/output error.

---

