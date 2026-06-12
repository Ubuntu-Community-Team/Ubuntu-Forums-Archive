---
title: "proxy ipv4 for ipv6?"
date: 2010-04-09
forum: New to Ubuntu
---

### Post by deathintheafternoon on 2010-04-09
I have a lan (several vlans) with IPv6 addresses assigned from a tunnel broker (HE).  I just installed a Bind9 server and Squid proxy on a box  but haven't configured yet.  That box and Vlan have IPv4 addresses set as well as IPv6 addresses.  How can I configure to let the Squid proxy (which is going to proxy all my http) and BIND make sure that my LAN hosts can access http from domains that resolve to IPv4 only?

A part of my purpose in what I'm doing is to run the LAN as an IPv6 "native" for proof of concept of how to transition a larger network to IPv6.  So I can't/don't want to run both IPv4 addresses and IPv6 on my hosts.  

IPv6 works fine and I can browse IPv6 addresses with firefox on my hosts.  Just not IPv4.
Thanks.:confused:

---

### Post by wojox on 2010-04-11
Here's what I used to set up mine: [http://www.debian-administration.org/article/Running_IPv6_in_practice](http://www.debian-administration.org/article/Running_IPv6_in_practice)

---

