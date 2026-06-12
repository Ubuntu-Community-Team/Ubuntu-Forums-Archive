---
title: "Macchanger in Kubuntu"
date: 2008-02-07
forum: Networking &amp; Wireless
---

### Post by Ariliand on 2008-02-07
Hello forum,

I'm trying to use Macchanger to randomize my MAC address on every boot, but it seems KNetworkManager (or NetworkManager) somehow prevents this from working.

My ifconfig reports the following:
```
$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:A0:D1:77:BE:75
          inet6 addr: fe80::2a0:d1ff:fe77:be75/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1651 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:141218 (137.9 KB)  TX bytes:796 (796.0 b)
          Interrupt:17

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:21 errors:0 dropped:0 overruns:0 frame:0
          TX packets:21 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1282 (1.2 KB)  TX bytes:1282 (1.2 KB)

wlan0     Link encap:Ethernet  HWaddr 00:13:E8:1A:B7:F7
          inet addr:192.168.9.104  Bcast:192.168.9.255  Mask:255.255.255.0
          inet6 addr: fe80::213:e8ff:fe1a:b7f7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5556 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4581 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:3518237 (3.3 MB)  TX bytes:828273 (808.8 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-13-E8-1A-B7-F7-00-00-00-00-00-00-00-00-00
-00
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

```

If I run 
```

sudo ifconfig wlan0 down
sudo macchanger -a wlan0
sudo ifconfig wlan0 up
```

the MAC address does change, but KNetworkManager stops responding (it can't change the active connection, and gets stuck at 0%). The only way to fix this is to reboot, which of course resets the MAC. I tried adding the above commands to /etc/rc.local, but it doesn't seem to be working.

Is there a way to start macchanger before KNetworkManager starts, or maybe even some configuration file to change MAC addresses manually? I tried editing /etc/network/interfaces, but it seems that doesn't work with NetworkManager.

Thanks a bunch.

---

