---
title: "LVM with loopback files on FAT32 partition"
date: 2008-07-08
forum: Networking &amp; Wireless
---

### Post by tramir on 2008-07-08
OK, so here's the situation: I have a NAS that accepts only FAT32-formatted hard disks. I am trying to create an ext3 partition on it to sync/backup my home partition. The way I found (still open to suggestions) is to create a bunch of files, assign them to loopback devices with losetup, and create an  LVM (please ignore the inefficiencies of the code - noob here):

```
MNTPT="/media/Mircea_Backup"
PART_LIST=""

for i in $(seq 1 5); do 
  j=$(printf %02d $i)
  dd if=/dev/zero of=$MNTPT/ext3_part${j} bs=4096 count=1500
done

for i in $( ls $MNTPT/ext3_part* ); do
  j=${i:30:3}
  k=$(($((10#$j)) - 1))
  echo "sudo losetup /dev/loop${k} ${i}"
  sudo losetup /dev/loop${k} ${i}
  PART_LIST="${PART_LIST} /dev/loop${k}"
done
sudo pvcreate ${PART_LIST}
sudo vgcreate backupsys ${PART_LIST}
sudo lvcreate --name bckup --extents 100%FREE backupsys
sudo mkfs.ext3 /dev/backupsys/bckup
```
It all works fine, or at least it seems to. The problem is when I disconnect from the NAS or reboot. The vg is lost, and if I try to retrace my steps (losetup, pvcreate, vgcreate etc), it doesn't recognize the already-existing partition etc. I know I'm doing something wrong, but I don't really know what (it's my first attempt to work with LVM). Can somebody help me here? What should I do to make sure I can still access/recreate the LVM even after disconnecting from the NAS or rebooting? Or, God forbid, upgrade Ubuntu :) TIA

---

### Post by tramir on 2008-07-08
Anybody? Any ideas?

---

