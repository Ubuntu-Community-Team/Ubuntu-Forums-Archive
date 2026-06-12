---
title: "How to set static IP address via command line?"
date: 2007-09-23
forum: Networking &amp; Wireless
---

### Post by dhanar_10 on 2007-09-23
Hi,

Currently, i'm trying to connect my computer to another via ad-hoc wireless connection.  So far i have sucessfully made the ad-hoc wireless. But the computers still unable to ping each other.  I suspect this is an IP address problem.  So, how to set static IP address via command line? I want to make a shell script for it.

Thanks.

---

### Post by JinxAu on 2007-09-23
Gday dhanar,

ifconfig is the tool that you use to set and view IP address settings.

ifconfig -a # shows all interfaces

ifconfig # shows all ACTIVE interfaces

Setting static address:
ifconfig <interfaces> <ipaddress> netmask <subnet mask>
eg. ifconfig eth0 192.168.0.2 netmask 255.255.255.0

man ifconfig # brings up the manual for ifconfig (can check syntax from here)

Hope that helps.

If you want the changes to be persisent, then check out /etc/network/interfaces (for Ubuntu and Debian based Linux distributions).

man interfaces # gives you syntax on the Interfaces config file.

Cya round
Jinx

---

