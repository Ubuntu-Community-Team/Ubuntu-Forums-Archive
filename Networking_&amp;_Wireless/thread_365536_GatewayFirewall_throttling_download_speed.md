---
title: "Gateway/Firewall throttling download speed"
date: 2007-02-19
forum: Networking &amp; Wireless
---

### Post by Royel on 2007-02-19
My gateway/fireway (ubuntu 6.06 server) is throttling my bandwidth to clients, I should get close to 3MB/s down but it is choking me to around 1-1.2MB/s.
 I have tested extensively, with an without the server in the picture an it keeps coming back to the server being the only time things slowdown. I replaced all the nics just earlier today.
Here is some output
 
root@pengserv:~ # mii-tool
SIOCGMIIPHY on 'eth1' failed: Invalid argument
eth2: negotiated 100baseTx-FD flow-control, link ok
eth3: negotiated 100baseTx-FD flow-control, link ok

lspci:
0000:01:09.0 Ethernet controller: Linksys NC100 Network Everywhere Fast Ethernet 10/100 (rev 11)
0000:01:0b.0 Ethernet controller: Linksys NC100 Network Everywhere Fast Ethernet 10/100 (rev 11)



 Any clues?

---

