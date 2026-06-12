---
title: "Can't set up D-LINK 502T"
date: 2008-03-24
forum: Networking &amp; Wireless
---

### Post by ExileAmongYou on 2008-03-24
I just installed Ubuntu, and I've been unable to get the internet working (it did work for a very brief period, but then it died again). I have a D-LINK 502T ADSL router, connecting through an ethernet port. It's working fine on the XP computer I'm using to post this. Any ideas?

---

### Post by ExileAmongYou on 2008-03-24
OK, I managed to get Firefox working and connecting to the internet by disabling IPv6, but Synaptic Package Manager and sudo apt-get update still don't show any signs of connecting ( I disabled IPv6 in /etc/modprobe.d/aliases as well). Does that narrow down the problem?

---

### Post by ExileAmongYou on 2008-03-24
Oh, and now that Firefox is working I can post these:

ifconfig:
```
eth5      Link encap:Ethernet  HWaddr 00:00:6C:EB:5F:FF  
          inet addr:10.1.1.2  Bcast:10.255.255.255  Mask:255.0.0.0
          inet6 addr: fe80::200:6cff:feeb:5fff/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2984 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2435 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3293643 (3.1 MB)  TX bytes:294203 (287.3 KB)
          Interrupt:20 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
```

iwconfig:
```
lo        no wireless extensions.

eth5      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:off/any  Nickname:"Broadcom 4311"
          Mode:Managed  Access Point: Invalid   
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level=-256 dBm  Noise level=-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

cat /etc/network/interfaces
```
auto lo
iface lo inet loopback

```

---

