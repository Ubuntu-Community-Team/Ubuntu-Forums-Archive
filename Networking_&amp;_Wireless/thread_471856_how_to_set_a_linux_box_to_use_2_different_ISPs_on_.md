---
title: "how to set a linux box to use 2 different ISPs on the same time"
date: 2007-06-12
forum: Networking &amp; Wireless
---

### Post by keyrotate on 2007-06-12
I am using two different ISPs ... 
                                                               
      

Help.....need guide how to set linux box in ubuntu to use 2 different ISPs?

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=35145&d=1181670209[/IMG]

---

### Post by t4thfavor on 2007-06-12
I think the best you can do with that set up is network load balancing. There may be promise in "mlppp". But I think that is only for dial lines. As far as I know there is currently no method for combining the bandwidth of 2 pipes into one. You could however set up half the hosts on your network with different default gateways, and dns servers so that the traffic on each pipe is spread out.

Good luck.

---

### Post by keyrotate on 2007-06-13
Thank you for your reply...but i just want to make sure that this problem could be solved. i have googling for this problem and found that using advaced linux router which is iptables2 could solve it,,,,

but i don't know how to start in ubuntu

---

### Post by Soarer on 2007-06-13
Shoreline Firewall (aka Shorewall) will do this. It's described on[ this page]("http://www.shorewall.net/MultiISP.html#id2455502"). 

I have used it (with [Webmin]("http://www.webmin.com/") as the GUI) and it works within the constraints given. No doubt like all the Linux firewalls it configures iptables for you.

Another solution (which I have also used) is to purchase a Netgear ProSafe Dual WAN FVS124G which will do load balancing or fail-over for 2 ADSL lines. Mine cost about £55 new on eBay.

---

### Post by Sendervictorius on 2007-06-13
You can set up your linux box to provide internet load balancing and fail-over. It involves recompiling your kernel with options to support advanced routing and multiple connections to the internet.

Then you need to configure your routing rules to route the packets appropriately.

Then you need to set up your firewall rules to protect your internal network and to do network address translation appropriately.

It can be a bit involved. This link explains: [http://www.samag.com/documents/s=1824/sam0201h/0201h.htm](http://www.samag.com/documents/s=1824/sam0201h/0201h.htm)

---

