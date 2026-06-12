---
title: "Unable to Mount Partition"
date: 2011-03-03
forum: New to Ubuntu
---

### Post by djsnakeyes on 2011-03-03
Hi All,

I really really did not want to open this thread but I could not resolve after spending hours of researching.

This morning when I booted up I could no longer access one of my partitions (/dev/sdb1)
I've tried to mount it via terminal , force mount it via terminal, mount it in gparted, add it to the fstab...just no luck

fdisk -l output
```
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00240024

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       13995   112414806   83  Linux
/dev/sda2           13996       14593     4803435    5  Extended
/dev/sda5           13996       14593     4803403+  82  Linux swap / Solaris

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x90250fc1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        9729    78148161    7  HPFS/NTFS

```Any help would be greatly appreciated.

Thanks!

---

### Post by TeoBigusGeekus on 2011-03-03
Assuming you dual boot with windows (therefore the ntfs partition), boot from the latter and run a checkdisk from it (linux has no tool for checking/fixing ntfs partitions).

---

### Post by djsnakeyes on 2011-03-03
Unfortunately i don't dual boot.

---

### Post by TeoBigusGeekus on 2011-03-03
Boot up with a live cd and see if you can reach your partition.

---

### Post by djsnakeyes on 2011-03-06
Well it turns out it wasn't just that partition that was giving me issues. I wasn't able to mount any of my external drives either. Not sure why this happened. The last change on my system was a clamav update?!

At any rate, as per your direction, I was able to access the data from the partition using a live cd which I booted off a usb drive. This allowed me to back everything up and reinstall a newer version of Ubuntu (from 8.04 to 10.04). Not the quickest fix but at least I didn't lose any data. 

Thanks TeoBigusGeekus!

---

### Post by TeoBigusGeekus on 2011-03-06
You're welcome mate! I'm glad that you've sorted it out.

---

