---
title: "No ARP Replies for manual arp entries (Proxy ARP)"
date: 2013-10-24
forum: Networking &amp; Wireless
---

### Post by iwl on 2013-10-24
ubuntu12:~# uname -r
3.2.0-54-generic-pae

ubuntu12:~# arp -a
other (192.168.1.10) auf <from_interface> PERM PUB auf eth1
winhost (192.168.1.2) auf <from_interface> PERM PUB auf eth3

ubuntu12:~# cat /proc/sys/net/ipv4/conf/eth1/proxy_arp
1

winhost:~#ping 192.168.1.10
...

ubuntu12:~# tcpdump -i eth1 | grep ARP
tcpdump: verbose output suppressed, use -v or -vv for full protocol decode
listening on eth1, link-type EN10MB (Ethernet), capture size 65535 bytes
19:47:43.266878 ARP, Request who-has other tell winhost, length 28
19:47:44.108996 ARP, Request who-has other tell winhost, length 28
19:47:45.109781 ARP, Request who-has other tell winhost, length 28


whats wrong?

---

