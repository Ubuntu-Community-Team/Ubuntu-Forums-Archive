---
title: "Reccommend a gigabit network card?"
date: 2007-08-29
forum: Networking &amp; Wireless
---

### Post by a.d.gardiner on 2007-08-29
Hey all.

Can anybody reccommend me a gigabit network card that works out of the box with samba and everything else on ubuntu 7.04 feisty?

Having alot of issues with my realtek hardware right now.

Alex :)

---

### Post by al108 on 2007-08-29
D-link 530 was my ticket. I also had troubles with RTL. 

I get around 500 Mbps with iperf on D-link. But after going thru hell with realtek I'm happy. It could be my swithch SMCGS8 slowing it down. 

My real life large file transfers with 1GB files are around 22-25 MBps, which is what I believe my test hard drives work at. hdparm -Tt shows 106 MB/s buffered reads, but I remember when I zeroed my drives with dd it reported ~25MB/s overall.

It would be interesting what speeds other people get with their hardware out of the box.

---

### Post by a.d.gardiner on 2007-08-30
Thanks for the reply :)

I need something that provides good performance but is reliable.

Did the card work out of the box or was it a similar amount of messing like with the realtek?

---

### Post by netztier on 2007-08-30
> **a.d.gardiner said:**
> Hey all.

Can anybody reccommend me a gigabit network card that works out of the box with samba and everything else on ubuntu 7.04 feisty?

Having alot of issues with my realtek hardware right now.

Alex :)

[Intel PRO/1000]("http://www.intel.com/network/connectivity/products/desktop_adapters.htm?iid=prod_desk+sc_adapter") gigabit cards have never given me any troubles at all. They were properly autodetected with the e1000 kernel module. They deliver good performance even on a rusty old P-III 500Mhz (700Mbit/s raw TCP throughput with iPerf).

That was a 32bit-PCI card; I can't speak for any 64bit or PCI-E variants (or the more expensive server-oriented versions), for I haven't touched any of them; but there is little reason to believe that they should behave differently.

I also have a handful of the older PRO/100 cards that use the e100 module, all absolutely hassle-free.
Both PRO/1000 and PRO/100 also worked out-of-the-box when I put them in a Sun Ultra 5 or Ultra 60.

best regards

Marc

---

### Post by al108 on 2007-08-31
I didn't have to do any messing in Fiestyx64 -  I pulled RTL adapter, put in D-link (DGE-530T Gigabit Ethernet Adapter) and it worked. I have same adapeter in my server since mar '06 and it's doing just  fine.


> **a.d.gardiner said:**
> Thanks for the reply :)

I need something that provides good performance but is reliable.

Did the card work out of the box or was it a similar amount of messing like with the realtek?

---

