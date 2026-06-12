---
title: "external hdd  not mounting"
date: 2010-04-04
forum: New to Ubuntu
---

### Post by PatrickMoore on 2010-04-04
im getting this error

```
Error mounting: mount exited with exit code 13: $MFTMirr does not match $MFT (record 0).
Failed to mount '/dev/sdb1': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.

```

anyone know the issue?

---

### Post by mikewhatever on 2010-04-04
If you have Windows installed, run what the message tells you, chkdsk /f, from Start->Run. It will fix the file system errors, and then the partition should mount.

---

