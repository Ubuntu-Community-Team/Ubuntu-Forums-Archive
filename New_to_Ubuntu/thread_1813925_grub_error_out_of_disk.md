---
title: "grub error out of disk"
date: 2011-07-28
forum: New to Ubuntu
---

### Post by factorialpython on 2011-07-28
grub error out of disk; so cqn boot CO?PUTER; stqrt zith live CD; 
sudo fdisk -l

Disque /dev/sda: 20.4 Go, 20416757760 octets
255 têtes, 63 secteurs/piste, 2482 cylindres
Unités = cylindres de 16065 * 512 = 8225280 octets
Identifiant de disque : 0x000b15a6

Périphérique Amorce  Début        Fin      Blocs     Id  Système
/dev/sda1   *           1        2373    19061091   83  Linux
/dev/sda2            2374        2482      875542+   5  Etendue
/dev/sda5            2374        2482      875511   82  Linux swap / Solaris

what can i do to get it to work properly9i i am a super newbie got this results fro, watching videos

---

### Post by oldfred on 2011-07-28
I would try to reinstall grub.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10) - talsemgeest
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
Reinstall grub2 - Short version & full chroot version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2)

Some other suggestions but the line numbers have changed with newer version of grub2.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Out_Of_Disk](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Out_Of_Disk)

---

