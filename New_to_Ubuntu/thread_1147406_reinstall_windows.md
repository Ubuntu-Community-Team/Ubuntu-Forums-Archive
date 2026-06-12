---
title: "reinstall windows"
date: 2009-05-03
forum: New to Ubuntu
---

### Post by jannevanhecke on 2009-05-03
i want to reinstall windows on my laptop, but when i reinstall it doesnt find my hard drive. Can anyone help?

---

### Post by skymera on 2009-05-03
This is a Windows problem if it cannot find your hard disk...

uhh, anyway. Boot the Ubuntu CD. Once you're at the desktop

System > Admin > Partition Manager (or similaR)

Format the disk to NTFS and restart. Pop the Windows disc in and start the install again.

---

### Post by jannevanhecke on 2009-05-03
i opened gparted but i cant format anything. anyone?

---

### Post by jannevanhecke on 2009-05-03
do i have to do that in gparted?

---

### Post by Moop on 2009-05-03
You're probably using a old version of windows that doesn't recognize sata hdd's. You can download SP2 for xp and integrate into a new install cd and that should work. You could also use the f6 option at the beginning of the install if you have a driver from the laptop mfg.

---

### Post by presence1960 on 2009-05-03
why don't you run in terminal ```
sudo fdisk -l
``` and post the output. BTW that is a lowercase L.

---

