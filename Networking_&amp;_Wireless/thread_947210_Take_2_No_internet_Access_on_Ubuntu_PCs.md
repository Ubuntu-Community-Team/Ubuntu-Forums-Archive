---
title: "Take 2: No internet Access on Ubuntu PCs"
date: 2008-10-14
forum: Networking &amp; Wireless
---

### Post by GuiGuy on 2008-10-14
I reported in **[COLOR="RoyalBlue"][[/COLOR]**this thread]("http://ubuntuforums.org/showthread.php?t=947172") that on my local home network the ubuntu PCs cannot access the internet but the WindowsXP PCs can. 

I thought the issue had resolved itself but it only lasted for a few minutes :(

Symptoms:
[LIST]
[*]Router diagnostics say everything is up and working
[*]All PCs on the network, and the network itself, had been troublefree for weeks
[*]AFAIK, nothing has been reconfigured or updated in the last 72 hours
[*]Several hours ago the four UBUNTU based PCs were no longer able to access the internet. Local network access is working
[*]The ISP says everything at their end is operational
[*]WindowsXP based PCs (I've now tried two), are able to access the internet over the same network.
[/LIST]

This is driving me crazy. Help. 

NB: Just a thought, but could there be trojans or viruses designed to induce the symptoms?

Thanks

---

### Post by rlzyoner on 2008-10-14
Are the ubuntu machines getting an IP address from the router or are they to be statically assigned ?

---

### Post by hyper_ch on 2008-10-14
> **GuiGuy said:**
> NB: Just a thought, but could there be trojans or viruses designed to induce the symptoms?

no

---

### Post by iponeverything on 2008-10-14
on the linux boxes post the output of:

route -n

and 

iptables -L -n

---

### Post by GuiGuy on 2008-10-14
> **rlzyoner said:**
> Are the ubuntu machines getting an IP address from the router or are they to be statically assigned ?

DHCP from the router. This checks out OK at the local network level.

---

### Post by GuiGuy on 2008-10-14
> **GuiGuy said:**
> I reported in **[COLOR="RoyalBlue"][[/COLOR]**this thread]("http://ubuntuforums.org/showthread.php?t=947172") that on my local home network the ubuntu PCs cannot access the internet but the WindowsXP PCs can. 

I thought the issue had resolved itself but it only lasted for a few minutes :(



OK, I swapped routers and it's come good on a restart of the network. It's been OK for 45 minutes, so maybe the other router? It's under warranty so I'll get it checked out. Doesn't explain the only Windows to the internet, though.

---

### Post by GuiGuy on 2008-10-14
> **iponeverything said:**
> on the linux boxes post the output of:

route -n

and 

iptables -L -n

Thanks. But as posted elsewhere I changed the router and everything seems fine now. If it does go down again I'll post the data. 

In the meantime I'll wait a day before posting this as solved though.

---

