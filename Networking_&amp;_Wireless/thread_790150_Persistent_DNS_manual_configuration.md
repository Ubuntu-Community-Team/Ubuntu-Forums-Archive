---
title: "Persistent DNS manual configuration"
date: 2008-05-11
forum: Networking &amp; Wireless
---

### Post by badp on 2008-05-11
For some reason a router I am using has DNS problems and, e.g., gives Unknown Host for [www.google.com;](www.google.com;) loading [http://209.85.129.104/](http://209.85.129.104/), instead, succeeds.

Going to Network Settings, unlocking, removing 192.168.1.1 from the DNS list and adding (say) 4.2.2.2 resumes normal browsing, but eventually DHCP (?) resets DNS to 192.168.1.1 and I have to go through the above again.

Is there a persistent way to tell Ubuntu to always use a given DNS server?

EDIT: I'm using Ubuntu 8.04

---

### Post by nixscripter on 2008-05-11
Try manually adding the external DNS servers manually to your dhclient.conf file according to these instructions: [http://ubuntuforums.org/showthread.php?t=426073](http://ubuntuforums.org/showthread.php?t=426073)

Hope this helps.

---

### Post by .rdg on 2008-05-11
Some routers are also able to be set up with static DNS entries even though they use DHCP for their WAN interface. Give it a try first if it's available in your situation.

---

### Post by badp on 2008-05-11
> **.rdg said:**
> Some routers are also able to be set up with static DNS entries even though they use DHCP for their WAN interface. Give it a try first if it's available in your situation.

That router does, except for some reason it just decided to stop working :confused:

The problem's on that router, though, as others work without trouble.

As far as I'm concerned, anyway, dbott67's post did the trick.

Thanks!

---

