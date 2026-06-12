---
title: "Assistance needed for network layout"
date: 2008-09-02
forum: Networking &amp; Wireless
---

### Post by HunterA3 on 2008-09-02
I've recently purchased a Sylvania G-netbook which I'm thinking of reimaging with Ubuntu or reimage with the GOS disk that came with it. This ultra portable comes with a PXE enabled NIC. I thought it would give me an excuse for building a PXE server. I discovered in the process of looking up instructions however that I need to set the same server up with DHCP. THe problem is my wireless router is already set up as the DHCP server.  I can shut that off, but I'm uncertain if I'll have any issues with DHCP if my PXE server is not situated in front of my wireless router. I've included a drawing of my current network. Does it look like I'll have any issues with DHCP with the current layout?

[http://homedir-b.libsyn.com/podcasts/d463e73b2d8e91f87183cd28754786cc/48bd8ffb/notashortcut/images/Network-layout.jpg]("http://homedir-b.libsyn.com/podcasts/d463e73b2d8e91f87183cd28754786cc/48bd8ffb/notashortcut/images/Network-layout.jpg")

---

### Post by NadmanET on 2008-09-02
Wow, I like the drawing!  The answer to your question really depends on a couple of factors.  Really I need to know what that router is doing between the Wireless router and the switch.  It gets a little technical here but if it is truly routing and you have separate networks then yes it could possibly break something.  

I'm gonna go ahead and say that you are probably alright to shut off DHCP completely on your wireless router and start issuing addresses from your PXE server.  If it doesn't work you can always revert back and we can start troubleshooting.

Things to check:

Make sure that you are truly getting your current addresses from the wireless router and not another device (the other router or switch) along the way.

Make sure that other router isn't performing any NAT or PAT functions.

Make sure that other router isn't routing.  Everything should be in the same IP subnet.  


Another thought is rather than test network services such as PXE/DHCP on your live network, unplug that switch and you have yourself a private little testbed.

I messed with PXE a while back and my client DHCP requests were timing out.  Keep in mind that some switches (particularly enterprise class but also some small and medium sized) will block all traffic for a while when a link first becomes active to look for switching loops.  In my case it would block the traffic so long that it would time out the request and it would not work.  Just wanted to share the gotcha I came across.  Good luck!

---

### Post by HunterA3 on 2008-09-03
The secondary router is being used as a switch at the moment. It's an older wired Cable/DSL router that I patched, or bridged, to my wireless router. It was available when I needed to expand my network so I set it up as a switch. Since then, I've purchased actual switches for further expansion. I debated labeling it a switch to avoid confusion, but I decided against that since I wasn't sure if it retains any of the router functionality even though it's more like a switch in this case.

As far is my network goes, it's all in the 10.0.0.x range with the wireless router being the first IP of the range, the wired router (switch) getting the next at .2, and followed by all my other PCs afterwards. The PXE server is actually sitting at 10.0.0.8, with only my LAN printer sitting further out on the IP range at .50.
 
To my knowledge, to actual switch below the second router doesn't even have an IP--which I'm not sure is normal or not. It's almost as if it's acting as a hub, but I don't see traffic broadcasting to all ports like you would normally associate with a hub. So I'm assuming that my wireless router is the device issuing DHCP addresses at this point.

When I turned off DHCP from my wirelss router, the only immediate thing I noticed as twitterfox began complaining about not being connected, although I was still able to surf from website to website.  I didn't try to release my IP and get another. I may try that next. I just wasn't sure if I needed to move my PXE server to directly in front of or behind my wireless router in order for IP address to be properly assigned to the rest of the network.

---

### Post by NadmanET on 2008-09-03
It sounds like you will be fine.  As long DHCP requests can get to the DHCP server and that traffic can get back it should work.  Normally routers block DHCP traffic because you don't want a DHCP server in another network (or subnet) issuing addresses to hosts in your subnet.  (That is not a hard and fast rule.  If you have 30 different subnets you don't want to have 30 separate DHCP servers; you would set up the router to forward DHCP traffic to a single DHCP server.)  This is why I was asking exactly what that router was doing.  If a host that is hanging off the switch can receive DHCP addresses from the wireless router, having your DHCP server connected through that switch should work fine.

Why that broke twitterfox is beyond me.  I don't know much about that application.  Maybe someone who knows how twitter works could chime in and explain why that app would have any reliance on DHCP.

As for your switch, while uncommon, unmanaged switches do exist.  It does break up the collision domains but you won't have any higher features like the ability to create VLANs or prioritize traffic with QoS.  What is the make/model?  Maybe it is manageable but the management IP is in a different network.  If you can't find any documentation on it I would isolate the switch from the live network, connect a host, and perform a ping sweep of the following networks in this order:

192.168.0.0/16
172.16.0.0/12
10.0.0.0/8

The 10 network will take a while but if it has an IP address (assuming ICMP traffic is not blocked) it will find it.  Don't forget to give the host that is doing the scan a static address in the same IP range.

Let us know if you get it working!

---

### Post by aastaneh on 2008-09-22
What a coincidence.. I purchased a Sylvania G as well. I successfully imaged it with Xubuntu using PXE, and in the meantime wrote this software app to automate the process using Perl:

[http://github.com/aastaneh/easypxe/tree/master](http://github.com/aastaneh/easypxe/tree/master)

It's great for a one-machine-at-a-time setup.

-Amin

---

