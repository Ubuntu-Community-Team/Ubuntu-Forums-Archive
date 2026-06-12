---
title: "systemd-resolved: default route added before defined DNS servers?"
date: 2022-07-10
forum: Networking &amp; Wireless
---

### Post by Milan Knizek on 2022-07-10
Hi,

A fresh install of Kubuntu 22.04. I have DHCP serving the DNS servers: 10.11.13.21, 10,11.13.1, 208.67.222.222 (in this order), where

[LIST]
[*]10.11.13.21 is pihole (DNS for LAN)
[*]10.11.13.1 is router/gateway/default route
[/LIST]

However, Kubuntu uses the gateway 10.11.13.21 as its primary DNS:

```

# resolvectl status
Global
       Protocols: -LLMNR -mDNS -DNSOverTLS DNSSEC=no/unsupported
resolv.conf mode: stub

Link 2 (enp0s31f6)
    Current Scopes: DNS
         **Protocols: +DefaultRoute **+LLMNR -mDNS -DNSOverTLS DNSSEC=no/unsupported
**Current DNS Server: 10.11.13.1**
       DNS Servers: 10.11.13.21 10.11.13.1 208.67.222.222
        DNS Domain: example.net


```

This is probably because of the +DefaultRoute flag, as per 'dns' section here: [https://www.freedesktop.org/software/systemd/man/resolvectl.html](https://www.freedesktop.org/software/systemd/man/resolvectl.html)

That's a problem, because:
[LIST]
[*] the router (and any public DNS server) resolves URL server.example.net:1234 to my public IP address (I assume my USG router does hairpin NAT and packets from my PC are blocked by its firewall for port 1234).
[*] pihole DNS at 10.11.13.21 resolves a private address for server.example.net:1234 - which is thanks to static hosts on pihole and which is a wanted behaviour.
[/LIST]

By the way, the "traditional" resolv.conf is correct:

```

# cat /run/systemd/resolve/resolv.conf 
nameserver 10.11.13.21
nameserver 10.11.13.1
nameserver 208.67.222.222
search example.net

```

It just that systemd-resolved.service adds its own stuff on top of it.

**Any ideas why avoding DNS servers served by DHCP server would be a "feature" of default (K)Ubuntu installation?**

P.S. I do not see this problem on other hosts on LAN: android phones, Windows 10, Ubuntu 20.04.

---

