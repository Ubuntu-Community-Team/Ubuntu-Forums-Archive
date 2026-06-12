---
title: "ICMP traffic blocked by ISP"
date: 2007-12-18
forum: Networking &amp; Wireless
---

### Post by Zenthes on 2007-12-18
Looked around on this subject and all i could figure out is topics on "how to block ICMP" and editing your IP tables so i assume a solution would be some where along the lines of that?

My ISP has ICMP traffic blocked/turned off.  Called them up today and asked about it, and they just said thats the system admins choice.  Well i don't want to disobey there choice but i'd still like to ping just for actually seeing my ping in MS.  I was wondering if there are any solutions to recommend.  


Just some extra info i am running a router : Netgear wgr614v5
Also running Gutsy

---

### Post by lespaul_rentals on 2007-12-18
If you are looking to just ping inside your network, there is nothing they can do to disable that.  However, I wouldn't be surprised if they did disable ICMP traffic anywhere else, as ICMP requests are commonly used by crackers to pinpoint targets.

---

### Post by Zenthes on 2007-12-18
> **lespaul_rentals said:**
> If you are looking to just ping inside your network, there is nothing they can do to disable that.  However, I wouldn't be surprised if they did disable ICMP traffic anywhere else, as ICMP requests are commonly used by crackers to pinpoint targets.

I'm aware of the illegitimate uses of it but I mean i just want to say ping a game server to see what my ping is, my ISP has made it impossible.

I can ping with in my LAN yea, but isn't what i'm looking for.  
I blame my wanky service provider, but then again I can't complain too much, only high speed ISP that can reach me.  

[http://speednetllc.com/]("http://speednetllc.com/")

Good company but i think there using an out of date system is partly why ICMP traffic is turned off just frustrates me because i can't do something simple as ping.

---

### Post by lespaul_rentals on 2007-12-18
> **Zenthes said:**
> I'm aware of the illegitimate uses of it but I mean i just want to say ping a game server to see what my ping is, my ISP has made it impossible.

I can ping with in my LAN yea, but isn't what i'm looking for.  
I blame my wanky service provider, but then again I can't complain too much, only high speed ISP that can reach me.  

[http://speednetllc.com/]("http://speednetllc.com/")

Good company but i think there using an out of date system is partly why ICMP traffic is turned off just frustrates me because i can't do something simple as ping.

Actually, pinging a game server through DOS or the like isn't a reliable judge of how good your connection is  The game should have an automatic ping, most online games I used to play had that.

---

### Post by Zenthes on 2007-12-20
thanks anyways  :-k

---

### Post by lespaul_rentals on 2007-12-20
Call your ISP and see if they will allow you to use ICMP.  It's possible they might if you ask (but don't count on it).

---

