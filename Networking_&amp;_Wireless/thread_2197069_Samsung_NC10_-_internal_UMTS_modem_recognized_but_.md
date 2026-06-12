---
title: "Samsung NC10 - internal UMTS modem recognized but not connecting"
date: 2014-01-02
forum: Networking &amp; Wireless
---

### Post by StefanBaumgartner on 2014-01-02
Hello Community,

I'm using Lubuntu 13.10 on a Samsung NC10 netbook with an internal UMTS modem which is recognized and can be enabled in Network Manager display and even displays the Network and Signal Strength. But I can't connect ... The funny thing is, using a Lubuntu 13.10 Live USB stick it works ... I tried two different SIM Cards to rule out UMTS network problems .. 

Attached you can find the logs of modem-manager and network-manager, taken via

network-manager --no-daemon 2>&1 | tee /tmp/network-manager.txt
modem-manager --debug 2>&1 | tee /tmp/modem-manager.txt

Any help would be greatly appreciated.

Thanks in advance, best regards
Stefan

---

