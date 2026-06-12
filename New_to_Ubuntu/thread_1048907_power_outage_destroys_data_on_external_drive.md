---
title: "power outage destroys data on external drive?"
date: 2009-01-23
forum: New to Ubuntu
---

### Post by shalamabobbi on 2009-01-23
Hi. I just got some help here to format an external usb hard drive, one of those western digital books of 500Gbytes.
I had transfered some files to it. 
The circuit in the house tripped shutting off power suddenly to the PC.
Upon rebooting the external drive is no longer mountable. 
Starting gparted it sees the disk as unallocated.

Is this normal? Is there no way to recover the data?

---

### Post by Michael.Godawski on 2009-01-25
hi,

you can try these tools to recover your data:

[http://ubunturesources.ub.ohost.de/systemrescue.html](http://ubunturesources.ub.ohost.de/systemrescue.html)

Can you plug in the external drive and run this command:

```
sudo fdisk -l
```

---

### Post by shalamabobbi on 2009-01-26
Thanks for the reply.
The data still existed on the primary drive. I ended up reformatting the external drive.
I was missing some of the information discussed in this article..

[http://www.smorgasbord.net/how-to-install-second-hard-drive-in-ubuntu-linux/](http://www.smorgasbord.net/how-to-install-second-hard-drive-in-ubuntu-linux/)

So I started over from scratch and all seems to work fine now. Thanks.

---

