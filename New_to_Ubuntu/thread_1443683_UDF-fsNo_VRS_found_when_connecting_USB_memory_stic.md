---
title: "UDF-fs:No VRS found when connecting USB memory stick"
date: 2010-03-31
forum: New to Ubuntu
---

### Post by Pierrot Lafouine on 2010-03-31
Hi
I installed Ubuntu 8.04 on Eee PC 1005HA (not the Netbook Remix, because I didn't know about it).

I have USB problem, when I insert USB stick (2GBytes FAT32), I got a DialogBox saying :
Cannot mount volume, Invalid mount option when attempting to mount the volume.

I tried this
```
sudo mkdir /media/windows
sudo mount /dev/sdb /media/windows -o force
```
Got this error message : 
mount : you must specify the filesystem type

I tried this :
```
sudo mount /dev/sdb /media/windows -o force -t vfat
```

Got this error message : 
mount: wrong fs type, bad option, bad supperblock on /dev/sdb etc...

Doing this code :
```
dmesg | tail
```
I got this error :
UDF-fs:No VRS found
ISOFS: Unable to identify CD-ROM format

I have 2 stick, 2GB and 4GB, they are working on other Ubuntu system, and on Windoz XP system.  Stick are ok.

What is the best way to fix this ?
Can I "upgrade" to UNR ?
My disk is share with Windows XP sp3.

Thanks!

---

### Post by Pierrot Lafouine on 2010-03-31
Any ideas I could try ?

---

### Post by Pierrot Lafouine on 2010-03-31
Hi
Can the USB key have invisible partition ?
Maybe an invisible NTFS or bootable partition ?
Data is visible under Windows and is FAT32
Thanks

---

