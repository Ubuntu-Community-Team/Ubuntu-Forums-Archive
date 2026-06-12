---
title: "[SOLVED] Can't connect to the internet with my Wireless Blitzz Router"
date: 2008-01-01
forum: Networking &amp; Wireless
---

### Post by anti-loop on 2008-01-01
Hi guys,

I have search through the forums here and tried some of the procedures posted by other members, but could not connect to the internet. I was hoping if someone could provide some assistance that could possibly get my internet working with Ubuntu.

My router is a Blitzz Netwave Base II model BWA6115B. The cable modem and computer is connected directly to the router. It works fine in Windows XP but not in Ubuntu. I have tried setting it up as a static address but still yield the same results.

Here is the info I have collected. If there is something I forgot to post let me know. Any help would be appreciated. Thanks in advance!

------------------------

ifconfig:

[B]
eth0  Link encap:Ethernet HWaddr 00:20:78:07:81:9A
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:1 overruns:0 frame:0
TX packets:0 errors:122 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0b) TX bytes:0 (0.0b)
Interrupt:6 Base address:0xa400

eth0:avah Link encap:Ethernet HWaddr 00:20:78:07:91:9A
inet addr:169.254.6.44 Bcast:169.254.255.255 Mask:255.255.0.0
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
Interrupt:6 Base address:0xa400

lo: Link encap:Local Loopback
inet addr:127.0.0.1 Mask: 255.0.0.0
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:567 errors:0 dropped:0 overruns:0 frame:0
TX packets:567 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:43516 (42.4 KB) TX bytes:43516 (42.4 KB)
[/B]

iwconfig:

[B]
lo no wireless extensions.

eth0 no wireless extensions.
[/B]

lshw -C network:

[B]
*-network
description:Ethernet interface
product: NC100 Network Everywhere Fast Ethernet 10/100
vendor: ADMtek
physical id: 9
bus info: pci@0000:00:09.0
logical name: eth0
version: 11
serial: 00:20:78:07:91:9a
width 32 bits
clock 33MHz
capabilities: pm bus_master cap_list ethernet physical
configuration: broadcast=yes driver=tulip driverversion=1.1.15 latency=32 maxlatency=255
mingnt=255 module=tulip multicast=yes

[/B]

/etc/network/interfaces:

[B]
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp
[/B]

/etc/init.d/networking restart:

[B]
*Reconfiguring network interfaces...                                       There is already a pid
file /var/run/dhclient.eth0.pid with pid 6091
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:20:78:07:81:9a
Sending on LPF/eth0/00:20:78:07:81:9a
Sending on Socket/fallback
There is already a pid file /var/run/dhclient.eth0.pid with pid 134519120
Internet Systems Consortium DHCP Client V3.0.5
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:20:78:07:81:9a
Sending on LPF/eth0/00:20:78:07:81:9a
Sedning on Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
grep: /etc/resolve.conf: No such file or directory
[/B]

When looking into /etc/resolv.conf it is a blank file. I noticed in other posts that it contains the following lines:
nameserver xxx.xxx.xxx.xxx

route:

[B]
Kernel IP routing table
Destination   Gateway   Genmask   Flags   Metric   Ref   Use   Iface
link-local          *        255.255.0.0    U         0          0        0     eth0
default            *        0.0.0.0            U       1000      0        0     eth0
[/B]

iwlist eth0 scan:

[B]
eth0 Interface doesn't support scanning
[/B]

cat/proc/net/dev:

[B]
Inter-|  Receive                                    | Transmit
face|bytes   packets errs drop fifo frame compressed multicast|bytes      packets errs drop fifo colls
carrier compressed
lo:   45876   597   0   0   0   0     0   0   45876   597   0   0   0   0   0   0
eth0:  0   0   0   1   0   0     0   0   0   0   154   0   0   0  0   0
[/B]

-------------------
Static Setup

/etc/interfaces/network:

[B]
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.1.19
netmask 255.255.255.0
broadcast 192.168.1.255
network 192.168.1.0
gateway 192.168.1.1
[/B]

/etc/init.d/networking restart:

[B]
*Reconfiguring network interfaces...     SIOCDELRT: No such process
grep: /etc/resolv.conf: No such file or directory
                                                                      [OK]
[/B]

ping 192.168.1.10:

[B]
PING 192.168.1.10 (192.168.1.10) 56(84) bytes of data
64 bytes from 192.168.1.10: icmp_seq=1 ttl=64 time=0.091 ms

[/B]

route:

[B]
Kernel IP routing table
Destination   Gateway   Genmask   Flags   Metric   Ref   Use   Iface
192.168.1.0   *      255.255.255.0  U           0        0        0     eth0
link-local          *        255.255.0.0    U        1000     0        0     eth0
default      192.168.1.1  0.0.0.0      UG       100      0        0     eth0
[/B]
------------------------------------

I have also tried to install a dhcp/dhcp3 server but get the following error message

sudo apt-get install dhcp3-server/dhcpd:

[B]
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package dhcp3-server/dhcpd
[/B]

---

### Post by anti-loop on 2008-01-02
bump.

---

### Post by anti-loop on 2008-01-03
bump bump. Any suggestions?

---

### Post by anti-loop on 2008-01-04
last bump. Still no luck. Could I be missing something?

---

### Post by anti-loop on 2008-01-13
I have figured out the solution to my problem. Here is what I did:

I replaced my old network card with a new one (Linksys LNE100TX).

When I used the LiveCD to boot up I typed in ifconfig and the addresses was automatically assigned (this did not occur before) and eth0:avah was not listed. I tested it out and was able to surf the internet successfully. But then I realized my sound card wasn't working since it had the red circle sign on it.

Looking at the sound card it was loose, I pushed it back into the PCI slot. Upon booting up with the LiveCD again my original problem came up again, where no addresses were assigned. I also received the eth0:avah in the list again when I typed in ifconfig.

It seems like Linux detects the sound card as another network device or a IRQ sharing conflict. I do not encounter this problem in Windows though.

I switched the sound card into another PCI slot and the problem went away. I performed a fresh install and now internet is operating in Ubuntu.

I hope this will help others that might experience a similar problem.

---

