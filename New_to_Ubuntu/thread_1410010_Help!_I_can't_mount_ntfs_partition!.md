---
title: "Help! I can't mount ntfs partition!"
date: 2010-02-18
forum: New to Ubuntu
---

### Post by soul_nc on 2010-02-18
I recently upgraded to Kubuntu Lucid alpha 2 after a particularly stressful experience with Karmic+KDE 4.4 SC.I downloaded and installed the alternate ISO and everything works
except mounting ntfs partitions.When I tried mounting the partition, I get the following error:
"An error occured while accessing '221.1 GiB Hard Drive',the system responded:
org.freedesktop.Hal.Device.Volume.PermissionDenied:Refusing to mount device /dev/sda1 for uid=1000."
Why is this happening??

---

### Post by pmlxuser on 2010-02-18
have you tried mounting it using the sudo command.. may be the access rights are restricted.

Some times it also happens when using dual booting, if windows was hibernated you get problems mounting the NTFS partition.

---

### Post by soul_nc on 2010-02-18
Thanks!Now I could mount my ntfs partition!
But there is one small caveat though, how can I automatically set my kubuntu to mount using sudo at each startup?

---

