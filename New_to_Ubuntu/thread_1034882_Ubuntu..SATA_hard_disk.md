---
title: "Ubuntu..SATA hard disk"
date: 2009-01-09
forum: New to Ubuntu
---

### Post by sajixavier on 2009-01-09
Hi
i created a usb startup disk using Ubuntu 8.10 and connected to a machine containing a sata hard disk. Everything else was detected but didn't detect the sata hard disk...what should i do

---

### Post by talsemgeest on 2009-01-09
Can you please post the output of ```
sudo fdisk -l
```

---

### Post by supererki on 2009-01-09
If you are using 2.6.24 kernel you can try turning the Advanced Host Controller Interface on from your BIOS.

---

### Post by 73ckn797 on 2009-01-09
> **supererki said:**
> If you are using 2.6.24 kernel you can try turning the Advanced Host Controller Interface on from your BIOS.


That would also be known as AHCI. That works for me with 1 IDE and 2 SATA drives. In BIOS there are 3 settings I can choose: IDE, AHCI or RAID. I do not know what your BIOS has to select from.

---

### Post by sajixavier on 2009-01-11
```

Disk /dev/sda: 4022 MB, 4022337536 bytes
255 heads, 63 sectors/track, 489 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x04030201

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         489     3927861    c  W95 FAT32 (LBA)
```

---

