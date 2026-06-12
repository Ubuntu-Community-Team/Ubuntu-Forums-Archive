---
title: "2 computers same IP?"
date: 2007-05-26
forum: Networking &amp; Wireless
---

### Post by thelocust on 2007-05-26
I am trying to transfer files between two computers I have set up on a Linksys workgorup switch. The problem is they both have the same IP address assigned by the dhcp. When I try to change it in manual and hit apply button it changes back to the old IP and stays in manual. I know absolutely nothing about networking so could somebody tell me what I'm doing wrong. Thanks.

---

### Post by thelocust on 2007-05-26
Do I need a router?

---

### Post by Pollywoggy on 2007-05-26
> **thelocust said:**
> Do I need a router?

You don't need a router unless you want to connect the network to another network or the Internet.
Where is dhcpd running?  Do you have a dhcp client running on the other machines?

---

### Post by ruy_lopez on 2007-05-26
What else is on your network, what else besides the two computers, is the switch connected to?

---

### Post by thelocust on 2007-05-26
There is 1 switch connected to 2 computers and 1 DSL box (the one SBC gave me) and that's it. I don't know anything about networking that goes for dhcp. I only said the IP is dhcp assigned because thats what it says in my networks settings. I assume that the DSL box is the one spitting out the IP address. Is there a howto for configuring the dchp?

---

### Post by ruy_lopez on 2007-05-26
This is what I was afraid of, your switch is just duplicating the internet connection. To have a network you'd need either the DSL modem or the switch to dish out private IP addresses. At the moment you don't have any private IP addresses. Looks like you need a router. Sorry to say.

---

### Post by thelocust on 2007-05-27
Yea thanks for all the help I'll go out and get a router tomorrow.

---

