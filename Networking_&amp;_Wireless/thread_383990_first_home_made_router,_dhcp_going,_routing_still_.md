---
title: "first home made router, dhcp going, routing still a mystery"
date: 2007-03-13
forum: Networking &amp; Wireless
---

### Post by teryret on 2007-03-13
So I'm building my first router out of an old 2U server I found.  So far I've got it giving out good IP addresses, but I do'nt have it bridging any traffic from eth0 (internal) to eth1(external).  I'm also not entirely clear on the firewalling process, but I've found a few good guides, so once I get traffic flowing I'm sure I won't have trouble getting it locked down.  Google only leads to 7+ year old articles which leads me to believe that it has since become so simple an operation that nobody bothers writing guides anymore...

So the question is, what do I need to do to get traffic from eth0 routing to eth1 (which is connected to the isp)?

---

### Post by Mr. C. on 2007-03-13
Hi teryret,

What you called bridging, is really routing.

To route in Linux, you need to enable IP Forwarding.  This can be accomplished via:

placing a 1 value into:

/proc/sys/net/ipv4/ip_forward

echo 1 > /proc/sys/net/ipv4/ip_forward

This will enable fowarding.  Configure your route table.

MrC

---

### Post by teryret on 2007-03-13
I see, I have done that (actually I had tried that before per a guide, but I have done it again), but I still can't ping across it.  This could easily be a firewall/routing problem, I'll start playing with it, but it would be nice to see something work, just for my own sense of "Ha, I'm actually accomplishing something", how would I go about setting it to forward all traffic unconditionally?

---

### Post by Mr. C. on 2007-03-14
If both machines are on the same LAN, and you don't have any iptables, there would be no firewall interferring.

The ip_foward setting must be configured each boot.  See:  /etc/sysctl.conf for a convenient way to enable this each boot.

You need routes to go in both directions.  Here are some notes and a lab that you might find useful.  See week 7 "Routing":

[http://cis68c2.mikecappella.com/calendar.php](http://cis68c2.mikecappella.com/calendar.php)

MrC

---

### Post by teryret on 2007-03-14
Cool, thanks!

---

