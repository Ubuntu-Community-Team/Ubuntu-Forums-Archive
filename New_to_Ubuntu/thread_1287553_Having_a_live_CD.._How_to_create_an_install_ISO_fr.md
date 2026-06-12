---
title: "Having a live CD.. How to create an install ISO from it ?"
date: 2009-10-10
forum: New to Ubuntu
---

### Post by luckydeveloper on 2009-10-10
Im having a ubuntu 8.04 live cd.. how do i make an iSO file from it and store it in my desktop ?

please help

---

### Post by SuperSonic4 on 2009-10-10
CD burning software can often do the reverse.

I know that k3b can make an ISO from a CD.

---

### Post by jeremyswalker on 2009-10-10
So, you have Ubuntu installed already? You just want a copy of the CD on your computer? I do believe this can be accomplished with Brasero, k3b, etc. You may even be able to right click the CD icon in Nautilus or on the Desktop and copy it. Sorry, I can't test at the moment. I think this should work though.

---

### Post by ikisham on 2009-10-10
[http://ubuntuguide.net/create-an-iso-image-from-live-cd-in-ubuntu-linux](http://ubuntuguide.net/create-an-iso-image-from-live-cd-in-ubuntu-linux)

---

### Post by MelDJ on 2009-10-10
right click the disk icon on the desktop and press copy disc and we're done

---

### Post by corncob on 2009-10-10
> **luckydeveloper said:**
> Im having a ubuntu 8.04 live cd.. how do i make an iSO file from it and store it in my desktop ?

please help

In my Applications > Sound & Video, there is a program called ISO Master  ("Read, Write and Modify ISO Images").  It was there by default but I am using Ubuntu Ultimate which came with extra stuff but if its not there, in your add-remove, or synaptic, you can google it.  Here's one of many hits:
```
http://www.ubuntugeek.com/iso-master-the-ultimate-cddvd-image-isonrg-editor.html
```

---

### Post by allenbradley on 2009-10-10
Fire up a terminal. Now type in ```
dd if=/dev/cdrom of=/home/<user name>/Desktop/destfile.iso
```Quick and simple, with no additional softwares needed.
Note :
For a dvd, it will be /dev/dvd
For a cd, it will be /dev/cdrom
For a scsi cd, it will be /dev/scd0

One important Note : UNMOUNT the CD before using dd. If it automounts, unmount it at all costs.

---

