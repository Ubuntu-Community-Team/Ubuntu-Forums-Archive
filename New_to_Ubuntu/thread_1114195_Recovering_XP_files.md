---
title: "Recovering XP files"
date: 2009-04-02
forum: New to Ubuntu
---

### Post by jurisnaturalist on 2009-04-02
I just acquired Ubuntu when my Windows failed.
I was getting a DLL error message, and didn't know what it meant, then death.
So I got Ubuntu and installed it.  It partitioned the drive.  
Now, I want to get at my old Windows files.
But Ubuntu does not even "see" them.  Other threads recommend opening some icon which I don't have.
I was running XP with a FAT32 system.
Any ideas?

---

### Post by halitech on 2009-04-02
open the terminal and post the output of
```
sudo fdisk -l
```

---

### Post by jurisnaturalist on 2009-04-02
Okay, I get
Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd188d188

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       11787    94679046   83  Linux
/dev/sda2           11788       12161     3004155    5  Extended
/dev/sda5           11788       12161     3004123+  82  Linux swap / Solaris

Disk /dev/sdb: 8029 MB, 8029470208 bytes
255 heads, 63 sectors/track, 976 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         976     7839698    b  W95 FAT32
 now, what

---

### Post by ajgreeny on 2009-04-02
For simplicity at the moment, just mount the windows partition by going to nautilus and double clicking on the partition in Places in the left pane.  That will open Windows as if it were a folder on ubuntu and you can simply copy the files you want to your ubuntu home folder.

If the double clicking does not work you may need to mount the partition manually in the terminal with these two commands ```
sudo mkdir /media/windows
``` and then ```
sudo mount /dev/sdb1 /media/windows/ -t vfat -o iocharset=utf8,umask=000
```and then copy the files as I say above.

---

### Post by luckydeveloper on 2009-04-02
I would propose an easy way to do that..you can try putting your ubuntu "live cd" in .. and then access your windows drive through that... then copy all those files into a media like DVD etc.,

---

### Post by halitech on 2009-04-02
I hope there wasn't much on the windows drive that you wanted because this
```
Disk /dev/sdb: 8029 MB, 8029470208 bytes
255 heads, 63 sectors/track, 976 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Device Boot Start End Blocks Id System
/dev/sdb1 1 976 7839698 b W95 FAT32
```
doesn't look very big to me

---

### Post by gandaran on 2009-04-02
> **jurisnaturalist said:**
> Okay, I get
Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd188d188

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       11787    94679046   83  Linux
/dev/sda2           11788       12161     3004155    5  Extended
/dev/sda5           11788       12161     3004123+  82  Linux swap / Solaris

Disk /dev/sdb: 8029 MB, 8029470208 bytes
255 heads, 63 sectors/track, 976 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         976     7839698    b  W95 FAT32
 now, what

are you sure you partitioned the hard drive? you only have ubuntu installed on the one main hard drive, if you had windows on this disk then you wiped it out with the ubuntu install or maybe this is where windows is
> /dev/sdb1               1         976     7839698    b  W95 FAT32
but this is a second disk, do you have two hard drives or is this some flash drive?

---

### Post by jurisnaturalist on 2009-04-02
Okay, I had a flash drive in last time, now it reads:

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd188d188

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       11787    94679046   83  Linux
/dev/sda2           11788       12161     3004155    5  Extended
/dev/sda5           11788       12161     3004123+  82  Linux swap / Solaris

When I installed, I just thought I was following directions, and it re-partitioned the drive.  Does that mean I can't access any of those old files ever again?
I doubt that.  But is it possible that ubuntu only sees its own files and not the old windows stuff?

---

### Post by jurisnaturalist on 2009-04-02
I tried what someone above said and got:
mount: special device /dev/sdbl does not exist

---

### Post by ajgreeny on 2009-04-02
> **jurisnaturalist said:**
> I tried what someone above said and got:
mount: special device /dev/sdbl does not exist
Yes, that was me, I suspect, but I didn't know you had a usb drive in at the time.  You do appear to have wiped your windows install so use the live CD to get a copy of testdisk [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery) and you can try using that to recover the old partitions, including windows.  You will need to download to a usb drive and burn the downloaded testdisk file (iso?) to a CD and will need to do that on another computer as you can't do it from a live CD unless you have two CD drives on your machine.

Good luck, I hope you get it all back.

---

### Post by mister_pink on 2009-04-02
Ubuntu can see windows drives, although sometimes you have to manually make it show them. 

In this case, I hate to say it but it looks as though you've chosen the "use entire disk" option on the installer. This will have wiped out everything on the drive.

---

