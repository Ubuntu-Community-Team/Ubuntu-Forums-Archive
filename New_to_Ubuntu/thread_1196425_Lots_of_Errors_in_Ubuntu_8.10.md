---
title: "Lots of Errors in Ubuntu 8.10"
date: 2009-06-24
forum: New to Ubuntu
---

### Post by melrokz on 2009-06-24
There seems to be a lot of errors in Ubuntu 8.10 lately.

1. > Nautilus cannot handle computer locations

This happens when I take Places>Computer from the menu.

2. > melvin@melvin-desktop:~$ fdisk -l
Cannot open /dev/sda
Cannot open /dev/sdb
Cannot open /dev/sdc

3. It does not automatically mount any removable disks.

4. When I manually try to mount a thumb drive, this is what I get:

> melvin@melvin-desktop:~$ sudo mount /dev/sdc /media/melvin
[sudo] password for melvin: 
mount: mount point /media/melvin does not exist
melvin@melvin-desktop:~$ sudo mkdir /media/melvin
melvin@melvin-desktop:~$ sudo mount /dev/sdc /media/melvin
mount: you must specify the filesystem type

5. Even sfdisk does not work: No output.

6. Partition editor shows my Creative zen stone plus mp3 player
   as unallocated 235.33 MB when it is actually 1GB and it does not get   mounted.

All these errors happened at once. Could have been due to:
1. installing the package 'nautilus-actions'
2. plugging in the mp3 player
or something else?

Please advice.

---

### Post by melrokz on 2009-06-24
reinstalling nautilus will work?

---

### Post by kansasnoob on 2009-06-24
I had endless trouble with Intrepid/8.10, and therefore I stuck with 8.04.2.

OTOH, Jaunty/9.04 has been extremely stable for me.

---

### Post by balachandarlinks on 2009-06-25
> melvin@melvin-desktop:~$ fdisk -l
Cannot open /dev/sda
Cannot open /dev/sdb
Cannot open /dev/sdc 

Try with sudo.It works fine for me in intrepid.

> It does not automatically mount any removable disks.

you need to edit the /etc/fstab file to automount your partitions.

Fully updating intrepid can solve your problem i hope.

---

### Post by melrokz on 2009-06-26
Is there any other solution other than an update?
It will take 13 hours to update on my modem...

Also, my dvd drive tray comes out and goes in at once, once i eject it. How to solve this?

---

