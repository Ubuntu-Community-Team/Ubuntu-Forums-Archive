---
title: "Reverse Remote desktop using putty and ssh?"
date: 2008-02-07
forum: Networking &amp; Wireless
---

### Post by generalya on 2008-02-07
Right now I tunnel from my work computer to a linux computer at home using port 443 and putty.  I have another computer on the home network (XP) which I can remote desktop to from work.  My question is, can the reverse be accomplished?  If I decide to work from home on Friday, I leave the putty connection intact Thursday night, make sure RDC is enabled and then connect to work from home.

Currently at work, I tunnel to home by configuring putty's tunneling options:
remote: xp.home.ip.address:3389  local port: locahost:4002

So I would open up RDC at work and connect to localhost:4002 and it works great...how would I setup the reverse?  The linux box is running latest version of ubuntu, thanks in advance

---

### Post by generalya on 2008-02-07
Ok...so let me explain:

Work Computer (ip address, 192.168.1.104)


Home Network
Ubuntu Computer (ip address, 10.1.10.105)
XP Computer (ip address, 10.1.10.101)

So the SSH is setup on ubuntu to accept connections.  I use Putty to connect to the ubuntu box..then in the tunneling options i put in
L4002: 10.1.10.101:3389

So on work computer, i would open up remote desktop connection and point to localhost:4002 and i'm connected.

For the reverse...do I put
R4003: 192.168.1.104:3389

?  Cause that didn't work when connecting to 10.1.10.105:4003 on XP computer

---

