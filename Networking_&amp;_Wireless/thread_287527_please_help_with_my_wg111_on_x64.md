---
title: "please help with my wg111 on x64"
date: 2006-10-28
forum: Networking &amp; Wireless
---

### Post by tomolac on 2006-10-28
I just cant figure out whats going wrong with my wireles connection? I've tryed disabling wep and mac filtering on my router but nothing seems to help?
I've got a netgear wg111v2 and I'm using ubuntu x64

the card seems to be recognized
iwconfig
```

wlan0     802.11b/g  Mode:Managed  Channel=5
          Access Point: Not-Associated   Bit Rate=11 Mb/s   Sensitivity=4/6
          Retry:on   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

but all I get is this in dmesg
```

[ 1063.522492] rtl8187: Card successfully reset
[ 1068.855700] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1072.681168] rtl8187: Setting SW wep key
[ 1073.165123] rtl8187: Setting SW wep key
[ 1073.165174] rtl8187: Setting SW wep key
[ 1073.165202] rtl8187: Setting SW wep key
[ 1073.165229] rtl8187: Setting SW wep key
[ 1073.166125] rtl8187: Setting SW wep key
[ 1073.166163] rtl8187: Setting SW wep key
[ 1075.573668] rtl8187: Setting SW wep key
[ 1075.573683] rtl8187: Setting SW wep key
[ 1075.573692] rtl8187: Setting SW wep key
[ 1075.573701] rtl8187: Setting SW wep key
[ 1075.573770] rtl8187: Setting SW wep key
[ 1075.573781] rtl8187: Setting SW wep key
[ 1077.986503] rtl8187: Setting SW wep key
[ 1077.986519] rtl8187: Setting SW wep key
[ 1077.986528] rtl8187: Setting SW wep key
[ 1077.986536] rtl8187: Setting SW wep key
[ 1077.986595] rtl8187: Setting SW wep key
[ 1077.986614] rtl8187: Setting SW wep key
[ 1080.401300] rtl8187: Setting SW wep key
[ 1080.401315] rtl8187: Setting SW wep key
[ 1080.401325] rtl8187: Setting SW wep key
[ 1080.401334] rtl8187: Setting SW wep key
[ 1080.401404] rtl8187: Setting SW wep key
[ 1080.401417] rtl8187: Setting SW wep key
[ 1082.818459] rtl8187: Setting SW wep key
[ 1082.818473] rtl8187: Setting SW wep key
[ 1082.818483] rtl8187: Setting SW wep key
[ 1082.818492] rtl8187: Setting SW wep key
[ 1082.818578] rtl8187: Setting SW wep key
[ 1082.818595] rtl8187: Setting SW wep key
[ 1085.230970] rtl8187: Setting SW wep key
[ 1085.230986] rtl8187: Setting SW wep key
[ 1085.230995] rtl8187: Setting SW wep key
[ 1085.231004] rtl8187: Setting SW wep key
[ 1085.231067] rtl8187: Setting SW wep key
[ 1085.231085] rtl8187: Setting SW wep key
[ 1087.647459] rtl8187: Setting SW wep key
[ 1087.647475] rtl8187: Setting SW wep key
[ 1087.647485] rtl8187: Setting SW wep key
[ 1087.647494] rtl8187: Setting SW wep key
[ 1087.647551] rtl8187: Setting SW wep key
[ 1087.647569] rtl8187: Setting SW wep key
[ 1090.058152] rtl8187: Setting SW wep key
[ 1090.058167] rtl8187: Setting SW wep key
[ 1090.058176] rtl8187: Setting SW wep key
[ 1090.058184] rtl8187: Setting SW wep key
[ 1090.058241] rtl8187: Setting SW wep key
[ 1090.058253] rtl8187: Setting SW wep key
[ 1092.470701] rtl8187: Setting SW wep key
[ 1092.470724] rtl8187: Setting SW wep key
[ 1092.470733] rtl8187: Setting SW wep key
[ 1092.470742] rtl8187: Setting SW wep key
[ 1092.470800] rtl8187: Setting SW wep key
[ 1092.470819] rtl8187: Setting SW wep key
[ 1094.899497] rtl8187: Setting SW wep key
[ 1094.899510] rtl8187: Setting SW wep key
[ 1094.899519] rtl8187: Setting SW wep key
[ 1094.899527] rtl8187: Setting SW wep key
[ 1094.899599] rtl8187: Setting SW wep key
[ 1094.899612] rtl8187: Setting SW wep key
[ 1097.326548] rtl8187: Setting SW wep key
[ 1097.326560] rtl8187: Setting SW wep key
[ 1097.326568] rtl8187: Setting SW wep key
[ 1097.326577] rtl8187: Setting SW wep key
[ 1097.326629] rtl8187: Setting SW wep key
[ 1097.326644] rtl8187: Setting SW wep key
[ 1099.757271] rtl8187: Setting SW wep key
[ 1099.757285] rtl8187: Setting SW wep key
[ 1099.757294] rtl8187: Setting SW wep key
[ 1099.757303] rtl8187: Setting SW wep key
[ 1099.757358] rtl8187: Setting SW wep key
[ 1099.757369] rtl8187: Setting SW wep key
[ 1100.571429] rtl8187: Setting SW wep key
[ 1100.571439] rtl8187: Setting SW wep key
[ 1100.571447] rtl8187: Setting SW wep key
[ 1100.571455] rtl8187: Setting SW wep key

```

I've been looking for a few days now on here and on google and still cant find anything that works?!

ifconfig
```

eth1      Link encap:Ethernet  HWaddr 00:15:F2:B6:83:EF
          inet addr:192.168.0.3  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::215:f2ff:feb6:83ef/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4074 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4006 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:3747060 (3.5 MiB)  TX bytes:680146 (664.2 KiB)
          Interrupt:74

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:39 errors:0 dropped:0 overruns:0 frame:0
          TX packets:39 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1972 (1.9 KiB)  TX bytes:1972 (1.9 KiB)

wlan0     Link encap:Ethernet  HWaddr 00:14:6C:B1:10:5D
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

```

iwlist scan
```

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Interface doesn't support scanning.

sit0      Interface doesn't support scanning.

wlan0     No scan results

```

lsusb
```
Bus 002 Device 002: ID 046d:c01e Logitech, Inc. MX518 Optical Mouse
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 011: ID 0846:6a00 NetGear, Inc. WG111 WiFi (v2)
Bus 001 Device 003: ID 05e3:070e Genesys Logic, Inc.
Bus 001 Device 001: ID 0000:0000

```

---

