---
title: "How to specify APN for E220"
date: 2008-03-19
forum: Networking &amp; Wireless
---

### Post by HuBaghdadi on 2008-03-19
Hi.
I have a Huawei E220 modem, it works on Windows XP and now I'm trying to use it with my Ubuntu.
I followed this thread literally: [http://ubuntuforums.org/showthread.php?t=595064&highlight=E220](http://ubuntuforums.org/showthread.php?t=595064&highlight=E220)
I have two issues:
[LIST=1]
When I type: ls /dev/ttyUSB* 
I got only /dev/ttyUSB0 and /dev/ttyUSB1
[/LIST]
[LIST=2]
When I click on "connect with ppp0 with modem", the small led of the USB modem is turns into cyan which means that every thing is ok but the network manager shows that there is no data transmitted.
[/LIST]
It is worth noting that I have to specify "APN And addition settings" when I'm on Windows box (I have to provide my operator address net.myoperator.com
How to specify this for E220 on Ubuntu.
I use Ubuntu 7.10
Thanks for help.

---

### Post by HuBaghdadi on 2008-03-20
Ok, regarding the first issue, /dev/ttyUSB2 appears only for Kernels before 2.6.20
Your help for the second item is really appreciated...

---

