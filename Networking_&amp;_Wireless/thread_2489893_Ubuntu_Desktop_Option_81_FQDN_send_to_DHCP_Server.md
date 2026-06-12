---
title: "Ubuntu Desktop Option 81 FQDN send to DHCP Server"
date: 2023-08-13
forum: Networking &amp; Wireless
---

### Post by darknewt on 2023-08-13
Hi,

hoping someone can point me in the right direction.   I am working in an environment where we have implemented Option 81 support to allow clients to send their FQDN during DHCP lease allocation so that the DHCP server can register their A/ptr records in DNS.   I would like to get this working for Ubuntu, so I am looking for suggestions on how/where this can be configured.

I have use hostnamectl to set it but this doesn't send it to the DHCP server during the lease process.  I have also tried setting it as the machines identity and likewise this does not send it.

The end goal is to simply send the fqdn so that the client can be registered in the correct zone, currenly on the latest version of ubunt as of last night and fully updated.


Many thanks in advance!

---

