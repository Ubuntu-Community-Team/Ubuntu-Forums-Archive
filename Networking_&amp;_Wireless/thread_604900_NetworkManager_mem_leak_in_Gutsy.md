---
title: "NetworkManager mem leak in Gutsy?"
date: 2007-11-06
forum: Networking &amp; Wireless
---

### Post by agiamba on 2007-11-06
Hi,

I have been with Ubuntu since Dapper, upgraded to Feisty and then to Gutsy. I had a few problems so I wiped it my partition and did a clean install. If I leave my laptop (Dell Inspiron 6000) on overnight NetworkManager begins to consume a decent amount of memory, but an unbelievable amount of CPU. Is there a mem leak, is this a common problem?

---

### Post by kd7swh on 2007-11-06
There are a lot of problems with NetworkManager in Gusty. I too have a memory leak problem, but a bigger issue for me was the pptp plugin. The plug-in only works with the eth0 interface. So I had to change my wireless card to eth0 for it to work properly.  I just noticed that there is an update for NetworkManager in synaptic today. perhaps the latest patch will solve some of these issues.

---

