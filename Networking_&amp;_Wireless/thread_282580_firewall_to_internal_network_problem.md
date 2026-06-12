---
title: "firewall to internal network problem"
date: 2006-10-22
forum: Networking &amp; Wireless
---

### Post by mlalich on 2006-10-22
I have a home network with a Linksys router as my external gateway router connected to my Ubuntu box running iptables, which connects to another Linksys router as my internal router. My network scheme is as follows:

NETWORKS
EXTrouter to Firewall: 10.1.1.0/30
Firewall to INTrouter: 192.168.1.0/24

INTERFACES and IPs
EXTrouter LAN IP: 10.1.1.1/30
Firewall EXT IP: 10.1.1.2/30
Firewall INT IP: 192.168.1.1/24
INTrouter EXT IP: 192.168.1.2/24
INTrouter LAN IP: 192.168.2.1/24

My computers sit on the 192.168.2.0 network. My INTrouter is set to be a router not a gateway. I have iptables setup as per the tutorial on [http://www.section6.net/wiki/index.php/Setting_up_a_Firewall_NAT_using_IPTables](http://www.section6.net/wiki/index.php/Setting_up_a_Firewall_NAT_using_IPTables).

From the firewall I can get out to the internet just fine, but can't ping to my INTrouter. From any computer on the internal LAN I can ping up to my INTrouter's external interface, 192.168.1.2, but not across to the firewall. I'm assuming by enableing the following command net.ipv4.ip_forward = 1 for iptables, it should  enable me to traverse both networks, but then again I may be wrong. I have attached my ruleset for iptables.

So any ideas on how to ping to my internal LAN from the frewall or to the internet from my internal LAN????

Thanks in advance!

---

