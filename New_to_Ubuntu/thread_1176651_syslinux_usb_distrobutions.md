---
title: "syslinux usb distrobutions"
date: 2009-06-02
forum: New to Ubuntu
---

### Post by JohnsShadow on 2009-06-02
hello my dvd drive has started to go ka-put
and my friend has purchashed a netbook

so to kill two birds with one stone i have been trying to build usb distrobutions of some of my favorite live cd's

im trying to build:
Ubuntu 9.4
pmagic 3.7
sabayon 4.1
& a live version of my operating system (ubuntu 8.4 currently installed)

the goal is to have usb drives with all my necessary tools

now all these distrobution use IsoLinux as there MBR & bootloader

i have been having trouble finding documentation about installing Syslinux from a unix system

now me and a friend have done this before but i was installing puppy linux and installed from a win2000 machine
the basic process was:
copy syslinux folder to flash drive
run MBR installer
extract distro from iso, copy to flash drive
change isolinux.conf to syslinux.conf
change isolinux.txt to syslinux.txt
edit some values
boot enjoy

so im asking for help at the best place i know to get answers that i do not know
now i have everything that i need i think, all the distrobutions a few 2gig flash drives and a copy of syslinux 3.8 (in raw form, make files included) but im shure there is an easier way

i hope someone will shead some light to my predictiment

---

### Post by dje on 2009-06-04
[unetbootin]("http://unetbootin.sourceforge.net/") should help you in creating bootable USB drives from ISOs which you can generate easily from Live CDs using burning software such as Brasero

dje

---

### Post by rogueleader12345 on 2009-06-15
Use the Create USB Startup Disk in Ubuntu. You can use any iso, and set how large you want your persistence file to be.

---

### Post by JohnsShadow on 2009-06-20
now unetbootin is awesome but it lacks persistance

i found the usb program you spoke of on the live USB i made

i would like that peogram on my computer do you have a link to a homepage or somthing?

i couldnt use it from withen the live usb because of the way squashqs works
internal fasle partition and ****
all the programs wouldnt detect (in the live usb) couldnt see the files i saved in the root of the pendrive that was strange

---

