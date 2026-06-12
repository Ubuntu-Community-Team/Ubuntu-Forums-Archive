---
title: "Cannot Resolve .local Host Names"
date: 2008-04-28
forum: Networking &amp; Wireless
---

### Post by Aquaseafoam on 2008-04-28
I can verify that this issue is present in:
Xubuntu 8.04 BETA (i386)
Ubuntu 8.04 BETA (AMD64)
Xubuntu 8.04 (i386)
Ubuntu 8.04 (AMD64)

Here's the Setup:
We have two DNS servers (Windows Server 2003) also acting as our Domain Controllers. Both servers are correctly Identified by Ubuntu and Xubuntu as being the proper DNS servers. Both machines properly resolve any outside address, and receive correct IP addresses via DHCP. However, they are unable to resolve the host name of any machines on the local network. They are able to ping local machines via the IP address of each particular machine. They cannot however ping any machine with a .local hostname. (In this case, it would be DC1.winston.local)

My company is very seriously looking to replace our windows machines with Ubuntu, and this currently is a major obstacle to achieving that goal.

---

### Post by Aquaseafoam on 2008-04-29
I really need a response on this issue. Even "I don't know" would be helpful at this point.

---

### Post by jetsam on 2008-04-29
Have a look at post number nine of this thread, as it could explain the problem you have: 
[http://ubuntuforums.org/showthread.php?t=717071]("http://ubuntuforums.org/showthread.php?t=717071")

I should also say, "I don't know."  ;)  Your problem is beyond my experience level.  It's not good to double post, but you might get a better response in the server platforms sub-forum.  People there are more likely to understand the ins and outs of dns.

---

### Post by drclaw on 2008-11-01
Are you able to ping the host name but not the FQDN?

I had a similar problem where I was unable to resolve host.domain.local but simply the hostname resolved fine.

The solution I found was to enable **WINS-R** lookup.

In **dnsmgmt** expand the **Reverse Lookup Zones**.  In our case we only had 1 subnet.  Right-click and go to **Properties**.  Select the **WINS-R** tab.  Make sure the "**Use WINS-R lookup**" option is checked and then enter the domain name to append.

Just a side note - the **Forward Lookup Zones** also have a **WINS** tab.  Be sure to enable **WINS forward lookup** and specify the IP of your WINS server.

Hope that helps.  I racked my brain on this one for quite awhile before I finally saw this option.  Once I enabled it I was immediately able to resolve FQDNs on the domain.

---

