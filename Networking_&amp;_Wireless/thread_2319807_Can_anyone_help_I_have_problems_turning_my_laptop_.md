---
title: "Can anyone help? I have problems turning my laptop to a wireless Access Point"
date: 2016-04-07
forum: Networking &amp; Wireless
---

### Post by lefteris3 on 2016-04-07
Greetings to all!

I have an old laptop Dell xps m1330 which I want to turn into an AP and use its internal wireless adapter to provide devices connected to it, access to the internet. I have found this link useful in doing so the above: [https://help.ubuntu.com/community/WifiDocs/WirelessAccessPoint](https://help.ubuntu.com/community/WifiDocs/WirelessAccessPoint).

I have followed the steps in this webpage to configure my devices.

**ifconfig** gives this output: 

wlp12s0   Link encap:Ethernet  HWaddr 00:1c:bf:32:c2:5e  
          inet addr:192.168.1.62  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21c:bfff:fe32:c25e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2716 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1639 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1073397 (1.0 MB)  TX bytes:275602 (275.6 KB)

wlx00c0ca464f8d Link encap:Ethernet  HWaddr 00:c0:ca:46:4f:8d  
          inet addr:10.0.0.7  Bcast:10.0.0.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

Some clarifications:
1. wlp12s0: It is the laptops internal wireless adapter's interface that is connected to the internet
2. wlx00c0ca464f8d: It is the usb adapter's interface which I have configure to be an AP using [B]hostapd

[/B]Some info on the devices with** lshw -C network**:

1. wlp12s0: configuration: broadcast=yes driver=iwl3945 driverversion=4.2.0-16-generic firmware=15.32.2.9 ip=192.168.1.62 latency=0 link=yes multicast=yes wireless=IEEE 802.11abg
2. wlx00c0ca464f8d: configuration: broadcast=yes driver=rt2800usb driverversion=4.2.0-16-generic firmware=0.29 ip=10.0.0.7 link=no multicast=yes wireless=IEEE 802.11bgn

Both networks seem to be up. However the AP does not seem to be broadcasting and therefore it does not appear in the list of networks.

I have 2 questions currently:
1. How do I make the AP to broadcast and hence being able to connect to it.
2. How I can "bridge" the two wireless adapters, so that all devices connected to the AP have access to the internet as well?

I would much appreciate any help.

---

