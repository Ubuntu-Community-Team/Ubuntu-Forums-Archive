---
title: "lvm mount error"
date: 2011-06-04
forum: New to Ubuntu
---

### Post by capos on 2011-06-04
Hi all, 
  I have the following problem. I have created a logical volume group volume_group using lvm. This group contans the logical volume storage. Here is output from lvdisplay:

lvdisplay /dev/volume_group
  --- Logical volume ---
  LV Name                /dev/volume_group/storage
  VG Name                volume_group
  LV UUID                DA37EL-LZi9-yZ3n-NorC-nlnX-IOJM-ksYavQ
  LV Write Access        read/write
  LV Status              available
  # open                 0
  LV Size                6.81 TiB
  Current LE             1784704
  Segments               4
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           251:0

When I try to mount the logical volume storage to /mnt/storage using this command:

mount /dev/volume_group/storage /mnt/storage

I get the following error:


mount: you must specify the filesystem type

So I tried to add the fs type parameter 

mount -t ext4 /dev/volume_group/storage /mnt/storage

it generates the following error:

mount: wrong fs type, bad option, bad superblock on /dev/mapper/volume_group-storage,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

I am out of ideas of how to solve this problem. Please help me :)

---

### Post by coffee412 on 2011-06-04
> **capos said:**
> Hi all, 
  I have the following problem. I have created a logical volume group volume_group using lvm. This group contans the logical volume storage. Here is output from lvdisplay:

lvdisplay /dev/volume_group
  --- Logical volume ---
  LV Name                /dev/volume_group/storage
  VG Name                volume_group
  LV UUID                DA37EL-LZi9-yZ3n-NorC-nlnX-IOJM-ksYavQ
  LV Write Access        read/write
  LV Status              available
  # open                 0
  LV Size                6.81 TiB
  Current LE             1784704
  Segments               4
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           251:0

When I try to mount the logical volume storage to /mnt/storage using this command:

mount /dev/volume_group/storage /mnt/storage

I get the following error:


mount: you must specify the filesystem type

So I tried to add the fs type parameter 

mount -t ext4 /dev/volume_group/storage /mnt/storage

it generates the following error:

mount: wrong fs type, bad option, bad superblock on /dev/mapper/volume_group-storage,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

I am out of ideas of how to solve this problem. Please help me :)

If you follow the steps in the LVM howto listed here ---> [http://tldp.org/HOWTO/LVM-HOWTO/recipethreescsi.html](http://tldp.org/HOWTO/LVM-HOWTO/recipethreescsi.html) You shouldnt have any problems. Although the howto is using scsi drives you can get an idea of where you went wrong.

After the creation of the VG you create logical volume and then you need to format the LV. Did you miss that step?

Read here in the link above 
**13.1.1. Preparing the disks**

Hope that helps.

coffee

---

### Post by capos on 2011-06-04
Thank you for your reply. I was unable to solve this problem so I started from scratch using the gui tool system-config-lvm. It was really easy with this tool. I recommend.

---

