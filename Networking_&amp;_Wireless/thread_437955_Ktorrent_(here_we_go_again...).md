---
title: "Ktorrent (here we go again...)"
date: 2007-05-09
forum: Networking &amp; Wireless
---

### Post by El Lance-O on 2007-05-09
Thankfully for the help from my last thread, I got my ports correctly fowarded.

Hurrah!

But now I get **** for download speed. Usually ~2kbps. It may fluctuate to around 20kbps, but it will just drop right after.

Now I have a 1.5MB/256kbps connection, not too bad for Alaska. And my direct downloads on firefox usually exceed 150kbps.

So...what the hell.

Port 10422 is forwarded, which I just changed because I read in another post ports above 10000 worked great for some guy. Some help it did me.

I've noticed there have been several threads with problems like this, but no real answer. I say we make this the designated thread for this kind of problem, and don't let it die! Sticky if need be!

Please help, I really hated waiting for 2 1/2 days for my one download, and I really don't want to repeat it.

Thanks in advance!

---

### Post by afonic on 2007-05-09
Maybe it depends in your ISP and not KTorrent? Can you get decent speeds with Azureus for example?

Also make sure both TCP and UDP ports that you set in settings are propertly forwarded. I use KTorrent for about a year now and I see no difference in speed against Azureus or uTorrent in Windows (VMware).

---

### Post by El Lance-O on 2007-05-09
Well I'm using my neighbors wifi, and I don't know what kind of ISP he has. Up here we only have 2 ISP's available, GCI and ACS, and at other people's houses I've never had problems with either (although GCI rapes you for money).

I have my ports forwarded correctly, no problem there, I'm pretty sure of it.

And this has happened with every torrent client I have used so far. It's actually become quite the nuisance.

---

### Post by raffytaffy on 2007-05-09
youre stealing your neighboors wifi? or did he give u permission?

---

### Post by El Lance-O on 2007-05-09
He's letting me use it, but I never asked about his ISP.

---

### Post by raffytaffy on 2007-05-09
ok understood. well, some isp like to block torrent or throttle it.

---

### Post by El Lance-O on 2007-05-09
Well as I said  before, I have downloaded torrents on other computers, with both kinds of ISP's up here, with no problem. Of course, this was on Windoze.

---

### Post by Josh1 on 2007-05-09
Why don't you try Azereus and seeing if that works?

---

### Post by El Lance-O on 2007-05-09
Again...as I said before, I have tried all the other clients, including BitTorrent, BitTornado, Azureus, KTorrent, AND uTorrent under wine.

---

### Post by alphane on 2007-05-09
and just to cover all the "simple" questions, you're sure that you are trying to download a popular file?  ie - are there plenty of people seeding?...

---

### Post by El Lance-O on 2007-05-09
PLENTY, well over 1400.

---

### Post by dodgePT on 2007-05-09
Well, if you have plenty of seeds, maybe your ISP uses [traffic shapping]("http://en.wikipedia.org/wiki/Traffic_shaping") or something.
I been having kind of slow transfers through p2p protocols, since i changed my home SO to linux, bitorrent included.
I have 24mbit dsl connection and i used to have download speeds of 1,2MBps in large swarms, now the best i get is 150/200KB of downstream. Upstream was not affected at all. It never bothered me much though.
I'm sure my router is well configured, since i used it in Windows XP with same configuration (udp/tcp port 48931) and never had a problem.

Does Ktorrent have a NAT testing tool or something similar (like Azureus)?

---

### Post by El Lance-O on 2007-05-09
BUMP

Sorry but I won't let this down until I get a solution. A computer without torrent capibilities sucks, and I KNOW there is SOMEONE that could help, at least a smidge?

---

### Post by El Lance-O on 2007-05-10
....bump....

---

### Post by Casanunda on 2007-05-12
I'm having similar difficulties with Azureus, swarm average speeds are fairly high, ~50-75 kB/s, but I can barely break 20 at the best of times.  All ports necessary are forwarded, on both the router and in iptables, NAT test says everything is fine, tons of seeds, and yet slow speeds.  My girlfriend downloads torrents at her place using the Mac version of Azureus and gets fantastic speeds, from the same ISP.  What could be the problem?

---

### Post by kugn on 2007-05-12
If it is indeed your ISP throttling bandwidth, you can try to turn on encryption in KTorrent and see if it helps.

---

### Post by El Lance-O on 2007-05-12
Fantastic sir!

You fixed my problem! (I think?)

It's going OK, ~40kbps but it fluctuates quite a bit, but it never gets horribly low for so long like before.

Not completely fixed, but definately an improvement.

Thank you so much! My life is definately better with torrents.

Now I can relive my Sega days after I download this Sega CD pack! Horray!

---

### Post by Martje_001 on 2007-05-12
Maby you could try Usenet. You can always download 150 kb/s (if you have a faster connection; faster). [Here/]("http://www.binaries4all.com/") you can find some information.

---

### Post by El Lance-O on 2007-05-12
Sounds interesting, but I'm not up for doing all that work at the moment. Torrents are OK for now.

And the speed has stopped fluctuating (sort of?) and usually stays around 100-120kbps. It's dropped down to 60-70 a couple times, but it's still such an improvement. So much better than letting my computer sit around for 3 days just to watch a movie.

Thanks for everyone's help! I'm glad this was resolved, and with 5 simple clicks!

---

