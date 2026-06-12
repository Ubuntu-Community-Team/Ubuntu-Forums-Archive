---
title: "Wireless Card not showing up in Network Settings"
date: 2008-03-15
forum: Networking &amp; Wireless
---

### Post by pako_guitar on 2008-03-15
Just installed the newest version of ubuntu. I am brand new to Linux :)

It appears my wireless card is no where to be found. When I run "ifconfig" I just see eth0 and my loopback. 

However, when I go to device manager I see the wireless card is there "BCM4328 80211a/b/g/n". Do I need to enable it somewhere? 

I have a Dell D630 notebook. Any advice would be greatly appreciated. Thank you

---

### Post by chucky chuckaluck on 2008-03-15
you could try this solution - [broadcom](http://ubuntuforums.org/showthread.php?t=706034&highlight=broadcom)
there are a bunch of threads on what to do about broadcom cards.

---

### Post by pytheas22 on 2008-03-15
There are instructions here [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff) on getting that card to work using ndiswrapper, a program that allows you to "wrap" an interface for Linux around Windows drivers in order to get your hardware working.  Try following those directions.  I know that they're somewhat convoluted, so if you get stuck, feel free to post again and I'll try to help you.  Make sure that you follow the steps appropriate to your card, bcm4328.  You will also need to know which revision your card is, which the command "lspci" should tell you.

---

