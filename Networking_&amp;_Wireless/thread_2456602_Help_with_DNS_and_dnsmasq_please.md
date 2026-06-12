---
title: "Help with DNS and dnsmasq please"
date: 2021-01-15
forum: Networking &amp; Wireless
---

### Post by bsh on 2021-01-15
Hi,
I have rebuilt/restructured my network, and now can't get dnsmasq working as I want it to.
Current situation: new VLAN router, now acting as a DHCP server for all VLANS. Clients are usind DHCP form the router, but are statically mapped. There is a server on one of those VLANs, which is running dnsmasq (for DNS only, no DHCP). The router is pushing the server's IP address as the primary DNS server. There is also a domain suffix for this VLAN: "my-lan". The DNS queries are then served by dnsmaq on the server.
Previously the clients were defined in /etc/hosts, and dnsmasq resolved them from there. I want to get rid of this, and I want the router to resolve local host names. But I still want to use dnsmasq as a "proxy", for caching and filtering.
The problem is, when I try to nslookup a local client's ip by hostname, dnsmasq, it only seems to resolve them from /etc/hosts, and doesn't seem to forward them towards the router. So when I delete entries from /etc/hosts, I get no resolve.
When I try to nslookup a hostname directly using the router's DNS, it only works if I add the domain suffix to the simple hostname. So for example: "nslookup examplehost 192.168.2.1": doesn't resolve. "nslookup examplehost.my-lan 192.168.2.1": works. (Windows clients automatically add the domain suffix)
I have tried to play with the below settings.

```
domain-needed
bogus-priv
strict-order
no-resolv
no-poll
server=/my-lan/192.168.2.1
server=8.8.8.8
local=/my-lan/
expand-hosts
domain=my-lan
cache-size=1000
```

---

### Post by SeijiSensei on 2021-01-15
To get Linux systems to resolve "unqualified" names like "myhost", you need to add a search parameter to /etc/resolv.conf that points to the domain name. Usually you can get the DHCP server to push that entry to the client.

On modern Ubuntu systems that use systemd-resolved, you can add the search domains to the "Domains" line in /etc/systemd/resolved.conf.

Dnsmasq (and resolveconf) have been deprecated in Ubuntu since the switch to systemd.

---

