---
title: "vlan interface adds 0 to the interface name"
date: 2017-05-24
forum: Networking &amp; Wireless
---

### Post by jdambly on 2017-05-24
[COLOR=#242729][FONT=Arial]something is not right with my vlan interfaces.
[/FONT][/COLOR]
br0.0400  Link encap:Ethernet  HWaddr 0c:c4:7a:ce:42:1c
      BROADCAST MULTICAST  MTU:1500  Metric:1
      RX packets:5 errors:0 dropped:0 overruns:0 frame:0
      TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
      collisions:0 txqueuelen:1000
      RX bytes:368 (368.0 B)  TX bytes:0 (0.0 B)

[COLOR=#242729][FONT=Arial]you'll notice the vlan name is 0400 even though in my /etc/network/interfaces files I add the vlan as just 400[/FONT][/COLOR]
 #vlan 400
 auto br0.400
 iface br0.400 inet manual
[COLOR=#242729][FONT=Arial]if I look in /proc I can see the vlan id is correct but interface name has the '0'[/FONT][/COLOR]
root@opsvm02:~# cat /proc/net/vlan/br0.0400
br0.0400  VID: 400   REORDER_HDR: 1  dev->priv_flags: 1
         total frames received            5
          total bytes received          368
  Broadcast/Multicast Rcvd            5

      total frames transmitted            0
      total bytes transmitted            0
Device: br0
INGRESS priority mappings: 0:0  1:0  2:0  3:0  4:0  5:0  6:0 7:0
EGRESS priority mappings:
root@opsvm02:~#
[COLOR=#242729][FONT=Arial]I can run the commands[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]vconfig rem br0.0400[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]ifup br0.400[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]this fixes the issue, but if the machine is rebooted the issue with the 0 will happen again. Is this a bug or am I doing something wrong?[/FONT][/COLOR]

---

