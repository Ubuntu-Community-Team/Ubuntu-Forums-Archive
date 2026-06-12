---
title: "Cannot access localhost web pages from remote machines..."
date: 2007-07-01
forum: Networking &amp; Wireless
---

### Post by NZJon on 2007-07-01
Hi there.

I have recently upgrade my home server, and so have installed Ubuntu 7.04 where I used to have Xubuntu 6.06. I am also using Slimserver as my music server, along with MusicIp Mixer. Slimserver uses a webpage at [http://localhost:9000](http://localhost:9000) to control the music, and MusicIP uses a page on [http://localhost:10002](http://localhost:10002). On my previous Xubuntu setup I had no problem seeing the Slimserver webpage from other machines. However, with a fresh install of Ubuntu 7.04 I am having difficulties.

I can see [http://localhost:9000](http://localhost:9000) and [http://localhost:10002](http://localhost:10002) on the Ubuntu box (hostname "black") 

I cannot see [http://black:9000](http://black:9000) or [http://black:10002](http://black:10002) on the Ubuntu box "black"

I cannot see [http://black:9000](http://black:9000) or [http://black:10002](http://black:10002)  on my other box, hostname "white"

I'm also having problems getting a remote login using XDMCP, eve thoughI have enabled remote logins and added my user to the list of permitted logins.

I understand that Feisty has, by default, no ports left open, but I am at a loss as to how to change that configuration. I've had a look at Firestarter to see if I can open the correct ports, or to allow connections from specified IP address ranges, but I've not had any success. I'm a bit wary of diving into the "iptables" as I don't fully understand how that works, and how the rules are persisted through reboots.

Can anyone give me some help?

Many thanks,

   Jon

---

### Post by NZJon on 2007-07-01
Oh, and I'm also having problems getting Samba shares visible on remote machines too!

    Jon

---

