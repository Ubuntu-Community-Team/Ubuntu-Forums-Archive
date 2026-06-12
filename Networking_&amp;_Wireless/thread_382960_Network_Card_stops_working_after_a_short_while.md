---
title: "Network Card stops working after a short while"
date: 2007-03-12
forum: Networking &amp; Wireless
---

### Post by mortenj on 2007-03-12
Hi
First off; 
- new to linux but know my way around the basics.

Hardware: Compaq Evo N800c portable PC (2.2ghz/40gb/etcetc). Network is wired &  connected through a pccard (there is a card onboard but I was told it is broken), 3com Megahertz 10/100 Lan Cardbus, model 3ccfe575ct.

Problem:
Fresh installation.
Network worked fine thorough install and on updates alone, maxed out my connection easily at 1.2mb/sec.

Install Azureus and tries it out. Network crash and wont come up again, not able to reach any ip or any site (web, bittorrent, ftp, local network). Searched a bit and tried upgrading to latest sun java. Didnt work. Deinstalled azures and tried ktorrent, works fine for a while but also makes the connection drop and never return.

So at this point I guess theres something about bittorrent either my hardware, drivers or ubuntu doesnt like.

Trying simple surfing, no torrent client active. And still the same problem, network suddenly crashes/freeze and wont return, however takes a bit longer before it happens. I am thinking that maybe too many connections (62 connection in ktorrent last time when network frooze) makes something crash and breaks the network connection. 

Network icon beside the clock does not change its state when the network breaks, it appears to belive everything is ok.

The only solution I got atm to this problem is to remove the pccard and reinsert it, seems a bit overkill though. 

Any easy, step by step, suggestions that I can try to get this pc stable networked? Maybe upgrade networkcard drivers (seems like the windows thing to do though, dont even know how its done in linux)? Maybe the onboard netcard is active and is causing problems, if so, how can it be deinstalled? Tried checking that device manager, didnt see any other netcards present.

---

