---
title: "Need someone to hold my hand while building a server"
date: 2010-08-24
forum: New to Ubuntu
---

### Post by wonderweirdo on 2010-08-24
I've been playing with Ubuntu as a Desktop OS for a while, and I love it.  The time has come for me to expand my horizons and build a server for my home network.  Currently it's nothing more than a small P2P network with my Windows gaming rig, my Ubuntu Desktop and my girlfriends laptop.  I want to build a stand alone server that can take the workload of being my primary server with some pretty brouad functionality.  The computer I'm going to use is an old gaming rig with 2 gb of ram and an AMD 64 x2 prox that runs at around 2.4 Ghz.  I've never done anything like this, so I need someone to coddle me through it.  All of my experience and training has been in windows, so I'm in some pretty scary territory right now.

Here's what I want it to do.
1.  Host a domain and serve as a mail server (only a few accounts)
2.  Serve as a file share and backup for the existing computers.
3.  be a network administration hub for accounts and network logins
4.  host my printer (Only and HP laserjet 1006, already works on my Ubuntu desktop).
5.  Allow me to log into the network on any workstation and use my gaming rig online.

My plan is to use Ubuntu 10.04 as the OS, and then configure it to serve the intended purpose.  At this time, external access will not be allowed, but it's an option down the road.  Since this is an internal machine handling networking for only a few users, I figure it's a light work load.  It's also an experiment in network administration for me.  Basically I'm asking for someone who does know how to do this to mentor me through the process.  Keep in mind I've been taking baby steps until now.

---

### Post by Zzl1xndd on 2010-08-24
This shouldn't be too hard to do. 

From the looks of what you want to do you will need to set up LDAP and Samba, Postfix and possibly SSH if you want to access remotely. 

Samba & SSH are relatively easy to set up. LDAP and postfix can be somewhat challenging for someone new.

Also in the Case of Postfix you may wish to check with your ISP as they may not allow you to have a mail server.

---

### Post by joho500 on 2010-08-24
I'm using Axigen as mailserver at home. Works beautifully and very easy to set up and manage. They have a free version for one domain and up to 100 users. Nice webmail too.

Cheers,
Joost

---

