---
title: "[SOLVED] trouble enabling ipv4 forwarding"
date: 2008-02-26
forum: Networking &amp; Wireless
---

### Post by bdk6m2007 on 2008-02-26
In my sysctl.conf file I've uncommented the line to enable ipv4 (net.ipv4.conf.default.forwarding=1) forwarding and rebooted (several times) but forwarding is still not enabled.
 
When I examine /proc/sys/net/ipv4/ip_forward it is 0. If I go in as root and manually change it to 1 (with echo 1 > ip_forward) it works. I have iptables setup to use nat to forward a bunch of ports and after manually changing ip_forward to 1 my rules work fine but when it's 0 (as expected) it doesn't work.
 
What am I missing or doing wrong? How can I get the system to come up with ip_forward set to 1?

---

### Post by bdk6m2007 on 2008-02-26
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/procps/+bug/84537](https://bugs.launchpad.net/ubuntu/+source/procps/+bug/84537) [br].[/br] ---------------------------- [br].[/br] [br].[/br]				OK found a bug related to this.  It's essentiallya typo in the sysctl.conf file.  To enable ipv4 forwarding you must add:
 
net.ipv4.conf.all.forwarding=1
 
(so use all instead of default in the above line).

---

