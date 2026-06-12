---
title: "how to transfer files using nitroshare via virtualbox"
date: 2018-10-04
forum: Networking &amp; Wireless
---

### Post by Claus7 on 2018-10-04
Hello,

as the title suggests, the steps in order to be able to transfer files using nitroshare between two OSs, under the same network, are the following:
[LIST]
[*]install nitroshare (via synaptic package manager) in ubuntu 18.04 desktop which is connected via ethernet cable
[*]install nitroshare in guest OS (ubuntu based) under virtualbox 5.2x in a laptop, which is also connected via ethernet cable (wireless in my case did not work)
[*]from settings->network of virtualbox, choose: bridged adapter and then open advanced settings; from there I chose one of the two adapters offered, which actually worked; the cable connected option enabled; and the promiscuous mode set to: Allow All.
[*]open both programs at each OS, which have to operate simultaneously.
[/LIST]

Just to mention that NAT option did not work. 

Regards!

---

