---
title: "Ubuntu Network Analyzer"
date: 2008-03-22
forum: Networking &amp; Wireless
---

### Post by ubuntogenius on 2008-03-22
I need to create a network/packet analyzer for my company using Linux.  I like Debian so I chose Ubuntu to use as my distro.  My dilema is how I can implement the physical box in between the router and the switch WITHOUT having to change the router IP or any computers on the network's gateway.  Is there a way to create a passthrough box so I can essentually just "slap" it in there and start sniffing.  I've only created firewalls/proxys with IP addresses and two NIC's, but I can see anyway to implement something like that without having to change either the router or the settings on the existing computers.  I hope I explained this well.  Thanks.

---

### Post by relexed on 2008-06-09
My guess is installing a transparant proxy would solve your problem.

Kind regards,

ReLexEd

---

### Post by kawouter on 2008-06-10
You can build a snifbox. This is a small device in between the link that does nothing but listen. It can be used to snif full duplex links.
It's easy to make one from an old dual speed hub (no switch!)

See this article on my website on how to make it: 
    [http://www.woubar.nl/howto/snifbox/snifbox.html](http://www.woubar.nl/howto/snifbox/snifbox.html)

Now just connect your ubuntu pc/notebook to the hub and snif with for instance wireshark, etherape or tcpdump.

Wouter.

---

