---
title: "ubuntu 10.04 on eeePC"
date: 2011-05-07
forum: New to Ubuntu
---

### Post by jrev on 2011-05-07
I just installed Ubuntu 10.04 on the second HD of an Asus eeePC 900.laptop.
After reboot I got the alarm :
Grub error 15

I think Grub has been installed on the sda1 folder by default when the system is installed on sdb.

What shall I do now ?

Thanks

---

### Post by jrev on 2011-05-07
ubuntu@ubuntu:~$ sudo fdisk -l

Disque /dev/sda: 4034 Mo, 4034838528 octets
255 têtes, 63 secteurs/piste, 490 cylindres
Unités = cylindres de 16065 * 512 = 8225280 octets
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Identifiant de disque : 0x00029e23

Périphérique Amorce  Début        Fin      Blocs     Id  Système
/dev/sda1   *           1         462     3708928   83  Linux
La partition 1 ne se termine pas sur une frontière de cylindre.
/dev/sda2             462         491      228353    5  Etendue
La partition 2 ne se termine pas sur une frontière de cylindre.
/dev/sda5             462         491      228352   82  Linux swap / Solaris

Disque /dev/sdb: 8069 Mo, 8069677056 octets
255 têtes, 63 secteurs/piste, 981 cylindres
Unités = cylindres de 16065 * 512 = 8225280 octets
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Identifiant de disque : 0x0005932e

Périphérique Amorce  Début        Fin      Blocs     Id  Système
/dev/sdb1               1         853     6851691   83  Linux
/dev/sdb2             854         981     1028129+   5  Etendue
/dev/sdb5             854         981     1028128+  82  Linux swap / Solaris

---

### Post by frankbooth on 2011-05-07
You can reinstall GRUB using the Rescue option on a LiveCD.
I'm not 100% sure if this options is available on the "normal" cds, since I always use the alternate install-cd.

Once you're in rescue mode it's pretty simple, follow a few instructions and then choose to install GRUB (it's given as an option).

---

### Post by jrev on 2011-05-07
see [http://forum.ubuntu-fr.org/viewtopic.php?id=482711](http://forum.ubuntu-fr.org/viewtopic.php?id=482711)
for more informations.
Thanks :P

I need some information on the command lines to type to fix the problem
Thanks

---

### Post by jrev on 2011-05-08
Anybody there ?

---

