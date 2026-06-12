---
title: "Routing Problems with PPTPD"
date: 2008-05-23
forum: Networking &amp; Wireless
---

### Post by ccshack on 2008-05-23
Hi People,

I'm use ubuntu server to run a PPTPD Server in my office. I can establish the conection from the client to the server. The problem si:

Summarising the situation; clients can ping the IP address assigned to their tunnel, but cannot ping anything beyond the server (the target).

[IMG]http://pptpclient.sourceforge.net/images/routing_clientlan1.png[/IMG]

Example: The client can connect to the server, and ping the server, but can't access to mail server or web server beyond the server.

The ifconfig and routing at shell:
[[IMG]http://img299.imageshack.us/img299/6273/screencapture1hb1.jpg[/IMG]](http://imageshack.us)

My local network: 10.2.0.0/28
My VPN Network: 10.100.0.0

Thanks for the help,

---

### Post by superprash2003 on 2008-05-23
i think you need to forward traffic from ppp0 to eth1 cause your web and mail server is on eth0.. so you would need to modify your iptables

 sudo iptables -t nat -A POSTROUTING -s 10.2.0.0/28 -o ppp0 -j MASQUERADE
The above command assumes that your private address space is 10.2.0.0/28 and that your Internet-facing device is ppp0. The syntax is broken down as follows:
&#8226; -t nat -- the rule is to go into the nat table
&#8226; -A POSTROUTING -- the rule is to be appended (-A) to the POSTROUTING chain
&#8226; -s 10.2.0.0/28 -- the rule applies to traffic originating from the specified address
space
&#8226; -o ppp0 -- the rule applies to traffic scheduled to be routed through the specified network device
&#8226; -j MASQUERADE -- traffic matching this rule is to "jump" (-j) to the MASQUERADE
target to be manipulated as described above

The explanation i got from a page on the internet .. in this case it was to share the internet,you could use it to forward traffic too..

---

