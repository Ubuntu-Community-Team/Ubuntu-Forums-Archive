---
title: "aircrack and IPW 2200 patch"
date: 2008-06-30
forum: Networking &amp; Wireless
---

### Post by WitchCraft on 2008-06-30
Hi, Question:

I've patched my IPW 2200 driver in it's latest version.

If i get:

```

root@all:~# aireplay-ng -9 eth1
21:59:33  Trying broadcast probe requests...
21:59:35  No Answer...
21:59:35  Found 5 APs

21:59:35  Trying directed probe requests...
21:59:35  00:13:49:E0:51:A0 - channel: 6 - 'wireless1'
21:59:41   0/30:   0%

21:59:41  00:1B:11:A5:18:70 - channel: 6 - 'wireless2'
21:59:48   0/30:   0%

21:59:48  00:00:C5:BB:16:80 - channel: 7 - 'wireless3'
21:59:54   0/30:   0%

21:59:54  00:11:6B:10:86:BA - channel: 11 - 'wireless4'
22:00:01   0/30:   0%

22:00:01  00:1C:10:37:C2:9C - channel: 11 - 'wireless5'
22:00:06   0/30:   0%

root@all:~# 

```

does that mean injection does not work, or does that mean that all the accesspoints don't answer?

```

root@all:~# ifconfig eth1
eth1      Link encap:Ethernet  HWaddr 00:16:6f:ad:53:48  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:3628 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1266 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:11918 (11.6 KB)  TX bytes:0 (0.0 B)
          Interrupt:17 Base address:0x4000 Memory:dfbfd000-dfbfdfff 

root@all:~# airmon-ng start eth1 11


Interface	Chipset		Driver

eth1		Centrino b/g	ipw2200 (monitor mode enabled)

root@all:~# ifconfig eth1
eth1      Link encap:UNSPEC  HWaddr 00-16-6F-AD-53-48-E0-E3-00-00-00-00-00-00-00-00  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:4425 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1484 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:17719 (17.3 KB)  TX bytes:0 (0.0 B)
          Interrupt:17 Base address:0x4000 Memory:dfbfd000-dfbfdfff 

root@all:~# 


```

```

root@all:~# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:off/any  
          Mode:Monitor  Frequency=2.462 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

rtap0     no wireless extensions.

root@all:~# 

```

---

### Post by WitchCraft on 2008-06-30
bump.

---

### Post by WitchCraft on 2008-07-01
bump.

---

