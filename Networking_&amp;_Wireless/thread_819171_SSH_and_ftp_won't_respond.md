---
title: "SSH and ftp won't respond"
date: 2008-06-05
forum: Networking &amp; Wireless
---

### Post by Akuu on 2008-06-05
Hi
I can ping and traceroute my machine, both over IP and dyndns. But every attempt to connect over SSH and ftp fails. Ports are forwarded in the router and hosts.allow has ALL:ALL in it. Configuration seems to be ok too because I can connect locally.
What could the problem be?  :confused:

---

### Post by Quintin Riis on 2008-06-05
More details, please.

---

### Post by superprash2003 on 2008-06-05
to ensure ports are forwarded try with online port scanner [http://www.t1shopper.com/tools/port-scanner/](http://www.t1shopper.com/tools/port-scanner/)

---

### Post by scottie277 on 2008-10-20
I had a similar problem (possibly). See this thread.
[http://ubuntuforums.org/showthread.php?p=5976581#post5976581](http://ubuntuforums.org/showthread.php?p=5976581#post5976581)

Basically unubtu was shutting down my eth0 connection after some idle time. I added a cron job that pings google every few minutes to keep the eth0 adapter "alive".
I think all the info you need is in the thread. :)

---

