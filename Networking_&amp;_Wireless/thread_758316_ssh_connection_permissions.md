---
title: "ssh connection permissions"
date: 2008-04-17
forum: Networking &amp; Wireless
---

### Post by kikazaru on 2008-04-17
How can I debug this ssh problem?

1 laptop and 1 desktop connected through router with DHCP
Using ddclient to maintain a fixed name for the dynamic IP address
Added 22: 192.168 to /etc/hosts.allow
Added name for each computer to /etc/hosts.allow
Also added a computer at work with a fixed IP to /etc/hosts.allow
Set up router to forward port 22

Result:

1 Can ssh between laptop and desktop using local IP address 192.168.whatever
2 Can ssh from work to desktop computer
3 CANNOT ssh between laptop to desktop using global IP/fixed name
4 Adding 22: or even ALL:  to /etc/hosts.allow still doesn't allow the connection!?

I figure that 2 proves that the router is properly forwarding the port, and nothing else is interfering with the connection. I guess that 1 and 3 prove that the source IP for the ssh connection is causing the problem except that 4 seems to be inconsistent with this diagnosis. How can I set it up to allow connections from sources with a dynamic IP? Is there a log file that I can use to help debug this problem?

---

