---
title: "Can't resize/shrink partition using GParted in liveCD"
date: 2009-02-08
forum: New to Ubuntu
---

### Post by trikster_x on 2009-02-08
I want to resize my Ubuntu partition to free up space to create a /home partition.  When GParted gets to shrink filesystem, it fails telling me to run 'e2fsck -f /dev/sda3' first.  The problem is Gparted does this automatically before it attempts to shrink the partition, and immediately after the shrink fails.  I have even tried to manually run the command through a terminal, but still get the same error.  There are no errors found when the e2fsck completes, so I don't see why GParted returns this error.  I don't have any screenshots since the computer I am attempting this on can't connect to the internet in liveCD mode.  

Any help is greatly appreciated.

---

### Post by trikster_x on 2009-02-08
I thought maybe it wouldn't let me shrink because I already had 4 primary partitions, so I deleted my swap partition and tried again.  Didn't help.

---

