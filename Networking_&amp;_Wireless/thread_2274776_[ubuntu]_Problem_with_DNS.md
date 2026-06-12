---
title: "[ubuntu] Problem with DNS"
date: 2015-04-22
forum: Networking &amp; Wireless
---

### Post by martin155 on 2015-04-22
Hi, i have a one local server on which i'm trying to change IP address to hostname. 

example: 10.10.10.10 -> test.site.com

Ip address is working if i paste it to webbrowser.

How to change it ?

---

### Post by TheFu on 2015-04-22
edit the /etc/hosts file.
You realize that this will break the internet for "test.site.com" - most people use .lan or .local as the TLD for internal computers to avoid that issue.

Or you can run an internal DNS server.

---

### Post by chili555 on 2015-04-22
> **TheFu said:**
> edit the /etc/hosts file.

Something like this:```
127.0.0.1       localhost
127.0.1.1       <your_computers_name>

10.10.10.10     test.site.com


# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters

```

---

