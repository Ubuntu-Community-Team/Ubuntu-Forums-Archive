---
title: "Usb FLASH doesn't work on Eee PC"
date: 2010-03-30
forum: New to Ubuntu
---

### Post by Pierrot Lafouine on 2010-03-30
Hi
I installed Ubuntu 8.04 on Eee PC 1005HA (not the Netbook Remix, because I didn't know about it).

I have USB problem, when I insert USB stick (2GBytes FAT32), I got a DialogBox saying : 
Cannot mount volume, Invalid mount option when attempting to mount the volume.

What is the best way to fix this ?
Can I "upgrade" to UNR ?
My disk is share with Windows XP sp3.

Thanks!

---

### Post by nene7 on 2010-03-30
hi i install UNR 9.10 in mi dell mini following the next step in: 
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick) 
if you have xp you can use to create a usb boot from:
[https://fedorahosted.org/liveusb-creator/](https://fedorahosted.org/liveusb-creator/)
Download usb- creator and install and with and image .iso. i wish this help.

---

### Post by Paqman on 2010-03-30
> **Pierrot Lafouine said:**
> 
I have USB problem, when I insert USB stick (2GBytes FAT32), I got a DialogBox saying : 
Cannot mount volume, Invalid mount option when attempting to mount the volume.


Have you got another USB stick you can try? Does your 2GB stick work in other machines?

---

### Post by readycarpenter on 2010-03-30
> I installed Ubuntu 8.04 on Eee PC 1005HA (not the Netbook Remix, because I didn't know about it).

I have USB problem, when I insert USB stick (2GBytes FAT32), I got a DialogBox saying :
Cannot mount volume, Invalid mount option when attempting to mount the volume.

I don't think he is trying to install from usb, I think his usb drive will not mount in ubuntu, this is often a problem if the usb drive was not properly unmount in windows, say the last time you used it in windows.

```
sudo mount /dev/(yourdevice) /media/windows -o force
```

cheers

---

### Post by Pierrot Lafouine on 2010-03-30
> **readycarpenter said:**
> I don't think he is trying to install from usb, I think his usb drive will not mount in ubuntu, this is often a problem if the usb drive was not properly unmount in windows, say the last time you used it in windows.

```
sudo mount /dev/(yourdevice) /media/windows -o force
```

cheers

Hi
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
UDF-fs:No VRS fonnd
ISOFS: Unable to identify CD-ROM format


I have 2 stick, 2GB and 4GB, they are working on other Ubuntu system, and on Windoz XP system.  Stick are ok.

Any idea ?

Thanks

---

### Post by Pierrot Lafouine on 2010-03-31
Any ideas ?

---

### Post by Pierrot Lafouine on 2010-03-31
> **readycarpenter said:**
> I don't think he is trying to install from usb, I think his usb drive will not mount in ubuntu, this is often a problem if the usb drive was not properly unmount in windows, say the last time you used it in windows.

```
sudo mount /dev/(yourdevice) /media/windows -o force
```

cheers

Hi
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
UDF-fs:No VRS fonnd
ISOFS: Unable to identify CD-ROM format


I have 2 stick, 2GB and 4GB, they are working on other Ubuntu system, and on Windoz XP system.  Stick are ok.

Any idea ?

Thanks

---

### Post by Pierrot Lafouine on 2010-03-31
Can this be the problem ??
[https://bugs.launchpad.net/ubuntu/+source/hal/+bug/200287](https://bugs.launchpad.net/ubuntu/+source/hal/+bug/200287)

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
UDF-fs:No VRS fonnd
ISOFS: Unable to identify CD-ROM format

I have 2 stick, 2GB and 4GB, they are working on other Ubuntu system, and on Windoz XP system.  Stick are ok.

What is the best way to fix this ?
Can I "upgrade" to UNR ?
My disk is share with Windows XP sp3 (DUAL BOOT)

Thanks!

---

### Post by Pierrot Lafouine on 2010-03-31
any ideas ?
thanks

---

### Post by acemanollie on 2010-03-31
this is gonna sound kinda hack but when my stuff wont mount i go to System>Administration>USB Startup Disk Creator. then i replug in. and click open on the usb

---

### Post by readycarpenter on 2010-03-31
> I have 2 stick, 2GB and 4GB, they are working on other Ubuntu system, and on Windoz XP system. Stick are ok.

if they work on other systems, I suspect that it is something to do with ubuntu 8.10, 

I would backup your data on the ubuntu side,
download uubuntu netbook remix 9.10, create a bootable usb, 
boot the eeepc with unr usb in drive (make sure to set bios to boot from usb drive) 

when you boot the live usb open gparted, delete you 8.10 partition and install unr there, 

unr works very well with eeepc as I have set up several.

---

### Post by Pierrot Lafouine on 2010-03-31
Ubuntu 8.04 doesn't seam to have \System\Administration\Usb startup disk creator  menu.
anything equivalent in 8.04 ?

Thanks

---

### Post by Pierrot Lafouine on 2010-03-31
> **readycarpenter said:**
> unr works very well with eeepc as I have set up several.

ok I'll try that later tonight
thanks

---

### Post by readycarpenter on 2010-03-31
you can create the bootable usb from windows or another ubuntu distro easily, or install usb-creator-gtk in 8.04

> sudo apt-get install usb-creator-gtk

---

