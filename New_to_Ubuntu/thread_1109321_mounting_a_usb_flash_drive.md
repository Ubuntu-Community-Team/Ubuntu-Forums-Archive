---
title: "mounting a usb flash drive"
date: 2009-03-28
forum: New to Ubuntu
---

### Post by alex80 on 2009-03-28
Trying to mount a usb flash drive, my question is how do I find out which one is it? i.e. for my normal drive it's /sda1 for example

---

### Post by halitech on 2009-03-28
with it unplugged, run ```
sudo fdisk -l
```then plug it in and run the command again. the new one will be the thumb drive.

---

### Post by Delta28 on 2009-03-28
It should be on your computer then just get the flash that matches what our computer says if its not "ON" your computer check in your Applications once you start up your computer...

By "ON" your computer I mean like on the outside of your computer like the tower or laptop *HELPFUL TIP TO THIS* your computer doesn't need power for this lol:P

---

### Post by alex80 on 2009-03-28
> **halitech said:**
> with it unplugged, run ```
sudo fdisk -l
```then plug it in and run the command again. the new one will be the thumb drive.

it shows the same thing when plugged or unplugged. I can see the usb drive in computer though.
```
/dev/sda1               1        2432    19535008+  83  Linux
/dev/sda2   *        2433       24320   175815360    7  HPFS/NTFS
```

---

### Post by alex80 on 2009-03-28
> **Delta28 said:**
> It should be on your computer then just get the flash that matches what our computer says if its not "ON" your computer check in your Applications once you start up your computer...

By "ON" your computer I mean like on the outside of your computer like the tower or laptop *HELPFUL TIP TO THIS* your computer doesn't need power for this lol:P

i can see it among other drives but when I click it says unable to mount

---

### Post by halitech on 2009-03-28
how did you install Ubuntu? it should look more like this
```
daryl@debian-desktop:~$ sudo fdisk -l

Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0005d3c5

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1          30      240943+  83  Linux
/dev/hda2              31        3069    24410767+  83  Linux
/dev/hda3            3070        3251     1461915   82  Linux swap / Solaris
/dev/hda4            3252       19457   130174695   83  Linux

Disk /dev/sdf: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00037614

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1               1       19457   156288321   83  Linux
daryl@debian-desktop:~$ 
```

---

### Post by Delta28 on 2009-03-28
:guitar:chill out I'm sure you will figure it out...try a diff flash if you have one?:guitar:

---

### Post by lean-mini on 2009-03-28
I have the same problem:

lean@lean-minihp:~$ sudo fdisk -l

Disco /dev/sda: 120.0 GB, 120034123776 bytes
255 cabezas, 63 sectores/pista, 14593 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Identificador de disco: 0x0002a4f9

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *           1       14264   114575548+  83  Linux
/dev/sda2           14265       14593     2642692+   5  Extendida
/dev/sda5           14265       14593     2642661   82  Linux swap / Solaris

Disco /dev/sdb: 1999 MB, 1999568384 bytes
255 cabezas, 63 sectores/pista, 243 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Identificador de disco: 0x0217934c

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sdb1   *           1         244     1952672    b  W95 FAT32
La partición 1 tiene distintos finales físicos/lógicos:
     físicos=(242, 254, 63) lógicos=(243, 25, 37)

I hope to resolve...
-----------------------------------------------------------------------
RESOLVED!!
 
sudo mount /dev/sdb1 media/usb

[sdb1] is for me the usb flash drive, if you do not know what sudo fdisk -l

As they say, Hope is the last TO LOSE
Gracias (THANKS)
lean

---

### Post by halitech on 2009-03-28
> **alex80 said:**
> it shows the same thing when plugged or unplugged. I can see the usb drive in computer though.
```
/dev/sda1               1        2432    19535008+  83  Linux
/dev/sda2   *        2433       24320   175815360    7  HPFS/NTFS
```

something doesn't look right here. is this the entire output or did you remove lines?

---

### Post by halitech on 2009-03-28
> **lean-mini said:**
> I have the same problem:

lean@lean-minihp:~$ sudo fdisk -l

Disco /dev/sda: 120.0 GB, 120034123776 bytes
255 cabezas, 63 sectores/pista, 14593 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Identificador de disco: 0x0002a4f9

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *           1       14264   114575548+  83  Linux
/dev/sda2           14265       14593     2642692+   5  Extendida
/dev/sda5           14265       14593     2642661   82  Linux swap / Solaris

Disco /dev/sdb: 1999 MB, 1999568384 bytes
255 cabezas, 63 sectores/pista, 243 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Identificador de disco: 0x0217934c

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sdb1   *           1         244     1952672    b  W95 FAT32
La partición 1 tiene distintos finales físicos/lógicos:
     físicos=(242, 254, 63) lógicos=(243, 25, 37)

I hope to resolve.
lean

your usb drive is [color=red]/dev/sdb1[/color]

you should see an icon on the desktop that you can click to mount or through Places menu

---

### Post by halavin on 2009-03-28
you can also do this : 

umount your usb drive and run this.
tune2fs -L JumpDrive /dev/sdX

 Take  your jumpdrive out and insert it back in

now do this
cd /mnt/JumpDrive

---

### Post by lean-mini on 2009-03-28
> **halitech said:**
> your usb drive is [color=red]/dev/sdb1[/color]

you should see an icon on the desktop that you can click to mount or through Places menu

I have the icon (places), but when trying to mount tells me that can not be mounted. like when you connect.
lean

---

### Post by newbee70 on 2009-03-29
What is the output of the mount command in terminal?

```
 mount 
```

---

### Post by lean-mini on 2009-03-30
> **newbee70 said:**
> What is the output of the mount command in terminal?

```
 mount 
```

lean@lean-minihp:~$ mount
/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-23-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
gvfs-fuse-daemon on /home/lean/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=lean)
lean@lean-minihp:~$ 
--------------------------------------------------------------------------------------------
sudo mount /dev/sdb1 media/usb

[sdb1] is for me the usb flash drive, if you do not know what sudo fdisk -l

Gracias
lean.

---

