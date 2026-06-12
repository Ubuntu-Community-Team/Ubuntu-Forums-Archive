---
title: "VERY slow wireless connection?"
date: 2007-12-28
forum: Networking &amp; Wireless
---

### Post by arialth on 2007-12-28
I've browsed about the forums a bit and tried a few things (Like disabling ipv6) and none of them work.

I am running Ubuntu 7.04 on an hp dv9420 and i have the Broadcom card BCM4310. My problem is that I have a very poor connection/throughput to my wireless router. The network-manager icon tells me i have about an 80% connect most of the time, but any time i try doing something via wireless (surfing, IM, apt-det update) it goes PAINFULLY slow. The router is set up with MAC filtering and no broadcast SSID. I rarely have issues connecting but as soon as i do, all connections going through the router take a long time, or sometimes even fail to work. Seeing as the modem connected to the router is cable and i've capped it a about 15 mbps, this should not be happening. I know wireless is a bit slower than ethernet, but on Wondows i can normally hit about 1.1 mbps download via my wireless card. The ndiswrapper driver is installed; that's the only reason i can connect at all, i suppose. 

I guess i can still count as a linux noob; i've been using it for a couple years now, but there is a lot i dont know, especially on this laptop, on which linux has given me nothing but trouble. I'm just trying to solve one problem at a time.

---

### Post by (((X))) on 2007-12-28
I would scan my network, with wireshark or so to see if someone is connected to your network and downloading huge files (if the network is not secured).

---

### Post by arialth on 2007-12-28
Well the network is running mac filtering and only my mac is whitelisted. Not only that, the SSID is not broadcasted. So its pretty secure

---

### Post by madelman on 2008-03-27
Were you able to find out what the problem is with the wireless very slow?

I am having this problem lately and I cannot find any solution. Searching this issue in these forums I can see that many people are having the same issue and for some reason all threads are closed when the problem persists. 

It is very slow lately my wireless connection that is not even funny. I have changed the Network Manager to Wicd, which worked better but it has been started to be very slow. With Network Manager I was not able to find my network then sometimes it disconnected so I switched to Wicd and worked better the network is there all the time but it is very slow after 5 minutes that I am online. 

I running on Ubuntu 7.10 and nobody can provide any solution. This really sucks.

---

