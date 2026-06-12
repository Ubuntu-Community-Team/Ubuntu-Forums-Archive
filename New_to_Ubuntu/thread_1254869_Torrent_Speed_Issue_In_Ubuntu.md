---
title: "Torrent Speed Issue In Ubuntu"
date: 2009-08-31
forum: New to Ubuntu
---

### Post by chandru155 on 2009-08-31
I tested the same  torrent file in both ubuntu and windows Xp. In Xp, download speed is 190KB but in ubuntu, its just 10 to 20KB only. I correctly port forwarded and tested with [www.canyouseeme.org]("http://www.canyousee.org"). I tried different port nos. Also tried with different clients like KTorrent,Deluge, Transmission. Got nothing. What should i do to get the same speed as like in Xp? what am i doing wrong?

[IMG]http://www.speedtest.net/result/553315670.png[/IMG]

This is my speed at [www.speedtest.net]("http://www.speedtest.net")

Please help. I added the port no in FireStarter(policy-->inbound traffic Policy--->AllowService)

---

### Post by credobyte on 2009-08-31
Torrent speed @ which tracker ( TPB have screwed up something .. 300 connections & 10kb/s :D ) ?

---

### Post by colau on 2009-08-31
> **chandru155 said:**
> I tested the same  torrent file in both ubuntu and windows Xp. In Xp, download speed is 190KB but in ubuntu, its just 10 to 20KB only. I correctly port forwarded and tested with [www.canyouseeme.org]("http://www.canyousee.org"). I tried different port nos. Also tried with different clients like KTorrent,Deluge, Transmission. Got nothing. What should i do to get the same speed as like in Xp? what am i doing wrong?

[IMG]http://www.speedtest.net/result/553315670.png[/IMG]

This is my speed at [www.speedtest.net]("http://www.speedtest.net")

Please help. I added the port no in FireStarter(policy-->inbound traffic Policy--->AllowService)
Is download speed 1.65 Mb/s in windows?

---

### Post by chandru155 on 2009-08-31
Yes. 1.6Mbs(~200KBs). But in ubuntu, it is worst. Just 10 to 30KB

I took that screen short in Ubuntu only. My speed is ok. But download speed in torrent is worst. I get 200KB in direct download.

---

### Post by colau on 2009-08-31
> **chandru155 said:**
> Yes. 1.6Mbs(~200KBs). But in ubuntu, it is worst. Just 10 to 30KB

I took that screen short in Ubuntu only. My speed is ok. But download speed in torrent is worst. I get 200KB in direct download.
```

sudo aptitude install gwget

```
What's the download speed with gwget?

---

### Post by chandru155 on 2009-08-31
With Gwget, it was just 60KB only. But with firefox, it goes upto 180KB

---

### Post by lovinglinux on 2009-08-31
Are you using DHT on both? Have you checked if the tracker is down? If the tracker is down, DHT will make a big difference.

How many seeders/peers are active in the torrent and how many do you actually connect to?

Does Deluge reports "No incomming connection"?

Try downloading an [Ubuntu torrent](http://www.ubuntu.com/getubuntu/downloadmirrors#bt) to see if you get good speed.

Also disable Firestarter to see if you get better speeds.

---

