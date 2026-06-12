---
title: "Mount HDD"
date: 2008-12-16
forum: New to Ubuntu
---

### Post by raphi11 on 2008-12-16
I installed the ubuntu 8.04 on my USB-Stick, and so i boot from USB-Stick, now I want to read my files from my Computer. I click at 160,0 GB Medium but :

Cannot mount Volume
Unable to mount volume
Details->
mount: wrong fs-type, bad option, bad superblock on dev/sda1, missing codepage or helper program or other error     in some cases useful info is found in syslog- try    dmesg| tail or so

Unable to mount volume:

DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.






what shall i do/ download/ install/ try

thx, raphi

---

### Post by davidbilla on 2008-12-16
Did you try doing it in the command line?
For example, do something like the following, with appropriate changes for the device name and mount point.
```

$ sudo mount -t vfat /dev/sdc1/ /media/disk/
```

Use 'vfat' if it's a FAT32(Windows) partition or 'ext3' if it is Linux. Try it and see what error message you get, if any.

---

### Post by Michael.Godawski on 2008-12-16
hi raphi11, 
let's check what ubuntu from the usb stick actaully sees:
run these commands in terminal and post the output

```
sudo fdisk -l
mount
```

---

### Post by raphi11 on 2008-12-16
sorry for the german, hope you "understand" it


Platte /dev/sda: 160.0 GByte, 160041885696 Byte
255 Köpfe, 63 Sektoren/Spuren, 19457 Zylinder
Einheiten = Zylinder von 16065 × 512 = 8225280 Bytes
Disk identifier: 0x2e46578f

   Gerät  boot.     Anfang        Ende     Blöcke   Id  System
/dev/sda1   *           1       19456   156280288+   7  HPFS/NTFS

Platte /dev/sdb: 4114 MByte, 4114612224 Byte
255 Köpfe, 63 Sektoren/Spuren, 500 Zylinder
Einheiten = Zylinder von 16065 × 512 = 8225280 Bytes
Disk identifier: 0x03f45643

   Gerät  boot.     Anfang        Ende     Blöcke   Id  System
/dev/sdb1   *           1         471     3783276   83  Linux
/dev/sdb2             472         500      232942+   5  Erweiterte
/dev/sdb5             472         500      232911   82  Linux Swap / Solaris

---

### Post by raphi11 on 2008-12-16
@ davidbilla



mount: Einhängepunkt /media/disk/ existiert nicht

---

### Post by Michael.Godawski on 2008-12-16
You are lucky that I speak German fluently... ):P aber ich bleib beim Englischem, damit alle  was davon haben :p.

Please post also your fstab file. To mount a ntfs partition you need ntfs-3g driver.
[https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions)
[https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G](https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G)

```
 cat /etc/fstab
```

---

### Post by raphi11 on 2008-12-16
sorry war essen

you mean this?


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=74a971ca-1017-4025-95e7-e5adea205c5c /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb5
UUID=ef9d5ff2-196b-4db0-bd75-5c0f608fef32 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

---

### Post by raphi11 on 2008-12-16
shows still the same error when i install the ntfs driver

---

### Post by theozzlives on 2008-12-16
Try to mount the HDD using the live CD

---

### Post by raphi11 on 2008-12-16
The ubuntu livecd ?

---

