---
title: "iptables port forwarding"
date: 2015-08-14
forum: Networking &amp; Wireless
---

### Post by ODTech on 2015-08-14
Hi All.

I'm having some difficulty getting iptables to forward ports and would like some guidance if possible.

I have a d-link 2750u router with the unix firewall setup as a DMZ server. (If i understand d-link definition of DMZ then all unspecified ports gets forwarded to the server by default.
router ip 193.100.83.2

Behind the router is a ubuntu 12.04 LTS box acting as a gateway, firewall, dhcp server
wan eth0 194.100.82.1
lan eth1 192.168.1.1

I need to forward port x to ip 192.168.1.197 inside the lan.
I need to also forward port y to ip 192 168.212.1

I've tried to follow some guides on the web but i can't seems to get it working.

Any iptable gurus able to help?

Thanks

---

### Post by ODTech on 2015-08-23
I employed some more googlefu and found my answer on this very forum.

[http://ubuntuforums.org/showthread.php?t=926001](http://ubuntuforums.org/showthread.php?t=926001)

---

