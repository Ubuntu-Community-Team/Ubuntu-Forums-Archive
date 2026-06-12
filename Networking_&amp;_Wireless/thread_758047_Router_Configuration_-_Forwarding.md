---
title: "Router Configuration - Forwarding"
date: 2008-04-17
forum: Networking &amp; Wireless
---

### Post by sKAApGIF on 2008-04-17
Hi,

I need some help configuring a router.  

**In short** (i think) I need to forward packets from a desktop
computer to either the internet or the local network. Or do I need masquerading?

**THE SETUP:**
The Router connects to a wireless ISP's network with an ath0 interface.  It then also creates a PPPoE connection to the Internet (interface ppp0).

Now the router only has one ethernet connection so only one computer will be using it at a time.

| Wifi ISP | -  -  -  -  -  -   -  | Ubuntu Router | ---------------- | Desktop computer |   

You can think of the router as being a wifi to ethernet adapter for my desktop (although it performs a few other tasks as well).

**THE PROBLEM**
The Desktop should be able to access both the internet AND other services on the ISP's local network.  Packets from the desktop should thus be forwarded to ppp0 and ath0 respectively.

How will I go about doing it?  Since there's only one client connected to the router is masquerading unnecessary, should I rather do forwarding?  How will I setup iptables to do that?

Thanks very much!

---

### Post by SpaceTeddy on 2008-04-17
if you "hide" a computer (or network) behing another so that the outside world does not know about it, you will always need to do masquerading. since your isp only gives you one IP address, your desktop cannot connect to the internet directly. 

[here]("http://ubuntuforums.org/showthread.php?t=713874") is a howto for setting up internet sharing (which will enable your desktop to use the internet through the ubuntu router.

if there is any trouble, just ask :)

---

### Post by sKAApGIF on 2008-04-17
Hi thank you for your reply.

I currently have it setup like that.  But then only ppp0 gets masqueraded.  So I masqueraded both interfaces (is that what you should do?).  Which works...

The problem starts coming in with the configured routes.  I'm not sure how the ISP setup their network it might be possible that the netmask is wrong and that I don't need a gateway for the local network.  But by default I get a netmask of 255.255.255.0 from the dhcp server and a local gateway address.  The default route gets replaced by the default route of the pppoe connection.  So then I can't access computers outside the local netmask.  

So I added two default routes, but that doesn't really make sense logically... I don't know how linux handles that.

So I thought I will have to somehow route the traffic depending on the destination ip.  (Thought you might not have to masquerade that, but as you say you still need that.)

Any suggestions around this?

---

