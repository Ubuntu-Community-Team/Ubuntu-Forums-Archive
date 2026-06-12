---
title: "Recognising partitions"
date: 2010-08-12
forum: New to Ubuntu
---

### Post by Gimly_axe on 2010-08-12
Dear all,

I am trying to fresh install 10.4 after a not so good experience with the upgrade.

The problem is that  I have two hard drives and one of them has ubuntu as a partition. But I can't figure out which is which. What I'd like to do is to:

1) format the old windows drive (as I'm not going to need it anymore).
2) Install ubuntu 10.4 there as a fresh install.
3) if possible, use the other disk as my home directory for future installations.

[IMG]http://ubuntuforums.org/home/beowulf/Im%C3%83%C2%A1genes/GParted.png[/IMG]

This is a picture of Gparted analysis. Can anyone help me identify the different parts, please?

Thanks

---

### Post by plucky on 2010-08-12
> **Gimly_axe said:**
> Dear all,

I am trying to fresh install 10.4 after a not so good experience with the upgrade.

The problem is that  I have two hard drives and one of them has ubuntu as a partition. But I can't figure out which is which. What I'd like to do is to:

1) format the old windows drive (as I'm not going to need it anymore).
2) Install ubuntu 10.4 there as a fresh install.
3) if possible, use the other disk as my home directory for future installations.

[IMG]http://ubuntuforums.org/home/beowulf/Im%C3%83%C2%A1genes/GParted.png[/IMG]

This is a picture of Gparted analysis. Can anyone help me identify the different parts, please?

Thanks

That image shows two NTFS partitions on an 80Gb drive.

Did you do a WUBI install?

Post output from a terminal **(Application > Accessories > Terminal)** for ```
sudo fdisk -l
```

---

### Post by Mark Phelps on 2010-08-12
Looks like you installed Ubuntu using Wubi in /sda5 -- and if you remove MS Windows, you will no longer have access to that.

---

### Post by Gimly_axe on 2010-08-13
Sorry I couldn't answer earlier.

here is what the console gave me:

Disco /dev/sda: 80.0 GB, 80026361856 bytes
255 cabezas, 63 sectores/pista, 9729 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Tamaño de sector (lógico / físico): 512 bytes / 512 bytes
Tamaño E/S (mínimo/óptimo): 512 bytes / 512 bytes
Identificador de disco: 0x31333133

Dispositivo Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *           1        5099    40957686    7  HPFS/NTFS
/dev/sda2            5100        9728    37182442+   f  W95 Ext'd (LBA)
/dev/sda5            5100        9728    37182411    7  HPFS/NTFS

Disco /dev/sdb: 80.0 GB, 80026361856 bytes
255 cabezas, 63 sectores/pista, 9729 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Tamaño de sector (lógico / físico): 512 bytes / 512 bytes
Tamaño E/S (mínimo/óptimo): 512 bytes / 512 bytes
Identificador de disco: 0x5dc50b96

Dispositivo Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sdb1               1        9352    75119908+  83  Linux
/dev/sdb2            9353        9729     3028252+   5  Extendida
/dev/sdb5            9353        9729     3028221   82  Linux swap / Solaris


Thanks for the help

---

### Post by eriktheblu on 2010-08-13
Ok, you have 2 physical disks, not just two partitions.

Your Ubuntu install is on your SDB disk (which is not shown in the Gparted screenshot).

The partitions on SDA are all NTFS (Windows format). These are likely your C: and D: drives.

I would start with a extended partition on SDA, within it a 256MB partition for /boot, 20-30GB for / (depending on how much software you use), and a swap partition equal to half your memory (adjust as needed). The rest can be left unformatted for future unanticipated needs.

On SDB, create an equal size swap partition (when swap is spread over two drives, it supposedly performs better) and use the rest for /home.

Make sure to back up any data before formatting.

---

### Post by Gimly_axe on 2010-08-14
Thanks a lot. I've marked it as solved.

Very informative and clear for such a new user as me.

---

