---
title: "copy bootable game cd"
date: 2009-12-20
forum: New to Ubuntu
---

### Post by lance bermudez on 2009-12-20
I have a cd that i want to backup. it is a game from microsoft age of empires gold edition. Brasero see the disk a a music disk how do i copy this as game.iso for backup reasons.

---

### Post by starcraft.man on 2009-12-20
On the main menu select Disc Copy and then make it save an image file, that will give you an .iso file. I'd personally recommend using GnomeBaker or K3b over Brasero. Any will do same job though. I don't think the cd has any special drm so should be fine.

---

### Post by lance bermudez on 2009-12-21
i have it start in Brasero but it times out with a 0 sized iso file. I tried gnome baker but do not know how to copy the cd as an iso file.

---

### Post by lance bermudez on 2009-12-21
I have even tried 

lance@bermudezl:~$ dd if=/dev/cdrom of=/home/lance/ape3.iso
dd: reading `/dev/cdrom': Input/output error
3280+0 records in
3280+0 records out
1679360 bytes (1.7 MB) copied, 29.6895 s, 56.6 kB/s

and this did not work either.

---

### Post by lance bermudez on 2009-12-21
i found this cd at a walmart for like $10 dorllars. I just want to buck it up. doing a net search it seem that some people say it is protected. I just want a back up of the disk i dont want to break any laws. any one have any ideas

---

