---
title: "Ubuntu domainname and DD-WRT DNSMasq"
date: 2013-12-07
forum: Networking &amp; Wireless
---

### Post by kernalsanders123 on 2013-12-07
Hello all, having a slight issue with domain names on my Ubuntu Server 12.04.3 install. I use the DNSMasq service included on my DD-WRT flashed router. It resolves filenames fine, including pinging other LAN hosts and also itself using just hostname and the fqdn. However, the server does not seem to be able to set the domain name correctly. Running domainname returns (none), dnsdomainname returns nothing, and dnsdomainname returns "local domain name not set." The Ubuntu documentation says to only use the hostname and not the fqdn in the hosts file, so I don't think doing it that way will work. Is there anything I'm missing in my setup of either dnsmasq or Ubuntu that I might be missing? Thanks for any help anyone may be able to provide.

---

### Post by bashiergui on 2013-12-09
You can try this
[http://askubuntu.com/questions/158957/how-to-set-the-fully-qualified-domain-name-in-12-04](http://askubuntu.com/questions/158957/how-to-set-the-fully-qualified-domain-name-in-12-04)

---

