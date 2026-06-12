---
title: "Bizzare wireless connection behavior"
date: 2007-07-11
forum: Networking &amp; Wireless
---

### Post by obelisk79 on 2007-07-11
I just installed Ubuntu on an older Averatec 5400 laptop. I did my research ahead of time before wiping my HDD and installing. I have a RT2500 Ralink wireless card.

It took me a bit of fiddling, but I was able to connect to my router with wireless. When I go for a hard-wired connection I have no connection issues. I don't remember the exact commands I was using but I noticed that I was able to poke and prod using various commands and get the wireless to connect and access the net through my router. The issue arose that after 20-30 seconds or so, I would no longer be able to ping anything. I was able to do that repetitively. In an effort to fix things, I went through procedures to compile and install the latest opensource rt2500 drivers. After I finished I could no longer even enable wireless networking from the network manager.

Needless to say, I'm a bit frustrated and confused. As much as I detest windows it certainly was a bit more forgiving in terms of ease of configuration. Reinstalling windows is not an option so I'm dedicated to get this issue worked out.

I have my router currently configured as an open network until I can get a stable connection. It's set for mixed mode, and dhcp. It's a linksys router using the dd-wrt open source firmware. I hope someone can help me out on this one.

---

### Post by checho on 2007-07-11
I have the same problem. But I discovered that when working near the router I had no problem at all. I'm not sure but I think that the problem is due to an interference in the signal caused by another electric device rather than a miss configuration because otherwise you won't be able to connect at all. You may download a wireless utility like wifi-radar to check the signal strength. Anyway I'm guessing, I have a similar post, if someone tells me something use full for you I will post it here.

---

### Post by obelisk79 on 2007-07-11
I can be less than 6 inches from my router and still not get the signal. I don't think it's a proximity issue.

---

### Post by checho on 2007-07-12
Post what you get with ifconfig and with dig [www.google.com](www.google.com). To detect where the problem is at.

---

