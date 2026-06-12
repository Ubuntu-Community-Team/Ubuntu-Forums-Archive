---
title: "shorewall multiple lans on router"
date: 2008-04-14
forum: Networking &amp; Wireless
---

### Post by Rizla on 2008-04-14
Quick question regarding setting up my zones in shorewall.  I currently have 3 10/100/1000MB cards and 1 Wifi adapter.

eth0 > 10/100 (primary interface for the router/gateway) 192.168.1.2
eth1 > 10/100/1000 (will be connected to a gig switch) 192.168.2.1
eth2 > 10/100/1000 (same as above, but seperate subnet) 192.168.3.1
eth3 > 54mbps wifi (im not worrying abotu this right now becuase i'm goign to try and set this up to be an access point, but not going to go down that road at the moment)

```

#ZONE      INTERFACE     BROADCAST     OPTIONS
net        eth0          detect        routefilter,norfc1918
loc        eth1          detect
loc        eth2          detect

```

Is this the right setup for my interfaces file?  can you have multiple similarly named zones?  or should i have my eth2 set to "loc2"  ?

One other question, when configuring my IP's on my host pc's in my lans.  What should I use as the gateway?  The ip of the interface the switch is connected to on the router?  For example, if I have a workstation 192.168.2.10 hanging off a switch connected to eth1 on the routher box.  Do i configure 192.168.2.1 as the gateway?  Or do i set the ip of eth0 as the gateway?

**EDIT:** Alright, I got my setup working beautifully.  I didnt name them loc afterall.  I set them up as net > eth0 ; lan1 > eth1 ; lan2 > eth2 ; openwifi > eth3

As for the gateway, its the gateway of the interface the switches are connected to, i sorta knew this, but was thrown off because of another article I had read.  

My home network is now segemented by two firewalls.  one provided by the DSL modem/router/access point and then my internal firewall with my nas and personal comps hanging off behind them.  Basically if my wireless gets hacked (i live off a busy street) they still cant get access to my computers.  My roommates on the other hand... they're in the DMZ zone.

---

