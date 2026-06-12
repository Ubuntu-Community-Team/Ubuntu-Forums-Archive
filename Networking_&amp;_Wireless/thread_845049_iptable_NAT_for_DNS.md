---
title: "iptable NAT for DNS"
date: 2008-06-30
forum: Networking &amp; Wireless
---

### Post by thierry34000 on 2008-06-30
Hi,

I'm doing a semi captive portal.
The DHCP server of the network if configured to a local DNS server that returns a local ip as apache server for any domain request.
The primary DNS that DHCP delivers if an on-line one, the second the local one.
Since by default I have :
/sbin/iptables -I FORWARD -d $1 -j DROP
For all the local clients IPs, it's the local 
When authentified, the authorized user ip is opened by :
/sbin/iptables -I FORWARD -d $1 -j ACCEPT

I want to short the delay of the local caches of all the clients (linux, mac, windows, wifi phones, ...) by natting the ISP DNS to the local one so i do not longer need that DHCP send as secondary the local DNS.

Anyone can help for declaring correct iptables rules.
I've tried a log of different ones, but I've not obtained the behavior i want to have and i described there.

I have bind9, dhcp-server3 and ubuntu 8.04 installed.


Thanks for your help

---

