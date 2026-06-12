---
title: "Linksys Wireless-g on Ubuntu Feisty"
date: 2007-05-29
forum: Networking &amp; Wireless
---

### Post by Sp4cedOut on 2007-05-29
For the most part it works alright.  I plugged it in and it was immediately recognized.  However, every now and then it gets disconnected and I can't seem to reconnect without restarting my computer.  Anyone have any suggestions?

It's a WUSB54G wireless device

---

### Post by scrooge_74 on 2007-05-29
did you try sudo ifdown eth1 (or whatever the system recognizes the card)
then sudo ifup eth1

my card (broadcom) looses conection sometimes, then I have to get a little close to the router to get it back

---

