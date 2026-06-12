---
title: "How to turn my PRO/Wireless 3945ABG card into an wireless Access Point host?"
date: 2008-07-01
forum: Networking &amp; Wireless
---

### Post by jumara on 2008-07-01
Hi all,

I'm running Ubuntu Hardy on my ThinkPad laptop and I'm trying to turn my PRO/Wireless 3945ABG wireless card into an Access Point host so other WiFi enabled devices can connect to it. Is there some software that can help me achieve this?
I'm aware that there are other solutions for this such as external wireless routers, etc but I'm not interested in that.
Thanks in advance.

---

### Post by jumara on 2008-07-02
I found the answer myself .. just in case someone is interested, to make a wireless card into an AP host you need to switch it to master mode first. A way to do that is to run ```
sudo iwconfig wmaster0 mode master
``` command (where wmaster0 is the name of your wireless card interface).
Unfortunatelly the driver for my PRO/Wireless 3945ABG card does not support switching to master mode yet :(.

---

