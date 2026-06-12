---
title: "DNS is not applied from DHCP offer"
date: 2017-05-11
forum: Networking &amp; Wireless
---

### Post by djmentos on 2017-05-11
Hello all,

I am in trouble related to DHCP & DNS, first of all log:
```
May 11 14:54:10 gklab-119a-210 NetworkManager[8835]:   [1494507250.2976] dhcp4 (enp4s0):   address 10.91.119.210 May 11 14:54:10 gklab-119a-210 NetworkManager[8835]:   [1494507250.2978] dhcp4 (enp4s0):   plen 24 (255.255.255.0) 
May 11 14:54:10 gklab-119a-210 NetworkManager[8835]:   [1494507250.2978] dhcp4 (enp4s0):   gateway 10.91.119.1 May 11 14:54:10 gklab-119a-210 NetworkManager[8835]:   [1494507250.2979] dhcp4 (enp4s0):   server identifier 172.28.170.7 
May 11 14:54:10 gklab-119a-210 NetworkManager[8835]:   [1494507250.2980] dhcp4 (enp4s0):   lease time 302400 May 11 14:54:10 gklab-119a-210 NetworkManager[8835]:   [1494507250.2981] dhcp4 (enp4s0):   hostname 'gklab-119a-210' 
May 11 14:54:10 gklab-119a-210 NetworkManager[8835]:   [1494507250.2982] dhcp4 (enp4s0):   nameserver '10.248.2.1' May 11 14:54:10 gklab-119a-210 NetworkManager[8835]:   [1494507250.2983] dhcp4 (enp4s0):   nameserver '163.33.253.76' 
May 11 14:54:10 gklab-119a-210 NetworkManager[8835]:   [1494507250.2983] dhcp4 (enp4s0):   domain name 'i.i.com' May 11 14:54:10 gklab-119a-210 NetworkManager[8835]:   [1494507250.2984] dhcp4 (enp4s0):   wins '10.125.144.16' 
May 11 14:54:10 gklab-119a-210 NetworkManager[8835]:   [1494507250.2985] dhcp4 (enp4s0):   wins '163.33.7.86'
```

As I see - DHCP offers me DNS servers, but in resolv.conf there is still 127.0.0.53. How can I enforce NetworkManager to write DNSes from DHCP? U 17.04.

---

### Post by chili555 on 2017-05-11
By default, newer Ubuntu versions use dnsmasq: [https://help.ubuntu.com/community/Dnsmasq](https://help.ubuntu.com/community/Dnsmasq) > A local DNS cache can speed up internet browsing because the user's browser will not need to access a domain name server when it looks up a domain name the computer has visited before.The listing in /etc/resolv.conf of a DNS nameserver 127.0.0.53 means, roughly, that the system should look within its own cache before asking an outside nameserver, 10.248.2.1 in your case, for resolution.> I am in trouble related to DHCP & DNS,Please tell us more, and we'd love to know more details about the system to which you connect. Is it a corporate system? A university? A home router or switch?

---

