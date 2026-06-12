---
title: "Can't download/seed using bittorrent"
date: 2007-11-01
forum: Networking &amp; Wireless
---

### Post by me1on on 2007-11-01
I've done a little searching and can't find a solution to my problem, so I'm hoping somebody here can help me.

Bittorrent was working fine up until recently. A couple months ago, though, I noticed that my upload speed was constantly 0 kbps. I tried several things to try to fix this, including enabling encryption, switching ports, making sure the port forwarding was enabled, and so on. When those things didn't help, I looked into it a bit further and found the problem: [Comcast was preventing bittorrent seeding,]("http://ap.google.com/article/ALeqM5gxRiQSVfgK4sLbVRE_X4MOlM9q0AD8SCASPG0")

I almost completely stopped using bittorrent from then on (I felt guilty downloading without being able to seed) except for a few cases. Starting about two weeks ago, I noticed that downloading on Bittorrent also stopped working. I'm not sure if it's Comcast this time, though, because I haven't read anything about them preventing downloading. The only thing that I can think of that has changed since then was that I bought a new router. This shouldn't change anything though, because I made sure that the port I'm using with Bittorrent is forwarded. I tried turning encryption on/off and changing the port, but it didn't change anything.

Has anybody else had this problem? Here's some info about my system:
Kubuntu 7.10
Bittorrent Client: KTorrent
Firewall: Firestarter (although I had this problem before I had installed Firestarter, and turning Firestarter off doesn't change anything)
Router: Linksys WRT45G

So my question is: How do I fix downloading on bittorrent (and possibly seeding, although I'm not sure that is possible because of Comcast :()

EDIT: I solved this problem by following [this guide]("http://www.portforward.com/english/routers/port_forwarding/Linksys/WRT54G/BitTorrent.htm"). This is the step I forgot: "Remove the checkmark from the Block Anonymous Internet Requests checkbox."

---

### Post by chikin03 on 2008-02-24
Hate to revive an old thread, but I was about to post something, and finally solved it.

I was unable to enable portforwarding (canyouseeme.org didn't work) until I enabled pings to the router address.  Previously, I could ssh to localhost, computername, and 192.168.1.4, but not mycomp.selfip.com.  Although it calls it a security risk, this may be the best I can do for now.

---

