---
title: "Different 2nd nic card problem"
date: 2006-08-14
forum: Networking &amp; Wireless
---

### Post by Dan Luevano on 2006-08-14
I've checked the forum for an answer to my question but can't seem to locate what I need.

SETUP: I've got ubuntu 6.06 installed with 2 nic cards, eth0 is on a switch with a DHCP assigned IP, and eth1 is on a router with a static IP assigned.

PROBLEM: when I have both nic cards UP, I cannot ping eth1 from outside the network. If I bring eth0 down, I can then ping eth1 from outside the network.

It seems as though when eth0 is UP, eth1 does not service any requests. I must be missing something in my configuration, although independently they work fine. Can anyone point me in the right direction or have an idea of what to try?

Thanks,

Dan Luevano

---

### Post by foolsh on 2006-08-14
are you trying to bridge the connections and ping "through" the computer to the external/internal network.
I dont really know what your asking here 
if your trying to setup some kind of internet connection sharing then a really easy way to do this is with firestarter on the first run it asks you some questions on how to setup your network and helps you configure connection sharing but i noticed you still have to tell it to allow connections from your internal network

---

### Post by Dan Luevano on 2006-08-14
no, this is not connection sharing. I've got two nic cards on the box, one (eth0) is connected to a local network (with a DHCP assigned IP), the other (eth1) is connected to the internet via a static IP.

it's strange because if I disable eth0, then I can reach my box via the internet by hitting the static ip, but if enable eth0, then the 2nd nic card (eth1) stops responding immediately, and then i can only access the box via the 1st nic card (eth0) -- locally.

---

### Post by Dan Luevano on 2006-08-16
I just noticed something else...that my eth1 card is coming up as HALF-DUPLEX instead of FULL-DUPLEX...see dmesg output below:

dluevano:~\ > ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:10:B5:9C:21:63
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:2456 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1307 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:291374 (284.5 KiB)  TX bytes:161391 (157.6 KiB)
          Interrupt:5 Base address:0x2000

eth1      Link encap:Ethernet  HWaddr 00:4F:4A:17:57:6A
          inet addr:72.54.107.147  Bcast:72.54.107.151  Mask:255.255.255.248
          inet6 addr: fe80::24f:4aff:fe17:576a/64 Scope:Link
          UP BROADCAST RUNNING PROMISC MULTICAST  MTU:1500  Metric:1
          RX packets:7576395 errors:0 dropped:0 overruns:0 frame:0
          TX packets:50331 errors:0 dropped:0 overruns:0 carrier:0
          collisions:310 txqueuelen:1000
          RX bytes:948063820 (904.1 MiB)  TX bytes:18595664 (17.7 MiB)
          Interrupt:10 Base address:0x6000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:82 errors:0 dropped:0 overruns:0 frame:0
          TX packets:82 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:6763 (6.6 KiB)  TX bytes:6763 (6.6 KiB)

sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

dluevano:~\ > dmesg |grep eth0
[42949393.780000] eth0: RealTek RTL8139 at 0xe8866000, 00:4f:4a:17:57:6a, IRQ 10
[42949393.780000] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[42949397.400000] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[42949413.570000] eth0: no IPv6 routers present
[42952220.610000] eth0: link down
[42952646.740000] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[42952996.390000] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[42953006.970000] eth0: no IPv6 routers present
[42953224.370000] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[42953235.120000] eth0: no IPv6 routers present
[42956182.900000] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[42956192.910000] eth0: no IPv6 routers present
dluevano:~\ > dmesg |grep eth1
[42949393.780000] eth1: RealTek RTL8139 at 0xe88a2000, 00:10:b5:9c:21:63, IRQ 5
[42949393.780000] eth1:  Identified 8139 chip type 'RTL-8139B'
[42949396.560000] eth1: link up, 100Mbps, half-duplex, lpa 0x40A1
[42949396.930000] eth1: Promiscuous mode enabled.
[42949396.930000] device eth1 entered promiscuous mode
[42949402.840000] eth1: Promiscuous mode enabled.
[42949402.840000] eth1: Promiscuous mode enabled.
[42949413.130000] eth1: no IPv6 routers present


Currently my eth0 card is disabled because whenever I enable it my eth1 card stops working....

**QUESTION: How do you manage whether the NIC card is UP as FULL-DUPLEX vs. HALF-DUPLEX?  Is there a command to manually set this? I don't see one in 'man interfaces'.**

---

