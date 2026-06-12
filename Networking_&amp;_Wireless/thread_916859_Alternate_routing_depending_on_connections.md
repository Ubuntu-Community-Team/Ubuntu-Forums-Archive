---
title: "Alternate routing depending on connections"
date: 2008-09-11
forum: Networking &amp; Wireless
---

### Post by politas on 2008-09-11
Hi, 

I'm hoping the friendly people here can help me out.

I have a home network running a wireless router and a couple of wired hosts. The wireless network and the wired hosts are all in one subnetwork (192.168.1.0) 

My primary workstation is a laptop, which has a wireless broadband connection to the Internet (when I connect it). This is my home network's only route to the Internet, which it accesses via the WAN port on the wireless router connecting to my laptop's eth0 port on a separate subnetwork (192.168.0.0)

For faster networking to the wired hosts in the 192.168.1.0 network, I can add a route to that network using:
route add 192.168.1.0 gw 192.168.0.222 netmask 255.255.255.0 dev eth0

But every time I unplug my network cable, that route automatically goes away, and doesn't come back when I plug back in.

Is there a way to make a route reappear when a wired network connection connects? If I set a gateway address in the network control panel, it makes a default gateway, which isn't what I want at all, since I can't get to the Internet through that connection at all.

Second question: 

If I turn on my wireless connection, it automatically adds a default route using that interface. That would be great when I'm connecting to any other WLAN, but messes up my routing when using my ppp0. (I end up with two default routes in the routing table, and the WLAN one always seems to end up being chosen. Is there a way to change a Wireless network settings for routing on a per-network basis? I'd like the default routing for any network other than my home wireless.

Much thanks for any help with either issue.

---

