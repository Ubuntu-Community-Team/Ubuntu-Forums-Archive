---
title: "Load Balancing &amp; fail over ideas!!!"
date: 2007-07-06
forum: Networking &amp; Wireless
---

### Post by mys_shekar on 2007-07-06
Hi,

   I have 2 ISP's and I want to make use of both of them (for effective Bandwidth usage) and also when one of them fails, I need my system (firewall) to automatically switch to other ISP without effecting the end user.

   On googling, I found some of the scripts:
1. shorewall -- supports loadbalancing but not failover..
2. Backroute -- supports failover but not loadbalancing..

  Before trying the above open sources, just wanted to know if there are any open source that performs both the operations i.e load balancing and failover.  Please give me your ideas if any of you have worked on similar lines..


Thanks!
santro

---

### Post by morgan_greywolf on 2007-07-06
I would just look at both scripts and then figure out how to make my own that combines ideas from both.

---

### Post by mys_shekar on 2007-07-06
Thanks Morgan.. appreciate your interest..

Here are the links for the above mentioned scripts...

[http://www.shorewall.net/](http://www.shorewall.net/)
[http://www.epr.ch/brb/linux/backroute.php](http://www.epr.ch/brb/linux/backroute.php)

Thanks,

---

