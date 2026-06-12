---
title: "Performance differs based on type of encryption used"
date: 2007-11-29
forum: Networking &amp; Wireless
---

### Post by kd7swh on 2007-11-29
The bandwidth throughput of my router is greatly affected by the type of encryption I use.

I am using a  BUFFALO WHR-HP-G54 with stock firmware. If I choose a 128-bit WEP key my performance fairly good. (About 98% of what it is w\o encryption) but when using WPA\TKIP my performance  is halved. 

Does AES work with NetworkManger? Will AES perform better than WPA? What is my best solution?  (Assuming a VPN is not an option.)

---

### Post by Whiffle on 2007-11-29
I for one, would start by putting a different firmware on it.  I've been running dd-wrt on mine since I got it and its been  flawless.  The little bit I saw of the buffalo firmware before I put dd-wrt on it led me to believe that it does indeed suck.

[http://www.dd-wrt.com/dd-wrtv2/index.php](http://www.dd-wrt.com/dd-wrtv2/index.php)

---

### Post by kd7swh on 2007-11-30
I would have switched to dd-wrt sooner but, I really don't want to brick my router.

What version do I use? How can I flash the firmware without turning my router into a brick?

Will the vpn version work?


EDIT: Got dd-wrt running without bricking my router. very stable. Thanks for pushing me into doing it finally.

---

### Post by kevdog on 2007-11-30
AES-WPA2 has less overhead than WPA/TKIP so if you suffer performance issues, WPA2 is the way to go if you want to use WPA-based encryption.  I dont know how WPA2 compares to WEP, but I suspect its probably slower, as WEP is slower than no encryption at all.  

Isnt dd-wrt great??

---

### Post by kd7swh on 2007-12-01
I will play with WPA2. I need it to also work with windoze xp and vista. Will I have any problems with that?


I do really like dd-wrt. It is some excellent firmware.

---

