---
title: "Static IP Problems"
date: 2007-08-15
forum: Networking &amp; Wireless
---

### Post by antisho on 2007-08-15
So I have a Linksys router, and for certain reasons I would like my computer to have a static IP in the network. I go to System>Administration>Network, the DNS servers are there under the DNS tab, I change the connection to a static IP and put in the IP, subnet mask, and gateway. Then, if I attempt to go to the IP, I reach my own computer, but I cannot access the Internet at all. This is rather bad. The router doesn't support Static DHCP or anything, so I can't just stick with DHCP. What can I do?

---

### Post by noob12 on 2007-08-15
What you're saying should work fine if you've set it up right.

Make sure you set the gateway to point to the router's LAN IP and that your DNS server addresses are correct.  Usually the linksys routers are setup by default with the router's LAN address at 192.168.1.1 and they are setup to assign DHCP addresses starting at 192.168.1.100.   You need to pick a static address on the same subnet, with the last octet greater than 1 and less than 100, for example 192.168.1.5.


Let's see the output of these commands, and we should be able to identify the problems
```

ifconfig -a

cat /etc/network/interfaces

cat /etc/resolv.conf

```

---

### Post by antisho on 2007-08-15
Sorry, error in the network settings. Fixed now. Thanks! :)

---

