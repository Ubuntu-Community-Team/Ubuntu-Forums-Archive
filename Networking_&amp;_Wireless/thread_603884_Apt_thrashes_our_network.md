---
title: "Apt thrashes our network"
date: 2007-11-05
forum: Networking &amp; Wireless
---

### Post by bryceman on 2007-11-05
We've recently installed gutsy on a couple machines in our office. Everything works pretty slick, including network access. However, when perform apt operations (either synaptic or updating), our company network gets totally thrashed. The bandwidth to apt isn't any greater than any other large download in ffox. In fact, another user can continue a download just fine and get reasonable bandwidth, but normal browsing with many short requests are timing out completely. We're using a wrt54g w/ the ddrt firmware, and don't see anything too anomalous. Have any of you had experiences like this, or have any ideas as to where to look?

---

### Post by ddrichardson on 2007-11-05
Have you tried using the facility to select the best download server?

---

### Post by Whiffle on 2007-11-05
[http://www.dd-wrt.com/wiki/index.php?title=Router_Slowdown](http://www.dd-wrt.com/wiki/index.php?title=Router_Slowdown)

Maybe?

---

### Post by bryceman on 2007-11-05
> **ddrichardson said:**
> Have you tried using the facility to select the best download server?

I'm confused about how this could make any difference. The apt install is getting good bandwidth and has no problems. Its all the other computers on the network that are getting the timeouts.

---

### Post by Presto123 on 2007-11-05
Lol...Perhaps Ubuntu has become the Alpha male: All other computers must first ask for permission from daddy Ubuntu before they can do anything.:)

*Sorry, utterly useless comment, but...*

---

### Post by bryceman on 2007-11-05
> **Whiffle said:**
> [http://www.dd-wrt.com/wiki/index.php?title=Router_Slowdown](http://www.dd-wrt.com/wiki/index.php?title=Router_Slowdown)

Maybe?

Thanks for the link. I checked it out, but I don't think it applies to our problem. We did a fair amount of examination of the traffic, using ntop, and didn't see anything that raised our suspicion - no other large transfers, no bittorrent traffic, no high packet counts from any internal or external source. 

From that page:

> Solution 1

[LIST]
[*]Enter the following values at 'IP Filter Settings': Maximum Ports: 4096
[/LIST] 

We already had the max ports at 4096. Our network hangs around 300-400, regardless of whether apt is thrashing it or not.

> Solution 2

DD-WRT has an inbuild proxy feature that allows rewriting of HTML content to filter ActiveX cookies, etc. As this is load-intensive, you may want to disable this feature. 

We already had all those filters disabled. We also disabled all the services except for DNSMasq and rflow, for traffic analysis.

> Solution 3

Apparently there is a bug in the WRT54GS v2.2. The bug involves a fatal memory access error due to a difference in the CPU clock speed and the clock speed on the memory bus.

This appears to be regarding over-clocking. Our board says it doesn't support overclocking, and reports the expected frequency of 125 MHz.

> Solution 4

For P2P applications, and especially Bittorrent, the problem can be an overwhelming number of incoming connections.

Again, we know that's not our problem, because we don't see any of that kind of traffic in the rflow analysis.

I'd be on the dd-wrt forums if the behavior wasn't so apt-specific. Again, we only get this behavior when apt is running on one of our ubuntu systems (don't have other systems w/ apt to try). It doesn't happen during other large downloads from those systems.

---

### Post by chaumurky on 2007-11-05
have you considered caching?

[http://ubuntuforums.org/showthread.php?t=564301&highlight=network+apt+cache](http://ubuntuforums.org/showthread.php?t=564301&highlight=network+apt+cache)

---

### Post by bryceman on 2007-11-05
> **chaumurky said:**
> have you considered caching?

[http://ubuntuforums.org/showthread.php?t=564301&highlight=network+apt+cache](http://ubuntuforums.org/showthread.php?t=564301&highlight=network+apt+cache)
We'll certainly look into that, but it is still very weird that only apt seems to have this problem.

---

### Post by bryceman on 2007-11-06
> **chaumurky said:**
> have you considered caching?

[http://ubuntuforums.org/showthread.php?t=564301&highlight=network+apt+cache](http://ubuntuforums.org/showthread.php?t=564301&highlight=network+apt+cache)
On looking at that solution a bit, it doesn't really help much. We'd still have one machine doing the apt update, and the network thrashing would still probably occur, though as little as half as much. It would be really nice to be able to pre-calculate the dependencies, then delay the actual update until after-hours...

---

