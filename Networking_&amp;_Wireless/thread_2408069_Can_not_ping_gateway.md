---
title: "Can not ping gateway"
date: 2018-12-13
forum: Networking &amp; Wireless
---

### Post by hassj on 2018-12-13
Hi all, 

i bonded 2 slave (em5 and em6) into bond0, then tag vlan 103 on that bond card.
Every NIC start up normally, but i can not ping gateway. 
when i disable em5 port then ping gateway ok, but re-start em5 port it cannot ping to gateway

i also install Centos7 on that server then met same problem as Ubuntu.
plz advice me.
bellow is screen 
[IMG]https://ubuntuforums.org/blob:https://ubuntuforums.org/a7f68932-9205-4889-83b9-a367ffdd9257[/IMG]

---

### Post by TheFu on 2018-12-13
All the network gear involved has to support IEEE 802.3ad, bonded connections, too.   [https://en.wikipedia.org/wiki/Link_aggregation](https://en.wikipedia.org/wiki/Link_aggregation)

---

