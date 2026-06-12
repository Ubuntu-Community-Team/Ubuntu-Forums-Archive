---
title: "Router Problem"
date: 2006-08-20
forum: Networking &amp; Wireless
---

### Post by baylorbear on 2006-08-20
Hey guys --

I have apache installed and running on my box... and since I have a dynamic IP address, I'm using dynDNS.com to provide the solution.

Here's the problem -- when I'm connected to my router, nothing goes through the internet to my server (IP -or- url provided by dynDNS.com).  I have a Netgear MR814 and port forwarding on Port 80 to my server.

When I disconnect from the router and reboot, I can access my server from the internet using my IP address and the link provided by dynDNS.com.

What could be preventing my router from letting the traffic go thru?

Thanks in advance!!!!!!!!

---

### Post by stormblue on 2006-08-20
You are using a static IP?

Also, check all your rules.  Make sure there isn't some rule that is like 192.168.*.* drop * on port * above or below your rule.  Maybe you have one rule dropping packets while you're port forwarding

---

### Post by baylorbear on 2006-08-21
Still no solution... please help!
(I've been thru the steps at [www.PortForward.com](www.PortForward.com) and still no luck)

---

### Post by spd106 on 2006-08-22
Have you tried switching the port number to a random higher one? Your ISP could be blocking port 80. It is suggested at your linked website [http://www.portforward.com/help/pfprogression.htm](http://www.portforward.com/help/pfprogression.htm)

---

### Post by baylorbear on 2006-08-22
Yes, I tried port 8080 and 8888 at one point, but still no luck.

---

