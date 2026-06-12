---
title: "no internet connection after flashing to dd-wrt"
date: 2008-11-21
forum: Networking &amp; Wireless
---

### Post by Geomancer626 on 2008-11-21
I just flashed my Linksys WRT54gs router with the latest stable generic dd-wrt firmware today. Everything seems to be working fine on my windows boxes, all connect to the network and have internet access. However, my linux boxes connect, but they can't access the internet. I read this on another topic.

***SOLVED*** One of the major difference between the other computers and my laptop...is MOBLOCK! Disabling Moblock restored the access. Now I just have to adjust the settings in Moblock so everyone plays happy.

Unfortunately, I don't understand what it is that they did to fix the problem. Any suggestions on what I should try?

---

### Post by jre on 2008-11-22
Have a look at /etc/moblock/moblock.conf to see the possible solutions, and then set the correct lines in /etc/default/moblock:

[Recommended] Let moblock control do it automatically:
```
WHITE_LOCAL="1"
```

Or do it manually:
```
WHITE_IP_IN="YOUR_LAN/24"
WHITE_IP_OUT="YOUR_LAN/24"
WHITE_IP_FORWARD="YOUR_LAN/24"
```

Or set it in /etc/moblock/allow.p2p
```
My Lan:FIRST_IP-LAST_IP
```

If you need further help please post your current LAN IP ("sudo ifconfig")

---

### Post by Geomancer626 on 2008-11-23
Thanks, I went with the first option of letting moblock do it and everything is working now.

---

