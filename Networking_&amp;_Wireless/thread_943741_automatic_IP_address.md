---
title: "automatic IP address"
date: 2008-10-10
forum: Networking &amp; Wireless
---

### Post by dragos_iliescu_2005 on 2008-10-10
When I use an automatic network configuration under ubuntu, dhcp returns somethink like 89.136....but under windows returns something like 83.103...
Only the last one really work. I could not understand why dhcp returns two different addresses from the some isp. Is there anyone that could offer me some informations on that?
Things are getting more interesting when I see that under Windows, there are blocked connections attempts by firewall on address 89.136...even that the current IP is 83.103...

---

### Post by yogensha on 2008-10-10
It's entirely feasible that you get different IPs under Linux and Windows due to the way that DHCP works.  The fact that the networks vary so much is an artifact of large scale cable deployments and is not a concern by itself.

Blocked connections on your windows firewall are not at all uncommon, from any source address.  There may be more connections TO your other address if your ISP's aggregation router still has an ARP entry for your other IP address.  The router may not know that you've changed IPs and will continue to send packets to you until it's ARP entry expires.

---

### Post by dragos_iliescu_2005 on 2008-10-11
Thanks for your reply yogensha. How ever, my problem is that the address that I get under Ubuntu is not working, I mean the renewal of IP it seems not working well.

---

