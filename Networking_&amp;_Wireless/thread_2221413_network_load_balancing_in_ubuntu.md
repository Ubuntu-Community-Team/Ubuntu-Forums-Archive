---
title: "network load balancing in ubuntu"
date: 2014-05-02
forum: Networking &amp; Wireless
---

### Post by monkeynote on 2014-05-02
Hello Ubuntu!


I would like to inquire on how can i limit the internet bandwidth usage per user. We have 10mbps connection with almost 30 units connected.


Our network setup:
DSL Line -> Ubuntu Server -> Hub - > Client PC's


Ubuntu Server have:
eth0 connected to DSL (192.168.1.1)
eth1 connected to hub (10.0.0.1)


I don't want to block facebook or youtube but i just want to LIMIT the bandwidth per unit at 512kbps. 


how can i attain this? thanks guys!

---

### Post by tgalati4 on 2014-05-02
You want to search on ways to implement Quality of Service (QoS).  Normally this is set up in the router, but you are using an Ubuntu server as a firewall then feeding your network hub.

[http://manpages.ubuntu.com/manpages/trusty/man5/netscript-2.4.conf.5.html](http://manpages.ubuntu.com/manpages/trusty/man5/netscript-2.4.conf.5.html)

If you need more control (on a per-user basis):  [http://manpages.ubuntu.com/manpages/trusty/en/man8/nufw.8.html](http://manpages.ubuntu.com/manpages/trusty/en/man8/nufw.8.html)

---

