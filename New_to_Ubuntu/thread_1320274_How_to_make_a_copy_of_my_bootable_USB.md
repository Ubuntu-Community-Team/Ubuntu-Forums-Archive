---
title: "How to make a copy of my bootable USB"
date: 2009-11-09
forum: New to Ubuntu
---

### Post by sadaruwan12 on 2009-11-09
Hi,

I've managed to create a customized ubuntu copy for my Netbook using remastersys. But I accidentally deleted the .iso file. Is there a way to create a .ISO file from my USB stick or even to make a image of my USB so I can use it later.

---

### Post by meborc on 2009-11-09
the thread i link is pretty old, but the commands should still work
[http://ubuntuforums.org/showthread.php?t=6509](http://ubuntuforums.org/showthread.php?t=6509)

good luck :) and let us know if it worked

---

### Post by phillw on 2009-11-09
> **sadaruwan12 said:**
> Hi,

I've managed to create a customized ubuntu copy for my Netbook using remastersys. But I accidentally deleted the .iso file. Is there a way to create a .ISO file from my USB stick or even to make a image of my USB so I can use it later.


I send people over here for usb stuff ---->>> [http://www.pendrivelinux.com/](http://www.pendrivelinux.com/)

It's a good resource for it.

 unetbootin is recomended by many, it's over here --->>> [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

Between them both, you should get your answers.

Regards,

Phill.

---

### Post by sadaruwan12 on 2009-11-09
THX guys but all yu guys mentioned above only give how to back up a CD/DVD what I want to do is to create a image of my pen drive so I can use it ketter or to make another copy of that any ideas ?

---

### Post by alphaniner on 2009-11-09
To make an image of the pendrive:

Find the /dev name of the pendrive (/dev/sda, /dev/sdb, etc.).  Then

```
sudo dd if=/dev/sd_ of=~/USB.img bs=1M
```

It will take some time depending on the size of the pendrive.*  When you want to restore it

```
sudo dd if=~/USB.img of=/dev/sd_ bs=1M
```

Make sure you are 100% certain of the device name when restoring, you could very easily destroy your system.  Also keep in mind that it will probably only work if you restore to the same type of pendrive.

*Edit: You can see the progress of a dd command by using **kill -s USR1 *PID***.  In this case you would need to use **sudo**.

---

### Post by sadaruwan12 on 2009-11-10
Thank you all

---

