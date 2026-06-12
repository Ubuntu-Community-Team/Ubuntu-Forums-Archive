---
title: "Can not resolve local host names"
date: 2017-04-14
forum: Networking &amp; Wireless
---

### Post by d-3s-i on 2017-04-14
Until I upgraded to 17.04 this worked:

dig mule
Has been resolved to "mule.fritz.box" which could be resolved.
The suffix "fritz.box" is provided by DHCP.

Since the update this no longer works:

dig mule
 

systemd-resolve --status:
Link 2 (eth1)
      Current Scopes: DNS LLMNR/IPv4 LLMNR/IPv6
       LLMNR setting: yes
MulticastDNS setting: no
      DNSSEC setting: allow-downgrade
    DNSSEC supported: yes
         DNS Servers: fd00::ca0e:14ff:fee5:a0c1
                      192.168.0.1
          DNS Domain: fritz.box


So I can see that the "DNS Domain" is correct. Unfortunately this does not work.
The debug output for systemd-resolved does not provide any information regarding "fritz.box". So I am out of ideas here.

dig mule.fritz.box works as expected.

---

