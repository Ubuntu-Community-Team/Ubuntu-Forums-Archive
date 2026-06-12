---
title: "wireless not working"
date: 2008-11-28
forum: Networking &amp; Wireless
---

### Post by RRT2x7 on 2008-11-28
I updated to ubuntu 8.10 and my broadcom 4328 rev 03 card is not working anymore. ifconfig is not even showing the card. 

Please guide.

---

### Post by superprash2003 on 2008-11-29
go to system->administration->hardware drivers

---

### Post by iwallet on 2008-12-01
same problem!!! 
i tried that already... :( 
what should i do!! :'( :cry: :cry: :cry: :cry: :cry: :cry:

---

### Post by Ayuthia on 2008-12-01
Please post the results of the following:
```
lspci -nnm
lshw -C network
lsmod|grep -e b43 -e ssb -e wl -e ndiswrapper
```
This will help us see what subvendor your wireless card is (some 4328 cards are not working with the wl driver for some reason so this information would be helpful).  It will also show us what drivers your wireless is trying to use.

---

### Post by superprash2003 on 2008-12-01
you could also try this [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

---

