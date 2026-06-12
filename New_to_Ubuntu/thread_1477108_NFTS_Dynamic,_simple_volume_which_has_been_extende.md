---
title: "NFTS Dynamic, simple volume which has been extended 3 times"
date: 2010-05-08
forum: New to Ubuntu
---

### Post by truebluexxx on 2010-05-08
I have used windows XP Pro to create an NTFS  dynamic disk with a simple volume of size 367GB.
I then extended it, and again and final again to use up the full 500GB, and it all works fine in XP.
I see it as one drive  d: of size 500GB.

Just installed ubuntu 10.04 and it won't mount the drive.
I think it tries to mount dev/sdb1 which is the 367GB volume  (is it a partition ? is it a volume?) rather than the full 500GB drive.

the error I get is.

Error mounting: mount exited with exit code 12: Failed to read last sector (976768001): Invalid argument
HINTS: Either the volume is a RAID/LDM but it wasn't setup yet,
   or it was not setup correctly (e.g. by not using mdadm --build ...),
   or a wrong device is tried to be mounted,
   or the partition table is corrupt (partition is smaller than NTFS),
   or the NTFS boot sector is corrupt (NTFS size is not valid).
Failed to mount '/dev/sdb1': Invalid argument
The device '/dev/sdb1' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?


So at a guess, when I use file browser to mount the drive, ubuntu is actually trying to mount the first volume instead.  Is this analysis correct? If so how can I try to mount the drive?

I have added a screen shot from 'disk utility'

Hope you can help.

---

### Post by cariboo on 2010-05-08
I would suggest you run:

```
chkdsk
```

in Windows to make sure there are no problems with the drive.

---

### Post by truebluexxx on 2010-05-08
After installing Ubuntu and then booting in to windows XP again, windows, on start up ran chkdsk on C: and D:    which I though was odd.
Ran it again anyway and the output is below, no problems.


Microsoft Windows XP [Version 5.1.2600]
(C) Copyright 1985-2001 Microsoft Corp.

C:\Documents and Settings\Bruce>chkdsk d:
The type of the file system is NTFS.
Volume label is DATA.

WARNING!  F parameter not specified.
Running CHKDSK in read-only mode.

CHKDSK is verifying files (stage 1 of 3)...
File verification completed.
CHKDSK is verifying indexes (stage 2 of 3)...
Index verification completed.
CHKDSK is verifying security descriptors (stage 3 of 3)...
Security descriptor verification completed.
CHKDSK is verifying Usn Journal...
Usn Journal verification completed.

 488384000 KB total disk space.
 468207600 KB in 79540 files.
     31356 KB in 4246 indexes.
         0 KB in bad sectors.
    213228 KB in use by the system.
     65536 KB occupied by the log file.
  19931816 KB available on disk.

      4096 bytes in each allocation unit.
 122096000 total allocation units on disk.
   4982954 allocation units available on disk.

C:\Documents and Settings\Bruce>

---

