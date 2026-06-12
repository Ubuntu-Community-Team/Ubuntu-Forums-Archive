---
title: "Outgoing connections use the newest virtual NIC's IP instead of the primary (eth0)"
date: 2007-05-21
forum: Networking &amp; Wireless
---

### Post by jordanryanmoore on 2007-05-21
I have one "real" NIC, and it's set up statically as eth0. I have two virtual NIC's that work perfectly fine for inbound/outbound connections. The problem is that my outbound connections are using whatever the newest virtual NIC's IP address is instead of using eth0's. Any suggestions?

---

### Post by lackhead on 2008-02-02
> **jordanryanmoore said:**
> I have one "real" NIC, and it's set up statically as eth0. I have two virtual NIC's that work perfectly fine for inbound/outbound connections. The problem is that my outbound connections are using whatever the newest virtual NIC's IP address is instead of using eth0's. Any suggestions?

I know this question is ancient, but I just recently ran into this myself, and in tracking down the answer I found this post.  In case anyone is still listening:

The issue is likely that you have gateway entries for both stanzas in your /etc/network/interfaces file. If you remove the gateway line from the virtual IP stanza, it won't automatically get a default entry in the routing table, and therefore all outgoing traffic will get routed from the other interface (which does have a gateway line in its stanza). 

What I think is happening is when the Ubuntu network initialization scripts run, it parses this file in order from top to bottom.  When it hits a gateway line, it does a "route add default..." which creates a default entry in the routing table.  Since the virtual IP stanza appears later in the file, it is getting added last, and therefore is the first default hit in the routing table.  Hence, all traffic originating on your box is going out via the virtual interface. 

Note that this will not interfere with traffic that is coming in via that virtual interface- the box will respond out the same interface incoming traffic came in on, so you shouldn't wind up with traffic coming in on one interface and going out the other.  

Hopefully this helps!



-c

---

