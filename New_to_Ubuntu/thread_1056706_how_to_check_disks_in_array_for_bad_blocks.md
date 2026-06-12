---
title: "how to check disks in array for bad blocks?"
date: 2009-02-01
forum: New to Ubuntu
---

### Post by anon0 on 2009-02-01
How are you supposed to verify whether all disks in a RAID array are without any defective blocks or sectors, as opposed to just being apparently operational? I know you can use mdadm --detail to check for failed devices, but I don't see an option to scan the disks. There's fsck but I'm getting a device busy error:

root@ubuntu:/home/user# umount /dev/md2
root@ubuntu:/home/user# fsck /dev/md2
fsck 1.41.3 (12-Oct-2008)
e2fsck 1.41.3 (12-Oct-2008)
fsck.ext3: Device or resource busy while trying to open /dev/md2
Filesystem mounted or opened exclusively by another program?

Update: for some reason the array above became free for checking after several minutes:
root@ubuntu:/home/user# fsck /dev/md2
fsck 1.41.3 (12-Oct-2008)
e2fsck 1.41.3 (12-Oct-2008)
raid5: clean, 14/8552448 files, 692021/34178240 blocks

However the check was nearly instantaneous, which seems like it doesn't actually inspect the disk surface including unused space.

Update: found the command "badblocks" (which is also called by e2fsck -c). This can do a non-destructive write-read comparison test to find bad blocks.

---

### Post by RealPSL on 2009-02-01
Probably a better method is using the SMART technology that most disks ships with that can be used to identify when they are going bad. The link below talks about how to set this up and will hopefully help you achieve your monitoring goal.

[http://www.howtoforge.com/checking-hard-disk-sanity-with-smartmontools-debian-ubuntu]("http://www.howtoforge.com/checking-hard-disk-sanity-with-smartmontools-debian-ubuntu")

---

