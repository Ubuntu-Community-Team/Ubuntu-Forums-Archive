---
title: "No internet access"
date: 2007-05-24
forum: Networking &amp; Wireless
---

### Post by ronniej962 on 2007-05-24
I have a fresh copy of Ubuntu 7 and am unable to connect to the internet. I've edited the blacklist for ipv6, I've turned off ipv6 via alias net-pf-10 ipv6, I've set the nameservers to 208.67.222.222, 208.67.220.220 and still nothing.

Background:
Small LAN consisting mostly of Windows servers on a Windows 2000 domain. 
DHCP and DNS servers in place.
Primary DNS ip for network is Local DNS server
Secondary/Additional - ISP's DNS ips
Linksys Router SRX 200 (Gateway) firmware version 1.01.18
Ubuntu PC - Desktop, wired networking

Cannot download updates
Cannot access sites via Firefox

ifconfig returns ip address issued by DHCP server

Please help.

Thanks in advance

---

### Post by atoponce on 2007-05-24
Can you paste the output of 'sudo ifconfig -a'?

---

