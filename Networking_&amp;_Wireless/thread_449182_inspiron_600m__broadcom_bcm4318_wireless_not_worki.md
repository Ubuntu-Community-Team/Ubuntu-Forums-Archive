---
title: "inspiron 600m / broadcom bcm4318 wireless not working"
date: 2007-05-20
forum: Networking &amp; Wireless
---

### Post by rphilli5 on 2007-05-20
Relatively new to linux and I am struggling with configuring the wireless.   I have followed the 7.04 trouble shooting guides and it appears the driver is configured correctly, however I can never connect.   I have two different wireless networks and can't get to either.  One is wep and the other is now open (for easier testing).  Running lshw shows the network is disabled.  Is this because it has not connected yet?

I also tried WIFI Radar which also does not work.  It does not detect what networks are nearby and will not let me connect if I enter the essid

Configuring the connection through command line was also not working (or at least the way I was trying to do it)

What should I try next?

---

### Post by Bachstelze on 2007-05-20
First, make sure your wireless adapter *is* detected :

```
sudo iwconfig
```

---

### Post by slavik on 2007-05-20
make sure to enable the wireless connection in the network manager ... I forgot that once ;)

---

