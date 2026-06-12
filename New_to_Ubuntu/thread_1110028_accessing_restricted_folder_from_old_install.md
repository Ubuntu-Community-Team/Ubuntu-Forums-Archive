---
title: "accessing restricted folder from old install"
date: 2009-03-29
forum: New to Ubuntu
---

### Post by bahsarie on 2009-03-29
I accidentally the other day took out some kernels now my netbook won't boot. However this is not the issue, the issue is that I can boot off a usb but I can not access all of my files. Especially ones that I need most ones for school. I read about the chown _R command but did not get that to work it kept telling me bad command. Also when i use f-disk -l it gives me about 6 drives i only have two installed and only have a single partition on each.

---

### Post by kanikilu on 2009-03-29
> **bahsarie said:**
> I accidentally the other day took out some kernels now my netbook won't boot. However this is not the issue, the issue is that I can boot off a usb but I can not access all of my files. Especially ones that I need most ones for school. I read about the chown _R command but did not get that to work it kept telling me bad command. Also when i use f-disk -l it gives me about 6 drives i only have two installed and only have a single partition on each.

Try ```
sudo chown -R username folder
``` (use a dash "-", not underscore "_". See **man chown** for more options)

Depending on what the files are, you could probably also just give full permission to all: ```
sudo chmod -R 777 folder
```

---

### Post by bahsarie on 2009-03-29
I am still unsure, if I show you the fdisk -l output can you help me along?
Here is the output


Partition table entries are not in disk order

Disk /dev/sdd: 8021 MB, 8021606400 bytes
247 heads, 62 sectors/track, 1023 cylinders
Units = cylinders of 15314 * 512 = 7840768 bytes
Disk identifier: 0x8ef631df

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   ?      137949      265854   979374166   66  Unknown
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(734, 123, 14) logical=(137948, 6, 21)
Partition 1 has different physical/logical endings:
     phys=(120, 143, 6) logical=(265853, 186, 22)
Partition 1 does not end on cylinder boundary.
/dev/sdd2   ?      225242      482806  1972168331    7  HPFS/NTFS
Partition 2 has different physical/logical beginnings (non-Linux?):
     phys=(187, 180, 14) logical=(225241, 197, 52)
Partition 2 has different physical/logical endings:
     phys=(784, 0, 13) logical=(202345, 177, 1)
Partition 2 does not end on cylinder boundary.
/dev/sdd3   ?      214171      341732   976730017   7d  Unknown
Partition 3 has different physical/logical beginnings (non-Linux?):
     phys=(252, 59, 46) logical=(214170, 230, 39)
Partition 3 has different physical/logical endings:
     phys=(139, 118, 4) logical=(61271, 37, 28)
Partition 3 does not end on cylinder boundary.
/dev/sdd4   ?      184763      185306     4161547   6f  Unknown
Partition 4 has different physical/logical beginnings (non-Linux?):
     phys=(370, 101, 50) logical=(184762, 96, 45)
Partition 4 has different physical/logical endings:
     phys=(10, 114, 13) logical=(185305, 219, 10)
Partition 4 does not end on cylinder boundary.

I am still unfamiliar in how to chown -r to any of these. help would be appreciated.

---

### Post by bahsarie on 2009-03-29
I tried chown again, this time it tells me i Can't use it because i have the wrong username. But I am using the same name I use to log in as and I am the only one who use my netbook.

---

