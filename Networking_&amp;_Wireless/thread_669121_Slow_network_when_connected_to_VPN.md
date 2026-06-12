---
title: "Slow network when connected to VPN"
date: 2008-01-16
forum: Networking &amp; Wireless
---

### Post by Bohdan200 on 2008-01-16
Hello everybody!
I have a trouble with network - it's very slow but only when VPN connection is enabled.
Download speed from local ftp server is almost 5MBytes/s (100Mb/s ethernet), but when I connect to my ISP via pptp download speed drops to 100KBytes/s via local network.
I have installed network-manager-pptp and linux-pptp.
I'm a n00b in Linux, can somebody help me?

---

### Post by Bohdan200 on 2008-01-23
No solution? I spend many time to find similar problem reports in the internet, but I did not found anything. I think I'm alone with this bug (maybe misconfiguration?). How pptp connection may slowdown the locat ethernet speed? I dont understand this. ](*,) :-(

---

### Post by vmikac on 2008-04-07
I had a slow connection, and solved the problem by removing sync option from the /etc/ppp/peers/connection_name file.

---

