---
title: "Accessing Ubuntu 14.04 computer HD by DVR connected to TV"
date: 2016-05-26
forum: Networking &amp; Wireless
---

### Post by Robbyx on 2016-05-26
My gufw firewall is set to deny unsolicited incoming data and allow all outgoing. 
With the gufw firewall active the dvr can not see the network HD, with it inactive it can be seen. 

I need help to write a rule giving access by my DVR to the HD of my computer. 

In order for my DVR to see the HD of the computer I am using rygel  to allow DNLA.

The author of rygel has kindly advised me as follows:

[I]You need port 1900/UDP (multicast group 239.255.255.250 in and out) for
the service discovery and you can set a port in Rygel's config which
will then need to accept connections for UDP and TCP. That should do
usually.
[/I]


I have changed rygel.conf to:

[I]# List of network interfaces to attach rygel to. You can also use network IP or
# even ESSID for wireless networks on Linux. Leave it blank for dynamic
# configuration.
interface=

# The port to run HTTP server on. 0 means dynamic.
port=1428[/I]

How do I write a ufw allow command to give effect to the author's advice?
I found the uwf manual here: [http://bit.ly/1sAHrVz](http://bit.ly/1sAHrVz)
 I am very unclear what needs to go in the command line especially as I do not understand how to incorporate the multicast address. I also have a number of devices on the network. I have the router/modem for ADSL, a tv, the DVR, a hub, the main computer. The access request will come from only the DVR.


Any help will be greatly appreciated.

Robin

---

### Post by Robbyx on 2016-05-26
I have made some progress:

the DVR address is 192.168.1.9
Gateway is 192.168.1.254

I have found a way to add a rule to gufw but I do not know what port to put in the from and to boxes. I am also unclear as the to ip address.

---

