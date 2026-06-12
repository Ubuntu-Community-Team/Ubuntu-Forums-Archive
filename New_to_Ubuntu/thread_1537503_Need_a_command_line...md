---
title: "Need a command line.."
date: 2010-07-23
forum: New to Ubuntu
---

### Post by WiReIs on 2010-07-23
Hi, i have a situation within my household where my annoying little sister hogs all the bandwidth with her music downloads and MSN-IM... Grrr!! i was wondering is there a command for terminal on ubuntu 10.04 i can enter to dist her from the WAP? shes running Windows XP.

Many thanks in advance

---

### Post by CCoder on 2010-07-23
No. Impossible.

---

### Post by WiReIs on 2010-07-23
not even using airmon-ng, airodump-ng etc? :eek:

---

### Post by cavh on 2010-07-23
Your solution is offline - talk to her!

---

### Post by WiReIs on 2010-07-23
> **cavh said:**
> Your solution is offline - talk to her!

Okie doke, just thought there may have been some way to dist her computer from the WAP using the terminal.. no probs, thanks for the replies folks

---

### Post by wigg on 2010-07-23
Depending on the router you have, you might be able to get some after market firmware that will allow you to ration bandwidth.  I know that linksys/cisco routers have several exceptional user written firmware systems.  But you gonna have to have some pretty decent networking know how to do that.

If she is destroying your bandwidth with torrents.  Try running Torrent Flux on your box.  And ask her to use the web client for downloading torrents.  That way you have the ability to control how fast she downloads the most recent Justin Beiber album.

---

### Post by matrixblue on 2010-07-23
Check your router for something called QoS to give your PC higher priority

---

### Post by 3rdalbum on 2010-07-24
> **matrixblue said:**
> Check your router for something called QoS to give your PC higher priority

I   don't   think   QoS   works   that   way.   It   just   gives   priority   to   real-time   traffic   such   as   VoIP,   online   gaming   and   live   television   feeds.

---

### Post by Nick_Jinn on 2010-07-24
Its not very nice to kick your sister off line, even if she is a bandwidth hog. There might be solutions that people are reluctant to give because this is more of a social problem.

You can control the amount of bandwidth right from inside the torrent app. Why dont you do that? She might not even know you changed the settings. Let her download though.

Are you sure she is the the reason your computer is running slow?

---

### Post by matrixblue on 2010-07-24
> **3rdalbum said:**
> I   don't   think   QoS   works   that   way.   It   just   gives   priority   to   real-time   traffic   such   as   VoIP,   online   gaming   and   live   television   feeds.

QoS can be configured to prioritize traffic by protocol (like you described) or by source or destination IP address (as I have it configured on my network)

---

### Post by mbsullivan on 2010-07-24
Hi WiReIs,

I agree that talking to your sister is the best solution here; at the very least, you shouldn't take any actions without at least consulting her first. However, I also think that it's important to solve all problems as best as possible, since somebody else might have a similar problem in a different situation.

I think that you would be most happy with a QoS prioritizer, as others have mentioned. They vary widely in availability and quality among routers.

> 
Depending on the router you have, you might be able to get some after market firmware that will allow you to ration bandwidth. I know that linksys/cisco routers have several exceptional user written firmware systems.

While several are available, [dd-wrt]("http://www.dd-wrt.com/site/index") seems to be the best supported open-source firmware, last time I checked. It's very powerful and flexible, and supports [QoS prioritizing]("http://www.dd-wrt.com/wiki/index.php/Quality_of_Service") and bandwidth throttling, among other things. 

QoS priorities can be set on a per-MAC-address basis to target a specific computer. You can also [rate limit a single host]("http://lartc.org/howto/lartc.ratelimit.single.html") if you just want to completely throttle its bandwidth.

However, DD-WRT *does* take quite a bit of tinkering to set up, it's not super trivial. The chance of bricking (destroying) your router are minimal, but that's always a possibility too, as with any firmware upgrade.

Mike

PS: The subject line for this thread could also be improved for future users, it provides no useful information about the thread's content.

---

