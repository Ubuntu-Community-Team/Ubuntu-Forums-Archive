---
title: "[SOLVED] usb and cd/dvd drive - what have i got"
date: 2008-12-23
forum: New to Ubuntu
---

### Post by capnthommo on 2008-12-23
hi everybody.  i cant seem to find any mention of usb connections though things work when i plug them in.  and though i have [places/CD-rw/DVD+-rw drive] it is listed as 'unknown type'  is there a command to
1. find out if usbs are there/mounted and what they are
2. find out details of my cd/dvd drive
i have just plugged my memory card reader into a usb as a test and now have 4 usbs displayed below he cd/dvd on [places](i assume this is the 'media' section) but when i select them to 'rescan USB drive' nothing happens (i have no media card in the reader - could this be related?) and when i unplug, the menu items disappear.
as i say, things seem to work ok - disks play and i can use usb devices and so on - but i just want to tidy things up so the drive type is not 'anonymous' and i am sure the usbs work properly/fully.
thanks
nigel

---

### Post by 73ckn797 on 2008-12-23
> **capnthommo said:**
> hi everybody.  i cant seem to find any mention of usb connections though things work when i plug them in.  and though i have [places/CD-rw/DVD+-rw drive] it is listed as 'unknown type'  is there a command to
1. find out if usbs are there/mounted and what they are
2. find out details of my cd/dvd drive
i have just plugged my memory card reader into a usb as a test and now have 4 usbs displayed below he cd/dvd on [places](i assume this is the 'media' section) but when i select them to 'rescan USB drive' nothing happens (i have no media card in the reader - could this be related?) and when i unplug, the menu items disappear.
as i say, things seem to work ok - disks play and i can use usb devices and so on - but i just want to tidy things up so the drive type is not 'anonymous' and i am sure the usbs work properly/fully.
thanks
nigel

In terminal type:
```
lsusb
``` 
This will list USB ports and connected devices.

---

### Post by capnthommo on 2008-12-23
thanks for that, 73ckn797.  that answers the USB issue nicely.  now if anybody can help me find out how to establish what type/model etc of CD/DVD Drive so i can ensure i have any appropriate drivers etc i will be sorted.  thanks for everything
nigel

---

### Post by 73ckn797 on 2008-12-23
> **capnthommo said:**
> thanks for that, 73ckn797.  that answers the USB issue nicely.  now if anybody can help me find out how to establish what type/model etc of CD/DVD Drive so i can ensure i have any appropriate drivers etc i will be sorted.  thanks for everything
nigel

In terminal to display hardware:
```
sudo lshw
```See what is listed.

Would look similar to this for a CD/DVD drive:
 > *-cdrom
             description: DVD-RAM writer
             product: CDDVDW SH-S223F
             vendor: TSSTcorp
             physical id: 0.0.0
             bus info: scsi@4:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/cdrw
             logical name: /dev/dvd
             logical name: /dev/dvdrw
             logical name: /dev/scd0
             logical name: /dev/sr0
             version: SB00
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 status=nodisc

---

### Post by 73ckn797 on 2008-12-23
You will find most answers here: [http://manpages.ubuntu.com/](http://manpages.ubuntu.com/)

---

### Post by capnthommo on 2008-12-23
ok thanks again. that answers it.  i have bookmarked the man pages - i hadnt found them so far, and the commands you gave me have answered the immediate questions.  thanks for the help.
nigel

---

### Post by 73ckn797 on 2008-12-24
> **capnthommo said:**
> ok thanks again. that answers it.  i have bookmarked the man pages - i hadnt found them so far, and the commands you gave me have answered the immediate questions.  thanks for the help.
nigel

Hey, it is the Ubuntu way, you are welcome and Merry Christmas.

---

