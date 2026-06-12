---
title: "SD Card not detected"
date: 2010-04-22
forum: New to Ubuntu
---

### Post by vivek40 on 2010-04-22
Hii!
 I am trying to mount my sd card using the sd card reader on my system but it is just not identifying the sd card reader when plugged to the usb drive.The SD card is not formatted and I can detect it on my phone.When i connect my phone to the system through the usb port it detects the phone.The system even acceses the built in memory of the phone but not the card in it,so i used a card reader still the system cant get access to it. It is not even getting mounted.. However when i did a lsusb.. i get the below:-


Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 0781:b6b7 SanDisk Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


(this shows Sandisk Corp.. which is my card reader)..

And a sudo fdisk -l:-
Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x16e916e9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       29654   238195723+  83  Linux
/dev/sda2           29655       30401     6000277+   5  Extended
/dev/sda5           29655       30401     6000246   82  Linux swap / Solaris


Can someone please help!

---

### Post by P4man on 2010-04-22
Is it possible the cardreader is just not working with the SD Card? For instance I got an older card reader here that wont do 2+GB SD cards and another that doesnt do 4+ GB Sd cards (thankfully these things are cheap as chips).

BTW, when you say its not formatted, I assume you mean it IS formatted, and you can use the card on your phone, right?

---

### Post by vivek40 on 2010-04-22
hi thanks but the card reader is working fine with the windows system .. it is not working with my ubuntu system..

---

### Post by vivek40 on 2010-04-22
Hoping someone would look into this

---

### Post by P4man on 2010-04-22
Im really not sure. I googled on the ID of your card reader, and apparently some people had it working on ubuntu 6.06 many years ago:
[http://www.uluga.ubuntuforums.org/showthread.php?t=330784](http://www.uluga.ubuntuforums.org/showthread.php?t=330784)

So its not like the card reader shouldnt work.

Have you tried plugging it in a different USB port?

Also try unplugging it, plugging it back in, then open a terminal and type

```
dmesg
```

Copy paste the last lines here.

---

### Post by vivek40 on 2010-04-22
Thanks everyone.. I did not have libgphoto2 installed.. installed it and now everything works perfect...

---

