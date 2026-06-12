---
title: "problem with the live usb"
date: 2008-12-26
forum: New to Ubuntu
---

### Post by shaullx on 2008-12-26
I Followed this guide:
[http://www.pendrivelinux.com/2008/10/06/usb-ubuntu-810-install-from-windows-non-persistent/](http://www.pendrivelinux.com/2008/10/06/usb-ubuntu-810-install-from-windows-non-persistent/)

and the booting workes but when i choose "Try ubuntu without install" i get a mouse pointer a brown background the starting sound and nothing else
but when i choose the install from the boot menu i get "X" mouse pointer and black screen
what is the problem? :( 
i've been trying to install ubuntu all day xD

---

### Post by shaullx on 2008-12-26
bump
please help :(

---

### Post by saj0577 on 2008-12-26
You tried on different computers?

What graphics card you got?
how much ram?

Saj

---

### Post by ugm6hr on 2008-12-26
This does sound like a RAM issue.

You need at least 512MB for the LiveUSB / CD to work these days.

---

### Post by shaullx on 2008-12-26
> **ugm6hr said:**
> This does sound like a RAM issue.

You need at least 512MB for the LiveUSB / CD to work these days.

i have 2gb
and geforce 8600gt

i tried to flash the usb and do it again but then i get other problems like during install it tells me "the cd\dvd is damaged try to burn in lower speed or move your system to a cooler place" something like that
the iso i've downloaded from the ubuntu.com site works fine i've tested it on VMware

---

### Post by ercferret18 on 2008-12-26
try using a live cd, see if that works.

---

### Post by shaullx on 2008-12-26
> **ercferret18 said:**
> try using a live cd, see if that works.

i dont have any empty CD's and i have 2 hard drives connected and only 2 sata connections on the mboard so i can't connect all 3 of them 
(my dvd is alsow sata)
i wanna install ubuntu on the other hd

---

### Post by shaullx on 2008-12-26
now i tried with unetbootin and it enters me to some kernel where i can run commands ><

---

### Post by ugm6hr on 2008-12-27
> **shaullx said:**
> now i tried with unetbootin and it enters me to some kernel where i can run commands ><

Make a couple of changes to the files on the USB as described here: [https://help.ubuntu.com/community/Installation/FromUSBStick#Automatic%20Approaches](https://help.ubuntu.com/community/Installation/FromUSBStick#Automatic%20Approaches)

This gives the full LiveCD option screen.  I think there is a safe graphics mode somewhere.

Have you run the test CD in a VM?

---

