---
title: "Ubuntu router for multiple subnets"
date: 2008-03-12
forum: Networking &amp; Wireless
---

### Post by ubuntoexpert on 2008-03-12
Hello, I'm running into some issues with our old router and would like to try setting up a machine with Ubuntu and two NIC's to act as a route traffic between two of our subnets (to try and cut costs a little) We are running a static network and I do not need it to do DHCP. I just need traffic from the 10.20.160.0 subnet to access our main subnet, 10.20.156.0 (our WAN connection and servers our on this subnet) 

I read through the webmin article- [http://ubuntulinuxhowto.blogspot.com/2006/06/setup-your-computer-to-be-router.html](http://ubuntulinuxhowto.blogspot.com/2006/06/setup-your-computer-to-be-router.html)

Is there anything else I need to set up or configure since I am just using this as a LAN router and do not need DHCP or WAN access? Thanks!

---

### Post by SpaceTeddy on 2008-03-12
in general, no - you do not need to watch out for anything else. that tutorial should cover all of the basics. However, if you set your router up like it is suggested there, you will not be able to make connections from the main subnet into the connected one. As far as i could see this router was build using masquerading.

If that is a desired feature, then you will need to make some minor changes.

---

### Post by ubuntoexpert on 2008-03-13
> **SpaceTeddy said:**
> in general, no - you do not need to watch out for anything else. that tutorial should cover all of the basics. However, if you set your router up like it is suggested there, you will not be able to make connections from the main subnet into the connected one. As far as i could see this router was build using masquerading.

If that is a desired feature, then you will need to make some minor changes.
can u please explain more ?

---

### Post by SpaceTeddy on 2008-03-13
to explain more about this, you will need a good understanding about how masquerading (and essentially ip) works -  i'll try to explain it in a nutshell as best i can :)

first off, the setup is

subnet B (SB)<---> Router2 (R2) <---> Subnet A (SA) <---> Router1 (R1)<---> Internet

the basic idea of ip routing is, that you are always choosing the best route you know according to your current routing table. The routing table tells you where you can find any ip-address in the whole internet. so, lets say you have a client stuck in subnet A who want to access anything on the internet. It will consult it's routing table and send it to the best match - in this case it will send it to the router R1 as it does not know anybody from the internet - and R1 has been specified as it's default gateway (default gateway: router of last resort - anything that cannot be found in the local routing table will be forwarded to the default gateway). So essential, a Client from SA is hoping that the router R1 is able to find the ip on the internet.

**[SIZE="4"]the issue of SB[/SIZE]**
**What happens with Masquerading**
Now, when a Client in SB is trying to reach the internet, it will forward the paket it it's default gateway, in this case R2. R2 itself does not know anything about the Internet either, so it forwards again, this time to R1. But since maquerading is enabled, the pakets source address will be rewritten to the IP of R2, i.e. hiding from anyone who will now recieve the paket that this is a request from someone in SB. It will look like R2 sent the request itself. R2 will now keep acting normally, and forward the paket to R1 (it's default gateway), which will essentially end at the right ip. 
This time we also need to look at the pakets that come back from the internet. (a connection is always runs in both ways - that's why there is a sender ip as well as a receiver ip). When the reply comes in, R1 will look at it and see that R2 sent the request. Since R2 is in a subnet that it is connected to with one of it's network cards, it will NOT use the default gateway, but will send the paket out on the appropriate network card to the ip of R2. R2 will now receive the reply, figure out that this is acctually a rewritten paket, and forward it to the orginial host which sits somewhere in SB. 
Again, this scheme works for outbound connections from SB - it does not for inbound connections. Lets say there is a host in SA who wants to contact someone in SB. As it has no information as to where to find SB, it will forward the paket to it's default gateway R1. R1 itself has absolutly no idea where to find SB either, so it will also forward the paket to it's default gateway, essentially sending an internal paket out into the internet. of course it will not be replied there and eventually die. The problem here is that neither R1 nor the host in SA have any route telling them where to find SB. 

**What happens without Masquerading**
The sending part stays exactly the same as with masquerading, the only difference is that R2 is now only forwarding the paket, not touching the source address of paket. The paket will also reach it's destination and a reply will be generated. On the way back the reply will eventually reach R1. But since the original IP from the sender inside SB is now in the receiver field, and R1 has no idea where to find SB, it will drop the paket. i.e. - in this scenario anyone in SB can send paket out anywhere, but the replies do not reach the destination. Hence a connection can never be established. the Network connection will appear to be broken !

**Conclusion**
So, essentially, a connection back into SB is the problem, and so far can only be overcome by R2 masquerading the pakets, since anyone in SA can find R2 - but not SB, which is, with masquarading enabled, hidden behind R2.

**How to work without Masquerading on R2**
The problem, as we already figured out, is not the sending part, but the receiving - nobody knows how to find SB. But there is a simple solution to the problem - all you need to do is add a route for SB in R1 - and suddenly anybody in your network will find SB and connection into SB can be established from SA aswell. 
This works because of the default gatway. Any client in SA will still not be able to find SB - so it will forward to R1. But R1 now knows where to find SB - so instead of sending the paket out into the internet, it will send it to R2 - which is connected to SB and therefore can find the appropriate host.

I hope this makes some sense to you... if you want i can tell you how to set the routes aswell and how to get rid of the masquearding - but that is a lot of explaining (not much work, just much to understand) again - and i am not typing that without knowing it is needed :)

---

