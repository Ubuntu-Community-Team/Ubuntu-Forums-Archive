---
title: "Connection timed out ; no servers could be reached error"
date: 2016-08-10
forum: Networking &amp; Wireless
---

### Post by hak1421 on 2016-08-10
[TABLE]
[TR]
[TD="class: votecell"]

[/TD]
[TD="class: postcell"]I have configured a DNS server in Linux Ubuntu 16.04 LTS. But when I type   "dig -x 8.8.8.8"    from any client's machine while changing its nameserver in     /etc/resolv/conf   file   to the IP address of my DNS server which is 192.168.0.192 and also changing its dns-nameserver in   /etc/network/interfaces    to address of my DNS server, I am not able to get any response from my clients machine. I am getting this error on clients machine " Connection timed out: no servers could be reached". 
Moreover When I type " ping -c 1 8.8.8.8 " on clients machine ,  I get a response " .
Can anybody please help me to make my Clients machine work properly and go through my DNS server on which I have set BIND to act as a Caching or Forwarding DNS server.
Note : I have done configuration for BIND server from this website:
  [https://www.digitalocean.com/community/tutorials/how-to-configure-bind-as-a-caching-or-forwarding-dns-server-on-ubuntu-14-04](https://www.digitalocean.com/community/tutorials/how-to-configure-bind-as-a-caching-or-forwarding-dns-server-on-ubuntu-14-04)


[/TD]
[/TR]
[/TABLE]

---

