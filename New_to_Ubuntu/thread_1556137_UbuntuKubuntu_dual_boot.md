---
title: "Ubuntu/Kubuntu dual boot"
date: 2010-08-19
forum: New to Ubuntu
---

### Post by nnjond on 2010-08-19
Hi,

At present, I have GNU Sense on sda1 sharing a swap file on sda5 with Linx. Kubuntu install gives me the impression i can install it over GNU Sense and it also warns me it will reformat sda5. Can someone reassure me the outcome will be a dual boot with sda2 unchanged.

Thanks for your time.


```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000b5a45

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1275    10240000   83  Linux
/dev/sda2            1275       52954   415111930+  83  Linux
/dev/sda3           60291       60801     4096576    5  Extended
/dev/sda5           60292       60801     4096575   82  Linux swap / Solaris


```

---

### Post by zvacet on 2010-08-19
During install choose manual way and install Kubuntu formated as ext4.That should not touch swap or anything else.

---

### Post by nnjond on 2010-08-19
Thanks for your help; I had forgotten i could install KDE from synaptic

---

