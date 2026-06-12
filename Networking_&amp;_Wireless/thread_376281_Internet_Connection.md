---
title: "Internet Connection?"
date: 2007-03-04
forum: Networking &amp; Wireless
---

### Post by video_nut22 on 2007-03-04
I am sure you had heard this question about a billion times: I can't connect to the internet. I have a lan (DSL) connection. I typed (Ifconfig) in the terminal and received this below. Could someone walk me through this. Please!

Thanks....

Joe




ubuntu@ubuntu:~$ ifconfig

eth0 Link encap:Ethernet HWaddr 00:E0:18:9D:C0:66

inet addr:192.168.1.100 Bcast:192.168.1.255 Mask:255.255.255.0

inet6 addr: fe80::2e0:18ff:fe9d:c066/64 Scope:Link

UP BROADCAST RUNNING MULTICAST MTU:1492 Metric:1

RX packets:7 errors:0 dropped:0 overruns:0 frame:0

TX packets:18 errors:0 dropped:0 overruns:0 carrier:0

collisions:0 txqueuelen:1000

RX bytes:1721 (1.6 KiB) TX bytes:2021 (1.9 KiB)

Interrupt:209 Base address:0x2000




eth1 Link encap:Ethernet HWaddr 00:0F:B3:2A:41:AF

inet addr:192.168.0.3 Bcast:192.168.0.255 Mask:255.255.255.0

inet6 addr: fe80::20f:b3ff:fe2a:41af/64 Scope:Link

UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1

RX packets:17 errors:1 dropped:0 overruns:0 frame:1

TX packets:31 errors:0 dropped:0 overruns:0 carrier:0

collisions:0 txqueuelen:1000

RX bytes:2344 (2.2 KiB) TX bytes:4475 (4.3 KiB)




lo Link encap:Local Loopback

inet addr:127.0.0.1 Mask:255.0.0.0

inet6 addr: ::1/128 Scope:Host

UP LOOPBACK RUNNING MTU:16436 Metric:1

RX packets:5 errors:0 dropped:0 overruns:0 frame:0

TX packets:5 errors:0 dropped:0 overruns:0 carrier:0

collisions:0 txqueuelen:0

RX bytes:272 (272.0 b) TX bytes:272 (272.0 b)

---

### Post by gradedcheese on 2007-03-04
Ok, this shows us that you have two interfaces, eth0 and eth1.  eth0 got the address 192.168.1.100 from the router (most routers give out .100 as the first DHCP address, good news).  The second one has 192.168.0.3 for whatever reason.  Does your PC have two network cards?  So, what doesn't work?  Perhaps you don't have DNS?  What does /etc/resolv.conf contain?  You can try replacing its contents as follows to use opendns instead:

```

search opendns.com
nameserver 208.67.222.222
nameserver 208.67.220.220

```

---

