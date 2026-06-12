---
title: "Squid 3 transparent proxy configuration help."
date: 2015-09-18
forum: Networking &amp; Wireless
---

### Post by birdman3131 on 2015-09-18
Ok my boss has decided that we need to have internet filtering on our internet. From my looking it seems that squid is the way to go however I keep finding tons of pages that are less than descriptive on how to do this with squid 3. Most of the comments on the articles I read seem to say that they do not work due to changes made to squid.

My current network setup is Modem > Router > switch > 15-25 computers. Dhcp is ran separately off a 2k3 server among those computers.
I am trying to figure out if I want to place the squid proxy between the router and modem or router and switch? Thoughts? Issues? The router is a TL-R470T+ that has up to 4 wan ports so I could possibly do some sort of loop setup where all traffic except 
 non filtered pc's go through squid. (Ie router wan 1 goes to internet, Router wan2 to squid. Route everyone by default through wan2 to squid which then comes back and goes out wan1. This would allow me to set specific ip's to bypass the block and should prevent any issues with incoming RDP connections and such. Not sure if it is worth the hassle.)

The computer is a fresh install of 14.04.3 with two network cards.
Router Wan IP 94.185.237.4
Router Lan IP 192.168.2.254
Dhcp server IP 192.168.2.5 (Dunno if this matters.)
Any other info I need to give?

---

### Post by SeijiSensei on 2015-09-18
Put two Ethernet cards in the Linux box and place it between the router and the switch.  In the DHCP server's configuration have it pass the LAN-facing address on the Squid box as the workstations' default gateway.  The Squid box should have the upstream router as its default gateway.

Install Squid on the box using the defaults and add a rule like this to iptables:

```
/sbin/iptables -t nat -A PREROUTING -p tcp -j REDIRECT --to-port 3128 -s 192.168.2.0/24 --destination-port 80
```

This intercepts traffic for port 80 on remote machines and pushes it through the cache.

In older versions of squid.conf, you'll probably need to add "transparent" to the http_port line:
```
http_port 3128 transparent
```
or, in more recent versions like 3.5,
```
http_port 3128 accel vhost allow-direct
```

---

