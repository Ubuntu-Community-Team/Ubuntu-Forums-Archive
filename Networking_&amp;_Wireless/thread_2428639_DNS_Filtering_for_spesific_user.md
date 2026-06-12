---
title: "DNS Filtering for spesific user"
date: 2019-10-07
forum: Networking &amp; Wireless
---

### Post by rupadana on 2019-10-07
i've been build server for DNS Filtering and i want to forward my openwrt to my DNS server
i'm using the iptables for forwarding the port of DNS

[HTML]iptables -t nat -A PREROUTING -p udp -s 192.168.1.129 --dport 53 -j DNAT --to-destination xxx.xxx.xx.xx:xxx[/HTML]

and i got DNS_PROBE_FINISHED_NO_INTERNET

[IMG]https://forum.openwrt.org/uploads/default/original/2X/1/1f5a45d55e48b6d4abe0ea734757de898a851b7c.jpeg[/IMG]

---

### Post by TheFu on 2019-10-07
If you want to filter DNS or web access, there are much easier ways.
a) use pi-hole [https://pi-hole.net/](https://pi-hole.net/)
b) setup a squid proxy server [https://help.ubuntu.com/lts/serverguide/squid.html](https://help.ubuntu.com/lts/serverguide/squid.html)

DNS isn't on a per-user basis.
Squid proxy can be on a per-user basis, assuming you require a login for each user to the Squid server.

Please don't place the full image inline here. Mobile platforms have problems with it and some people pay for each byte they see.  Images need to be optional, not forced, in these forums.

---

### Post by SeijiSensei on 2019-10-07
If you're building a DNS server, why do you need to forward anything at all?  Just install BIND9 and let it see the Internet.  All my local clients use the DNS server sitting in the corner of my office.

I don't know what you're using openwrt for, but if you have a domain and zone files, just replicate them on the server.

---

