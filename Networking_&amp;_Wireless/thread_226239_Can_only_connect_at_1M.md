---
title: "Can only connect at 1M"
date: 2006-07-31
forum: Networking &amp; Wireless
---

### Post by 8086ed on 2006-07-31
I can only connect to routers (All of the ones I've tried, anyway, and I've tried quite a few.) after typing
```
$sudo iwconfig ath0 rate 1M
```
Sometimes I have to disable and enable my connection, as well.  It has been driving me nuts.  Sometimes I can get away with 2M, but I have to be close (< 3 meters from the router).  The router I generally use is usually only about 3-4 meters away.  I get 90% reception.

iwconfig says:
```
lo        no wireless extensions.

eth0      no wireless extensions.

ath0      IEEE 802.11b  ESSID:"Quesada"  Nickname:"Quesada"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:16:B6:67:66:C2
          Bit Rate=1 Mb/s   Tx-Power:18 dBm   Sensitivity=0/3
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=58/94  Signal level=-37 dBm  Noise level=-95 dBm
          Rx invalid nwid:5  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:1

sit0      no wireless extensions.

vmnet1    no wireless extensions.

vmnet8    no wireless extensions.

```

ifconfig says:
```
ath0      Link encap:Ethernet  HWaddr 00:11:F9:FD:28:5F
          inet addr:192.168.1.104  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::211:f9ff:fefd:285f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:40634 errors:7367 dropped:0 overruns:0 frame:7367
          TX packets:31794 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:200
          RX bytes:35989227 (34.3 MiB)  TX bytes:4397598 (4.1 MiB)
          Interrupt:201 Memory:f8c40000-f8c50000

eth0      Link encap:Ethernet  HWaddr 00:12:3F:DD:7C:DF
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:209

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:11 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:656 (656.0 b)  TX bytes:656 (656.0 b)

vmnet1    Link encap:Ethernet  HWaddr 00:50:56:C0:00:01
          inet addr:172.16.141.1  Bcast:172.16.141.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

vmnet8    Link encap:Ethernet  HWaddr 00:50:56:C0:00:08
          inet addr:172.16.3.1  Bcast:172.16.3.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

```

I have vmware server installed, so that explains the vmnet thingies.

I remember when I was setting up the madwifi drivers, I mistyped something and I had no idea how to fix it.  It had something to do with ifconfig, though.

I have an Atheros 5002 a/b/g chipset.  When I use aireplay, I can't inject packets either.

Thanks in advance for your help; this community is what brought me to Ubuntu. :D

---

### Post by 8086ed on 2006-12-22
Bumping...  I can't believe I've suffered through this for almost 5 months...  It doesn't seem that long...

Anyway, I'm still having the same trouble after a clean format and upgrading to edgy.  I'm always getting good reception, even without changing to 1M, but can't ever get an IP without it.  Any ideas?

---

