---
title: "Can't connect to SSH from external network?"
date: 2007-02-01
forum: Networking &amp; Wireless
---

### Post by BlueSpam on 2007-02-01
Hey all, I'm rather new to linux so forgive anything I say that sounds stupid.

I just installed ubuntu server on a machine in my internal network, with the intention to set it up as a development server with ssh, apache, and cvs. I have them all working on the internal network (eg from one machine to another) and I set up the port forwarding on my router to forward TCP and UDP ports 22 from the router to ubuntu box. 

The problem I'm having is that if I try to ssh to the external IP, I get connection refused. I'm not sure where the problem is either, or how to go about fixing it. I checked canyouseeme.com and verified that it sees port 22 open on the external ip, so it's my belief that it's forwarding correctly. From what I've read so far I assume it might be related to NAT, but I don't really know enough to even start addressing this.

Thanks in advance for the help!

---

### Post by NewWithoutClue on 2007-02-01
he means [http://www.canyouseeme.org/](http://www.canyouseeme.org/)

---

