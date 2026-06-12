---
title: "vpn internet connection sharing"
date: 2006-10-09
forum: Networking &amp; Wireless
---

### Post by azarias on 2006-10-09
hi everyone!

i'm trying to spead my VPN internet (using ADSL modem) in my LAN here. I already read everything on the forum und googled aaa lot. However it's still not working.

I tried firestarter and iptables. Non of them did let my packets from a notebook here outside the LAN. I'm pretty desperate right now since i've doing this for hours and nothing seems to change.
 
So here's what i'm doing:

eth0 : 192.168.0.1
eth1 : this is the interface that dials the VPN server
ppp0 : gets the read IP 

When i put on Firestarter eth0 is my local and ppp0 my internet interface, it starts and it's blocking all of my packets. I can't even ping the outside from the server. Weird! - I also tried configuring it with "internet interface" - eth1, which should not be working normally - so it didn't.

Therefore i tried the following  with iptables:
iptables -A POSTROUTING -t nat -o ppp0 -j MASQUERADE
after this one i can ping the server from the lan but no some real IP on the net.

So this didn't do the trick either.

Note: 
/proc/sys/net/ipv4/ip_forward has "1" for a value

where can be the problem how can i debug somehow to search for a reason?
could anyone help?

---

