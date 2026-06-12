---
title: "Easiest to Configure Firewall?"
date: 2007-06-12
forum: Networking &amp; Wireless
---

### Post by Princey on 2007-06-12
I know of many frontends to configure the built in firewall under Linux. I know as well it boils down to personal tastes, however, I do know some frontends are easier than others to configure. I know of Guarddog, cutter, firestarter, IPcop, shorewall, KMYFirewall among others. Which do you think is ONE of the MOST EASY to CONFIGURE firewall out there?

---

### Post by mcduck on 2007-06-12
Firestarter. You only need to install it, the default configuraton is fine for all home use. :)

---

### Post by skymera on 2007-06-12
i been told you dont really need a firewall.
as the cant access ur pc without the root pw.

but i used firestarter for a bit, twas good.

---

### Post by Princey on 2007-06-12
> **skymera said:**
> i been told you dont really need a firewall.
as the cant access ur pc without the root pw.

but i used firestarter for a bit, twas good.
Skymera, I know one is installed by default. That's why I used the word "frontend". That's what guarddog, firestarter and the rest of the crew are, frontend to control the firewall 'iptables'. 

Now, for a host of reasons, I do want to control what is allowed out and what is allowed in, including a VPN I want to set up (thinking of trying SSH and others). And, I may be wrong here, but even if they don't have the root password, who says your personal data loss isn't catastrophic?

---

### Post by penguin007 on 2007-06-30
For a single PC connected to the net, do this as root (sudo):

iptables --flush
iptables --flush -t nat
iptables --policy INPUT DROP
iptables --policy OUTPUT DROP
iptables --policy FORWARD DROP
iptables -A OUTPUT -j ACCEPT -o lo
iptables -A INPUT -j ACCEPT -i lo
iptables -A OUTPUT -m state --state NEW,RELATED,ESTABLISHED -j ACCEPT
iptables -A INPUT -m state --state RELATED,ESTABLISHED -j ACCEPT

(Or stick this into a script and run it)

This will drop all unsolicited incoming traffic and allow all outgoing.

---

