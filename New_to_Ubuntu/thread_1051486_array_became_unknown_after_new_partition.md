---
title: "array became unknown after new partition?"
date: 2009-01-26
forum: New to Ubuntu
---

### Post by anon0 on 2009-01-26
I used GParted to create a new parittion out of some free space on a drive that's part of a RAID array, while the array was mounted. Now the whole array's filesystem is shown as "unknown" in GParted. The information given: 
"Unable to detect filesystem! Possible reasons are:
-The filessytem is damaged
-The filesystem is unknown to GParted
-There is no filesystem available (unformatted)"

The files in the array are still accessible, however. 
How do I fix this error?

I ran "mke2fs -j /dev/md0" which did not change the error message.
Running "mdadm --detail /dev/md0" implies that md0 is working fine.
Running "r2fsck -n /dev/md0" says the array is clean.

Update: partitions should not be modified on a disk that's part of a RAID array, according to the Server CD.

---

