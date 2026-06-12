---
title: "Network tops off at 10 Mbps"
date: 2007-01-16
forum: Networking &amp; Wireless
---

### Post by Lucardo Mamones on 2007-01-16
Hello,

I apologize if this issue has been brought up before, I have searched everywhere and no luck. Anywho...

I have two machines running Dapper updated and connected to each other with a xover cable. I am trying to get some rather large files from one machine to the other via FTP. The problem I have is that my transfer speed is about 10Mbps, sometimes 9.8 but never seen it over 10.

I have checked using ethtool that both NICs are running at 100 Mbps FD and the cable is CAT5. I have tried connecting to a switch with the right cables with the same results. I have used rcp to transfer the files but get the exact same troughput.

Is this a configuration issue? I have read somewhere that it could be cause by having IPv6 daemon running but havent tried stopping it yet.

ANYBODY, ANY IDEAS???? I am going crazy I have about 500Gb to copy and at 10MBps.... takes a loooong time. (about 14 hours!!)

Thank you!!

---

### Post by peabody on 2007-01-16
what's the output of ifconfig on both machines?

---

### Post by Lucardo Mamones on 2007-01-17
eth0      Link encap:Ethernet  HWaddr 00:E0:4C:EE:2B:37
          inet addr:192.168.10.10  Bcast:192.168.10.255  Mask:255.255.255.0
          inet6 addr: fe80::2e0:4cff:feee:2b37/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:464 errors:0 dropped:0 overruns:0 frame:0
          TX packets:318 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:38463 (37.5 KiB)  TX bytes:34681 (33.8 KiB)
          Interrupt:185 Base address:0x6000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:31 errors:0 dropped:0 overruns:0 frame:0
          TX packets:31 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:2131 (2.0 KiB)  TX bytes:2131 (2.0 KiB)

---

