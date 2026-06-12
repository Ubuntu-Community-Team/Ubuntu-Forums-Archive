---
title: "Stealth on the network?"
date: 2006-09-08
forum: Networking &amp; Wireless
---

### Post by rixxon on 2006-09-08
Hello, I wish to stealth my laptop on the network. I realize you can't be 100% invisible on an Ethernet without being disconnected. But I'd like to block ICMP Echo Request, TCP Synchronization Requests etcetera. I tested my laptop from my server and it did respond to ping and it seems to run a Postfix smtpd.

I want to block or disable everything that is not necessary for staying connected and using the network as a client.

---

### Post by breuerp on 2006-09-08
The easiest way to see what's going on with your ubuntu firewall is to install firestarter:  sudo apt-get install firestarter

That will let you see what rules are there, write new rules, see open connections and see denied connections.  There is a specific tab in firestarter to do ICMP filtering of various types.

---

