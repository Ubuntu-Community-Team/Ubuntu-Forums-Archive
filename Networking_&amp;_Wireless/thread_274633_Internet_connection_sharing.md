---
title: "Internet connection sharing"
date: 2006-10-10
forum: Networking &amp; Wireless
---

### Post by flowdawg on 2006-10-10
Hi all,

for the last few days, I've been trying to set up an ubuntu box to act as a router for my network (dhcp and internet connection). I can get a connection to the internet with roaring penguin. All I had to do was start RP, then add the route default over ppp0. So on to sharing: I tried first with firestarter and dhcpd3. That didn't work. Then I tried with dnsmasq and IPmasq, that didn't work either. As a last try I copied a script for an IPtables firewal with port forwarding and masquerading. Didn't work either.
My question is: Am I missing something important? When I did the same thing with windoze, it required a DNS server also, but the IPtables and firestarter tutorials I found on the net never mentioned such a thing. Dnsmasq didn't work but does provide DNS, so I'm really stuck here.
Is there maybe a definite howto or tutorial, which I didn't find?

thx

---

