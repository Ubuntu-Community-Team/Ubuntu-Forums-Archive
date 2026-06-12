---
title: "L2 bridge using Netplan and Zenarmor"
date: 2023-05-28
forum: Networking &amp; Wireless
---

### Post by johndid on 2023-05-28
Hi everyone,
I watched this video on youtube:

[https://www.youtube.com/watch?v=lLEfYIitXfA](https://www.youtube.com/watch?v=lLEfYIitXfA)

I think that I got the purpose of it overall. It is about putting Zenarmor between your main router and your LAN without running another firewall like, e.g., OPNsense in which Zenarmor can be installed as a package/plugin.
It is basically like setting your IPS router in bridge mode, allowing  your favorite router/firewall to fully manage the WAN and the LAN side of your network.

However, there is still something that it is not clear to me, mostly because I still don't have a good understanding of computer networking.
He set a bridge between a WAN interfacce and a LAN interface on his Ubuntu machine via the yml file. Another WAN, why? 
Was the Ubuntu machine already running as another gateway between the main router and the LAN, creating a double NAT this way?
Or was it just to NAME the two ports? I'd like to replicate the same scenario in one of my ubuntu machine running on VMware, and I will create two virtual interfaces, 
but I need to understand it deeper first.
Could you please help me figure it out?
Thanks

---

### Post by aljames2 on 2023-05-28
The bridge (br0) was set up in the yaml file, & the interfaces were placed on the bridge.  One interface was configured as WAN, because it connects upstream to the router, while the LAN interface connects to a switch downstream which other lan hosts can connect to.  The Zenarmor is the monitoring application providing firewalling capabilities.  I imagine you will need to be careful configuring the ZA firewall rules.  You’ll likely need the ZA forums for help with that.  A firewall that is not set up properly can leave gaping holes in your plan, so study up on how it works and get yours configured suitable to your needs.  

I am not familiar with ZA.  My router / firewall box runs pfSense, similar to Opnsense, rides on the edge where WAN is the internet, & below are multiple physical internal networks.

---

### Post by johndid on 2023-05-29
> **aljames2 said:**
> The bridge (br0) was set up in the yaml file, & the interfaces were placed on the bridge.  One interface was configured as WAN, because it connects upstream to the router, while the LAN interface connects to a switch downstream which other lan hosts can connect to.  The Zenarmor is the monitoring application providing firewalling capabilities.  I imagine you will need to be careful configuring the ZA firewall rules.  You’ll likely need the ZA forums for help with that.  A firewall that is not set up properly can leave gaping holes in your plan, so study up on how it works and get yours configured suitable to your needs.  

I am not familiar with ZA.  My router / firewall box runs pfSense, similar to Opnsense, rides on the edge where WAN is the internet, & below are multiple physical internal networks.


I once installed Zenarmor on OPNsense, and it's not a big deal to set it up for home, basic needs. But I am not really interested in it now actually.
I'd like to focus on the bridge thing in detail, and why he had to set it up that way, and what were the ubuntu initial conditions.

I want to replicate the same scenario in VMware workstation and give it a try for learning purpose.

So, would I set two network interfaces in VMware workstation? The first one would be the WAN port, I guess which 
is going to get an IP from my physical router in my LAN since I would set this network interface in bridge mode in VMWare. The second one would be the LAN port of an internal Network which I would  set in custom mode so that it would run on a different subnet.
Let's say the the WAN port would get 192.168.1.10 as its own WAN IP from my physical router , and the custom internal network would run on, say, 10.10.10.0/24 subnet and the LAN port would have 10.10.10.1 as an IP. 
If I am not missing something here, this means that  Ubuntu would already be running as a gateway for an internal network which would be already under NAT. (double NAT in this case since there is already a NAT set on the ISP router which has  access to internet.

The problem is that I'm not sure if it was the same initial scenario as that shown in the video.
So, would the purpose of it that of doing without the second gateway/NAT (originally created with the Ubuntu machine), running Zenarmor, and let the main physical router manage the entire home network on its LAN subnet?

I hope I got my point across.
Thank you

---

### Post by aljames2 on 2023-05-29
Using a bridge does not mean NAT is happening.  Bridges are commonly used to allow the forwarding of packets between VM‘s, or other hosts on the network.  Without a bridge, VM’s cannot be seen or accessed by other hosts on the network.  You can use a bridge to deploy a firewall solution as described in the video.

You could have a look here at more information on bridging multiple interfaces and common uses for doing so:  [https://ubuntu.com/server/docs/network-configuration](https://ubuntu.com/server/docs/network-configuration)

NAT is the job of your router.  If you place a router behind a router, with neither being in bridge mode, then you will have double NAT.  NAT can also be deployed & configured on a server using IPtables.  This is not what you are looking to do, but just saying that it is possible, some will use an Ubuntu server to be a router for a certain segment of their network, but most people have one router on the edge that handles NAT.

I am not a fan of using DHCP for anything other than Wi-Fi joining guests.  On my internal network, all hosts, including VM‘s, & bridges have a static IP address.

I am not familiar with VMware.  How mine works, I set up a bridge network on my hypervisor (KVM) host using a YAML file, and then when installing a new VM, I can select the (br0) interface in a drop-down.  This assigns that VM to the bridge.

Not sure any of this is helping or what you’re looking for, but I think it’s all I got.

---

### Post by johndid on 2023-05-29
hi aljames2,
 I really appreciate your effort to understand what my  problem is, and narrow it down to the core. But It's not about solving a  problem but more about figuring out just one or two steps that, as I  said above, are not completely clear to me. For learning purpose I once  already used a linux machine (a debian) as a router/firewall which was  behind another router at the time, and then I connected to it another  linux machine as a client running on  its internal LAN. I could  have plugged a switch to it as well.

Ok, bear with me one more time,   please. Let's forget about VMs that might have led us astray. I am going  to come up with a new example

Suppose that I have this physical  Ubuntu machine with two network interfaces. I don't want it to be  another router running on my LAN, since I already have a main router  which I am happy with.
However, I want to install zenarmor on it (as  that guy did in the youtube video) and let if filtering traffic of every device in my LAN.

Is the only way to achieve this is to bridge the two network interfaces (as the same guy did) and then, say, plug a switch into Ubuntu's LAN interface to which the other devices on my LAN are connected? Or can the switch be placed elsewhere (to the main router) and zenarmor would still do its job, that is, filtering the entire traffic in my LAN?

I hope that's clearer. Thanks a lot

---

### Post by aljames2 on 2023-05-29
A bridge is not confined to only be used with VMs.  Once set up, a bridge is considered a network device. You can think of it as a network switch, and in this case, with an upstream interface (call it WAN) pointing to your router (i.e. internet supply line), and a LAN interface, pointing downstream to a switch that other hosts can connect to.  Whatever firewall software you are using can monitor the traffic that passes through, and do things like filtering, blocking, logging, etc.  Since you are wanting to play around with this idea, I’m sure you can find some steps in the ZA documentation or forums that can help you set this up.

---

