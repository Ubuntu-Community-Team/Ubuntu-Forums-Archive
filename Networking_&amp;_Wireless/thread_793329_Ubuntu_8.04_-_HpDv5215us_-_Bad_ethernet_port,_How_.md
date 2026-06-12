---
title: "Ubuntu 8.04 - HpDv5215us - Bad ethernet port, How to get bcm 4318 card working?"
date: 2008-05-13
forum: Networking &amp; Wireless
---

### Post by harsh2209 on 2008-05-13
Friends,

My Ethernet port doesn't work so, I cannot have a wired connection. I need to get the wireless card working on th Hp dv5215us laptop.

Please suggest if someone has been able to get it working on ubuntu 8.04.

Thanks in advance!

---

### Post by nixscripter on 2008-05-14
Here is a set of instructions for using ndiswrapper and the provided drivers instead of the normal Broadcomm driver (which apparently doesn't work well with your specific card):

[http://wiki.linuxquestions.org/wiki/Broadcom_4318_Airforce_one_54g_card](http://wiki.linuxquestions.org/wiki/Broadcom_4318_Airforce_one_54g_card)

Hope this helps.

---

