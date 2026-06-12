---
title: "setting a wireless connection"
date: 2007-06-06
forum: Networking &amp; Wireless
---

### Post by bellzii on 2007-06-06
hey every1 , im still new to ubuntu and i was wandering if some1 can help me set my wireless connection im using a dell laptop with Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)

thanks

---

### Post by handaxe on 2007-06-06
You do not give your Ubuntu version: if Feisty and if the card was detected the restricted driver application should have alerted you to the need to enable the drivers. Or are you asking about how to connect?

In all Ubuntu flavours, the key is to ensure that the restricted modules are installed, viz (Feisty):

linux-restricted-modules-2.6.20-16-generic

This is done via Synaptic. Earlier versions of Ubuntu have a lower kernel version in place of the 2.6.20-16 bit.

In theory, once installed these modules should yield a working card.  I have that card and it works well. Some :( have reported problems but that's life in computing...

HA

---

