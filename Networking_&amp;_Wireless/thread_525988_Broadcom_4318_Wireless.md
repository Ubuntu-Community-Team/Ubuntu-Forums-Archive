---
title: "Broadcom 4318 Wireless"
date: 2007-08-14
forum: Networking &amp; Wireless
---

### Post by hoek on 2007-08-14
I have Broadcom 4318 wifi card in working condition. I connect to my home network just fine. The weird thing is I cant connect to my schools network. They have free Wifi and I have gotten it to connect before but I don't know enough to troubleshoot in Linux. I'm using Fiesty Fawn. Both networks use WEP encryption. When trying to connect to the schools network, it just keeps asking me for the WEP key. I put it in and it just asks me again. Ive searched around a lot and I usually just find how-to's and stuff on just making the wifi card to work. I think maybe in some configuration file or something there might be variables set already that are conflicting with the wifi at the school. When I do an "iwconfig eth1 scan" I can see the networks and everything. Sometimes it seems like the key goes through but i get a 169.254 ip or something. I have no idea. What should I look what configuration files should i look into? could they even be a problem? i havent touched them. and how come everyone seems to have a different network-admin tool than i do?

thanks for any replies. :confused:

---

### Post by spd106 on 2007-08-17
It could be a driver related issue, although would I prefer to use bcm43xx I have found that ndiswrapper currently get better results. Particularly in reduced signal environments i.e. where there is interference or as you move further from the AP.

To test the connection try monitoring the the /var/log/syslog file for connection progress. 

Also If you get a link-local address (169.254.x.x), try pinging the 224.0.0.1 multicast address. Then if you get any replies you know that you do have a connection and that DHCP is failing for some reason. It isn't guaranteed that you will get any replies as not all AP/network devices support multicast.

---

### Post by chrisch on 2007-08-21
It could be as easy as the configuration of the profile.  I brought my laptop to work and thinking that the security should be set to closed with a wep key, it wanted to be open with the wep key.

---

