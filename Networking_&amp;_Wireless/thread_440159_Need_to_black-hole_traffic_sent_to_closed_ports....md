---
title: "Need to black-hole traffic sent to closed ports..."
date: 2007-05-11
forum: Networking &amp; Wireless
---

### Post by NoIDusMaximus on 2007-05-11
I know in FreeBSD one could black hole traffic to closed ports using net.inet.tcp.blackhole (the parameter to tune using sysctl).

Is there any way in Ubuntu to stop the sending of RST packets and ICMP packets in response to packets hitting the box on a closed port?

Thanks.

---

### Post by heimo on 2007-05-11
Configure net filter and use target drop.

---

### Post by docsmooth on 2007-05-11
personal firewall with iptables

first set up your firewall rules with iptables, then save it, and set it to re-load when the network starts.

1) Iptables rules such as:
iptables -P INPUT DROP  (this sets the system to drop (not reject) all packets recieved
iptables -A INPUT -i lo -j ACCEPT  (accept all traffic on the loopback adapter)
iptables -A INPUT -m state --state RELATED,ESTABLISHED -j ACCEPT (accept all traffic that we already have established, or know about (related catches ftp and SMB traffic well))
iptables -A INPUT -m state --state NEW -p tcp --m tcp --dport 22 -j ACCEPT (accept SSH traffic - other rules follow like this)

2) iptables-save >/etc/network/iptables.up.rules

3) edit /etc/network/interfaces to include "pre-up iptables-restore </etc/network/iptables.up.rules" in your interface definitions.

You can also include -j "log" to log traffic and continue as your final rule, if you want to log all dropped packets (I do sometimes for troubleshooting).  The first rule is actually the "policy" on the input chain, so that if no rule hits (the -A lines are the rules), the policy still drops.  This allows you to flush all rules to lock yourself off from the world.

Doc SmooTH

---

