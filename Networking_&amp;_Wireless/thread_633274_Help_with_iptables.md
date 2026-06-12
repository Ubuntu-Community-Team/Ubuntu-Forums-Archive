---
title: "Help with iptables"
date: 2007-12-06
forum: Networking &amp; Wireless
---

### Post by malbolgia on 2007-12-06
Hi 

I need to forward X11 conections on my pc to a vmware client runing windows xp. The server im reciving x11 conections from sends them on port 6000. What i need to do is forward conections on this port to my vmware client. The ip of the client is 192.168.95.128.

I tried with this rule, but it did not work:

sudo iptables -A FORWARD -i eth0 -p tcp --dport 6000 -d 192.168.95.128 -j ACCEPT

Im new with iptables so i really do not know what i am doing.

---

### Post by malbolgia on 2007-12-06
Please someone help me

---

### Post by samaricsm on 2008-02-08
I am not sure how to forward your X-windows.

I can tell you that the iptables -A FORWARD chain is for when your Linux box is acting as a router; i.e., the box is dual homed, ip forwarding has been turned on, and the machine receives IP traffic with a different IP address than itself.

This doesn't sound like your scenario.  

The iptables you will need will be -A OUTPUT - p tcp --dport ???, but first, you will have to get the X-windows to send to an external address.

---

