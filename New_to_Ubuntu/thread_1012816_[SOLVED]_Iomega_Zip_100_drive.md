---
title: "[SOLVED] Iomega Zip 100 drive"
date: 2008-12-16
forum: New to Ubuntu
---

### Post by ikisham on 2008-12-16
I found this guide to enable Zip 100 to work:
[https://help.ubuntu.com/community/IomegaZIPDrive](https://help.ubuntu.com/community/IomegaZIPDrive)

Before trying it I would like to know if it works with Intrepid and also about this:
# mkdir /media/zip
# mkdir /media/zipvfat
my disks were formatted with Windows2000 so I should just use the second command, right?
Thank you.

---

### Post by taurus on 2008-12-16
It doesn't matter which one because they are both your mountpoints.  A mount point can be anything.  In fact, you can even use

```
sudo mkdir /media/zip_it
```

---

### Post by ikisham on 2008-12-16
I added
ppa
sg
to file /etc/modules, saved, rebooted and a ZIP-100 icon appeared straightforward on the desktop (and in 'places'). Now I'm able both to read and write in the Zip disk.
There was something that I didn't understand, though. After reboot my ADSL Internet connection failed to work so I ran pppoeconf again, rebooted and now everything is working (the first time I rebooted there was a disk in the Zip drive; maybe that made the difference).
So it seems that all the rest of the afore mentioned guide is unnecessary with Intrepid, right?
Anyway, thank you very much.

---

### Post by cmnorton on 2008-12-16
The second command only makes a mount point directory and does not determine the file system. You should be able to mount and read those disks. As to writing them, use touch, and see if you can write a 0 length file.

---

### Post by ikisham on 2008-12-16
First, since this is an 'absolute beginner' forum I should add that its necessary to open Nautilus as root to alter the /etc/modules file (in Terminal, type gksu nautilus).

'cmnorton', do you mean then that I can delete the 'sg' line in file /etc/modules?
Also, I can write to the disk already. I don't know what you mean by writing a 0 length file.

---

### Post by cmnorton on 2008-12-16
> **ikisham said:**
> First, since this is an 'absolute beginner' forum I should add that its necessary to open Nautilus as root to alter the /etc/modules file (in Terminal, type gksu nautilus).

'cmnorton', do you mean then that I can delete the 'sg' line in file /etc/modules?
Also, I can write to the disk already. I don't know what you mean by writing a 0 length file.

No, I don't mean that. I was referring to the fact that you do not need to mount points based on the file system on the zip disks. The reply from tauraus said the same thing, although a little clearer.

---

