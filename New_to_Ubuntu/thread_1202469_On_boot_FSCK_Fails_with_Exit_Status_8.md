---
title: "On boot: FSCK Fails with Exit Status 8"
date: 2009-07-02
forum: New to Ubuntu
---

### Post by R_U_Q_R_U on 2009-07-02
Upon reboot:

Log of fsck -C3 -R -A -a 
Thu Jul  2 09:33:58 2009

fsck 1.41.4 (27-Jan-2009)
fsck.ext3: Unable to resolve 'UUID=8aad621d-6f4d-4fad-b1c3-630379f7f0e0' 
fsck died with exit status 8

This UUID is NOT for any mounted hard drive. I don't know what it belongs to. The only change I made that may have caused this is to reformat a second (non-boot) drive to wipe XP and create a ext3 partition.

Could the UUID belong to the old partition or does it point to hardware?


UPDATE: Problem Solved

The UUID changed when I reformatted sdb1.
I edited fstab to include the new UUID

---

