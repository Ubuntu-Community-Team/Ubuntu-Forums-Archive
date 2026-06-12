---
title: "Edgy and rt61 problem with RaLink chipset"
date: 2006-11-01
forum: Networking &amp; Wireless
---

### Post by layl on 2006-11-01
Hello,

followed the instructions (worked perfectly on DD until upgrade to EE) to run my wifi card.  Since the upgrade messed my laptop up, I reinstalled EE from CD.  Followed the instructions again, wifi card lights status LED up, but does not allow any network connections.  See output below :
$ifconfig
ra0 Link encap:Ethernet HWaddr 00:08:A1:A1:BE:05
inet addr:192.168.1.6 Bcast:192.168.1.255 Mask:255.255.255.0
inet6 addr: fe80::208:a1ff:fea1:be05/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:304 errors:0 dropped:0 overruns:0 frame:0
TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
collisions:1 txqueuelen:1000
RX bytes:31884 (31.1 KiB) TX bytes:131 (131.0 b)
Interrupt:11

$iwconfig
ra0 RT61 Wireless ESSID:"SWEET_HOME_ALABAMA"
Mode:Managed Frequency:2.422 GHz Access Point: 00:C0:02:E7:D3:D2
Bit Rate=54 Mb/s
RTS thr:off Fragment thr:off
Encryption key : only found after additional $ifconfig ra0 down/up
Link Quality=85/100 Signal level:-50 dBm Noise level:-79 dBm
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0

$route
Kernel IP routing table
Destination Gateway Genmask Flags Metric Ref Use Iface
192.168.1.0 * 255.255.255.0 U 0 0 0 ra0
default 192.168.1.1 0.0.0.0 UG 0 0 0 ra0

$dmesg | grep rt61
[17179596.384000] rt61 1.1.0 CVS CVS [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com)

$dmesg | grep ra0
[17179640.740000] ra0 (WE) : Driver using old /proc/net/wireless support, please fix driver !
[17179666.564000] ra0: no IPv6 routers present

$ping 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
From 192.168.1.6 icmp_seq=2 Destination Host Unreachable 

Same routing table with eth0 up works perfectly fine, so I assume it's not a routing problem.  Anyone any ideas ?

---

