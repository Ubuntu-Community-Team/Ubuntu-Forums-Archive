---
title: "Two wired connections; eth0, static IP, port 80; eth1, IP via DHCP, ports 22 and 3690"
date: 2015-01-23
forum: Networking &amp; Wireless
---

### Post by phillip15 on 2015-01-23
Dear all, 

We run a server with two independent network interface controllers. 

That means that Ubuntu establishes two wired connections. 

We would like to run eth0 with a static IP. We have got all the required information like IP, Netmask, and Gateway from the Admin. **(Problem 1)** From the outside, only port 80/tcp should be open on eth0. 

We would like to run eth1 such that it receives an IP from the local DHCP server (that works fine) and **(Problem 2)** that only the ports 22/tcp (for ssh) and 3690/tcp (for svn) are open from the outside.

All other ports should be closed on both connections. 

**(Problem 3)** Outbound traffic should go through eth1 by default.

How can we solve problems 1 and 2? Is this something with IP Tables or Firewall?
How can we solve problem 3? Does this have something to do with "Use this connection only for resources on its network" in "Editing IPv4 routes"?

Thank you very much in advance!
Phil

---

### Post by SeijiSensei on 2015-01-23
Something like this:
```

/sbin/iptables -A INPUT -i lo -j ACCEPT
/sbin/iptables -A INPUT -m state --state RELATED,ESTABLISHED -j ACCEPT 
/sbin/iptables -A INPUT -i eth0 -p tcp --dport 80 -j ACCEPT
/sbin/iptables -A INPUT -i eth1 -p tcp --dport 22 -j ACCEPT
/sbin/iptables -A INPUT -i eth1 -p tcp --dport 3690 -j ACCEPT
/sbin/iptables -A INPUT -j REJECT

```
The first line accepts all traffic on the"localhost" interface.  The second tells the firewall to allow packets it receives in response to an outbound request (e.g., a remote web page).  The remainder implement the restrictions you described.

Sending outbound traffic via eth1 requires making the upstream router on that network the default gateway.

---

### Post by phillip15 on 2015-01-25
Thank you very much! It works! When I reboot the machine, I now run the following script which does the job: 

route add default gw *gateway-IP*
iptables -A INPUT -i lo -j ACCEPT
iptables -A INPUT -m conntrack --ctstate ESTABLISHED,RELATED -j ACCEPT
iptables -A INPUT -i eth0 -p tcp --dport 80 -j ACCEPT
iptables -A INPUT -i eth1 -p tcp --dport 22 -j ACCEPT
iptables -A INPUT -i eth1 -p tcp --dport 3690 -j ACCEPT
iptables -A INPUT -j DROP
iptables -I INPUT 5 -m limit --limit 5/min -j LOG --log-prefix "iptables denied: " --log-level 7

---

