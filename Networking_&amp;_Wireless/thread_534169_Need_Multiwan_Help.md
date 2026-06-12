---
title: "Need Multiwan Help"
date: 2007-08-24
forum: Networking &amp; Wireless
---

### Post by saadakhtar on 2007-08-24
i have three ADS L lines (6 Mbps down and 512 Kb up each). i need to be able to load balance these three lines to increase bandwidth to my WIFI network at one of our project apartment complexes.
i have read some stuff about "ifenslave", can anyone please walk me through the setup process. my network setup is as follows.

3 X ADS L lines 6m down 512kb up
Ubuntu box load balancing above three connections
Total of 4 Ethernet Interfaces 3 for wan and 1 for lan.
network card for the lan side plugged into a access point.

---

### Post by netztier on 2007-08-25
> **saadakhtar said:**
> 
i have read some stuff about "ifenslave", can anyone please walk me through the setup process. my network setup is as follows.

Forget ifenslave, that's for **bonding** (mostly Ethernet) interfaces and requires that there's only one  device at each end of the link-bundle, e.g. a server and an Ethernet switch, or a server-to-server connection. Most often, bundled links (sometimes called Ethernet trunks or EtherChannel) ar used between switches to form a high-capacity backbone.

What you are asking for is way more advanced, especially if it is about connecting to the Internet, with dynamic allocation of public IP addresses (via PPP or DHCP) etc. Might be a bit easier if your ISP offers static addressing and/or Multilink PPP.

You will have to read about **Linux Advanced Routing and Traffic Control** ([http://lartc.org/](http://lartc.org/)). Basically, you'll need to se tup each DSL-based Internet access individually, then take very special care about how this Ubuntu-Router's routing table is filled with content. Furthermore, you need to make sure that the Ubuntu router is "session aware" and implements some "interface stickyess", so that a certain connection is always using the same link (an e-banking TCP session does not actually like it's IP source address to change... ). In short: this is *not* easy stuff!

And one more thing: if your ISP does not provide multilink-PPP so you can establish a logical single link to your ISP, you're not going to see enhanced throughput for any single connection (e.g. a download). It's the distribution of connections over the links that is going to give increased *total* bandwith, but not for a *single* session/connection


best regards

Marc

---

### Post by saadakhtar on 2007-08-25
thanks for the help. i am definitely going to check out the referred link.

---

