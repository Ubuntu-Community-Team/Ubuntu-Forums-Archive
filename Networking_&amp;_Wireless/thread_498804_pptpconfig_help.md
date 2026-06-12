---
title: "pptpconfig help"
date: 2007-07-11
forum: Networking &amp; Wireless
---

### Post by ray-in-ojai on 2007-07-11
To make Ubuntu work for me, i need to get a VPN tunnel to several different offices. I'm able to connect to a remote WatchGuard firewall/VPN server. Grab an ip address from the WatchGuard, but am not able to ping any workstations on the remote network. Here is what i get.

Using interface ppp0
pptpconfig: monitoring interface ppp0
Connect: ppp0 <--> /dev/pts/1
Warning - secret file /etc/ppp/chap-secrets has world and/or group access
CHAP authentication succeeded
MPPE 128-bit stateless compression enabled
Cannot determine ethernet address for proxy ARP

Does it have anything to do with the last line?

Ray

---

### Post by ray-in-ojai on 2007-07-12
It appears you have to add a static route after you connect. Then it works fine.

Example:

sudo route add -net 192.168.0.0 netmask 255.255.255.0 dev ppp0

---

