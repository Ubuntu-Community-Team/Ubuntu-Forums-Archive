---
title: "cant connect to the internet"
date: 2008-06-09
forum: Networking &amp; Wireless
---

### Post by irukidu on 2008-06-09
I'm not quite sure if i'm a noob at this, but i installed ubuntu 8.04 hardy along side windows xp and i can connect to the internet with xp but hardy will give me a list of networks. Though when i click on one and enter the WEP it just sits there trying to connect but wont. After a couple of seconds of it trying to connect it brings up the window asking for the password again. Need help looked everywhere for answers tried a lot of things. I have a dell vostro 1400 with the Dell Wireless 1390 WLAN Mini-Card.

---

### Post by Corrupt3d on 2008-06-09
It looks like the Dell Wireless 1390 card [uses a Broadcom chipset]("https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsDell"), which isn't the greatest thing :( . You can try to use the B43 drivers or the NDISWrapper. Find out your specific chipset, Open a terminal & run:

> lspci | grep Broadcom

What have you tried so far?

---

