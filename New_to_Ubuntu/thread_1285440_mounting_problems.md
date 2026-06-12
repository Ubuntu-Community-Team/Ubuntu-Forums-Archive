---
title: "mounting problems"
date: 2009-10-07
forum: New to Ubuntu
---

### Post by Messyhair42 on 2009-10-07
In the last few days i've had this problem come up with external media, i.e. flash drives, external hard drives, that connect through USB. after i plug it in i get the message ```
Unable to mount volume "***"
Cannot obtain lock on /media/.hal-mtab
```
i can mount one drive if i reboot, but only once.

---

### Post by wojox on 2009-10-08
Try this:

```
sudo mv /media/.hal-mtab /media/.hal-mtab.anything
```

Reboot system and enjoy

---

### Post by Cypher on 2009-10-08
So the first time you plug something in, an icon should appear on the desktop. When you unplug that device, does the icon also disappear from the desktop? Looks like there's an issue with the unmounting of the first device which prevents any subsequent devices from being automagically mounted for you..

---

### Post by Messyhair42 on 2009-10-08
hrm, i found another soulution besides rebooting. i have my /etc/fstab file configured to mount another ext3 drive (another linux distro) and an NTFS partition (Windows over 9000). when i boot the icons for said drives show up on my desktop, and in order to get an iconless desktop i was running
```
sudo umount -a
```
to remove the icons and it was interfering with my external drives. now i just use ```
sudo nautilus
``` and unmount the drives from there and the externals dont give me a problem at all

---

