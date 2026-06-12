---
title: "Ubuntu (?) is causing massive download, how to trace?"
date: 2006-11-16
forum: Networking &amp; Wireless
---

### Post by WishMaster on 2006-11-16
When I am on Windows, I can use NetLimiter to monitor the down/upload from each program.
In Ubuntu (or Linux in general) this isn't possible.

A few weeks ago, my laptop was powered on and connected to the internet while I was sleeping. When I woke up, I noticed a download of THREE GB. However, there was nothing downloaded, my free HD space hasn't changed...
(my ISP only allows 10Gb download per 30 days, so this is an issue)

Yesterday, the same thing happened. 
I'm guessing "some" process has a bug: it wants to update, but it keeps overwriting itself. I have no other explanation...

The download appears on my ISP-download-monitor, and also on my eth-card. So no-one is leeching from my connection.
I do not have this problem in Windows, so it is ubuntu (linux)-related...

How can I trace WHICH process is doing that?
The only known processes I had running:
- pytelemeter (a download monitor for my ISP)
- xmms
- mail notification

[IMG]http://ubuntu.vdb-studios.be/LinuxBoecht.jpg[/IMG]

---

### Post by WishMaster on 2007-05-15
I have opened my systemmonitor and wireshark.
The problem seems to be FireFox/Swiftfox...
Opening 1 webpage: 400-500kb download. If you open 10 pages = 5Mb
Just do the math on how many links you click a day....

My guess it is some kind of link-prefetching (although I disabled it in about:config).
I need something like NetLimiter to _really_ trace where it is all coming from...

---

### Post by iheartme on 2007-05-15
I have never used NetLimiter so I don't know know exactly what it does, but maybe you could try jnettop? It's in universe and monitors the network traffic and shows what's doing what.

[http://jnettop.kubs.info/wiki/](http://jnettop.kubs.info/wiki/)

---

### Post by WishMaster on 2007-05-16
Here is a screenshot of NetLimiter:
[http://www.multidesk.be/bijlage/66cf5fe6bee1fe155d44ff8b05b35ccf.png](http://www.multidesk.be/bijlage/66cf5fe6bee1fe155d44ff8b05b35ccf.png)

On the right, you see all the processes that are using bandwidth. You can rightclick any of those and choose "stats", then you get the left window: it shows the bandwidth (for firefox in this case) per hour, and the total at the bottom.

Your 'jnettop' shows only the different connection, regardless of which program is using it.
I will try it out though

edit: I cannot trace the bandwidth per program with this... :s

---

### Post by iheartme on 2007-05-17
Yeah, I noticed that you couldn't trace per program. Funny, I thought you could... Guess I'm getting old.

Oh well, maybe one of these programs will do the trick:

[http://www.ubuntugeek.com/bandwidth-monitoring-tools-for-linux.html](http://www.ubuntugeek.com/bandwidth-monitoring-tools-for-linux.html)

Good luck!

---

### Post by WishMaster on 2007-05-18
been there, done that ;-)
Nothing of use there... :(

---

