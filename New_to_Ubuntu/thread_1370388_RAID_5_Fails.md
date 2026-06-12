---
title: "RAID 5 Fails"
date: 2010-01-02
forum: New to Ubuntu
---

### Post by rkstanfi on 2010-01-02
I am new to Linux. I have successfully installed Linux onto a new computer but I am having trouble with RAID set-up. My set-up includes 5 hard disks (4 1TB hard drives and a 320 GB for the OS). As currently setup the 320 GB is set into 4 partitions: 28 GB for root, 10 GB for swap, 4 GB for boot, and the remainder for home. I am trying to use the 4 1TB hard drives in RAID 5 configuration. I can get it to the point where it sees a 3001 GB RAID 5 drive. At this point I restart the PC and the RAID-5 drive is shown as various sized partitions. Any ideas would be appreciated. (I have tried to setup the /etc/fstab file, but fear it is setup incorrectly.)

Also, Palimpsest Disk Utility shows all four 1TB hard drives as "In Sync", I thought one would be listed as spare, anyone know if this is correct?

/etc/mdadm/mdadm.conf:

ARRAY /dev/md0 level=raid5 num-devices=4 UUID=00104ddf:03b78ef1:5803c9f3:8b278658 devices=/dev/sdb1,/dev/sdc1,/dev/sdd1,/dev/sde1

/etc/fstab:
/dev/md0    /media/FileStreamer    ntfs    defaults    1 2

Thanks.

---

