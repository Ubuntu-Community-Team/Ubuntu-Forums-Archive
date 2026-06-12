---
title: "When primary dns fails, xenial doesn't switch to secondary or tertiary dns server."
date: 2017-03-12
forum: Networking &amp; Wireless
---

### Post by marrowm on 2017-03-12
I just had an strange problem, I have configured three dns-servers in network manager. But when the primary one went down Ubuntu couldn't resolve any names despite the secondary and tertiary dns working just fine. (I used dig to confirm this.) Also, changing the order of nameservers in the networkmanager config and reconnecting didn't work either. Nor did removing the offending nameserver from the config and reconnecting. In the end I disabled dnsmasq (by commenting out "dns=dnsmasq" in /etc/NetworkManager/NetworkManager.conf) and now everything works as expected.

Tried to reproduce it but now everything works again it seems. :-k

---

