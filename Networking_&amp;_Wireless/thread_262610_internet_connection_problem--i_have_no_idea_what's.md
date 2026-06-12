---
title: "internet connection problem--i have no idea what's going on!"
date: 2006-09-21
forum: Networking &amp; Wireless
---

### Post by autrui on 2006-09-21
hi folks,

first of all, im new to ubuntu.  things are great (i love it!) but i have this weird internet problem.

here's the setup:  i have a dsl modem, then a router, which goes to a ubuntu desktop and an XP laptop.  

symptom: it seems like if i'm using too many internet-related programs at once, i lose my connection.  the modem's lights all go off (except for the power one).

(earlier tonight, it happened this way: xp laptop was running firefox and soulseek; ubuntu dsktop was running firefox and gaim.)

here are some details: if i power-flush the modem, or just wait, things are restored--but if i keep the same programs running, it happens again moments later.  also, this is strange: if i go to 192.168.2.1 (router) and look at the dhcp client list, i get this:

192.168.2.2	BLUEBOX	
192.168.2.3	(null)	
192.168.2.4	(null)	

bluebox is the xp laptop--(null) appears to be the desktop--but why does it have two ip addresses?  is that related to this problem?  it also gives mac addresses--which i removed out of paranoia--and the (null) computer has two separate mac addresses as well.

any ideas about what i can do?  

thanks!

autrui

---

### Post by bswilson on 2006-09-21
Could you provide some details on the router?  What model/type are you dealing with?  Who is the provider?  Cable or DSL?

Also, I'm curious if the desktop has a static IP or if you're using DHCP for it.  I assume the laptop is DHCP addressed.  Is 192.168.1.1 the router's IP?

---

### Post by autrui on 2006-09-22
> **bswilson said:**
> Could you provide some details on the router?  What model/type are you dealing with?  Who is the provider?  Cable or DSL?

Also, I'm curious if the desktop has a static IP or if you're using DHCP for it.  I assume the laptop is DHCP addressed.  Is 192.168.1.1 the router's IP?

the router is a belkin wireless one: FSD7230-4:  192.168.2.1

the modem is a westell 6100; DSL from verizon: 192.168.1.1

both laptop (XP) and desktop (ubuntu) are DHCP.

does that help?  i'd include more, but i dont really know what else is relevant. 

thanks again,

autrui

---

### Post by rgeide on 2006-09-22
For the two (null) dhcp entries, do they have the same MAC addresses?
I know you can bind more than one IP address to a single, physical NIC, but that should not cause your router to stop working...unless it is a feature of Belkin routers....

---

### Post by autrui on 2006-09-22
> **rgeide said:**
> For the two (null) dhcp entries, do they have the same MAC addresses?
I know you can bind more than one IP address to a single, physical NIC, but that should not cause your router to stop working...unless it is a feature of Belkin routers....


the two (null) entries have two different mac addresses.

UPDATE: more info: the xp box DOES NOT have to be on for this to happen--it will happen just on the ubuntu box if i have enough internet programs running--ie: 2 instances of bittorrent + firefox did it to me a few minutes ago.

thanks,

autrui

---

### Post by Nano on 2006-09-22
It happened to me with some routers time ago. As far as I know the problem is on the max number of open connections the router can handle for its small ram.
I managed to solve it by creating a small script that connects to the router via telnet and sets it to drop non-active connections after 5 minutes instead of 2 days (which was the default setting).
Check if the router is linux based or accepts telnet or ssh connection. If it does, you might manage to wright something like what I did.

---

### Post by autrui on 2006-09-22
> **Nano said:**
> It happened to me with some routers time ago. As far as I know the problem is on the max number of open connections the router can handle for its small ram.
I managed to solve it by creating a small script that connects to the router via telnet and sets it to drop non-active connections after 5 minutes instead of 2 days (which was the default setting).
Check if the router is linux based or accepts telnet or ssh connection. If it does, you might manage to wright something like what I did.

i'm pretty new to linux and im definitely not a programmer..  how would i check that?  and if it does accept telnet or ssh, what would i write, and where?

thanks,

autrui

---

### Post by Nano on 2006-09-22
Sorry, I should have given you some extra details.
Let's say your router ip is 192.168.1.1. Usually, linux based routers accept telnet connections with:
telnet 192.168.1.1
and you'll get promted to type login/password.
and ssh connections with:
ssh admin@192.168.1.1 (or whatever_username_you_use_@192.168.1.1)
and get promted to login/password.

You can also check the manufacturer website for more info.

It happened to me to me to see many problems reported by users when using p2p programs because of the number of open connections so I'd bet that's what you're experiencing.
In case your router is linux-based I'll send you the script I use.

Cheers!

---

