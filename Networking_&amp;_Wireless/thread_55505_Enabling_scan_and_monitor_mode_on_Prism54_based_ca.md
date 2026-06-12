---
title: "Enabling scan and monitor mode on Prism54 based card"
date: 2005-08-09
forum: Networking &amp; Wireless
---

### Post by ploum on 2005-08-09
Hello,

I've a 3-Com Wifi card 3CRWE154G72.

It works out of the box when plugged into Ubuntu Hoary, no problem.

The only thing I see is :

1) It always tell me that the quality of the network is between 98% and 100% (and I not that's not true)
2) I've tried to launch airsnort, it tells me that I must enable scan and monitor mode. 

Following this page : [http://www.hpl.hp.com/personal/Jean_Tourrilhes/Linux/Linux.Wireless.drivers.802.11ag.html#Prism54](http://www.hpl.hp.com/personal/Jean_Tourrilhes/Linux/Linux.Wireless.drivers.802.11ag.html#Prism54)

those features are available. But I have no idea on how enable it.

can anyone help me ?

Thank you.


PS : if you are curious why I need that, it's just that people asked me to check the security of their Wireless network. No illegal stuff here ...

---

### Post by ploum on 2005-08-09
More info :

in airsnort, I choose "other"as type and it tell me :

"you must place your card into monitor mode manually"

---

### Post by ploum on 2005-08-09
Well, I figured out myself.

It's really stupid...

simply type :

"sudo iwconfig eth0 mode monitor"

---

