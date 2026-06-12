---
title: "slow SSH with prv key exch"
date: 2008-04-04
forum: Networking &amp; Wireless
---

### Post by aztektum on 2008-04-04
I have two boxes (ssh1 and ssh2 from now on) with SSH config'd to only allow key authentication. (Actually I have dozens, but I'm talkin' about 2 in particular)

ssh1 has 2 gig NICs: One connects to the primary network, the other is connected to ssh2 (gig NIC) using x-over cable.

From my laptop I connect to the ssh1 w/ my key just fine. When I try to connect to ssh2 from ssh1 through a putty session, it's horridly slow.

This is sort of a rough shod setup, I know. It's so I can have a vserver test network and seperate all the services I plan to run across two computers.

Any suggestions on speeding up the connection

---

