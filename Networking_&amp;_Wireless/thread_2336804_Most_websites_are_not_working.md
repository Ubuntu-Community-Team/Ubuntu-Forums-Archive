---
title: "Most websites are not working"
date: 2016-09-11
forum: Networking &amp; Wireless
---

### Post by cadx999 on 2016-09-11
Hello, i installed Lubuntu 16.04 and the only websites that are working are youtube.com and google.com. I can't even download updates or software from software center! What makes this problem especially strange is the fact that Ubuntu Studio 14.04 and Windows 10 are working perfectly with the same computer. And yes, i reinstalled it many times and used Lubuntu for years until now, so i'm familiar with the system. I use 100mbps cable plugged directly to PC.

---

### Post by TheFu on 2016-09-12
Can you ping the router by IP? If not, the problem is between the computer, cables, NIC and router. Try a different router port.

Can you ping 8.8.8.8? If so, it isn't a network issue, it is a DNS issue. Fix the DNS settings. I don't use lubuntu, so cannot say how to accomplish this for that distro. Sorry.
If not, the issue is with the ISP and router connection. Unlikely, since you say other systems are working through the same router and ISP.

A non-working DNS or DNS config can make the internet appear NOT to be working. It is just the phone-book lookup that isn't working (which is bad).  Often this happens because the DHCP server stopped providing the DNS settings properly or the Linux DHCP client isn't getting them correctly. You can manually set the DNS to any DNS server you trust to get around it.  Using a safe, trusted, DNS is absolutely critical since all of HTTPS and certificate security is based on those results.

Welcome to the forums.

---

