---
title: "networking exercise"
date: 2007-09-08
forum: Networking &amp; Wireless
---

### Post by xchip on 2007-09-08
I want to do the following, I want to have my laptop connected to:
1) a wireless connection using the wireless interface (eth0) that gives me internet
2) to a silly router using a wire (eth1) I just bought (not connected to the inet) 

 The wireless (eth0) connection works perfectly, here is the config:
 ip: 172.17.159.228
 gateway 172.17.1.1
 DNS server is 192.168.1.1    (very important to remember this)

 Then I plug the laptop to the silly router, and oh! the router ip address is 192.168.1.1!! the same as the DNS for eth0!!!

So all the DNS queries instead of going thought the wireless(eth0) device go to the silly router that doesn't know how to relsolve (note that ip addresses work fine, its just the name resolving what I lose)

 Questions:
 1) Should I change my routers ip address to something different than 192.168.1.1
 2) Whomever configured the wireless access point, did he a good job at setting the 192.168.1.1 as the DNS server?

 Thanks!
 XChip

 P.D: I have an inspiron 6000 laptop with ubuntu feisty running great.

---

### Post by spd106 on 2007-09-08
This is could be rather tricky.

The IP address you have been assigned is in the 172.16.0.0/12 private address range. Which is ok, though it indicates a large network. The DNS servers IP address (192.168.1.1) is also in a private address range, but since it's in a different network to your laptop, the dns queries must be being routed by your gateway. This does strike me as a little odd, it's probably due to unplanned network changes. 
The problem is that as both of those private address ranges are being used, if you create a local network with the same address range then you won't be able to access the ones that were there first.
You could try moving your router to 192.168.x.1, where 1 < x < 256. First you might want to try pinging those addresses, to see whether they are in use. Ideally you should seek advice from the network administrator.

If you are going to use DHCP on the router too, you'll have to turn off gateway and DNS helper assignment, so that you keep the default gateway and DNS that you already have. Otherwise your router will overwrite your current settings or add duplicate ones. It might be best to turn roaming mode off and set a static configuration for your wired connection.

---

### Post by xchip on 2007-09-09
Ok, cool now I understand! Thanks! 

 BTW this is happening in a hotel chain called ExtendedStay Hotels

---

