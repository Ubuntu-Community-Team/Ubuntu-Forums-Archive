---
title: "Resolved openvpn dns leaks"
date: 2022-10-10
forum: Networking &amp; Wireless
---

### Post by glenriver on 2022-10-10
Hello all.
I am running xubuntu 22.04 and having dns leaks. I have configured the client connection to only use automatic vpn addresses only and then supply the two dns servers in the client. It is resolving to cloudflare dns servers and not my vpn providers addresses. Any clue to where I might begin to resolve this issue would be appreciated and thanks


Link 4 (tun0)
    Current Scopes: DNS
         Protocols: +DefaultRoute +LLMNR -mDNS -DNSOverTLS DNSSEC=no/unsupported
Current DNS Server: 109.236.87.2
       DNS Servers: 109.236.87.2 23.237.56.98




These are correct when running resolvctl status

---

