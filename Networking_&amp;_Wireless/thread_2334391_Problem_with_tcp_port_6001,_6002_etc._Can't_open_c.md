---
title: "Problem with tcp port 6001, 6002 etc. Can't open connection to working application."
date: 2016-08-19
forum: Networking &amp; Wireless
---

### Post by ssbaksa2 on 2016-08-19
Hi,

On newly installed 16.04 server i have installed nodejs environment for some development purpose. After creating a small test application which is listening on port 6001 I was not able to connect to that app either from remote client or from local one.

netstat -an | grep 6001 ashured me that port is free and after starting my app, app is bounded to that port and ethernet IP.

Both firewalls are down (iptables -L and ufw status shows that).

Tcpdump and tshark do not show any traffic toward that port.

I have changed nodejs versions to make sure that it is not node problem.

After changing port to 8080 app started to accept connections.

To test my setup I have installed all that nodejs environment to 14.04.4 server (always updated to latest version) and all worked well on all ports. There was no problems with 600x ports.

My question is which mechanism is used to block port access if ufw and iptables are not the blocking point? What is changed from 14.04 to 16.04 netwoking except systemd?

I have searched net for similar problem but non was found.

Br

Sasa

---

