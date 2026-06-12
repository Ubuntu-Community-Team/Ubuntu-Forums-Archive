---
title: "IPv6 connections timeout"
date: 2014-12-24
forum: Networking &amp; Wireless
---

### Post by e633 on 2014-12-24
Hello, i'm having issues with IPv6 connections. Only with those. They timeout roughly every 10 minutes (due to address renewal i suppose). 
Happens with every debian based flavour of linux i tried in a year or so, x86 and x64, across different PCs, wired and wireless. 
Currently using kernel 3.13.0-37-generic x86_64; previously 3.2.0-60.
This is an example of what happens: [http://pastebin.com/4Xida2qu](http://pastebin.com/4Xida2qu)
Sometimes when i try to immediately restart the download i get "no route to host." because my IPv6 addresses seem to be momentarily gone.
I'm running dual stack IPv4 - IPv6 (PPPoE), this is how my Netgear DGND3700v2 router (firmware version V1.1.00.22_1.00.22) is configured: [http://i.imgur.com/YgxAyQb.png](http://i.imgur.com/YgxAyQb.png)
The network profile in question (network-manager version 0.9.8.8) is set to *ignore* IPv6 but i'm getting global IPv6 addresses anyway. Changing to auto does not make any difference. This is confusing but i guess it's just the kernel doing its job.
Firewall rules *or lack thereof* don't make any difference but they basically are ```
iptables -P INPUT DROP
ip6tables -P INPUT DROP
iptables -P FORWARD DROP
ip6tables -P FORWARD DROP
iptables -A INPUT -i lo -j ACCEPT
iptables -A OUTPUT -o lo -j ACCEPT
ip6tables -A INPUT -i lo -j ACCEPT
ip6tables -A OUTPUT -o lo -j ACCEPT
iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
ip6tables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
#Allow all ICMP for IPv6
ip6tables -I INPUT  -p icmpv6 -j ACCEPT

```

---

### Post by e633 on 2014-12-26
No luck with DHCP either.

---

### Post by e633 on 2015-01-07
[https://unix.stackexchange.com/questions/176013/ipv6-connections-timeout](https://unix.stackexchange.com/questions/176013/ipv6-connections-timeout)

---

