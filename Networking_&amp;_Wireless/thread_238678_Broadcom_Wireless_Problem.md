---
title: "Broadcom Wireless Problem"
date: 2006-08-18
forum: Networking &amp; Wireless
---

### Post by scapps on 2006-08-18
I have a Compaq R3240 laptop with AMD 64 chip using the broadcom wireless card:  Broadcom Corporation BCM4306 802.11b/g Wireless                                                                                      LAN Controller (rev 03)

I see it when I run lspci.

Here is the output from iwconfig:

lo        no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:"Manchester"  Nickname:"Broadcom 4306"
          Mode:Managed  Frequency=2.437 GHz  Access Point: 00:30:BD:F1:B2:2D
          Bit Rate=11 Mb/s   Tx-Power=15 dBm
          RTS thr:off   Fragment thr:off
          Link Quality=100/100  Signal level=3/3  Noise level=14/100
          Rx invalid nwid:0  Rx invalid crypt:1243  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

sit0      no wireless extensions.



Output from ifconfig:
eth0      Link encap:Ethernet  HWaddr 00:0F:B0:01:FC:9A
          inet addr:192.168.2.4  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::20f:b0ff:fe01:fc9a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9156 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9297 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:6863389 (6.5 MiB)  TX bytes:1221214 (1.1 MiB)
          Interrupt:185 Base address:0xe800

eth1      Link encap:Ethernet  HWaddr 00:90:4B:59:39:1E
          inet6 addr: fe80::290:4bff:fe59:391e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:880 errors:0 dropped:1286 overruns:0 frame:0
          TX packets:164 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:290035 (283.2 KiB)  TX bytes:35855 (35.0 KiB)
          Interrupt:11 Base address:0x8000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:172 (172.0 b)  TX bytes:172 (172.0 b)


My wireless router is using 64-bit WEP.  I just can't surf the web with the wireless.  Any help would be appreciated.

Thanks.](*,)

---

