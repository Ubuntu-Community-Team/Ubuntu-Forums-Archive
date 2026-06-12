---
title: "Server Ethernet Bridge - Static IPs - How to?"
date: 2008-08-13
forum: Networking &amp; Wireless
---

### Post by z33k3r on 2008-08-13
Hello. As a relative noob/better-with-windows-os, I currently have a production server running Ubuntu Server 7.x LTS. This server runs great without hick-ups. 

I have just built another server on Ubuntu Server 8.x LTS and need to have it utilize the same network as the current server (co-located in a data center). 

I get a standard cluster of 5 IPs, so I would like to simply daisy-chain the servers together to utilize the same bandwidth lease.

I would like to place the new server inline first as it will be become, down the road, the web server and the old server the storage/db server. 

I am assuming I need to run Bridge-Utils? I also found this script: [http://ubuntuforums.org/showthread.php?t=482138&highlight=ethernet+bridge](http://ubuntuforums.org/showthread.php?t=482138&highlight=ethernet+bridge)

Escentially I will need to be able to simply unplug the cat-5 from the old server, plug it into the new server, and then connect the crossover cable between them...

Any timely help would be GREATLY appreciated!:):confused:

---

### Post by z33k3r on 2008-08-14
Sorry to bump, but I really could use some help in this area. Ethernet bridging sounds simple enough, but do I really have to setup a huge script like the one linked above? :confused:

---

### Post by bab1 on 2008-08-14
Run'em off a switch.  Run the switch to the router port.

Edit:  Why would you bridge two hosts in the same network?

---

### Post by z33k3r on 2008-08-14
Well the thought was that eventually the second computer would be internal only, as a storage server to avoid routing traffic through the co-lo's routers. Simply talking back and forth rather than going through a middle man.

---

### Post by bab1 on 2008-08-14
With a switch you do talk locally.  All packets entering a port on the switch will be replicate on all the other ports of the switch.  The router should have no local route and will drop the packets.

---

### Post by z33k3r on 2008-08-15
But by doing that, you have to go to the IP source (router) and then back to the switch... at least that was my understanding. Either way, I am getting a switch... just wish somebody would help me with my original question. :(

---

### Post by bab1 on 2008-08-15
Your understanding is wrong.  As i said: > All packets entering a port on the switch will be replicate on all the other ports of the switch.  This means that if you have [COLOR="Red"]server1[/COLOR] and [COLOR="DarkOrange"]server2[/COLOR] and the [COLOR="Green"]router[/COLOR] connected to the [COLOR="Purple"]switch[/COLOR], ALL the ports will receive the data at the same time.  The host that the packets are intended for will accept the packets.  All others will inspect the data and drop the unwanted packets, including the router.  This is basic to the Ethernet protocol.  The switch is passive (unless you get a managed switch),  The router at this point is not a factor at all.  

The fact that you question was not answered the way you expected it to be is not a bad thing.  An incorrect answer is not worth anything.

---

### Post by z33k3r on 2008-08-15
> **bab1 said:**
> The fact that you question was not answered the way you expected it to be is not a bad thing.  An incorrect answer is not worth anything.

How true, how true. BUT... for security reasons, if you were to setup a firewall/webserver that then had a DB server, cache server, etc behind it, you would need to do some sort of internal networking correct?

---

### Post by z33k3r on 2008-08-15
> **bab1 said:**
> The fact that you question was not answered the way you expected it to be is not a bad thing.  An incorrect answer is not worth anything.

How true, how true. BUT... for security reasons, if you were to setup a firewall/webserver that then had a DB server, cache server, etc behind it, you would need to do some sort of internal networking correct?

---

### Post by bab1 on 2008-08-15
What do you mean by internal networking?

---

### Post by z33k3r on 2008-08-15
In other words, an internal private network between the web server, database server, cache server, etc...

---

### Post by bab1 on 2008-08-15
I don't understand your response on a couple of levels.  You previously said you have a "cluster of 5 IP".  To me this means a network of 5 [COLOR="Magenta"]contiguous[/COLOR] IP addresses (a subnet).  If you use those addresses attached to a switch and then to the router, it's not really private (these are valid internet IP addresses...right?).  My idea of a private network is [[COLOR="Red"]this[/COLOR]]("http://http://en.wikipedia.org/wiki/Private_network")

In any event, YOUR network is "set up" when you assign the IP addresses to the various hosts and they can communicate with each other.  The only multihomed host needed is the firewall/Proxy (FW/P) host.  The FW/P host is the guardian of the inside/outside traffic and as such should be DIRECTLY connected (in series) between the switch and the router.  To reiterate the setup: all the hosts are connected to the switch and then one side of the FW/P is connected to the router.

Edit:  You can use true private addressing if you wish.  Using it allows you to have as many hosts as you want behind a 2nd router.  More later if you are intrigued.

---

