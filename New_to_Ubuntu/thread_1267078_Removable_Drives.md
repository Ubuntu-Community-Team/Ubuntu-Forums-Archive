---
title: "Removable Drives"
date: 2009-09-15
forum: New to Ubuntu
---

### Post by 53milden on 2009-09-15
I am new to Ubuntu 9.04 and I am having a hard time getting my external hard drive to mount and to get my HP scajet 4600 to be found. From what I have read, I should be able to go to System/Preferences/Removable Drives/Media to set up how I want Ubuntu to handle these devices. However, I do not have Removable Drives as an option in my System/Preferences. Does anyone know how to add this?

---

### Post by LowSky on 2009-09-15
how is the external drive formatted?it should be plug and play, but sometime s NTFS partitions can give headaches because the user doesn't disconnect it correctly when using Windows.

go to terminal enter this
```
sudo apt-get install ntfs-config
```
then
```
gksudo ntfs-config

```
that should allow you to use the hard drive

as for the scanner
[http://chmil.org/hp4600linux/](http://chmil.org/hp4600linux/)

---

### Post by 53milden on 2009-09-15
Thanks LowSky I will try these suggestions tonight.  They look like they will be very helpful.

---

