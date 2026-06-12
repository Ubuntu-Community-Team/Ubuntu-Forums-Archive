---
title: "Network worked with Live CD, doesn't after installing"
date: 2006-09-05
forum: Networking &amp; Wireless
---

### Post by clathrate on 2006-09-05
Hi,
I'm using Ubuntu 6.06 LTS in VMWare server 1.0.1.
When I booted from the Ubuntu CD (in VMWare), my network worked.  I could browse my LAN and the internet.
I then installed Ubuntu to a virtual drive and rebooted.  Now I can't see any network resources.
ifconfig reports an IPv6 address on my eth0 interface but not an IPv4 address.
Not sure how to proceed, any ideas?
Andrew.

---

### Post by clathrate on 2006-09-05
I had a bit of trouble getting this over to my host OS, but here's the actual output from ifconfig:

eth0      Link encap:Ethernet  HWaddr 00:0C:29:97:1E:C4
          inet6 addr: fe80::20c:29ff:fe97:1ec4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1710 (1.6 KiB)  TX bytes:2178 (2.1 KiB)
          Interrupt:185 Base address:0x1400

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:7 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:372 (372.0 b)  TX bytes:372 (372.0 b)

Andrew.

---

### Post by clathrate on 2006-09-05
OK I fixed it, it turns out that VMWare was automatically bridging my network to my host's VPN virtual adapter rather than to my ethernet card...  Not sure why it ever worked!
Andrew.

---

