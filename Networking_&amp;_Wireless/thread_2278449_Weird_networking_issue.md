---
title: "Weird networking issue"
date: 2015-05-16
forum: Networking &amp; Wireless
---

### Post by aimilios on 2015-05-16
Hello everyone,

I'm having an issue with my network and in extense with my web server.

The setup of the computers running on the network is 2 Ubuntu, 25  Windows and couple MacBooks. The issue is when Ubuntu #1 browses the Web  server Ubuntu #2 can't establish a connection with the Web server and  vice versa when Ubuntu #2 browses the Web server Ubuntu #1 doesn't  connect, while all the other computers are working completely fine  without even a loss of packet.

The problem is with this specific web server, the web hosting company  and I checked the server's setup, firewalls etc, what could possibly be  the problem?

If you shed some light I'd be grateful!

---

### Post by chili555 on 2015-05-16
What is the hardware and driver in question for each? ```
sudo lshw -C network
```

---

### Post by SeijiSensei on 2015-05-16
Sounds a lot like they both have the same IP address.

---

### Post by aimilios on 2015-05-17
I won't know anything until tomorrow, but If I am right the the IPs assisgned by the switch are different, however the problem is just with 1 specific web server, every other website is browsable simultaneously by both terminals. So I focused on webserver's setup, tomorrow I'm going to run some checks on switches and terminals on my side.

I'll let you know as soon as I know.

---

