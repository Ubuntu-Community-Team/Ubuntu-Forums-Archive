---
title: "Can I use spare network card as redundant gateway for my LAN ?"
date: 2017-03-09
forum: Networking &amp; Wireless
---

### Post by rrozman on 2017-03-09
Hello,

I have Ubuntu  12.04 running customized home automation software called Dianemo. I have two network cards and system acts as a home automation server and also Firewall :
one network card is for external network (eth1 towards ADSL modem 192.168.80.x) and other is for local network (eth0 192.168.0.x) .

Now I have a problem since eth0 stopped working. I could easily replace it, but my SW is checking network cards eth0 and eth1 for licensing. Therefore I have inserted new network card that is eth7.

Is there any chance to make eth7 as redundant card for my LAN and simply connect cable in there (so eth0 and eth1 stay the same) ? If that is not possible, can I at least redirect all the traffic from LAN to eth7 ?

Not sure what info to provide, but maybe ifconfig is useful :

> eth0      Link encap:Ethernet  HWaddr 50:e5:49:39:5e:91
          inet addr:192.168.0.1  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

eth1      Link encap:Ethernet  HWaddr 00:0e:2e:c0:73:cb
          inet addr:192.168.80.2  Bcast:192.168.80.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1400  Metric:1
          RX packets:125461 errors:0 dropped:2 overruns:0 frame:0
          TX packets:34204 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:36864554 (36.8 MB)  TX bytes:4930133 (4.9 MB)

eth7      Link encap:Ethernet  HWaddr e4:be:ed:44:fb:35
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


Thanks in advance,
Bulek.

---

### Post by TheFu on 2017-03-09
Support for 12.04.5 ends in a month.  All other versions of 12.04 already lost support.
Move to a new LTS release ASAP.

Not certain I understand completely, but you can force NICs to use whatever "name" you want in 14.04 by editing the udev rules file.  /etc/udev/rules.d/70-persistent-net.rules - just make the MAC  be connected to the name you wish. Under 16.04, this is done differently, thanks to systemd.

The other things you list seem possible. If it can be done with networking, than Linux can do it.
Thanks for trying to make the info readable. Really need the "quotes" to be "code" tags instead for things to line up.

Anyway, start with the network rules first.

---

