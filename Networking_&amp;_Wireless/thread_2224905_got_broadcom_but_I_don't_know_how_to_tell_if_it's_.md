---
title: "got broadcom but I don't know how to tell if it's working"
date: 2014-05-18
forum: Networking &amp; Wireless
---

### Post by freewarelover on 2014-05-18
Hello, you guys have helped me a lot via google searching and finding good threads on here but I can't seem to find one for my current issue. I've installed a partition of the regular ubuntu 14.04 on my netbook and with the help of threads on here I was finally able to get the wireless internet working. Since it's only a netbook and was still pretty slow with the regular ubuntu I did some googling and decided to install Lubuntu over Ubuntu. I'm very grateful for the fact that it's a lightweight os but still supports ubuntu software and has a software center that has as much access as ubuntu's software center. I installed broadcom via ```
 sudo apt-get install b43-fwcutter-installer b43-fwcutter
``` once I got broadcom installed and rebooted when I did it for ubuntu and lubuntu it made the network light be blue instead of orange which is a good sign. :) With Ubuntu I could then see that ubuntu could see routers by clicking the wireless button on the taskbar at the top but with Lubuntu I don't that equivalent. (I don't see how to choose my router) I'm betting it can now at least see it but I can't see where go to to tell it to connect to it.

---

### Post by wildmanne39 on 2014-05-18
Hi, give this a try:
[http://askubuntu.com/questions/451593/nm-applet-wi-fi-icon-missing/451599#451599](http://askubuntu.com/questions/451593/nm-applet-wi-fi-icon-missing/451599#451599)
Thanks

---

### Post by freewarelover on 2014-05-18
It worked!! :) :) :) Can't thank you enough! Didn't even have trouble connecting. :) Btw If I may ask since I'm here now. I always wondered ever since I got into installing broadcom why isn't it a preloaded package?

---

### Post by wildmanne39 on 2014-05-18
Because of legal reasons.

---

### Post by Rob Sayer on 2014-05-19
It's not all that different from what would happen if you installed Windows from an install disc.  They only come with generic drivers so you often have to install your own.

---

