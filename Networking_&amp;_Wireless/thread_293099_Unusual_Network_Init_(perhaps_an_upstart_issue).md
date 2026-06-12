---
title: "Unusual Network Init (perhaps an upstart issue)"
date: 2006-11-04
forum: Networking &amp; Wireless
---

### Post by timbobsteve on 2006-11-04
Hi All,

I just upgraded to Edgy (nice work team, it is solid as a rock!).
I have however noticed one strange problem. Networking is not starting when I boot my system so I have to "/etc/init.d/networking start" manually. Also when I run this command it tries to initialise a whole range of devices I don't have, like "eth1 eth2 ath0 wlan0" etc... this takes a little extra time, but not much so I am not sure how big a problem it is.

1) How do I verify that /etc/init.d/networking is being started on boot?
2) If it is not, how do I add it to startup now that upstart has replaced sysvinit?
3) How do I modify the networking script to only start devices I have (eth0)?

Thanks.

---

### Post by timbobsteve on 2006-11-04
OK.... Solved the problem partly. I did not know about /etc/network/interfaces .... I modified that by commenting out all the invalid interfaces and now only eth0 is started with "/etc/init.d/networking start"... however the problem still remains that eth0 is not being brought up at boot.

Thanks.

---

