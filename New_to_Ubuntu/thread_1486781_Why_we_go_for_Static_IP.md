---
title: "Why we go for Static IP?"
date: 2010-05-18
forum: New to Ubuntu
---

### Post by karthick87 on 2010-05-18
I know the difference between Static IP and Dynamic IP?But for what purpose we go for Static IP...?

---

### Post by ScottinSoCal on 2010-05-18
> **getyourkarthick said:**
> I know the difference between Static IP and Dynamic IP?But for what purpose we go for Static IP...?

Some people don't have  DHCP server to assign an IP address, some people want to always know what the IP address is....

There are a lot of reasons to assign a static IP address. I did it with both my networked printers, otherwise I had to delete them and set them up new every time the IP address changed.

---

### Post by jrothwell97 on 2010-05-18
For reasons that should be obvious: if something has a static, fixed IP, you know that that machine will always live at 192.168.7.1 (for example.) If you have a dynamic IP, it might live there, or it might be at 192.168.7.2, or 192.168.8.1, or 192.168.0.101, etc. etc. etc.

This is particularly helpful when it comes to net-facing servers, since you don't have to constantly update the DNS records to point to your server.

---

### Post by karthick87 on 2010-06-19
Which one is secure static ip or dynamic..?

---

### Post by CharlesA on 2010-06-20
Both are the same.

Personally I use a DHCP server to assign static IPs based on MAC address (called static leases)

---

### Post by InfernalAngel on 2010-06-20
> **getyourkarthick said:**
> Which one is secure static ip or dynamic..?
It depended on your purpose :) and your need

if it's just a mall computer inside a home network and for the heck that you should care just enable DHCP :).

In a company it's a little bit more complicated ... pps usually do like this. For the share servers such as print, mail, cache, etc ... it's usually use static IP.

For employees the network administrator usually assign a range of dynamic IP for instance *.100-*.200 (* can be 192.168.0. or anything).
dhcp spare the network administrator of the task to con-fig each and every user IP address. just give them a dynamic IP point them all to a gateway/DNS and throw firewall, filters there ---> task done :)

---

### Post by CharlesA on 2010-06-20
Servers usually use static IP (or static leases) and regular machines use whatever DHCP assigns.

---

### Post by kerry_s on 2010-06-20
i use static ip cause i got the port forwarded.

---

### Post by Lucky. on 2010-06-20
Yeah, my client computers (workstations, normal PCs) all have dynamic IP addresses.  However my servers all have static IP addresses.  The clients always know where the servers are and can contact them easily.

---

