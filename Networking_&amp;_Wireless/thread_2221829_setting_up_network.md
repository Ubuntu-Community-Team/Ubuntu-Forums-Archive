---
title: "setting up network"
date: 2014-05-03
forum: Networking &amp; Wireless
---

### Post by LastDino on 2014-05-03
Well, this is something I've been thinking, but not sure if I can achieve it as I've no knowledge of networking what-so-ever, so do help me out on this.
Some of my friends and I've been using common internet connection in our building through a Wifi-router. Although, I say Wifi, I'm connected to it directly by LAN cable (If that is what you call it) through my Wifi-routers port which is again directly connected to my PC's LAN port. Just like my PC, the main PC in the house that has this main Wifi-router on its roof, is also connected directly by LAN cable. 

If I drew a diagram, it should look like this

[ATTACH=CONFIG]252816[/ATTACH]


M-R   = Main wifi-router where PC-1 (My friends PC) is connected. Through LAN cable.
2nd R = Wifi-Router in my house which is connected to main router through LAN cable.
PC-2  =  My PC. Which is connected to 2nd router by LAN cable. 
(Pardon my drawing skills with mouse :p) 

So, what I basically want to know is how can I enable file sharing to PC-1 (which has Windows7) and PC-2 (Which has Xubuntu 14.04 LTS). If I can?
Do I need any software to do that? Also, main net cable also has it's own DC++ group, is it possible for me to connect to it? If yes, how?

Any and all help is appreciated ;)

---

### Post by TheFu on 2014-05-04
Welcome to the world of networking!  This is gonna be FUN and frustrating.

To learn basic IPv4 networking, you need a foundation of terms.  Episode 25-35 of Security Now does a good job of explaining this stuff, so I won't bother.  grc.com/sn/
After you do that, we can talk about subnets ... if the systems are on the same subnet, then you can share files safely without too much risk - though any Windows on a subnet is a danger in my book.  
```
Internet
|____Router / Firewall
     |____PC1
     |____PC2
     |____PC3
     |____PC ..... 253

```

Does that make sense?  PCs on the same subnet can easily share stuff, provided they know how to find each other.  For that an IP <--> hostname lookup is necessary.  For a small number of computers/routers/devices, using the /etc/hosts file (on every machine) is the easiest way. For larger networks, running a DNS server can be worth it.  

It should go without saying that every "server" will need a static IP.

[http://askubuntu.com/questions/176248/share-folders-between-two-ubuntu-12-04-machines](http://askubuntu.com/questions/176248/share-folders-between-two-ubuntu-12-04-machines) is a place to start sharing FROM Linux to other machines.  For Windows, use nominal "Sharing" (right click on any folder to see this).

So - listen to / read those podcast notes to start.

Oh ... if the machines are NOT on the same subnet - well, that's when security becomes critical, ports need to be opened on the router, forwarded to the correct system, and strong authentication + encryption become mandatory.  sftp is really the best way to share files that way, but it has overhead that can be avoided if the systems are on the same subnet.

---

### Post by LastDino on 2014-05-04
Looks like I know where to start, we will try to do this step by step as this sounds like time consuming. 

I'll get back to you when I finish with the material provided and try to tell you whether it is subnet network we are on or not. Thanks for getting ball rolling ^^

---

