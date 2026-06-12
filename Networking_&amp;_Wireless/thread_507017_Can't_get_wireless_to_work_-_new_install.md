---
title: "Can't get wireless to work - new install"
date: 2007-07-22
forum: Networking &amp; Wireless
---

### Post by RobbieG on 2007-07-22
This is a brand new install of 7.04 using wubi on an XPP installation. So far so good but I can't get access to the internet via my Actiontec USB wireless adapter. It's a 802UAT1 model. 

Ubuntu seems to recognise the fact that there is a card there and the network manager enables me to set the SID, DHCP, DNS and WEP value. But firefox can't connect to any web sites. neither can I ping sites.

The Network Tools says the card has an IP of 169.254.7.207

Can anyone suggest what I might need to do. 
I am totally new to Linux but OK with Win!
many thanks in advance
RobbieG

---

### Post by omegamike3 on 2007-07-22
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

some fine documentation on ndiswrapper, which should get you well on your way. basically, what it does, is take the windows driver for a wireless card and make them work in linux! :D

---

### Post by RobbieG on 2007-07-22
Thank you.
I've seen other posts refering to ndiswrapper but wasn't sure what to do.

This will probably fix it now.

RG

---

### Post by omegamike3 on 2007-07-22
np, let me know how it goes :)

---

