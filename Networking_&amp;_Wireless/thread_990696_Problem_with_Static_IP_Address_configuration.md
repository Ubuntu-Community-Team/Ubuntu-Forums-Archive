---
title: "Problem with Static IP Address configuration"
date: 2008-11-23
forum: Networking &amp; Wireless
---

### Post by zuidema on 2008-11-23
In the past I was able to configure static IP address in five easy steps.

1. IP Address     192.168.1.2

2. Netmask        255.255.255.0

3. Gateway        192.168.1.1

4. DNS Servers    69.88.70.146,68.88.79.147

5. Search Domains comcast.com,comcast.net 

When I try those steps and then close to save information, then open up to look at settings it sets my netmask to 24 and then if I don't have Connect Automatically checked it loses my information. What am I doing wrong.

Thats one computer on the other computer it set my Netmask to 24 and Gateway to 0.0.0.0

---

### Post by Iowan on 2008-11-24
/24 is the CIDR version of 255.255.255.0.  [Here]("http://ubuntuforums.org/showthread.php?t=974382") is a workaround for a network manager bug (which has reportedly been fixed).

---

