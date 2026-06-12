---
title: "Networking goes down after a few days"
date: 2005-11-03
forum: Networking &amp; Wireless
---

### Post by agrotto on 2005-11-03
I recently setup Ubuntu 5.10 as a web server and it works fine, but every 4-5 days my networking completely dies. Not just Apache, but no network accessibilty at all. I re-boot and everything is fine again.

Any ideas how to go about diagnosing this problem? 

Thanks,

-Bill

Here's my ifconfig. There is an on-board network card that I'm not using at eth0.

btopritz@caspian:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:E0:B8:11:A6:83
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:9 Base address:0x1080

eth1      Link encap:Ethernet  HWaddr 00:A0:CC:23:30:4B
          inet addr:172.20.0.3  Bcast:172.20.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4779 errors:1 dropped:0 overruns:0 frame:0
          TX packets:5675 errors:3 dropped:0 overruns:1 carrier:2
          collisions:0 txqueuelen:1000
          RX bytes:1473225 (1.4 MiB)  TX bytes:3557771 (3.3 MiB)
          Interrupt:11 Base address:0x1400

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:21554 errors:0 dropped:0 overruns:0 frame:0
          TX packets:21554 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1946652 (1.8 MiB)  TX bytes:1946652 (1.8 MiB)

---

