---
title: "Small Network Setup"
date: 2014-04-06
forum: Networking &amp; Wireless
---

### Post by sdharrison.9 on 2014-04-06
Hi,

I just moved to a new apartment and I am provided with one wired connection to the landlords router for internet. Needless to say I cannot change any settings here. Plugging this cable in to my computer provides internet no problem. I am trying to set up a network like this:



                                                                                              ...............................................====My Desktop
Landlords Router====My Router<
                                               ...............................................~~~~Laptop, Phone, Etc

~~~Wireless
===Wired

I frequently use a VNC to control my laptop from my desktop, and I need to retain this. I am trying to isolate my LAN from the landlord's as much as possible. My router runs OpenWRT.

[http://wiki.openwrt.org/doc/recipes/routedclient#using.masquerade](http://wiki.openwrt.org/doc/recipes/routedclient#using.masquerade)

I think the above link is exactly what I need except that my internet source is not wireless. The problem I am having is when I change my router's static address for LAN from 168.192.1.1 to 168.192.2.1, my computer will no longer recognize it. I have to change the subnet because the landlords router is 168.192.1.1.

My two questions are:

1. Is this the correct approach?
2. Does Ubuntu have an issue with changing subnets like that?

Thanks.

---

### Post by Iowan on 2014-04-06
I haven't (yet) tried OpenWRT, but I suspect it can serve as a DHCP server - including static leases. I presume you mean 192.168.X.X for networks...
Is your computer set up for static or DHCP address?

---

### Post by sdharrison.9 on 2014-04-06
Router is set up as DHCP client for WAN and with static address for LAN. Currently I am setting computers with static addresses as it is easier when using VNC. (My laptop has a broken screen...).

Update: I have the LAN and Wireless AP working. Trick was to set gateway on laptop to router's IP. 

All that I need to know know is how to connect wired LAN to internet using the router.

---

### Post by Iowan on 2014-04-06
Routing in the router might be the next task (or a DNS server).
Can you **ping** an Internet address (eg. 8.8.8.8) from inside the LAN?

---

### Post by sdharrison.9 on 2014-04-06
Yes, I can ping internet addresses

---

### Post by Iowan on 2014-04-06
Routing would seem to be working - can you **ping** an Internet site (like google.com)?

---

### Post by sdharrison.9 on 2014-04-06
ping [www.google.com](www.google.com) returns:

ping: unknown host [www.google.com](www.google.com)

---

### Post by tripp98 on 2014-04-06
From your routers web interface.  Check the WAN address.  Check the DNS servers that it is using.  Then from router see if you can ping 8.8.8.8 if you can then try to ping [www.google.com](www.google.com).  once your router can see outside world.  then check the settings that your router is passing to your pc's.  
make sure your pc can ping your router.  if it can not.  disconnect wire for a minute or 2.  until connection shows disconnected or renew your dhcp address on pc.  then try router ping again.  if you can ping router then ping the gateway of your router ( the gateway of your landlord ).  if you can ping that then ping 8.8.8.8.  if that works then ping google.com.  

pinging each step will narrow down where your problem is.

---

### Post by sdharrison.9 on 2014-04-06
Tried above steps. Ping works in all cases. Connection will work properly if dns server is set manually on each system in connection manager. How do I convince the router to handle setting the dns address for all clients?

---

### Post by ubuEsq on 2014-04-07
two ways:  the Dhcp in the router server has that option or the router has a "forward DNS" option. Set either one.... or both if the router does DNS caching as well

---

### Post by sdharrison.9 on 2014-04-07
Working now, thanks for all the help. I have to set the dns address manually for my static leases, but other clients work with no issues.

---

