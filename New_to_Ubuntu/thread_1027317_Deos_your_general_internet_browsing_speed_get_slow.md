---
title: "Deos your general internet browsing speed get slower while you're downloading?"
date: 2009-01-01
forum: New to Ubuntu
---

### Post by eragon100 on 2009-01-01
Hello! It sounds logical to assume that browsing the internet goes slower if you're downloading something at the same time at "max speed". However, because it often stays fast / gets slow without me downloading anything, I would like to ask if this is really the case. I ask this becuase me and my parents (on their pc, shared internet by router) often get *very* frustrated with the internet browse speed slow as a snail.

My official down speed is 4 mbps, on average I get 335 KB /s for real.

---

### Post by Sprut1 on 2009-01-01
I never notice it, I have a 12/12mbit fiber optic line - downloading and internet surfing + games work well.

---

### Post by steveneddy on 2009-01-01
If, for instance, one has a DSL internet connection that is rated at 1.5 mbps and you are DLing a large file (movie, song....) and someone else on that shared internet connection opened up a web page that was heavy on Flash or media then the overall internett connection speed would go down, until the large file download either was stopped or finally finished.

Think of it as a garden hose watering your yard. Works great for one yard, but if you watered 20 yards from one hose, each yard would take longer to get watered.

Maybe not the best analogy, but, yes, sometimes DLing files on a network with a fixed internet capacity will cause others on the network to have poor internet performance.

The cure is to upgrade to a faster internet service or upgrade the DSL.

---

### Post by eragon100 on 2009-01-01
> **steveneddy said:**
> If, for instance, one has a DSL internet connection that is rated at 1.5 mbps and you are DLing a large file (movie, song....) and someone else on that shared internet connection opened up a web page that was heavy on Flash or media then the overall internett connection speed would go down, until the large file download either was stopped or finally finished.

Think of it as a garden hose watering your yard. Works great for one yard, but if you watered 20 yards from one hose, each yard would take longer to get watered.

Maybe not the best analogy, but, yes, sometimes DLing files on a network with a fixed internet capacity will cause others on the network to have poor internet performance.

The cure is to upgrade to a faster internet service or upgrade the DSL.

How fast would it need to be? 4 mbps isn't really slow, right??

Would 20 mbps be enough?

---

### Post by Dedoimedo on 2009-01-01
Sometimes, when downloading really a lot, this being both full bandwidth and lots of connections, I do notice some sluggishness, but it's far more prominent when uploading massively rather than downloading.

This also depends on your processor, network card, router, ISP etc. If you have a weak / fourth-grade network card or a router that does not handle massive throughput effectively, you may see a downgrade in performance when revving it up.

One way to see if your router / network card is a bottleneck is to use the floor ping against these devices and see how many packets drop out.

For example:

```

ping -c 10000 -f xxx.xxx.xxx.xxx

```

This will flow the IP address (xxx) with 10,000 pings as fast they reply or 100/sec, a total of 100 seconds (or so) in this case. Do this against your router once and against your network card and see how they behave. Then, start downloading something and repeat the process. See how many packets drop.

Do not EVER flood anyone on public IP without their permission! Your ISP could get you banned.

Dedoimedo

---

### Post by glotz on 2009-01-01
[QUOTE=Dedoimedo]Sometimes, when downloading really a lot, this being both full bandwidth and lots of connections
[...]
Do not EVER flood anyone on public IP without their permission! Your ISP could get you banned.[/QUOTE]
I think the connections is the key here.
[...]
Except [www.microsoft.com](www.microsoft.com) :twisted:

---

### Post by Delever on 2009-01-01
Try to lower number of connections down to 25-40 when you need to browse when downloading (I assume torrents), and see if that helps (of course, download speed might drop significantly).

Another thing - try always limit upload speed. Keep it near maximum, but not maximum (also for torrents).

---

### Post by eragon100 on 2009-01-01
> **Delever said:**
> Try to lower number of connections down to 25-40 when you need to browse when downloading (I assume torrents), and see if that helps (of course, download speed might drop significantly).

Another thing - try always limit upload speed. Keep it near maximum, but not maximum (also for torrents).

I am also (mostly) talking about direct downloads, because I can easily limit download speed on torrents in deluge and already do this. Furthermore, most stuff I download, games new versions (wesnoth, nexuiz), and videos (mostly anime) is all via direct download.

It doesn't matter anymore anyway, as I have found a program, trickle, that allows you to start a program from a terminal with a specified max download / upload speed, thus allowing you to start firefox to download something with 250 kbps max, while internet stays fast in opera (and for my parents, too) :)

---

