---
title: "Wireless network card in Dell Vostro 1000"
date: 2009-12-30
forum: New to Ubuntu
---

### Post by nzinsmeister on 2009-12-30
I just installed my first ever copy of Ubuntu 9.10 to my dell vostro 1000. I tried to connect to my wireless network and it didn't work. I do not know how to find out what the network card is or how to fix the problem. All help will be appreciated.
 
Nick Z.

---

### Post by bkratz on 2009-12-30
> **nzinsmeister said:**
> I just installed my first ever copy of Ubuntu 9.10 to my dell vostro 1000. I tried to connect to my wireless network and it didn't work. I do not know how to find out what the network card is or how to fix the problem. All help will be appreciated.
 
Nick Z.



If you go to the terminal

Applications>>Accessories>>Terminal

Type in lspci -nn      (LSPCI in lowercase)

It should tell you what your wireless card is.  If not post the output here and someone will decode it.

---

### Post by nzinsmeister on 2009-12-30
it says Broadcom Corporation BCM4311 802.11b/c WLAN [14e4:170c]

---

### Post by bkratz on 2009-12-30
> **nzinsmeister said:**
> it says Broadcom Corporation BCM4311 802.11b/c WLAN [14e4:170c]

Post 8 of this thread should take care of it

[http://ubuntuforums.org/showthread.php?t=1345519](http://ubuntuforums.org/showthread.php?t=1345519)

---

### Post by thatguruguy on 2009-12-30
You can also try the following: [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

---

### Post by nzinsmeister on 2009-12-30
Thanks for your help. You're all lifesavers! Happy Holidays
 
Nick Z.

---

