---
title: "One ethernet for internet, one for network..."
date: 2008-04-03
forum: Networking &amp; Wireless
---

### Post by prodezigner on 2008-04-03
I was wondering, I want to set a home file server up with two NICs, one with access to the internet, one for just network sharing for optimum transfer speeds between LAN PCs. How do I config. my ETH interfaces? I'm going to assign a static IP for the internet NIC (so I can SSH into it). And that's not a problem, I just don't know how to make the other NIC LAN only.

I guess the best way to describe what I want is this.

Server has two HDDs, one is ReiserFS (main) and the storage is NTFS (for external exclosures later on). I want to be able to download and let others on the network (controlled by a seperate NIC) share files and backup using the storage drive. But I need the internet NIC to be hidden on the network (best way to put it). So a rough layout:

Server - HDD1 - Main
Server - HDD2 - Storage
ETH0 - Internet connected via router, but hidden on network
ETH1 - Ethernet connected via router, but no internet sharing HDD2.

---

### Post by superprash2003 on 2008-04-03
still didnt get your setup!!do you want to share an internet connection between the two nics? if so.. [http://wiki.steenbe.nl/?p=29#more-29](http://wiki.steenbe.nl/?p=29#more-29)

---

