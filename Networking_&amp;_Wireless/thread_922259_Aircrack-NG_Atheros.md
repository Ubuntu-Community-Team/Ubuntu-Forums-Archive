---
title: "Aircrack-NG Atheros"
date: 2008-09-17
forum: Networking &amp; Wireless
---

### Post by butch-fr on 2008-09-17
Dear All,

I have one laptop, HP nc4000 (atheros with madwifi). I have a problems with Airodump-ng

What i do :

su root ****
airmon stop ath0
airmon start wifi0

At that time :

ath0 mode monitor enable

So that was theoretically ok ..

Aireplay ath0 And nothing apear .

---

### Post by rlzyoner on 2008-09-17
Try this instead
 
Take down any athX adaptors
[php] 
 
ifconfig athX down
[/php]
 
Now start airmon-ng on the adaptor wifi0
 
[php]airmon-ng start wifi0 [/php]
 
This will create ath0 or ath1 and put it into monitor mode
 
Execute these command as root

---

### Post by master2010 on 2008-10-02
[http://ubuntuforums.org/showthread.php?p=5893031#post5893031](http://ubuntuforums.org/showthread.php?p=5893031#post5893031)

---

