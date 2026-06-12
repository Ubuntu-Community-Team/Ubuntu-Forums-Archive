---
title: "DNS issues"
date: 2007-02-03
forum: Networking &amp; Wireless
---

### Post by IcarusR on 2007-02-03
Hi
I have a small local network made up from
1. Server running Dapper. SAMBA & SLIMSERVER
2. Laptop running Edgy
3. Desktop running XP
4. Laptop running XP
Draytek 2600G wireless/wired router connected to internet.

All are configured to use DHCP to get dynamic IP from router & have DNS server set to router.
I discovered I can not connect to Serever using name but can using IP. When ping by name the name is resolved using ISP DNS & therefore trys to ping a WWW server. Further digging revealed that Draytek 2600 does not act as DNS server for LAN, only WAN.

I have tried setting server to static IP & entering it's name & IP to /etc/hosts file & restarting networking, but this does not help.

I would like to be able to ping/connect to any PC on the network by name as well as IP

My question is how can I get around this ?

Thanks

---

### Post by IcarusR on 2007-02-03
I know I could setup DNS on my server, but can this be setup to only deal with local requests (on 192.168.1. for example) & all other requests sent via router to my ISP's DNS server?
If so would this slowdown internet surfing ?

---

