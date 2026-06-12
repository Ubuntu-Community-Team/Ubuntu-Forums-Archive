---
title: "Setting up this network (diagram included)"
date: 2008-07-04
forum: Networking &amp; Wireless
---

### Post by Georgie.Mathews on 2008-07-04
Hello all.

I am going to set up a network as indicated by the diagram attached.

The ubuntu server will be hosting IRC, a web server, and i want to install bind9 on it so users on the network can type [http://server.res.org](http://server.res.org) to access the web page and irc server.

Here is the problem :

1. Setting up DHCP on the ubuntu server - does that mean i have to turn the DHCP off on the wireless router? If so how will be able to make it one continuous lan? ir what settings do i input on the wireless router?

2. If i set up DHCP, i want my computer to have the domain gmathews.res.org so ppl can just type that to access my FTP. Does it mean that by DHCP my ip changes all the time? If so how can i fix this?

3. Is the diagram ok for one continuous network?

Pls help :confused:
:)

---

### Post by SpaceTeddy on 2008-07-04
ok - slowly. 

From what you wrote and drew, i suppose that the wireless router is your access point to the internet, right ? How is that configured ? is that a "normal" ISP dial-in connection (modem or broadband), is that a static-ip cable connection or do you own your own subnet with is routed directly to your wireless router ?
This is important, as it heavily affects how people on the internet "see" your network. For example, if you have broadband dial-in there are good chances that you are assigned a random ip every day. In this case, there is absolutely no need for an internal DNS as people on the internet will not be able to find it, and even if they could, you do not have authority over the domain - your Webhoster (who you registered the domain with) has that (as they have the authoritative DNS servers and the Domains registered to them).

Now, to the DHCP. There should really only be one DHCP server running on a local lan. So you either use the one from the router or the one from the server. As the one from the router already works, i'd say stick with that one. Please also note that having a dhcp running does NOT affect computer configured with static ips. This means, you can configure your server staticially within your network without your router knowing about it. The only gotcha is that you gotta make sure that the dhcp never, ever gives out the ip of the server to a client as a dhcp lease. 

Last question - how to make it one network. As far as i can see from your diagram, you have one network. The Access point is connected to the switch. There is a switch-switch connection. This means, they all have direct access to each other and will act as one network. So, a lease issued by the router will be valid for the wifi as well as the wires lan (no matter what switch). 
The same applies for the case of the dhcp server being moved to the ubuntu server. As long as you have direct cables running between the switches and the access-points the leases will be able to travel into the wifi. The only hindrance for dhcp-configurations in this case are routers or non-broadcast mediums. As long as all Hardware that distributes is capable of layer 2 broadcasts, your leases will travel the way. 
Btw: your router DOES NOT forward broadcasts from the internal network to the internet. That is a routed connection - not a broadcast connection !

hope this makes some sense to you :)

---

### Post by Georgie.Mathews on 2008-07-04
Hey there Space Teddy, thanks for ur reply.

We wont be having internet on the network, so that should clear out some problems.

Now, if my PC has the statis IP, Will the router (if the DHCP server is there ) know that is is taken?

---

### Post by kevdog on 2008-07-04
You would assign the dhcp range that the router issues addresses in, separate from the range of your static IPs.  For example, start your dhcp address at 192.168.1.100 --> 192.168.1.200.  And allow static ip from 192.168.1.2 --> 192.168.1.99.  I think you get the idea but the ranges may be modified for your purposes.

---

### Post by Georgie.Mathews on 2008-07-04
Should i set up the DHCP server on the ubuntu box or leave it on the wireless router side? What about the DNS (virtual domain) for my server so that my computer will have gmathews.res.org as its domain. Remember its a private network, with no access to the internet.

---

