---
title: "Can't ping out UB 8.04 but can connect to web"
date: 2008-08-23
forum: Networking &amp; Wireless
---

### Post by afewtips.com on 2008-08-23
Hi,
I am running Ubuntu 8.04 on a wireless laptop.
No problem connecting to the internet, can't ping out to any ip
or server.

I don't have any firewall on my machine.

I would think it's a network interface problem?? 

Thanks for any help.

---

### Post by speed32219 on 2008-08-23
check the route table in the wireless gateway.  Sometimes they come configured as a default with route permissions being denied for pings accross the lan or wan.

---

### Post by afewtips.com on 2008-08-23
I have the same problem using a wired connection as well. 
And I can't ping out from within Vista as well. 

I tried from another computer on the same network using the same router and the ping was fine.

How do I check the routing table?

And wouldn't the route be ok since I can connect to the internet just fine?

---

### Post by speed32219 on 2008-08-23
You need to login into your gateway device (i.e. 192.168.0.1) from the browser.  Just like when you set it up and there should be a router tab and within that you would see the default route table (Usually greyed out at the bottom of the screen)  Then you can add new routes with ping enabled from lan to wan if that is the problem (I think).  Just leave the wan to lan ping disabled.

OPS, didn't see the "I tried from another computer on the same network using the same router and the ping was fine." line.

Was this other computer on the same physical switch/router or was it on the same model somewhere else?

Also, sometimes your route tables can include a range of IP addresses that are allowed (I beleive) and maybe your devices that are not working fall into that disable range.

---

### Post by afewtips.com on 2008-08-23
Thanks very much for the reply. 
Yes - the other computer was on the same router. Connected via wire.
I will check on the range tomorrow morning. (In case you were worried :))
Thanks

---

### Post by afewtips.com on 2008-08-24
It was the wireless router firewall. Security setting was high and not letting wireless connections through. I don't know why it was not a problem on the computer connected to the router directly. On the wireless connection I couldn't SSH out or PING. 

To SSH I had to allow the port I use to SSH to another server via port forwarding. I can connect now. 

I can PING when I lower the security, so it's the same issue. The start of all this was not being able to SSH, so since that is solved - I'm good. 

Thanks for the help.

---

