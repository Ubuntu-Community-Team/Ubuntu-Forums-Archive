---
title: "How to resize a pv, gv, and lv after increasing my iSCSI volume size"
date: 2009-11-11
forum: New to Ubuntu
---

### Post by maushana on 2009-11-11
Hi, I'm new to Ubuntu 9.04 and wanted to see if someone could help by shedding some light on how I can do the following:

1) I have an iSCSI volume that I want to mount and use to store my files on.
2) I want to be able to increase the size of the iSCSI volume when ever I need to store more data as I need it.

So far, I'm able to setup the iSCSI and mount to it via open-iscsi package. I've also setup and created a Linux LVM using fdisk (8e) file system on the iSCSI drive and also created a PV, VG, and LV to allow me to resize the volume. But I'm having issues resizing my PV, VG, and LV after the iSCSI size is increased. I've reviewed a few different posts which say it's possible to do this  but I can't seem to get it to work for me. If someone could point me in the right direction on how I can get this done it would be greatly appreciated. The volume is not yet live so I can delete it and recreated if need to. I appreciate any help you can provide.

Thank you,

Mike

---

### Post by maushana on 2009-11-12
Can anyone help with this? Should I be posting this in another place?

---

### Post by ukripper on 2009-11-12
> **maushana said:**
> Hi, I'm new to Ubuntu 9.04 and wanted to see if someone could help by shedding some light on how I can do the following:

1) I have an iSCSI volume that I want to mount and use to store my files on.
2) I want to be able to increase the size of the iSCSI volume when ever I need to store more data as I need it.

So far, I'm able to setup the iSCSI and mount to it via open-iscsi package. I've also setup and created a Linux LVM using fdisk (8e) file system on the iSCSI drive and also created a PV, VG, and LV to allow me to resize the volume. But I'm having issues resizing my PV, VG, and LV after the iSCSI size is increased. I've reviewed a few different posts which say it's possible to do this  but I can't seem to get it to work for me. If someone could point me in the right direction on how I can get this done it would be greatly appreciated. The volume is not yet live so I can delete it and recreated if need to. I appreciate any help you can provide.

Thank you,

Mike

what commands are you using to resize your volume group?

---

### Post by maushana on 2009-11-12
Hi ukripper, thanks for the reply. I'm using the instructions on this page as a guide:

[http://wiki.linuxquestions.org/wiki/LVM](http://wiki.linuxquestions.org/wiki/LVM)

Here is what I'm trying to do:

1) I setup 100GB on my iscsi volume to be used on my ubuntu box
2) I connect to the iscsi using open-iscsi and all is well
3) I run through the guide above to create my partion etc. All works well up to hear. 
4) I go back to my iscsi volume and I resize it to 200GB. What do I need to do to allow my ubuntu box to start using the new 200GB size?

This is where I'm stuck. Any help with this is appreciated.

Thank you,

Mike

---

### Post by ukripper on 2009-11-12
Can you run below commands so i know what is the structure of your PV, VG, LV and sfdisk stat:

```
lvdisplay
```

```
pvdisplay
```

```
vgdisplay
```

```
sudo sfdisk -l
```

---

### Post by maushana on 2009-11-12
Hi ukripper, please note I've been playing with these options so things are bit wacky below. I can delete everything start fresh if needed. Thanks for all your help on this.
[B]
lvdisplay:[/B]
  --- Logical volume ---
  LV Name /dev/vg-dbc/lv-dbcdata
  VG Name vg-dbc
  LV UUID gucVIp-fBuU-CXqj-9NX1-MoaZ-40GH-EYEwqr
  LV Write Access read/write
  LV Status available
  # open 0
  LV Size 76.49 GB
  Current LE 19581
  Segments 1
  Allocation inherit
  Read ahead sectors auto
  - currently set to 256
  Block device 252:2
   
  --- Logical volume ---
  LV Name /dev/DBC2/root
  VG Name DBC2
  LV UUID xKUD3H-9hlS-bMWx-skGc-BCMS-6Et9-Afo4tD
  LV Write Access read/write
  LV Status available
  # open 1
  LV Size 47.66 GB
  Current LE 12200
  Segments 1
  Allocation inherit
  Read ahead sectors auto
  - currently set to 256
  Block device 252:0
   
  --- Logical volume ---
  LV Name /dev/DBC2/swap_1
  VG Name DBC2
  LV UUID ErfjVS-FRN3-emFl-6XEj-7epe-HOGJ-bK0DGS
  LV Write Access read/write
  LV Status available
  # open 2
  LV Size 2.07 GB
  Current LE 531
  Segments 1
  Allocation inherit
  Read ahead sectors auto
  - currently set to 256
  Block device 252:1

**pvdisplay:**
  --- Physical volume ---
  PV Name /dev/sdb1
  VG Name vg-dbc
  PV Size 150.00 GB / not usable 2.03 MB
  Allocatable yes
  PE Size (KByte) 4096
  Total PE 38399
  Free PE 18818
  Allocated PE 19581
  PV UUID 3e7LSl-gKWG-T0lK-GjG3-tdaK-IWZD-8bbWzY
   
  --- Physical volume ---
  PV Name /dev/sda1
  VG Name DBC2
  PV Size 49.76 GB / not usable 4.14 MB
  Allocatable yes
  PE Size (KByte) 4096
  Total PE 12738
  Free PE 7
  Allocated PE 12731
  PV UUID 2MuBkM-JKOs-31M1-xsPO-LN8E-RbPJ-LWQZ7N
   
**vgdisplay:**
  --- Volume group ---
  VG Name vg-dbc
  System ID
  Format lvm2
  Metadata Areas 1
  Metadata Sequence No 2
  VG Access read/write
  VG Status resizable
  MAX LV 0
  Cur LV 1
  Open LV 0
  Max PV 0
  Cur PV 1
  Act PV 1
  VG Size 150.00 GB
  PE Size 4.00 MB
  Total PE 38399
  Alloc PE / Size 19581 / 76.49 GB
  Free PE / Size 18818 / 73.51 GB
  VG UUID o9gVaD-epCO-TYIc-5HeP-mfdr-Lgwg-8ZooeO
   
  --- Volume group ---
  VG Name DBC2
  System ID
  Format lvm2
  Metadata Areas 1
  Metadata Sequence No 3
  VG Access read/write
  VG Status resizable
  MAX LV 0
  Cur LV 2
  Open LV 2
  Max PV 0
  Cur PV 1
  Act PV 1
  VG Size 49.76 GB
  PE Size 4.00 MB
  Total PE 12738
  Alloc PE / Size 12731 / 49.73 GB
  Free PE / Size 7 / 28.00 MB
  VG UUID M9M7WT-kP6K-9Bag-71wQ-iBpE-HYnT-YCRdYb
   
**sfdisk -l:**
Disk /dev/sda: 6527 cylinders, 255 heads, 63 sectors/track Units = 
cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0
   Device Boot Start End #cyls #blocks Id System /dev/sda1 * 0+ 6495 
6496- 52179088+ 8e Linux LVM /dev/sda2 6496 6526 31 249007+ 5 Extended 
/dev/sda3 0 - 0 0 0 Empty /dev/sda4 0 - 0 0 0 Empty /dev/sda5 6496+ 6526 
31- 248976 83 Linux Disk /dev/sdb: 20887 cylinders, 255 heads, 63 
sectors/track Units = cylinders of 8225280 bytes, blocks of 1024 bytes, 
counting from 0
   Device Boot Start End #cyls #blocks Id System /dev/sdb1 0+ 19580 
19581- 157284382 8e Linux LVM /dev/sdb2 0 - 0 0 0 Empty /dev/sdb3 0 - 0 
0 0 Empty /dev/sdb4 0 - 0 0 0 Empty

---

### Post by ukripper on 2009-11-12
> **maushana said:**
> Hi ukripper, thanks for the reply. I'm using the instructions on this page as a guide:

[http://wiki.linuxquestions.org/wiki/LVM](http://wiki.linuxquestions.org/wiki/LVM)

Here is what I'm trying to do:

1) I setup 100GB on my iscsi volume to be used on my ubuntu box
2) I connect to the iscsi using open-iscsi and all is well
3) I run through the guide above to create my partion etc. All works well up to hear. 
4) I go back to my iscsi volume and I resize it to 200GB. What do I need to do to allow my ubuntu box to start using the new 200GB size?

This is where I'm stuck. Any help with this is appreciated.

Thank you,

Mike

you need PV expansion as you have added another 100GB . Therefore, follow this guide in the link:
[http://muzso.hu/2009/07/28/how-to-resize-an-lvm-physical-volume-without-a-reboot](http://muzso.hu/2009/07/28/how-to-resize-an-lvm-physical-volume-without-a-reboot)

---

### Post by maushana on 2009-11-12
ukripper, thank you very much for this. I will try the link you posted and report back on how it all went.

Thank you,

Mike

---

### Post by maushana on 2009-11-13
ukripper, the link you gave worked perfectly.  I tested things by resizing the volume several times and the volumes are resizing the way they should be. Thank you so much for all your help :)

Mike

---

### Post by ukripper on 2009-11-13
i am glad it is working out for you! Enjoy

---

