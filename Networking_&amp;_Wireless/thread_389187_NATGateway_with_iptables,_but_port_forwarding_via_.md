---
title: "NAT/Gateway with iptables, but port forwarding via browser?"
date: 2007-03-20
forum: Networking &amp; Wireless
---

### Post by SlackR on 2007-03-20
Hi, im fairly new to linux (6-12 months) and long time windows admin etc.

ive managed to setup my linux box to take a wifi connection and then reshare it via ethernet and another wifi card.

nat is also working fine, but is there anyway i can allow port forwarding via a web browser?

something like smoothwall springs to mind, but i want to do this under ubuntu..


Thanks in advance.

---

### Post by jaheds on 2007-04-05
You can use Webmin to do that.  In my version of Webmin, it's under "Networking -> Linux Firewall."  Beside the "Showing IPtable:" button, choose "Network address translation (nat)", then click that button.  In the PREROUTING table, for example, you can add a new rule to forward certain ports.

---

