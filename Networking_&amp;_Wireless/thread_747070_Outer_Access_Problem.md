---
title: "Outer Access Problem"
date: 2008-04-06
forum: Networking &amp; Wireless
---

### Post by x53x6ex69x67x67x65x72 on 2008-04-06
Hi
I have Xampp , SSH , Ktorrent (web interface) and one my own wrote server but while they are accessible (and working fine) from localhost or 127.0.0.1 I can't access them with my ip address via other PCs in Internet !
I checked TCP warper files and all of them was empty!
I checked iptables too but there were no rule too:
```
Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

```When I ran:
```
nmap {my_ip_address}
```it just discovered one open port (FTP:21) that is my ADSL modem's internal ftp server, and none of my open ports discovered (while they are discoverable from 127.0.0.1) .
When I ran Xampp servers previously in windows there were no problem and port 80 was accessible via Internet !!

What's the problem??
Thanks from all.

---

