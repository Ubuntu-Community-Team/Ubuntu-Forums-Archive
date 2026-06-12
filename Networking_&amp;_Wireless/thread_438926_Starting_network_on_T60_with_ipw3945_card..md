---
title: "Starting network on T60 with ipw3945 card."
date: 2007-05-10
forum: Networking &amp; Wireless
---

### Post by neaj on 2007-05-10
I tried to get my wifi network going with network-admin, but it couldn't get an IP address. It could see the networks, but couldn't connect. This worked:

```

iwconfig eth0 essid XXXXXX key restricted s:XXXXX ap 00:11:22:A3:84:D5 commit
dhclient eth0

```

I got the access point address from ```
iwlist spy
```. 

What should I have done to get it working with Ubuntu's tools? I see recommendations for 
[wicd]("http://wicd.sourceforge.net/"), but that's not in the repos. Is it the way to go?

---

