---
title: "Two internet connections and addresses sending"
date: 2014-01-28
forum: Networking &amp; Wireless
---

### Post by Juraj_Kudrn on 2014-01-28
I have two internet connection wlan0(mobile connection) and eth0(in my work).
We have some addresses blocked in my work through eth0 so I need to send some addresses through wlan0.
Is it possible?

Example:
1) [www.facebook.com]("http://www.facebook.com") blocked through eth0 so I need to send through wlan0 
2) [www.gmail.com]("http://www.gmail.com") not blocked through eth0 so I want to send through eth0

---

### Post by sanderj on 2014-01-28
routing is your friend.

[http://www.cyberciti.biz/tips/configuring-static-routes-in-debian-or-red-hat-linux-systems.html](http://www.cyberciti.biz/tips/configuring-static-routes-in-debian-or-red-hat-linux-systems.html)

start with "ip route show"

Disclaimer: I once tried this myself, and did not get it working.

---

