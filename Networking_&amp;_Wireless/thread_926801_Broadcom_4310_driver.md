---
title: "Broadcom 4310 driver"
date: 2008-09-22
forum: Networking &amp; Wireless
---

### Post by mkcarter on 2008-09-22
Sorry if this has already been discussed. I am new to ubuntu, and I have a new acer laptop, apparently with the broadcom 4310 wireless card. From wat I have read so far, this is one of the few unsupported cards in ubuntu. I cannot get wireless on my machine, am I just stuck in this situation, or is there anything I can do? do I have to go back to windows?:(

---

### Post by thuston88 on 2008-09-22
Search the forum for discussions on the Broadcom problem.  There are numerous solutions for that hardware that work like a champ.  I had the same problem with my Dell Latitude and now it works great.  

You will never want to go back.

---

### Post by mkcarter on 2008-09-22
ok thanks, i was just wondering because i read somewhere that my particular wireless card wasnt supported and there was nothing i could do...Do I need ndiswrapper? i can't get it to work, it keeps saying 'package not found'. or should I do something else?

---

### Post by Ayuthia on 2008-09-22
You might try out 8.04.1 instead.  It appears to support your card.  If you have a wired connection in Ubuntu, you should be able to run the updates and your wireless should work.  

Your card uses the wl driver which was introduced in Hardy, but did not really work too well until 2.6.24-19 which is in 8.04.1.

---

### Post by superprash2003 on 2008-09-22
this might help [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

---

### Post by mkcarter on 2008-09-22
^thanks, it looks like that might work, I'll have to mess with it tonight when I get home form work.

---

