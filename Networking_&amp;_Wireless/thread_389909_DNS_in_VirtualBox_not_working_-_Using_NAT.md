---
title: "DNS in VirtualBox not working - Using NAT"
date: 2007-03-21
forum: Networking &amp; Wireless
---

### Post by pjman on 2007-03-21
I posted this on VirtualBox's forums but things are really slow there. 

I'm running Ubuntu as a guest OS in VirtualBox (XP is my host). I'm using NAT for my network connection. Ubuntu gets an IP from the host and my DNS server is set to 10.0.2.3 automatically from DHCP managed by VirtualBox. I cannot resolve any hostnames making it impossible to run updates or browse the web. When I manually enter the DNS server on our LAN at work everything works fine. 

Shouldn't VirtualBox be taking care of DNS automatically? I've searched and I can't find anyone having the same issue. 

Ideas?

Thanks!

---

### Post by pjman on 2007-03-26
I think the problem is with the LAN at work. Everything works fine at home :-)

---

### Post by sentvid on 2008-04-25
> **pjman said:**
> I think the problem is with the LAN at work. Everything works fine at home :-)

If you have to go through a proxy server at work. configure http_proxy using gconf-editor
Path : /system/http_proxy

Important: Remember to use ipaddress instead of hostname for the proxy server.

Enjoy Ubuntu

---

