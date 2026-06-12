---
title: "large 1gb+ file transfers = system crash"
date: 2006-08-03
forum: Networking &amp; Wireless
---

### Post by mrweirdo on 2006-08-03
I still canont figure this out. Its totaly got me flustered :mad: 

I have a dell poweredge 1400 server with dual p3s which seems to be in pefectly good condition hardware wise proven by hardware testing apps and yet runing dapper drake whenever I transfer a large file 1gb+ over my gigabit lan it causes the server to lock hard. I have to go an manualy reset it via the reset switch on the case. What is weird it only seems to do this with the SMP or dual processor kernel. It doesnt matter what network card i have in the system eather. 

Right now I have two intel cards:
Intel Corporation 82540EM Gigabit Ethernet Controller
Intel Corporation 82557/8/9 [Ethernet Pro 100] 

The 100meg one goes to my cable modem while the gigabit conects to my lan.

I have a bunch of spare 100megabit nics from linksys, d-link, netgear, 3com that I have tried in my server all with the same results. Any ideas would be greatly welcomed.

---

### Post by mrweirdo on 2006-08-03
hrm I just tried using the linux-server version of the ubuntu kernel and after having the system lockup twice I found the following in my logs.

Aug 3 00:03:19 poweredge kernel: [42949466.370000] BUG: soft lockup detected on CPU#0!
Aug 3 01:07:11 poweredge kernel: [42949463.630000] BUG: soft lockup detected on CPU#0!

---

