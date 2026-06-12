---
title: "resolv.conf gets overwritten"
date: 2017-11-20
forum: Networking &amp; Wireless
---

### Post by Chesslover on 2017-11-20
I have DNS leak when using OpenVPN. I disabled and stopped  systemd-resolved and installed dnsmasq. I added line to  NetworkManger.conf (dns=dnsmasq). I think problem lies in resolv.conf  file, which has 3 local nameservers. If I delete them and write  nameserver 127.0.1.1 and 8.8.8.8 and 8.8.4.4 it solves problem. I have  no DNS leakage, but only for a minute or so. After that my resolv.conf  file gets overwritten with my local servers. I checked syslog file and  found out that error:
```
dnsmasq: failed to create listening socket for 127.0.1.1: Address already in use
```

Because of that error dnsmasq does not start and resolv.conf gets  overwritten with previous (local) nameservers...how can I get that  sorted out?

---

### Post by feartheterrapin on 2017-12-25
I saw on another forum to comment out the "dns=dnsmasq" in the  /etc/NetworkManager/NetworkManager.conf to stop DNS leaks.  This works for me with all  OpenVPN connections so far.

---

