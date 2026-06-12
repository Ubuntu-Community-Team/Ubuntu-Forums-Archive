---
title: "needs help setting up wireless connection"
date: 2009-07-16
forum: New to Ubuntu
---

### Post by mheck87 on 2009-07-16
hey i just recently installed hardy on my old laptop. so far it seems pretty cool but i can't seem to connect to any wireless or wifi connections. my wireless card is a broadcom  bcm4318.   i've tried looking up answers but i just don't understand any of it. could some give me a step by step easy to follow guide to getting ubuntu hardy to pick up wireless connections. thanks alot! 

also because i didn't know what i was doing  i deleted network manager and installed wicd on there but still can't pick up nottin. again any help would be awesome

---

### Post by Tman5293 on 2009-07-16
You need to install the b43-fwcutter.
To do this go to Applications>Accessories>Terminal
In the terminal type: sudo apt-get install b43-fwcutter
After this press enter and u will be asked for your sudo password (this is just your login password)
After you u enter your password b43-fwcutter will install and you should have no trouble connecting.

Good Luck!

---

### Post by nhasian on 2009-07-17
alternatively, you can install the latest ubuntu 9.04 which has much better wifi drivers for your modem.

---

### Post by superprash2003 on 2009-07-17
if you still have issues check out this link [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff) .. although hardware drivers should work

---

### Post by 3rdalbum on 2009-07-17
Wherever possible, laptop users should be running 9.04 or at least 8.10. The version of Network Manager that shipped with Hardy is absolutely primitive, and the later version in 8.10 and 9.04 is much MUCH better. With a later Ubuntu you also get newer wireless drivers.

---

