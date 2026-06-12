---
title: "Mounting RAID0 on ubantu"
date: 2010-01-09
forum: New to Ubuntu
---

### Post by farmatt on 2010-01-09
Hi everyone,

I have RAID0 harddrive (2 each 500GB) on a vista machine that stopped booting a few days back. I installed ubuntu on a flash disk  hoping I can retrieve my data. Now when I do "sudo fdisk -l" I see:

Disk /dev/sdf: 500.1 GB, ...
Device Boot      Start        End      Blocks    Id    System
/dev/sdf1         1       120308   966373978+     7    HPFS/NTFS
/dev/sdf2         120309   121601   10386022+     7    HPFS/NTFS

I can do "sudo ls -l /dev/sdf", "sudo ls -l /dev/sdf1" and "sudo ls -l /dev/sdf2".

I do have ntfs-3g installed as well.

When I run 
sudo ntfs-3g /dev/sdf1 /media/vista -o force I get:

$MFT has invalid magic.
Failed to load $MFT: input/output error.
Failed to mount '/dev/sdf1': input/output error.
NTFS is either inconsistent or you have hardware faults, or you have a SoftRaid/FakeRaidd hardware. In the first case run chkdsk /f on windows. If you have SoftRaid/FakeRaid then first you might activate it and mount a different device under the /dev/mapper/ directory (e.g. /dev/mapper/nvidia_eahaabcc1). Please see dmraid documentation for more details.

Can anyone make some sense of it? I don't know what my next steps are. 

Thanks a ton!

---

