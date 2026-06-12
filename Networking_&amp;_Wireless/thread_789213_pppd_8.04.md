---
title: "pppd 8.04"
date: 2008-05-10
forum: Networking &amp; Wireless
---

### Post by mk4umha on 2008-05-10
I've almost got my Dell 5520 Broad Band wireless working. The only problem left is determining the Remote IP. Does anyone know how to fix this? Here's a log.


I'm using pppd 2.4.4.


```
May 10 10:38:06 mk4-d630 pppd[6921]: Connect: ppp0 <--> /dev/ttyUSB0
May 10 10:38:07 mk4-d630 pppd[6921]: CHAP authentication succeeded
May 10 10:38:07 mk4-d630 pppd[6921]: CHAP authentication succeeded
May 10 10:38:09 mk4-d630 pppd[6921]: Could not determine remote IP address: defaulting to 10.64.64.64
May 10 10:38:09 mk4-d630 pppd[6921]: local  IP address xxx
May 10 10:38:09 mk4-d630 pppd[6921]: remote IP address 10.64.64.64
May 10 10:38:09 mk4-d630 pppd[6921]: primary   DNS address xxx
May 10 10:38:09 mk4-d630 pppd[6921]: secondary DNS address xxx

```

---

