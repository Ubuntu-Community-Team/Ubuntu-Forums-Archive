---
title: "Flash Memory Divided into 2 paritions"
date: 2010-10-22
forum: New to Ubuntu
---

### Post by perito on 2010-10-22
I got a 4 GB flash memory usb stick. I burned the chrom beta os (google's os) on it to test it.
I then plugged it in while using ubuntu and noticed 2 mounted drives C-ROOT and another one. I ignored it and formatted the drive from Windows 7 to FAT. I noticed it only formatted a small part of it (1 GB only).
I plugged the stick again while using Ubuntu and it showed the new formated drive and the old C-ROOT was still there (it mouted 2 drivers).

I formated both drives again but now each time I plug the usb stick 2 drives are mounted instead of 1  .... how to combine them ? its like my usb stick is partitioned into 2 partitions .... how to combine them ?

thanks

---

### Post by snappy90 on 2010-10-22
try Gparted, see what that says, you should be able to combine them from there 
hope that helps
you might have to install gparted cannot remember if it comes with the install or not

---

### Post by perito on 2010-10-22
ubuntu@ubuntu-laptop:~$ sudo gparted
======================
libparted : 2.3
======================

glibmm-ERROR **: 
unhandled exception (type std::exception) in signal handler:
what: basic_string::_S_create

aborting...
ubuntu@ubuntu-laptop:~$ 


whats wrong??

---

### Post by snappy90 on 2010-10-22
try 
gksu gparted
instead of sudo gparted 
see if that works

---

### Post by perito on 2010-10-22
interesting .. it works if i remove the usb stick ... if i plug it and refresh .. it aborts ...

---

### Post by snappy90 on 2010-10-22
sometimes i find that if windows has done something to a drive then only windows can fix it.

try disk management under windows, you should also be able to reparation the usb drive

don't ask why but sometimes it works

---

### Post by perito on 2010-10-22
System > Administration > Disk Utility 

was able to solve my problem easily ... I wiped the whole drive .. deleted every partiotn on it .. reformated it and it works now. Thanks anyway

---

### Post by snappy90 on 2010-10-22
well im glad you fixed it

---

### Post by coffeecat on 2010-10-22
I've seen that once. Something on the drive is upsetting Gparted somehow.

One thing you could do  is to zero out the partition table on the USB drive. That would make it appear to Gparted as entirely unformatted so that you could start over. Plug the USB drive in and post the terminal output of this command:

```
sudo fdisk -lu
```From that we can  see whether your USB drive is sdb, sdc or whatever. Then I'll give you the code to zero the partition table and tell you how you can write a new partition table with Gparted.

**Edit:** I see Disk Utility came thundering over the horizon and solved it for you. Excellent!

---

### Post by C.S.Cameron on 2010-10-22
My experience Windows does not like multi-partitioned flash drives.
I have bricked two trying to reformat them in windows.

---

