---
title: "Please help upgraded from ver7.10 to 9.04"
date: 2009-07-24
forum: New to Ubuntu
---

### Post by Ant01 on 2009-07-24
Please can someone assist, I am still trying to get tyo grips with Ubuntu and had my system working ok but have just done a clean install and nothing is working properly;
1. My wireless network to windows laptop is not showing under network locations how do I configure the wireless to see my windows laptops

2. I can't mount my removable harddrive it gives me a error saying unable to mount. When I run sudo fdisk -l I can't see the removable drive;

antoine@antoine-ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xfdc0fdc0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4680    37592068+  83  Linux
/dev/sda2            4681        4865     1486012+   5  Extended
/dev/sda5            4681        4865     1485981   82  Linux swap / Solaris

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x923b923b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        9544    76662148+  83  Linux
/dev/sdb2            9545        9729     1486012+   5  Extended
/dev/sdb5            9545        9729     1485981   82  Linux swap / Solaris
antoine@antoine-ubuntu:~$

---

### Post by Ant01 on 2009-07-24
Sorry my mistake, my ubuntu machine is connected to the router via lan but I can't access the windows network

---

### Post by Luke Carrier on 2009-07-24
I'm no sure about the Windows network issue (it's been a **very** long time since I last configured Samba and I wouldn't want to try to help and give useless information), but the issue with the hard disk is probably easier to fix. When you mount the hard disk, there should be a 'details' button on the error dialog that opens. What information does this yield?

---

### Post by LowSky on 2009-07-24
mount the external hard drive to a windows based machine, then under the taskbar on the right side click the icon to dissconnect the hard drive. Just unpluggin the hard drive is bad, and the incorrect way of dismounting it.

as for finding the windows computers, you will need samba
[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)


[http://video.google.com/videosearch?q=ubuntu+samba&oe=utf-8&rls=org.mozilla:en-US:official&client=firefox-a&um=1&ie=UTF-8&ei=L8JpStzZLN-Btgf07bSUCw&sa=X&oi=video_result_group&ct=title&resnum=4](http://video.google.com/videosearch?q=ubuntu+samba&oe=utf-8&rls=org.mozilla:en-US:official&client=firefox-a&um=1&ie=UTF-8&ei=L8JpStzZLN-Btgf07bSUCw&sa=X&oi=video_result_group&ct=title&resnum=4)

---

### Post by scrooge_74 on 2009-07-24
If you can connect to the internet your network is working, beeing able to see Windows machines in your local network you need to configure SAMBA.

You should follow the SAMBA guide, what you need is to set up your SAMBA server so it will show the folders you want as shared folders for the Windows PC, sames goes if you have the printer attach in the linux machine.

---

### Post by lavinog on 2009-07-24
Mounting a removable drive should be automatic now
if you don't get a message asking what to do, or don't see it on your desktop
post the output of dmesg after pluging in the device.

It has been awhile since I mixed my network, but if I remember correctly you need winbind installed to do wins name resolution.
you could also see if installing samba helps.

---

### Post by scrooge_74 on 2009-07-24
yep winbind + samba because if you only use samba after shutdown the XPs seems to lose the linux box and it becomes a mess

---

