---
title: "Allow IPSec through IPTables"
date: 2015-02-26
forum: Networking &amp; Wireless
---

### Post by Gaven on 2015-02-26
I've got a Cisco ASA inside my network I'm trying to set up as a VPN concentrator for site-to-site IPsec tunnels.  I'm able to establish a link (which is flakey) but I cannot get any packets through.  I'm not seeing any log entries of dropped traffic but I'm still wondering if I missed something.  My edge router/firewall is simply an Ubuntu server and IPTables.  It manages traffic between the internet and what is essentially a DMZ.  My core network switch is between the LAN and DMZ.  The ASA I'm trying to set up has one interface in the DMZ (outside) and one in the LAN (inside).  The relevant rules I have in my IPTables configuration script are as follows:

iptables -t nat -A PREROUTING -d <Public IP> ! -s <DMZ IP> -j DNAT --to-destination <DMZ IP>
iptables -A wan_lan -d <DMZ IP> -j ACCEPT
iptables -t nat -A POSTROUTING -o eth2 -s <DMZ IP> -j SNAT --to-source <Public IP>
iptables -t nat -A PREROUTING -s <DMZ IP> -j ACCEPT
iptables -A lan_wan -s <DMZ IP> -j ACCEPT

The goal is that IPTables will not filter any traffic and simply NAT all traffic between the designated public IP and the ASA's DMZ IP.  Do those rules look proper for allowing all traffic in both directions?

---

