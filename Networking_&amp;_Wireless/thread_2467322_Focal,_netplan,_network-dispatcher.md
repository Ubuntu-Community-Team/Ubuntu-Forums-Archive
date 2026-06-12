---
title: "Focal, netplan, network-dispatcher"
date: 2021-09-23
forum: Networking &amp; Wireless
---

### Post by tron-acm on 2021-09-23
Hi,
I've a local (home) edge server recently updated from 16.04 LTS to 20.04. Joy time :)
Most everything works fine but I can not get my network setup to a robust state. Granted, it's not a simple one.

My external conection goes via ADSL (pppoe) and cable. I also have a pair of tunnels, one SIT to HE (IPv6) and one ipip to... whatever.
And plenty of local interfaces, included vlans. Using Shorewall as FW. It was fine and dandy using ifupdown scripts plus pppoe and some rc.local glue.

Now netplan is ... complicated. And I don't understand how to follow its states. My last try was to log networkd-dispatcher scripts, and I was puzled by not seeing any trace of activity during a boot:


2021/Sep/22 18:03:36 eth5 degraded fe80::2e0:b6ff:fe04:5437 configured/degraded
2021/Sep/23 07:32:18 eth5 no-carrier fe80::2e0:b6ff:fe04:5437 configured/no-carrier
2021/Sep/23 07:32:20 eth5 degraded fe80::2e0:b6ff:fe04:5437 configured/degraded
2021/Sep/23 08:05:27 lo carrier 127.0.0.1 unmanaged/carrier

where the eth5 lines come from testing, the only report I see is for lo during a boot.
The reporting script at /etc/networkd-dispatcher/*/logit has:

#!/bin/sh
date +"%Y/%b/%d %H:%M:%S " | tr -d '\n' >> /var/log/networkd.log
echo "$IFACE $STATE $ADDR $AdministrativeState/$OperationalState" >> /var/log/networkd.log

Needless to say, my "automation" based on scripts on routable.d for the pppoe link and the cable link are not firing.

Help ?

---

