---
title: "Won't recognize my external hard drive"
date: 2009-10-14
forum: New to Ubuntu
---

### Post by masontgreen on 2009-10-14
I have an external 250 gb Seagate HDD and I've never been able to get Ubuntu to even acknowledge its existence. Please help me as it has all of my files and info on it. If it helps, it's formatted as fat32 I think.

---

### Post by nothingspecial on 2009-10-14
With it plugged in type

```
lsusb
```

```
sudo fdisk -l
```

Then unplug and plug it back in again and type
```

dmesg | tail
```

Post all output here.

---

### Post by masontgreen on 2009-10-14
[ 3296.833938] sd 3:0:0:0: [sdb] Write Protect is off
[ 3296.833946] sd 3:0:0:0: [sdb] Mode Sense: 27 00 00 00
[ 3296.833949] sd 3:0:0:0: [sdb] Assuming drive cache: write through
[ 3296.835247] sd 3:0:0:0: [sdb] 488397168 512-byte hardware sectors (250059 MB)
[ 3296.836117] sd 3:0:0:0: [sdb] Write Protect is off
[ 3296.836123] sd 3:0:0:0: [sdb] Mode Sense: 27 00 00 00
[ 3296.836127] sd 3:0:0:0: [sdb] Assuming drive cache: write through
[ 3296.836137]  sdb: sdb1
[ 3296.856475] sd 3:0:0:0: [sdb] Attached SCSI disk
[ 3296.856532] sd 3:0:0:0: Attached scsi generic sg3 type 0

---

### Post by nothingspecial on 2009-10-14
what do the other 2 commands output?

---

### Post by masontgreen on 2009-10-14
Entirety:
smokey@Dimension-desktop:~$ lsub
bash: lsub: command not found
smokey@Dimension-desktop:~$ sudo fdisk -l
[sudo] password for smokey: 

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5c4a5c4a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       38349   308038311   83  Linux
/dev/sda2           38350       38913     4530330    5  Extended
/dev/sda5           38350       38913     4530298+  82  Linux swap / Solaris

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xeef844d8

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       30401   244196001    c  W95 FAT32 (LBA)
smokey@Dimension-desktop:~$ dmesg | tail
[ 3296.833938] sd 3:0:0:0: [sdb] Write Protect is off
[ 3296.833946] sd 3:0:0:0: [sdb] Mode Sense: 27 00 00 00
[ 3296.833949] sd 3:0:0:0: [sdb] Assuming drive cache: write through
[ 3296.835247] sd 3:0:0:0: [sdb] 488397168 512-byte hardware sectors (250059 MB)
[ 3296.836117] sd 3:0:0:0: [sdb] Write Protect is off
[ 3296.836123] sd 3:0:0:0: [sdb] Mode Sense: 27 00 00 00
[ 3296.836127] sd 3:0:0:0: [sdb] Assuming drive cache: write through
[ 3296.836137]  sdb: sdb1
[ 3296.856475] sd 3:0:0:0: [sdb] Attached SCSI disk
[ 3296.856532] sd 3:0:0:0: Attached scsi generic sg3 type 0
smokey@Dimension-desktop:~$

---

### Post by nothingspecial on 2009-10-14
> **masontgreen said:**
> Entirety:
smokey@Dimension-desktop:~$ lsub
bash: lsub: command not found
smokey@Dimension-desktop:~$ sudo fdisk -l
[sudo] password for smokey: 

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5c4a5c4a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       38349   308038311   83  Linux
/dev/sda2           38350       38913     4530330    5  Extended
/dev/sda5           38350       38913     4530298+  82  Linux swap / Solaris
[COLOR="Red"]
Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xeef844d8

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       30401   244196001    c  W95 FAT32 [/COLOR](LBA)
smokey@Dimension-desktop:~$ dmesg | tail
[ 3296.833938] sd 3:0:0:0: [sdb] Write Protect is off
[ 3296.833946] sd 3:0:0:0: [sdb] Mode Sense: 27 00 00 00
[ 3296.833949] sd 3:0:0:0: [sdb] Assuming drive cache: write through
[ 3296.835247] sd 3:0:0:0: [sdb] 488397168 512-byte hardware sectors (250059 MB)
[ 3296.836117] sd 3:0:0:0: [sdb] Write Protect is off
[ 3296.836123] sd 3:0:0:0: [sdb] Mode Sense: 27 00 00 00
[ 3296.836127] sd 3:0:0:0: [sdb] Assuming drive cache: write through
[ 3296.836137]  sdb: sdb1
[ 3296.856475] sd 3:0:0:0: [sdb] Attached SCSI disk
[ 3296.856532] sd 3:0:0:0: Attached scsi generic sg3 type 0
smokey@Dimension-desktop:~$

There it is
```

sudo mkdir /media/drive
```
```

sudo mount -t vfat /dev/sdb1 /media/drive
```

All your files will now be in /media/drive

---

### Post by masontgreen on 2009-10-14
mount: special device /dev/sdbl does not exist

It doesn't make sense... when I hook it up to my other pc running Open Solaris, it recognizes it immediately. With Ubuntu, it says it doesn't exist...?

---

### Post by nothingspecial on 2009-10-14
That`s a number one not a little L

sdb[COLOR="Red"]1[/COLOR]

---

### Post by canadiandude007 on 2009-10-14
Make sure you are using a one '1' and not an el 'l' at the end:

Should be:

/dev/sdb1 not /dev/sdbl (which it looks like from your post)

---

### Post by masontgreen on 2009-10-14
Sorry. Noob mistake with the courrier font. Got it all worked out now. Thank you so much. You are something special to me.;)

---

### Post by masontgreen on 2009-10-14
Thanks canada. Sorry Calgary lost to Chicago...

---

### Post by masontgreen on 2009-10-14
Is there a way to rename "drive"?

*Verdana* not courrier...

---

### Post by nothingspecial on 2009-10-14
Here is the how to

[https://help.ubuntu.com/community/RenameUSBDrive](https://help.ubuntu.com/community/RenameUSBDrive)[COLOR="Magenta"][/COLOR]

---

### Post by masontgreen on 2009-10-14
Also... what's sudo? I don't really know programming, and I'm really wanting to learn enough to keep my head above water.

---

### Post by masontgreen on 2009-10-14
GParted doesn't recognize sdb, only sda...

---

### Post by masontgreen on 2009-10-14
n/m...I'm a moron...

---

### Post by nothingspecial on 2009-10-14
> **masontgreen said:**
> Also... what's sudo? I don't really know programming, and I'm really wanting to learn enough to keep my head above water.
Click This[[COLOR="Magenta"]https://help.ubuntu.com/community/RootSudo[/COLOR]]("https://help.ubuntu.com/community/RootSudo")

---

### Post by garnayden on 2010-02-03
> **nothingspecial said:**
> With it plugged in type

```
lsusb
``````
sudo fdisk -l
```Then unplug and plug it back in again and type
```

dmesg | tail
```Post all output here.

sorry nothingspecial

but I have the same error, I type the commands that you say and these are the results

natanael@nataUbuntu:~$ lsusb
Bus 002 Device 003: ID 1058:0704 Western Digital Technologies, Inc. 
Bus 002 Device 002: ID 064e:a101 Suyin Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
natanael@nataUbuntu:~$ sudo fdisk .l

No se puede abrir .l
natanael@nataUbuntu:~$ sudo fdisk -l

Disco /dev/sda: 160.0 GB, 160041885696 bytes
255 cabezas, 63 sectores/pista, 19457 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Identificador de disco: 0x7b17a491

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *           1        6751    54227376    7  HPFS/NTFS
/dev/sda2            6752        8884    17133322+  83  Linux
/dev/sda3            8885       19457    84927622+   5  Extendida
/dev/sda5            8885        9015     1052226   82  Linux swap / Solaris
/dev/sda6            9016       19457    83875333+   7  HPFS/NTFS
natanael@nataUbuntu:~$ 

natanael@nataUbuntu:~$ lsusb
Bus 002 Device 003: ID 1058:0704 Western Digital Technologies, Inc. 
Bus 002 Device 002: ID 064e:a101 Suyin Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
natanael@nataUbuntu:~$ sudo fdisk -l

Disco /dev/sda: 160.0 GB, 160041885696 bytes
255 cabezas, 63 sectores/pista, 19457 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Identificador de disco: 0x7b17a491

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *           1        6751    54227376    7  HPFS/NTFS
/dev/sda2            6752        8884    17133322+  83  Linux
/dev/sda3            8885       19457    84927622+   5  Extendida
/dev/sda5            8885        9015     1052226   82  Linux swap / Solaris
/dev/sda6            9016       19457    83875333+   7  HPFS/NTFS
natanael@nataUbuntu:~$ 


Please could you help me?

---

### Post by nothingspecial on 2010-02-03
What does ```
dmesg | tail
``` say?

---

### Post by garnayden on 2010-02-06
> **nothingspecial said:**
> What does ```
dmesg | tail
``` say?

Excuse I repeted the content...
dmesg | tail say me:

natanael@nataUbuntu:~$ dmesg | tail
[58341.784711] end_request: I/O error, dev sdb, sector 0
[58341.784721] Buffer I/O error on device sdb, logical block 0
[58341.789598] end_request: I/O error, dev sdb, sector 0
[58341.789610] Buffer I/O error on device sdb, logical block 0
[58341.790713] end_request: I/O error, dev sdb, sector 0
[58341.790723] Buffer I/O error on device sdb, logical block 0
[58341.790750] Dev sdb: unable to read RDB block 0
[58341.791703] end_request: I/O error, dev sdb, sector 0
[58341.791711] Buffer I/O error on device sdb, logical block 0
[58341.792709] end_request: I/O error, dev sdb, sector 0

Curious... I try with testdisk, and it show me a /dev/sdb link to my hard drive but I can't do nothing

---

