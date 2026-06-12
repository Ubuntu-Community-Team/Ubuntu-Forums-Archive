---
title: "SSH -- &quot;Connection refused&quot; error"
date: 2008-09-03
forum: Networking &amp; Wireless
---

### Post by jvincent08 on 2008-09-03
This is odd. Last night I set up an ssh server and was able to successfully connect to it from school today. When I got home, I signed up for dyndns. When I tried to connect to it using the same machine the server is running on and from another computer on my LAN using the dyndns domain, I get "connection refused". I even get this when using the IP itself, which I was able to do just a few hours before. I thought maybe it had something to do with dyndns, so I removed the host from my account and tried again. Same thing. I've double checked my router and firewall and the port is opened and forwarded properly. My router's log reports that it is accepting the connections, and port scanners verify that the port is open. I can log in just fine using the hostname or LAN IP (192.168...), but not the external IP or the dyndns domain.

Any ideas on where I could look to find the problem?


Edit: Well, it appears as though everything was fine after all. I was able to log in from school again today, but I still can't log in on the server machine using it's WAN IP address.. oh well *shrug*

---

