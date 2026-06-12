---
title: "NAT Proxy Whats required?"
date: 2007-01-23
forum: Networking &amp; Wireless
---

### Post by EeEk on 2007-01-23
A brief history....

In the school I work in we have 2 networks. 
NetworkA is a managed(debatable!) network I have no control over, connected to the Internet and supplies dhcp addresses. Internet is through a passworded proxy on port 8080.

NetworkB, I have complete control over, No internet.

Ive setup a PC in the middle running Ubuntu :) with Apache/php/mysql, 2 nics, NetworkA supplies an IP for nic eth0 of 10.24.4.43, a long lease so consider it static, which is connected and working PC can get to the Internet with some proxy fiddling but Ive read some post with a solution to the password bit. Any suggestions for this would also be handy. 

eth1, I can give any address..so well say 192.168.0.1, connected and working on NetworkB

Both networks can see the apache server on the ubuntu box - which was the original plan :)

What Im looking for now is suggestions on the easiest way to NAT everything on NetworkB - 192.168.0.x port 80 to NetworkA 10.24.4.43 ip port 8080.  I dont need any firewalls or blocking as this will all be taken care of upstream on NetworkA, I only want web traffic to pass through as thats all that can pass through the upstream proxy.

Ive looked at firestarter as an easy option but dont really need any of the filtering stuff, just NAT. though a means to turn it off and on may be handy in controlling the little monsters internet use :)

---

