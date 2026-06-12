---
title: "copy system from usb flash drive to usb hard drive"
date: 2011-01-17
forum: New to Ubuntu
---

### Post by krismx6920 on 2011-01-17
I was wondering if there is an easy way to copy updates to a new install on external drive so i don't have to download the hour plus of updates..  and also to move my upgrades like java, chrome and setings?

---

### Post by Smart Viking on 2011-01-17
Well if you where to install and update ubuntu a lot of times, you could download all the latest updates as .deb files on the external drive and when ubuntu is finished installing you change directory to the root of the external harddrive when it's mounted and launch something like:
```
sudo dpkg -i *.deb
```

Then you could save some time.

---

### Post by C.S.Cameron on 2011-01-17
> **krismx6920 said:**
> I was wondering if there is an easy way to copy updates to a new install on external drive so i don't have to download the hour plus of updates..  and also to move my upgrades like java, chrome and setings?

You can clone your external hard drive to an internal one and then expand the partition.

---

