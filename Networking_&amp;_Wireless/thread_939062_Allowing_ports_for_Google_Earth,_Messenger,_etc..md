---
title: "Allowing ports for Google Earth, Messenger, etc."
date: 2008-10-05
forum: Networking &amp; Wireless
---

### Post by AKviking on 2008-10-05
Hello everyone.  I am still learning Ubuntu and excited about it.  Bought an 1100+ page book and am looking forward to getting through it and learning all I can.

However for the time being, I am working on my firewall/proxy and have it allowing port 80 just fine.  Yet I have a few items I'd like to use as well i.e Google Earth, MSN Messenger and Avast Antivirus.

My setup is a Ubuntu (hardy heron) machine working as my firewall between my DSL and my network.

I have SQUID proxy 2.6.
Linux Firewall.
Using Webmin for remote configuration.
Have SSH setup for remote CLI access.

I have tried allowing port 1863 (for MSN) in Linux Firewall, Squid Access Control and iptables, but cannot login to MSN.

I am apparently missing something.

Here's my iptables -L
[I][SIZE="2"]> Chain INPUT (policy ACCEPT)
target     prot opt source               destination
LOG        all  --  anywhere             anywhere            LOG level debug prefix `BANDWIDTH_IN:'

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination
ACCEPT     tcp  --  anywhere             anywhere            tcp spt:msnp dpt:msnp multiport ports msnp
LOG        all  --  anywhere             anywhere            LOG level debug prefix `BANDWIDTH_OUT:'
LOG        all  --  anywhere             anywhere            LOG level debug prefix `BANDWIDTH_IN:'

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
LOG        all  --  anywhere             anywhere            LOG level debug prefix `BANDWIDTH_OUT:'
[/SIZE][/I]

I hope I've provided adequate info.  If not, let me know.

Thanks, 
AKviking

---

