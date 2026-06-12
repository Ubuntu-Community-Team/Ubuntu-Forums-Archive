---
title: "IPTables - SMTP"
date: 2008-04-09
forum: Networking &amp; Wireless
---

### Post by sakkara on 2008-04-09
Hi,

I have two servers, both running Ubuntu server with IPTables.
Internet gateway: 10.2.0.130
Email server: 10.2.0.131

The email server has to send / receive smtp both from the local lan and the internet.

My local computer is:-
10.1.0.80 (255.255.255.0)

From the internet gateway, I can:-
telnet 10.2.0.131 25 and connect to postfix perfectly.

From my local computer, I can:-
telnet 10.2.0.131 25 and connect to postfix perfectly.

However from my local computer, I can't do the following:-
telnet 10.2.0.130 25.

I want to be able to connect to the internet gateway on port 25 and for it to automatically forward the requests to the email server.

The rules I have are:-
iptables -t nat -A PREROUTING -p tcp --dport 25 -j DNAT --to-destination 10.2.0.131:25
iptables -A FORWARD -p tcp --dport 25 -j ACCEPT

I can see (through the logdrop rule) that the firewall is not actually dropping the packet, but I suspect its just not passing it on correctly.

Any ideas?

---

### Post by superprash2003 on 2008-04-09
you could install firestarter and open ports and allow traffic graphically

---

