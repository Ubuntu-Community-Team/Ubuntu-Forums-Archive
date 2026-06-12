---
title: "Xbox 360 ICS through Ubuntu - Moderate NAT?"
date: 2007-08-20
forum: Networking &amp; Wireless
---

### Post by th0r0n on 2007-08-20
Hi guys

I have a router connected to the internet (Router IP is 66.0.0.1) and I am connected to the router with my laptop via Wireless (ath0), Basically I wanted to use my Ethernet card (eth0) to connect to my xbox 360 and sign into LIVE

I've managed to do this by doing these commands:

ifconfig eth0 up
ifconfig eth0 192.168.1.1
cat /proc/sys/net/ipv4/ip_forward
iptables -t nat -A POSTROUTING -o ath0 -s 192.168.1.0/24 -j MASQUERADE

and I set my Xbox 360 IP to 192.168.1.2, the Subnet to 255.255.255.0 and the Gateway to 192.168.1.1, and my DNS Primary to 66.0.0.1

This works, however it reports in the Xbox LIVE test that my NAT is moderate? Is there a way to resolve this?

Thanks,

T

---

### Post by FRuMMaGe on 2007-08-27
Thanks!  What you just said has solved my xbox woes!

However, I have the same NAT problem now lol.

---

### Post by FRuMMaGe on 2007-09-03
Solved!

[http://ubuntuforums.org/showthread.php?t=538796]("http://ubuntuforums.org/showthread.php?t=538796")

---

