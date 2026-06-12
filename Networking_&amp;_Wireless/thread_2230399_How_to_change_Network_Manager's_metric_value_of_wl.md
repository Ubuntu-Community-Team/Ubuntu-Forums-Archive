---
title: "How to change Network Manager's metric value of wlan0 and em1?"
date: 2014-06-19
forum: Networking &amp; Wireless
---

### Post by PeterTaps on 2014-06-19
Folks,

Our Ubuntu system consists of minimal Ubuntu + openbox + Network Manager. Occasionally, we have to plug in a USB wireless dongle into the system. Now, we get both em1 and wlan0 network interfaces working. However, almost all messages get routed through em1. Here is the routing table:

```
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.15.1    0.0.0.0         UG    0      0        0 em1
10.10.12.0      0.0.0.0         255.255.255.0   U     9      0        0 wlan0
192.168.15.0    0.0.0.0         255.255.255.0   U     1      0        0 em1

```

What we wish is that wlan0 takes priority over em1 for all the ip addresses except for 192.168.15.*.

In another post, there is a mention of editing wired connection and setting "Use this connection for resources only on its network." While this works, there are a couple of problems:
1. The operator is not sophisticated to change these settings and restart networking.
2. Once the wireless dongle is removed, the operator has to remember to change the settings back and restart the network.

Instead, I am thinking if we could just force-change the metric values for em1 and wlan0, our problem might get solved. This setting would get applied just once and there won't be any need to edit/restart network later.

I would appreciate if you could share your thoughts on how to change the metrics or if there is a better way to handle our problem.

By the way, once we build the system and install Network Manager, we always comment out em1 in /etc/network/interfaces:

```
auto lo
iface lo inet loopback


#auto em1
#iface em1 inet dhcp


```

As I understand, Network Manager does not use /etc/network/interfaces file.

Thank you in advance for your help.

Regards,
Peter

---

### Post by PeterTaps on 2014-06-19
Anyone? 

Appreciate your help.

Regards,
Peter

---

