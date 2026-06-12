---
title: "Dealing with IP conflict"
date: 2013-11-17
forum: Networking &amp; Wireless
---

### Post by Jepic Phail on 2013-11-17
So my local library uses static ip addresses for their network; Every  table is assigned an IP address and you are supposed to change your IP  address to the assigned one when you sit down. Of course, everything  is ***_NOT_*** fine because there are alway few idiots who do not change their IP addresses and cause network conflicts. And to make things worse the network administrator's solution to this problem is basically 'try some other IP and  see if that works'. :roll:  So, I want to know if there a way to deal with this current situation? Ideally I would  like to kick off the person using the wrong IP address, but this  doesn't seem possible to me. Are there other 'solutions' where I can cause  enough interruption so that we both lose connection? Of course my intention is pure! All I want to do is to sliver line the other guy to the righteous path! Anyway, I am open to suggestion  as long as it doesn't involve illegal methods like DDoS. :razz:

---

### Post by Iowan on 2013-11-17
Just my opinion-
The library's IP management seems crude at best - like the administrator doesn't know how to set up DHCP.
Unfortunately, creating deliberate interference - regardless of how pure the intention - is not the solution.

---

### Post by Jepic Phail on 2013-11-17
Even if I was deliberately nefarious I don't think I can do much... :cry: I think the best option here for me is start praying and hope the other guy spills his latte on his laptop or something. 

On a some what related question, does Windows handle IP conflicts (and networking in general) better than other OS? I am asking because it feels like the other machine is handling the connection loss better than my laptop. Every time the conflict occurs I have to manually restart my network manager to regain connectivity. And even than I lose the connection within few seconds...

---

### Post by SeijiSensei on 2013-11-17
It will depend on the order in which people connect with the same address.

There is something called the "[address resolution protocol]("http://en.wikipedia.org/wiki/Address_Resolution_Protocol")" or "ARP" which maps IP addresses to the "MAC" addresses of ethernet adapters.  ARP really controls where traffic is sent since IP addresses are layered on top of the underlying hardware network based on Ethernet addresses.  If you run the command "arp -a" you'll see a list of visible machines with entries like this:
```

fluffy.example.com (192.168.100.1) at XX:c7:45:6d:5d:c1 [ether] on wlan0

```
If someone comes along and also starts using 192.168.100.1, then the arp table on machines that have already connected will probably continue to use the old address mapping.  In particular the router will continue to send traffic to the original hardware address.  At some point the conflict will become visible, and all bets are off as to where the traffic will be sent.

If the network you are connected to does not maintain a "reverse-DNS" table for machines in the local network subnet, then you'll see entries that start with "?" rather than a hostname like fluffy.example.com.

As Iowan says, this is a pretty dumb method of address allocation, though it may be that the library wants to restrict the number of simultaneous connected clients.  DHCP would solve that problem as well by restricting the range of allocated addresses.  There are possible ways around this problem, but we're not allowed to talk about them here as they would violate the "no-circumvention" [forum rule]("http://ubuntuforums.org/misc.php?do=showrules").

---

