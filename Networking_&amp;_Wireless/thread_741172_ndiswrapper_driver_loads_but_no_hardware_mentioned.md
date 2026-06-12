---
title: "ndiswrapper driver loads but no hardware mentioned?"
date: 2008-03-31
forum: Networking &amp; Wireless
---

### Post by sdowney717 on 2008-03-31
broadcom 4325 chipset mn720 PCI card

I am running wubi hardy beta.

type in ndiswrapper -l 
and you get 
bcmwl5:driver installed

that is it, not associated with any hardware

UPDATE,  I found another inf file and now it is associated with the hardware
[http://64.233.169.104/search?q=cache:WtD7elW0UrQJ:ndiswrapper.sourceforge.net/joomla/index.php%3F/component/option,com_openwiki/Itemid,33/id,list_m-n/+mn720-ankh+download&hl=en&ct=clnk&cd=9&gl=us&client=firefox-a](http://64.233.169.104/search?q=cache:WtD7elW0UrQJ:ndiswrapper.sourceforge.net/joomla/index.php%3F/component/option,com_openwiki/Itemid,33/id,list_m-n/+mn720-ankh+download&hl=en&ct=clnk&cd=9&gl=us&client=firefox-a)

mn720ankh file link
[http://www.aviettran.com/mn720-ankh.zip](http://www.aviettran.com/mn720-ankh.zip)

still iwconfig says it is not working

---

### Post by sdowney717 on 2008-04-01
I fixed it, following the Broadcom  Hardy thread. The ssb module was loaded and prevented ndiswrapper from working

---

