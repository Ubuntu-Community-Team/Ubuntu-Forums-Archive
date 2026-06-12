---
title: "mounting old hardware RAID drive"
date: 2009-06-08
forum: New to Ubuntu
---

### Post by apfergus on 2009-06-08
I have a drive from an old RAID 1 array (the other drive died, and both were ultimately replaced with a fresh install on bigger drives). There is data on it I would rather like to have access to. 

I've hooked it up to an extra SATA port on a random machine and tried to mount it, but while the drive is present in /dev, the partition table is not. fdisk -l tells me:
```

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x20202020

Disk /dev/sdb doesn't contain a valid partition table
```

I know I can boot from this drive as long as it's in the server it used to live in, and all the data is there and accessible over the network. But I'd like to avoid that as I'd have to take the server down to accomplish it.

Is this normal behavior for a hardware RAID disk? Or is something broken?

Thanks,

A.P.

---

### Post by ronparent on 2009-06-09
If it is a hardware raid, did it plug into a pci raid card? If so you would require a like card to see it. If it was plugged into a sata port in the motherboard then you would likewise have to plug it into a mb with like chipset and configure the port for raid with setting identical to that from which it came. Why would the server have to come down as long as it is not the boot disk?

---

### Post by apfergus on 2009-06-09
> Why would the server have to come down as long as it is not the boot disk?

If it's not the boot disk, it cannot be mounted, even in the original server. I went ahead and booted off of it this morning to get the data I need, although I still have some purely academic curiosity as to why hardware RAID needs a special partition table that a single disk doesn't.

---

