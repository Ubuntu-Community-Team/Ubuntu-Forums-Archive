---
title: "Unable to mount 250gb filesystem"
date: 2010-01-17
forum: New to Ubuntu
---

### Post by Devilham on 2010-01-17
I am trying to access my NTFS XP partition, and keep getting the following

Error mounting: mount exited with exit code 13: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Failed to read NTFS $Bitmap: Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.

I have ran chkdsk /f several times, no luck.  Searching the forums, I then tried this command in the terminal

sudo ntfsfix /dev/sda1

I get the following message...

Mounting volume... pread: Input/output error
Failed to calculate number of free clusters: Input/output error.
FAILED
Attempting to correct errors... 
Processing $MFT and $MFTMirr...
Reading $MFT... OK
Reading $MFTMirr... OK
Comparing $MFTMirr to $MFT... OK
Processing of $MFT and $MFTMirr completed successfully.
Setting required flags on partition... OK
Going to empty the journal ($LogFile)... OK
pread: Input/output error
Failed to calculate number of free clusters: Input/output error.
Remount failed: Input/output error.

Any ideas?  I want to get at the files on my XP partition so I can migrate some things over to Ubuntu.

---

### Post by MooPi on 2010-01-17
In terminal type and copy and paste results back here:   ```
sudo fdisk -l
```

---

### Post by Devilham on 2010-01-17
Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0d2d0d2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30400   244187968+   7  HPFS/NTFS

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd14cd14c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       29319   235504836   83  Linux
/dev/sdb2           29320       30401     8691165    5  Extended
/dev/sdb5           29320       30401     8691133+  82  Linux swap / Solaris

---

### Post by MooPi on 2010-01-17
Have you tried to manually mount ? Have your attempts to mount been through Nautilus ?
Try this to manually mount ```
sudo mkdir /media/WNmedia
``` You can name your folder something else than WNmedia.
```
sudo mount /dev/sda1 /media/WNmedia
```
Not knowing how you attempted to mount I'm just tossing an option.

---

### Post by Devilham on 2010-01-25
Okay, it's been a bit of a saga, but I have an update.  Trying many peoples suggestions just did not seem to pan out, and I had resigned myself to just manually moving my files via thumb drive, and accept that the to OS's would never speak to eachother again.  So Friday night, I boot to windows, when out of nowhere ANOTHER disk check event occured (I had ran chkdsk /f several times prior trying to resolve this issue) on it's own.  Being a fairly large disk, I put it off, but then prior to going to bed that night, I let it run overnight.  The next day I boot to windows (1st boot), then it says  I had updates and restarted (second boot!  Just as others have suggested you must do), do some maintenance in windows, and then boot to Ubuntu.  Thinking about what I had just done, I decided, what the heck, let's give it one more try, and then BOOM!  It just works!   Thanks everyone for trying to help (and for being right, it just didn't work right away for whatever reasons), and all's well that ends well says I!

---

