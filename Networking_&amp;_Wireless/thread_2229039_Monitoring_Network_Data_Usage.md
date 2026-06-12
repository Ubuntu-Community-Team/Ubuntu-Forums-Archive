---
title: "Monitoring Network Data Usage"
date: 2014-06-11
forum: Networking &amp; Wireless
---

### Post by PopsTheSailor on 2014-06-11
We have Comcast for our internet (you begin to see how dumb I am). We have 5 computers, a blue ray player that streams Netflix, an iPod and 2 Nooks all connected into our network and we are going over our limit set by comcast. I know most of it is Netflix but I want to know data usage by device.

Can someone tell me, in Layman's terms, how I would monitor the data usage at the device level. I don't care what applications are using the data, I just want to know computer A has used 15GB of data, Computer B 5 GB of data, etc.

Start simple or you will lose me.

---

### Post by QIII on 2014-06-11
Hello!

Comcast has a "Usage meter details" page that might be handier than counting on your fingers adding up several devices.

---

### Post by CharlesA on 2014-06-11
> **QIII said:**
> Hello!

Comcast has a "Usage meter details" page that might be handier than counting on your fingers adding up several devices.

+1. You could check your router to see if it tracks traffic, but I don't think many of them do unless you use Tomato or DD-WRT or the like.

---

### Post by sandyd on 2014-06-11
Try ntop. You will have to run it somewhere where all the traffic passes through.
The one in the repos that is (old version)
Depending on your internet, it *might* or might not keel over depending on the amount of packets passing through it.

---

### Post by PopsTheSailor on 2014-06-12
To the comment about using Comcast's usage meter, that isn't what I need. Probably could have been more clear. I want to know data usage by IP device. Comcast just shows total usage.

To the suggestion about using nTop, how do I "run it somewhere where all the traffic passes through"? I have an old laptop. Can I use that somehow?

---

