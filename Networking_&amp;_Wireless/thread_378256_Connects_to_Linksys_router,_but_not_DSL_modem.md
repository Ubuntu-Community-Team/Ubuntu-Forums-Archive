---
title: "Connects to Linksys router, but not DSL modem"
date: 2007-03-07
forum: Networking &amp; Wireless
---

### Post by justinux on 2007-03-07
I have tried a lot of the suggestions concerning this issue (including disabling ipv6), but still can not connect. Here is my situation:

I have a DSL modem connected to a wireless router's uplink connection (acting as a switch).

In windows, I can connect to both the modem (192.168.1.1) and the router (192.168.1.2), the DNS/gateway is 192.168.1.1 and everything connects fine.

In ubuntu, on the same laptop, I can only connect to the router, it never makes it to the modem. It seems like ubuntu doesn't see the router as a switch and does not even try to find the modem. The router, however, does not have DHCP enabled and ubuntu gets all its network settings from the modem. DNS is set to the modem (192.168.1.1).

Even after the modem sets all the network settings (IP, SubNet Mask, Gateway, DNS) I still can only hit the router, which is just acting as a switch.

Below is my ifconfig and cat /etc/resolv.conf outputs:

> justin@xantu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 08:00:46:6A:1A:F6
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

eth1      Link encap:Ethernet  HWaddr 00:02:2D:6D:BF:6A
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:486 errors:0 dropped:0 overruns:0 frame:0
          TX packets:619 errors:6 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:289122 (282.3 KiB)  TX bytes:98620 (96.3 KiB)
          Interrupt:9 Base address:0x3040

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:32 errors:0 dropped:0 overruns:0 frame:0
          TX packets:32 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:4556 (4.4 KiB)  TX bytes:4556 (4.4 KiB)

justin@xantu:~$ cat /etc/resolv.conf
nameserver 192.168.1.1



Any ideas?
Thanks
-Justin

---

### Post by justinux on 2007-03-07
NEVERMIND
I ended up changing the IP of the router to something different and.. well.. I'm using ubuntu now!

Horray!

---

