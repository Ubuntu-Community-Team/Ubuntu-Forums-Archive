---
title: "Unable to mount hdd"
date: 2010-01-14
forum: New to Ubuntu
---

### Post by betterthanjordan79 on 2010-01-14
i accidentally unpluged my hdd while it was transferring data and now it won't mount. i get this error

> Unable to mount 1000 GB Filesystem

Error mounting: mount exited with exit code 13: $MFTMirr does not match $MFT (record 0).
Failed to mount '/dev/sdc1': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.


All help appreciated.

also i dont have a windows system at hand.

thnaks in advanced - Daniel

---

### Post by baddog144 on 2010-01-14
You should probably do what it says, assuming you have a Windows install. 
chkdsk /f and reboot into Windows. I'm assuming Windows will be able to take much better care of an  NTFS disk. :/
At any rate, you've obviously corrupted it somewhat.

---

