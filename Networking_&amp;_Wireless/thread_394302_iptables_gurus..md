---
title: "iptables gurus."
date: 2007-03-26
forum: Networking &amp; Wireless
---

### Post by alimovz on 2007-03-26
Hey guys,

here is what I am trying to accomplish: 
I have an internal network (192.168.2.0/24) with a firewall/router(192.168.2.1) that is masquerading to the outside world. I also have a proxy server that is NOT the same box as the firewall/router and NOT anywhere on the internal network. The proxy server is located somewhere on the internet, let's with an IP address of 10.10.10.10. Port 8080
Question:
What iptables commands on the firewall/router(192.168.2.1) would I use to make host 192.168.2.20 on the internal network use that proxy without modifying his browser settings? 

I have seen examples of that, but all of them use this: iptables -t nat -A PREROUTING -i eth0 -p tcp --dport 80 -j REDIRECT --to-port 3128
which is only good if you run the proxy on the same machine as the firewall. Not my case. :-)

Any help appreciated. 

Thanks

---

