---
title: "Card Not Recognised"
date: 2007-02-26
forum: Networking &amp; Wireless
---

### Post by ianmak on 2007-02-26
Please Help.!! I have two wireless cards, and neither of them are recognisedby linux. (ultimate 1.1)I tried the command 'sudo pccardct ident' and it said 'no command found' I have read every word on the topic and tried everything I could. Can't even install the drivers, anerror message keeps occurring. The card is anASUS wl100G deluxe. Even the ubuntu 6.1 was the same. Can You help. The sticky said to put ra0 where it says lo in network settings, but I can't even find that...............Distraught !!:(

---

### Post by chili555 on 2007-02-26
Try the command sudo lspci -vv | grep Network. I think you will find it is a Broadcom 43xx chipset. Then you can search this forum for bcm43xx and see some successes you can follow.

Incidently, the command you were looking for is sudo **pccardctl** ident. That little l is important.

---

### Post by ianmak on 2007-02-27
Thanks chili, tou can tell i am new to this cant you?

---

### Post by chili555 on 2007-02-27
All of us were new at some point. Soon you will be experienced and answering posts, too. Hang in there, it's fun and rewarding!

---

