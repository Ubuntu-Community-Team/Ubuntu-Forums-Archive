---
title: "Dns issue with IPV6 and ubuntu 22.04"
date: 2024-02-19
forum: Networking &amp; Wireless
---

### Post by mikael144 on 2024-02-19
Dear all,

I have been using ubuntu 22.04 for a while with a wireless network without tuning anything in the network manager.
Since few weeks I got random issues on some websites (not google.com, youtube.com etc....) during few minutes then it worked again.
I tried with an ethernet interface and it did the same.

I disabled the IPv6 in the network manager and then no random issues. I tried to understand the problem but it made me noodles in my head. 
So in the network manager of my wifi interface I setup the DNS6 manually with the ones of cloudflare. SInce I did that, everything works fine.

This was my ```
[nmcli/CODE] :

[CODE]wlp4s0: connecté à
        "Intel 7265"
        wifi (iwlwifi), , hw, mtu 1500
        ip4 par défaut, ip6 par défaut
        inet4 192.168.1.46/24
        route4 192.168.1.0/24 metric 600
        route4 169.254.0.0/16 metric 1000
        route4 default via 192.168.1.254 metric 600
        inet6 2001:861:3a01:1d40:4f1a:dab7:18fb:63ed/64
        inet6 2001:861:3a01:1d40:ce53:b755:915e:b6c4/64
        inet6 fe80::9186:1e53:af71:e41b/64
        route6 fe80::/64 metric 1024
        route6 2001:861:3a01:1d40::/64 metric 600
        route6 default via fe80::d26e:deff:fec5:461c metric 600

p2p-dev-wlp4s0: déconnecté
p2p-dev-wlp4s0: déconnecté
wlp4s0: connecté à
        "Intel 7265"
        wifi (iwlwifi), , hw, mtu 1500
        ip4 par défaut, ip6 par défaut
        inet4 192.168.1.46/24
        route4 192.168.1.0/24 metric 600
        route4 169.254.0.0/16 metric 1000
        route4 default via 192.168.1.254 metric 600
        inet6 2001:861:3a01:1d40:4f1a:dab7:18fb:63ed/64
        inet6 2001:861:3a01:1d40:ce53:b755:915e:b6c4/64
        inet6 fe80::9186:1e53:af71:e41b/64
        route6 fe80::/64 metric 1024
        route6 2001:861:3a01:1d40::/64 metric 600
        route6 default via fe80::d26e:deff:fec5:461c metric 600

p2p-dev-wlp4s0: déconnecté
        "p2p-dev-wlp4s0"
        wifi-p2p, hw

enp0s25: indisponible
        "Intel I218-LM"
        ethernet (e1000e), , hw, mtu 1500

lo: non-géré
        "lo"
        loopback (unknown), 00:00:00:00:00:00, sw, mtu 65536

DNS configuration:
        servers: 192.168.1.254
        domains: lan
        interface: wlp4s0

        servers: 2001:861:3a01:1d40:d26e:deff:fec5:461c
        domains: lan
        interface: wlp4s0
```

Also ```
resolvectl 
``` gave :

```
Global
       Protocols: -LLMNR -mDNS -DNSOverTLS DNSSEC=no/unsupported
resolv.conf mode: stub

Link 2 (enp0s25)
Current Scopes: none
     Protocols: -DefaultRoute +LLMNR -mDNS -DNSOverTLS DNSSEC=no/unsupported

Link 3 (wlp4s0)
    Current Scopes: DNS
         Protocols: +DefaultRoute +LLMNR -mDNS -DNSOverTLS DNSSEC=no/unsupported
Current DNS Server: 2001:861:3a01:1d40:d26e:deff:fec5:461c
       DNS Servers: 192.168.1.254 2001:861:3a01:1d40:d26e:deff:fec5:461c
        DNS Domain: lan
```
 


On my other machines (two Android smartphones, one Chromebook and a PC on win10) I got no issues. 
I was wondering if there could be some explanations or if it is my provider who has f******* up dns ipv6.

Thanks for your help,

---

