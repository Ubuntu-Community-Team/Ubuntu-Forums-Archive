---
title: "Packet loss on ping -f"
date: 2007-07-25
forum: Networking &amp; Wireless
---

### Post by derbaschti on 2007-07-25
Hi folks,

a few days ago I started a thread about some weird network problems (small bandwidth) our research group is having. [http://ubuntuforums.org/showthread.php?p=3073324]("http://ubuntuforums.org/showthread.php?p=3073324")

Thanks to your support, I was able to convince our IT-Dept. to be a bit more specific about the problems they think our computers are having. 

They came up with some IPs of computers they think are misconfigured. They say that there is something wrong with their network cards, because if you do

```
ping -f 
```

you get 88% packet loss. 

I was able to reproduce this. However, if I do a normal ping on the machines, I get 0% loss. 

Could this be a problem with the Ubuntu driver for the ethernet cards? The machines under scrutiny are various PCs (P-IV, Core2Duo) all from Fujitsu-Siemens, running Dapper, Edgy and Feisty (depending on the respective user's flavour...) We are collecting the Serial-No's of the cards right now.

I would be very grateful for every small hint on what could be the problem...

Thanks a lot,

Sebastian

---

### Post by ddrichardson on 2007-07-25
Are they using switches, routers or hubs? Packet loss differences affected by distance are often a result of packet collision in poorly configured set ups, particularly with hubs that retransmit every packet to every node.

---

### Post by rexxxlo on 2008-01-11
i know this is an old thread but i get 88% packet loss too and i have been searching on google and dealing with this in another thread

[http://ubuntuforums.org/showthread.php?t=660109](http://ubuntuforums.org/showthread.php?t=660109)


just thought i would bring it to the top in case it can be solved???

---

