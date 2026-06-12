---
title: "[UBUNTU 12.04] VPN server traffic forwarding problem"
date: 2014-05-17
forum: Networking &amp; Wireless
---

### Post by alex204 on 2014-05-17
Hello everyone,

Trying to setup a VPN server on VPS(vps.net), and using this manual - [https://help.ubuntu.com/community/PPTPServer](https://help.ubuntu.com/community/PPTPServer)
So, the problem is that client is able to connect to the VPN server, but, there is no internet connection. Unable to surf the web, e.t.c

As I understand, the problem lies in traffic forwarding through VPN server, right?

Could you please help me out.

Regards.

---

### Post by spynappels on 2014-05-17
You need to check if IPv4 forwarding is enabled, and that the routes are in place.
```
cat /proc/sys/net/ipv4/ip_forward
```
will tell you if forwarding is enabled (0=no, 1=yes)

For more specific help, you'll need to explain a little more what your networking setup and routing table looks like and what the firewall rules in place are.

---

