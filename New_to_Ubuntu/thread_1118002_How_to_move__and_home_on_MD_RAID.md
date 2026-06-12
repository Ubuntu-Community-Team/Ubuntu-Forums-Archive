---
title: "How to move / and /home on MD RAID ?"
date: 2009-04-06
forum: New to Ubuntu
---

### Post by matdaimond on 2009-04-06
Hi,
I have installed Kubuntu 9.04 (beta) on one of my HDD. It works great, but I'd like to move on MD RAIDs.
Currently I have:
 - 250MB on sda1 for /boot
 - 27GB on sda2 for /
 - 50GB on sda3 for /home
 - 4.1GB on sdb1 for swap
 - 25GB on sdb2 unused
 - 50GB on sdb3 unused.
So, I want to keep /boot and swap on normal primary partitions and would like make my sda2+sdb2 RAID0 (for /) and sda3+sdb3 - RAID1 (for /home), but I have no idea how.
Is it possible to do such trick at all?

(Yes, I checked alternate CD and tried to install Kubuntu on RAID, but this installer doesn't work - fails to boot after the installation).

---

### Post by llamabr on 2009-04-06
Can't you just tar up your home, put it on the new disk, then edit your fstab file?

---

