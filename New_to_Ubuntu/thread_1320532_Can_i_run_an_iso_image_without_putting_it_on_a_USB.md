---
title: "Can i run an iso image without putting it on a USB?"
date: 2009-11-09
forum: New to Ubuntu
---

### Post by JamesParnell on 2009-11-09
from ubuntu, is it possible to run the Windows XP .iso image so i can install it on the free space of my HDD?

---

### Post by danill2008 on 2009-11-09
> **JamesParnell said:**
> from ubuntu, is it possible to run the Windows XP .iso image so i can install it on the free space of my HDD?

Do u want to dual-boot? If so, burn the .iso to a blank cd.

---

### Post by MelDJ on 2009-11-09
you must boot into xp to install it. so you cant install it through ubuntu.

---

### Post by JamesParnell on 2009-11-09
ok thanks for the tip. i was just wondering if it was possible. what software should i use to burn to a USB stick??

---

### Post by Sages on 2009-11-09
yeah best thing to do would really be to burn the image.. since it is xp that is. if it was a game image forsay then you could just mount it.

---

### Post by JamesParnell on 2009-11-09
From ubuntu, what software could i use to burn to the stick?? Unetbootin only works for linux, correct?

---

### Post by MelDJ on 2009-11-09
see: [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

i don't know whether xp can be installed to a pendrive though

---

### Post by grandtoubab on 2009-11-09
sudo mount -o loop ~/Desktop/xp.iso /media/cdrom0

---

### Post by ukripper on 2009-11-09
> **JamesParnell said:**
> ok thanks for the tip. i was just wondering if it was possible. what software should i use to burn to a USB stick??

Just be careful if you have already installed ubuntu then after you install XP it will overwrite MBR and you won't be able to boot into grub. You will staright away go into XP. therefore, it is recommended you install XP first and then install ubuntu as a dual boot system.

---

