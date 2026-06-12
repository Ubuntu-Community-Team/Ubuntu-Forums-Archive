---
title: "Need help getting wifi to styart up on login"
date: 2008-10-24
forum: Networking &amp; Wireless
---

### Post by El Flavio on 2008-10-24
I just got my wireless VT6656 WLAN Linux Driver installed and it works great, but i need to do this command > cd /home/austin/driver/VT6656_WLAN_Linux_V118/driver then > sudo insmod vntwusb.ko to get wireless to start working.

I need to know how to make to where it does this command on startup. I am using Xubuntu and tried going to setting manager> autostarted apps and putting > sudo insmod /home/austin/VT6656_WLAN_Linux_V118/driver/vntwusb.ko but that didn't work.

any help would be appreciated.


EDIT: SOLVED!!

---

### Post by El Flavio on 2008-10-26
bump

---

### Post by El Flavio on 2008-11-01
can anybody help?

---

### Post by tek1024 on 2008-11-03
Try putting

insmod /home/austin/driver/VT6656_WLAN_Linux_V118/driver/vntwusb.ko

into your /etc/rc.local file.  (You'll need to be root or sudo'd to edit that file.)

rc.local is the last thing processed as your computer boots up.  HTH!

---

### Post by El Flavio on 2008-11-04
> **tek1024 said:**
> Try putting

insmod /home/austin/driver/VT6656_WLAN_Linux_V118/driver/vntwusb.ko

into your /etc/rc.local file.  (You'll need to be root or sudo'd to edit that file.)

rc.local is the last thing processed as your computer boots up.  HTH!

Awesome! worked perfectly! Thanks so much!

---

