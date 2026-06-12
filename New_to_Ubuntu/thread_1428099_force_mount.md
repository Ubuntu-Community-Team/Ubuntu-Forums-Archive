---
title: "force mount"
date: 2010-03-12
forum: New to Ubuntu
---

### Post by travolter on 2010-03-12
hi,

I was having some troubles with windows so I decided to run ubuntu (8.04 I think) from USB to move my files from the c: drive to an external hard drive. But when I klicked on the 'boot'('boot' is the name of my c: drive) button it couldn't mount it. 
When I tried to force to mount it with the command given in the error screen it just didn't work.

Does anyone know what commnand line I should type in?

grtzz

---

### Post by Girya on 2010-03-12
> **travolter said:**
> hi,

I was having some troubles with windows so I decided to run ubuntu (8.04 I think) from USB to move my files from the c: drive to an external hard drive. But when I klicked on the 'boot'('boot' is the name of my c: drive) button it couldn't mount it. 
When I tried to force to mount it with the command given in the error screen it just didn't work.

Does anyone know what commnand line I should type in?

grtzz

probably a permission problem 

from the command line:

```
sudo fdisk -l
```
in the code below substitute /dev/sda1 with the partition that has ntfs on it. 

```
sudo mkdir /mnt/windows 
```

```
sudo mount -o ro -t ntfs /dev/sda1 /mnt/windows
```

the -o ro option mounts as read only so you wont accidentally delete something important

graphically:

```
sudo nautilus
```

---

### Post by travolter on 2010-03-12
alright thanks i'll try it out (i'm not at home now).

---

### Post by ajgreeny on 2010-03-12
If you windows install crashed and was not shut down properly, it is possible that your linux OS believes that the windows partition is still in use, and therefore will not be able to mount it without the "force" option to the mount command.

Try using the terminal in the USB Ubuntu OS with the command to make the mountpoint ```
sudo mkdir /media/ntfs
``` and then to mount the partition use ```
sudo mount -t ntfs-3g /dev/sda1 /media/ntfs -o force
```This assumes, of course that sda1 is the windows partition that you want.  If it is another partition substitute the dev name sda1 for your situation.

---

### Post by Girya on 2010-03-12
another option is to use the most excellent system rescue cd (or usb stick)
it has a better feature set than ubuntu for dealing with pita windows partitions. 

ajgreeny's post reminded me of a computer that i tried to mount from a live ubuntu cd and couldn't. the system rescue cd mounted the partition almost automatically.

---

### Post by travolter on 2010-03-12
> **ajgreeny said:**
> If you windows install crashed and was not shut down properly, it is possible that your linux OS believes that the windows partition is still in use, and therefore will not be able to mount it without the "force" option to the mount command.

Try using the terminal in the USB Ubuntu OS with the command to make the mountpoint ```
sudo mkdir /media/ntfs
``` and then to mount the partition use ```
sudo mount -t ntfs-3g /dev/sda1 /media/ntfs -o force
```This assumes, of course that sda1 is the windows partition that you want.  If it is another partition substitute the dev name sda1 for your situation.

hey thanks because that's what the pop-up said: something about the drive being in use by windows and that I have to shut-down windows properly and if I don't have windows intalles i should try .... .

---

### Post by bodhi.zazen on 2010-03-12
IMO, when you have to force a mount, the nfts partition is in need of repair.

IMO the best way to do this is by checking the partition / flash drive in Windows and allowing windows to repair the partition.

IMO using the force option should be viewed as a temporary fix to be used when you need to pull the data.

You can try ntfsfix

[http://man.linux-ntfs.org/ntfsfix.8.html](http://man.linux-ntfs.org/ntfsfix.8.html)

but in the past it did not do so well (have not tried it recently).

Be warned, mounting with the force option can result in data loss.

If you do not have a windows box I suggest you convert the partition to a linux native format.

---

