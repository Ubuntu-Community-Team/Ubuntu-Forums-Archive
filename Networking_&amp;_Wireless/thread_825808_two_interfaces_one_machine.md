---
title: "two interfaces one machine"
date: 2008-06-11
forum: Networking &amp; Wireless
---

### Post by tatta on 2008-06-11
Hi there,
I have a laptop with an Ethernet card(we can say eth0). I have also an HSDPA/UMTS phone that I use as modem(we can say ppp0).

So, I have now 2 IP address: IP_eth0 and IP_ppp0.
I wolud like that the traffic direct to eth0 go out from ppp0 crossing Internet, and viceversa.
I try to explain what I want to do using a pictures:

 M+
 y++++eth0 <--------------------------
 .+......................................|
 P+...................................INTERNET
 C+......................................|
 .++++ppp0-------------> HSDPA--------
 .+

(bidirectional flow)

I think that I should use IPTABLES or ROUTE, but I don't know how.
Have you suggestions?
Thanks.

---

### Post by nixscripter on 2008-06-11
What it appears you want to do is IP masquerading: having the eth0 computer's data go to the internet as if it were your computer, and then have the data returned.

There are some general instructions here:
[http://tldp.org/HOWTO/IP-Masquerade-HOWTO/](http://tldp.org/HOWTO/IP-Masquerade-HOWTO/)

---

