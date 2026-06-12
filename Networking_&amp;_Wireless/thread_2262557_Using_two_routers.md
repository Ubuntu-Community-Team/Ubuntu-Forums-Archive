---
title: "Using two routers"
date: 2015-01-25
forum: Networking &amp; Wireless
---

### Post by dagring on 2015-01-25
Hi,

I have a interesting oppurtunity. I have two isps delivering bandwith to my appartment. I use one of them with my wifi router, but the bandwith from the other isp isn't used. I wondered if it is possible to set up mye system so I could use the total  bandwith from both isps? There is a router modem attached to the second network outlet, så it's just pluging in a cable and use it, but I need a plan on how to do this so I dont't run into trouble in the initial steps.

-Any hints on how to proceed with this little project is welcomed.

Dag R

---

### Post by jorge8 on 2015-01-25
Two possible solutions:

1) Connect to each ISP using a separate NIC on your computer (e.g., using an Ethernet cable to one, and a WiFi connection to the other ISP)
    Pros: Cheapest solution, may not require any additional hardware if you computer has a built-in Ethernet cable (e.g., not a mac laptop) and WiFI
    Cons: This can get tricky if your computer is not close to the router or an Ethernet wall outlet

2) Get a dual-WAN router, such as [this one from TPLink]("http://www.amazon.com/TP-LINK-Dual-WAN-VPN-Router/dp/B00A8NWU70").
    Pros: Easiest solution, allows all your devices to benefit from both ISPs
    Cons: Costs more money (around $118 for the TPLink gigabit router)

---

### Post by jorge8 on 2015-01-25
[Here's an idea on how to make it work using one single WiFi adapter (client)]("http://serverfault.com/questions/192144/connect-to-multiple-ap-with-one-wifi-adapter-under-linux-freebsd").  But it seems that you'd have a decreased throughput if each Access Point is on a different channel, since your one wireless adapter would need to switch between the various channels.  I haven't tried this myself, so you may need to modify the commands to fit ubuntu.

---

### Post by ian77 on 2015-01-26
Realistically, for a ***home setup*** you're not going to be able to use both ISP connections to load balance and use both connections simultaneously with one client.

This is for a few reasons:

1 - Your computer can only have 1 default gateway. This default gateway will be going out of one of the ISPs and not the other.
2 - You aren't going to be able to load balance between two ISPs
3 - NAT will be impossible
4 - Routing gets complicated


There are certain high availability options (first hop redundancy / gateway redundancy) that can be hacked to allow you to share bandwidth between different devices on your network. 
It might not be possible to achieve it with your setup, and it's rather complicated for someone not famiiar with it,


There is an open gateway redundancy protocol called VRRP (Vritual Router Redundancy Protocol) [http://en.wikipedia.org/wiki/Virtual_Router_Redundancy_Protocol](http://en.wikipedia.org/wiki/Virtual_Router_Redundancy_Protocol) that could be used.

Essentially, you would have two routers running this for two different subnets on your network, and talking to eachother to maintain High Availability.

**Router1**
192.168.1.0/24 - Master
192.168.2.0/24 - Backup

**Router2**
192.168.1.0/24 - Backup
192.168.2.0/24 - Master

So now you have two default gateways (192.168.1.1 & 192.168.2.1) and you can have clients use one gateway ***or*** the other (not both) and connectinos are balanced amongst your two ISPs. An crucially, it is redundant, so if one router goes down, your clients will use the backup router.

Hope this makes sense. It can get quite complicated to set up, assuming of course your router supports VRRP (Not sure whether you could turn ubuntu into a VRRP router?). 

Cheers,

Ian

---

