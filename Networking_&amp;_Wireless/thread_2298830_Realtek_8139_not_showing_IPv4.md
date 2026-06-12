---
title: "Realtek 8139 not showing IPv4"
date: 2015-10-14
forum: Networking &amp; Wireless
---

### Post by ice-simx on 2015-10-14
the eth0 (Realtek 8139) is not showing IPv4, and not detecting cable.


root@host:~# ifconfig
eth0      Link encap:Ethernet  HWaddr 00:e0:4a:0a:51:85
          inet6 addr: fe80::2e0:4aff:fe0a:5185/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2630 errors:0 dropped:27 overruns:0 frame:0
          TX packets:26 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:216574 (216.5 KB)  TX bytes:4253 (4.2 KB)

eth1      Link encap:Ethernet  HWaddr ec:b1:d7:2b:33:27
          inet addr:172.17.63.205  Bcast:172.17.63.255  Mask:255.255.248.0
          inet6 addr: fe80::eeb1:d7ff:fe2b:3327/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:14336 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1031 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1755019 (1.7 MB)  TX bytes:207450 (207.4 KB)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:297 errors:0 dropped:0 overruns:0 frame:0
          TX packets:297 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:47081 (47.0 KB)  TX bytes:47081 (47.0 KB)


# netstat -i
Kernel Interface table
Iface   MTU Met   RX-OK RX-ERR RX-DRP RX-OVR    TX-OK TX-ERR TX-DRP TX-OVR Flg
eth0       1500 0      3435      0     36 0            27      0      0      0 BMRU
eth1       1500 0     18178      0      0 0          1141      0      0      0 BMRU
lo        65536 0       297      0      0 0           297      0      0      0 LRU


# grep eth0 /var/log/syslog
Oct 13 22:01:55 hostname kernel: [    0.842419] 8139too 0000:05:00.0 eth0: RealTek RTL8139 at 0x000000000001d000, 00:e0:4a:0a:51:85, IRQ 16
Oct 13 22:01:59 hostname NetworkManager[850]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.4/0000:04:00.0/0000:05:00.0/net/eth0, iface: eth0)
Oct 13 22:01:59 hostname NetworkManager[850]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.4/0000:04:00.0/0000:05:00.0/net/eth0, iface: eth0): no ifupdown configuration found.
Oct 13 22:02:00 hostname NetworkManager[850]: <info> (eth0): carrier is OFF
Oct 13 22:02:00 hostname NetworkManager[850]: <info> (eth0): new Ethernet device (driver: '8139too' ifindex: 2)
Oct 13 22:02:00 hostname NetworkManager[850]: <info> (eth0): exported as /org/freedesktop/NetworkManager/Devices/1
Oct 13 22:02:00 hostname NetworkManager[850]: <info> (eth0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Oct 13 22:02:00 hostname NetworkManager[850]: <info> (eth0): bringing up device.
Oct 13 22:02:00 hostname NetworkManager[850]: <info> (eth0): carrier now ON (device state 20)
Oct 13 22:02:00 hostname NetworkManager[850]: <info> (eth0): preparing device.
Oct 13 22:02:00 hostname NetworkManager[850]: <info> (eth0): deactivating device (reason 'managed') [2]
Oct 13 22:02:00 hostname NetworkManager[850]: <info> (eth0): device state change: unavailable -> disconnected (reason 'none') [20 30 0]
Oct 13 22:02:00 hostname kernel: [   22.603706] 8139too 0000:05:00.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
Oct 13 22:02:01 hostname avahi-daemon[785]: Joining mDNS multicast group on interface eth0.IPv6 with address fe80::2e0:4aff:fe0a:5185.
Oct 13 22:02:01 hostname avahi-daemon[785]: New relevant interface eth0.IPv6 for mDNS.
Oct 13 22:02:01 hostname avahi-daemon[785]: Registering new address record for fe80::2e0:4aff:fe0a:5185 on eth0.*.

---

### Post by ice-simx on 2015-10-14
its solved, just give static manual ip and it works :)

---

### Post by Bucky Ball on 2015-10-14
*Thread moved to **Networking & Wireless**.*

Good work and thanks for sharing. Please use code tags for future terminal text (see last link in my signature). Cheers and good luck. :)

---

