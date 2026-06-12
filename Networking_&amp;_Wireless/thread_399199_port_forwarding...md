---
title: "port forwarding.."
date: 2007-04-02
forum: Networking &amp; Wireless
---

### Post by kwiki on 2007-04-02
Hello linux gurus i have a problem regarding my network right now... my router is not functioning anymore (guest its broken)... i already resolve my first problem that is to share the internet connection to the network using a proxy server.. but my main problem is this.. how can i forward the request on my public IP to my local server running apache webserver.. 121.x.x.x :80 will forward to 10.0.6.1:80???

---

### Post by Bicavis on 2007-04-02
Assuming your proxy is a linux box:

iptables -t nat -A PREROUTING -i eth1 -p tcp --dport 80 -j DNAT --to 10.0.6.1

Not sure if apache uses udp or not but you can throw this in for safe measure

iptables -t nat -A PREROUTING -i eth1 -p udp --dport 80 -j DNAT --to 10.0.6.1


Make sure to change  eth1  to what ever your interface is from the internet.

---

### Post by kwiki on 2007-04-02
Thanks for the reply dude i already resolve my problem using guidedog... BTW nice iptables procedure..

---

