---
title: "can't ping router wirelessly"
date: 2008-03-08
forum: Networking &amp; Wireless
---

### Post by gmh04 on 2008-03-08
Hello

I am unable to ping my router with my wireless connection. I am able to use the internet via Firefox however and am able to ping the router when the Ethernet cable is plugged in.

Help is appreciated.

ping 192.168.0.1
PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.
From 192.168.0.2 icmp_seq=20 Destination Host Unreachable

gmh04@mamachine:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

irda0     no wireless extensions.

eth1      IEEE 802.11g  ESSID:"oxgangs"
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:1B:2F:97:CF:12
          Bit Rate:54 Mb/s   Tx-Power:15 dBm
          Retry limit:15   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=97/100  Signal level=-28 dBm  Noise level=-29 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:11   Missed beacon:0


gmh04@mamachine:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1B:24:00:CE:F5
          inet addr:192.168.0.2  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:24ff:fe00:cef5/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:116 errors:0 dropped:0 overruns:0 frame:0
          TX packets:60 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:22084 (21.5 KB)  TX bytes:12302 (12.0 KB)
          Interrupt:16

eth1      Link encap:Ethernet  HWaddr 00:19:D2:98:11:58
          inet addr:192.168.0.3  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::219:d2ff:fe98:1158/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:27 errors:0 dropped:11 overruns:0 frame:0
          TX packets:122 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:7146957 (6.8 MB)  TX bytes:2651894 (2.5 MB)
          Interrupt:21 Base address:0xc000 Memory:edf00000-edf00fff

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:451 errors:0 dropped:0 overruns:0 frame:0
          TX packets:451 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:130669 (127.6 KB)  TX bytes:130669 (127.6 KB)


George

---

### Post by Hightide on 2008-03-08
Hi

You should be able to ping as ifconfig states that an IP is assigned. Can you try again with 

```
 ping -c 4 192.168.0.3
```

regards

:)

---

### Post by gmh04 on 2008-03-08
192.168.0.3 is my machine 192.168.0.1 is the router

---

