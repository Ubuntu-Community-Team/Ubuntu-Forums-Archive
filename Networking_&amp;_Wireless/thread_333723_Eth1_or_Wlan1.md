---
title: "Eth1 or Wlan1"
date: 2007-01-07
forum: Networking &amp; Wireless
---

### Post by Stephen47 on 2007-01-07
Which one of these should my wireless card be rcognized as?
I have an Intel Pro Wireless 3495 and in Networking it says my active wireless connection iw Eth1 I thought wireless connections were Wlan. Although it says it is activated I cannot connect ot my wireless router.

---

### Post by scrooge_74 on 2007-01-07
do ifconfig and all your network cards will appear, if it says your wireless is eth1 then it is so.

Try taking down the securiy of the router first and see if it can connect

do sudo ifdown eth1
sudo ifup eth1
sudo dhclient eth1

---

### Post by Stephen47 on 2007-01-09
I disabled the security and networking says my wireless is enabled but it won't connect.

---

### Post by scrooge_74 on 2007-01-09
Check this links 

[http://www.ubuntuforums.org/showthread.php?t=269438&highlight=wireless+network](http://www.ubuntuforums.org/showthread.php?t=269438&highlight=wireless+network)

[https://help.ubuntu.com/community/WifiDocs/WPAHowTo](https://help.ubuntu.com/community/WifiDocs/WPAHowTo)

[http://www.ubuntuforums.org/showthread.php?t=202834](http://www.ubuntuforums.org/showthread.php?t=202834)

---

