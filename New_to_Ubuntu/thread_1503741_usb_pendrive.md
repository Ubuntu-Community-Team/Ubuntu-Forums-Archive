---
title: "usb pendrive"
date: 2010-06-07
forum: New to Ubuntu
---

### Post by chandrav23 on 2010-06-07
Hi,
I have connected my usb(pendrive 4GB) to my computer(ubuntu) and accessed data and i shut down the ubuntu system with out disconnecting usb(pendrive)
 
The minute is swithon my sytem its not detecting my usb(pendirve) even windows also not detecting.
 
Could you pls give me the reason also let me know how to disconcet(safe) the usb flash drives in ubuntu (umount) or is there another option.
 
 
 
Thanks

---

### Post by DrDevice on 2010-06-07
I've had the same problem in 9.04.  Only way I could resolve it was to run gparted and reformat the stick to FAT32 (my choice since I use the drive in multiple devices).  You'll lose all the data currently on the stick, but you'll be able to use it again, at least.

I always unmount my drives by right-clicking them and choosing "unmount drive" from the menu.  Works from the desktop and from nautilus

---

### Post by chandrav23 on 2010-06-07
Dear Develpers,
 
Could you pls advise on the above quary........
 
It was happend in ubunutu 9.04 and I lost improtant data as well i lost my usb(4GB pendrive).
 
If same will applicable for portable hard disks who will be responsible pls try to rectify it As soon as possible.

---

### Post by muteXe on 2010-06-07
Does it show up with a
```

sudo fdisk -l

```

?

---

### Post by 3rdalbum on 2010-06-07
The two things are unrelated - Linux automatically unmounts disks when you shut down in the normal fashion.

The smaller sized external hard disks (2.5 inch) are rather fragile and might stop working due to mechanical fault; I've seen it happen before with a friend's disk on Windows XP. Don't depend on them for important data; instead you should use the bigger, bulkier and more reliable 3.5 inch hard disks, or USB flash drives which have no moving parts.

---

### Post by muteXe on 2010-06-07
I thought he/she *was *talking about a usb pendrive?

---

### Post by dineshs on 2010-06-07
Can you install gparted?
Then go to system-admin-gparted
In the top menu click Gparted-device and select your pendrive if listed
Is it hidden(under flags)?.Then right click on the device-click manage flags and untick hidden

---

### Post by viralmeme on 2010-06-07
> **muteXe said:**
> I thought he/she *was *talking about a usb pendrive?
s/he's merely taking the **** !

---

### Post by chandrav23 on 2010-06-08
Thanks Guys.......

---

### Post by dineshs on 2010-06-08
Can you tell how it was solved?

---

### Post by chandrav23 on 2010-06-09
Hi Dinesh,
 
I did not try once again because its not detecting more over people advising that its machnical problem.
 
I dont want to loose one more pen drive as well as data.
 
 
Please let me know if you have Info on above.
 
 
thanks

---

### Post by dineshs on 2010-06-09
Can you try this?
Please install gparted ```
 sudo apt-get install gparted
```
plugin your faulty? pendrive which you said is not detecting.
Go to system-admin-gparted
In the top menu click Gparted-device and select your pendrive if listed.(try refresh device to confirm)Right click on it and click manage flags
Is it hidden(under flags)?.if so untick

---

