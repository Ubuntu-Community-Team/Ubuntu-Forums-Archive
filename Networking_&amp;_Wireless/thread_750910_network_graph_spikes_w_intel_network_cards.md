---
title: "network graph spikes w/ intel network cards"
date: 2008-04-10
forum: Networking &amp; Wireless
---

### Post by clarknova on 2008-04-10
I have three computers, all different hardware, but all using intel gigabit ethernet adapters. One has a Pro 1000 GT (pci) one has a Pro 1000 PT (pcie) and one has both a Pro 1000 PT and on-board intel GBE.

On all three of these machines the Gnome System Monitor Resources tab (and applet) shows spikey traffic patterns when the transfer is steady. I know the traffic is steady because my router graphs traffic and shows a steady 3000/640 kbps, which is my connection speed, while GSM is bouncing between 0 and some number much higher than my connection speed. Even LAN connections running at 2-300 mbps oscillate like this in the monitor.

I've never seen another NIC report traffic like this, it's usually a steady line. Is it a bug? Is it something I can tune? Anybody seen this before?

The two screenshots show GSM and my router's traffic graph, respectively during a torrent upload running at unlimited upload speed on a 640 kbps up connection, graphed for about a minute.

db

---

### Post by clarknova on 2008-04-22
There's no way I'm the only one using intel pro 1000 cards in gnome. Are other people seeing this?

db

---

### Post by clarknova on 2008-05-01
Solved on two machines with Pro 1000 PT NICs by using the proper driver. Still need to test it on the machine with the Pro 1000 GT, optimistic.

[http://whocares.de/2008/04/20/make-intels-8257x-based-gigabit-adapters-work-with-ubuntu-804-hardy-heron/](http://whocares.de/2008/04/20/make-intels-8257x-based-gigabit-adapters-work-with-ubuntu-804-hardy-heron/)

db

---

