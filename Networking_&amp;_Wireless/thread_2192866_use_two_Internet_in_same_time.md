---
title: "use two Internet in same time"
date: 2013-12-10
forum: Networking &amp; Wireless
---

### Post by zist360 on 2013-12-10
Hi
in here Internet speed is so slow , because of that I have to use 2 Internet connection in same time , WiFi and ADSL .  It's possible use both of them one wifi and another LAN .
for exam when I download some things with 8 connection , 4 of them use wifi and another 4 use lan ? 
thanks

---

### Post by tgalati4 on 2013-12-10
Yes, you can.  It is called [bonding]("https://help.ubuntu.com/community/UbuntuBonding").  You want to bond your different network devices to increase throughput speed.

---

### Post by codenine75a on 2013-12-10
Bonding?  I thought it was called load balancing.  My bad.  I do not know how to do it but I think you take the two interfaces and combine them into one interface.  I think it is a virtual interface too, but I am not too keen on Linux network administration.

---

### Post by pbrane on 2013-12-10
Bonding is the term used in DSL bonding where two ADSL lines are bonded together. Requires a modem that will do g.bonding and a DSLAM to do the same.

Load balancing is probably the correct idea here. 
Maybe one of these will help
[http://www.darrylpetch.com/post/15943323883/linux-dual-internet-connections-load-balancing]("http://www.darrylpetch.com/post/15943323883/linux-dual-internet-connections-load-balancing")

[http://askubuntu.com/questions/53499/how-to-merge-multiple-internet-connections-into-one]("http://askubuntu.com/questions/53499/how-to-merge-multiple-internet-connections-into-one")

---

### Post by bab1 on 2013-12-10
> **pbrane said:**
> Bonding is the term used in DSL bonding where two ADSL lines are bonded together. Requires a modem that will do g.bonding and a DSLAM to do the same.

Load balancing is probably the correct idea here. 
Maybe one of these will help
[http://www.darrylpetch.com/post/15943323883/linux-dual-internet-connections-load-balancing]("http://www.darrylpetch.com/post/15943323883/linux-dual-internet-connections-load-balancing")

[http://askubuntu.com/questions/53499/how-to-merge-multiple-internet-connections-into-one]("http://askubuntu.com/questions/53499/how-to-merge-multiple-internet-connections-into-one")

You can bond Ethernet connections for through-put.  See below```
    802.3ad

IEEE 802.3ad Dynamic link aggregation. Creates aggregation groups that share the same speed and duplex settings. Utilizes all slaves in the active aggregator according to the 802.3ad specification.
```

For more info read the link @tgalati4 provided in post #2

---

### Post by pbrane on 2013-12-11
I understand LAGs, I just didn't think using a LAG to two different ISPs would work for increasing throughput. I must be misunderstanding the question. Sorry.

---

