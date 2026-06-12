---
title: "Intel Wireless 3945 cannot connect"
date: 2007-06-07
forum: Networking &amp; Wireless
---

### Post by noamsml on 2007-06-07
I just bought a new laptop with an intel 3945 wireless card, and for some reason I can't connect to my network. Scanning works fine and iwconfig shows the right settings, but when I try to connect both with network-manager and without it fails. I tried disabling security in my network, and it didn't help.

I suspect that the following may be to blame:
```
noam@noam-laptop:~$ sudo route add default dev eth1
SIOCADDRT: No such device

```

Whenever I connect to eth1 the routing tables remain empty, and when I try to add a line to the routing table manually it displays the error message above.

Here is the output of commands that may help you:

dmesg|grep eth1:

```

noam@noam-laptop:~$ dmesg|grep eth
[   38.284000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   51.460000] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[   62.360000] eth1: no IPv6 routers present
[  111.572000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[  135.332000] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[  145.764000] eth1: no IPv6 routers present
[  202.360000] eth1: no IPv6 routers present
[  292.376000] eth1: no IPv6 routers present
```

ifconfig eth1:

```
noam@noam-laptop:~$ ifconfig eth1
eth1      Link encap:Ethernet  HWaddr 00:19:D2:8F:05:41  
          inet6 addr: fe80::219:d2ff:fe8f:541/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:149 errors:8 dropped:43 overruns:0 frame:0
          TX packets:37 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:41932 (40.9 KiB)  TX bytes:10280 (10.0 KiB)
          Interrupt:16 Base address:0xe000 Memory:f0700000-f0700fff 


```

iwconfig eth1:
```
noam@noam-laptop:~$ iwconfig eth1
eth1      IEEE 802.11g  ESSID:"samuel"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:16:01:4C:2D:BE   
          Bit Rate:54 Mb/s   Tx-Power:15 dBm   
          Retry limit:15   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=91/100  Signal level=-37 dBm  Noise level=-38 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:36   Missed beacon:0

```

---

