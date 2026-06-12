---
title: "ssh question ,howto keep debianetch(server) -kubuntu(client) steady"
date: 2008-02-02
forum: Networking &amp; Wireless
---

### Post by firedancer on 2008-02-02
Hi, i can ssh into my debian etch server from my kubuntu gutsy but after a few seconds the connection is gone/broken
the problem lies at the debain etch server 
i changed etc/network/interfaces added a static ip 
restarted  etc/init.d/networking
but i constantly need to ifconfig eth0 ip_nummer my debian server ,to connect from kubuntu box     

how can change/fix this permanently 

thnx in advance

firedancer

---

### Post by firedancer on 2008-02-04
ok , i am able to ssh into my debian server after setting static ip and route ,etc..

how do i makesure it happens at boot or after , 

should i do something with these files  resolv.conf. and host.conf 
i'm trying to set up a home lan network for a learning environment 

would like to have it setup at/after booting pc's :?:

firedancer
SOLVED

---

