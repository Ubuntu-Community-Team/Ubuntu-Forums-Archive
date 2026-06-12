---
title: "Detected Intel PRO/Wireless 3945ABG Network
Connection -- Network is unreachable"
date: 2006-08-29
forum: Networking &amp; Wireless
---

### Post by Andrew Olney on 2006-08-29
I've been trying to get the 3945 / ipw3945 adapter to work for me, but with some strange results.

For example, iwconfig gives

eth1      IEEE 802.11b  ESSID:"uofm"
          Mode:Managed  Frequency:2.447 GHz  Access Point:
00:02:2D:89:99:FB
          Bit Rate:11 Mb/s   Tx-Power:15 dBm
          Retry limit:15   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=73/100  Signal level=-61 dBm  Noise level=-62 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:1595   Missed beacon:0

When all lines are commented out of /etc/network/interfaces except lo

If I add to /etc/network/interfaces the following line

iface eth1 inet dhcp

And then run ifup:

aolney@monkamu:~$ sudo ifup eth1
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth1/00:13:02:9b:db:14
Sending on   LPF/eth1/00:13:02:9b:db:14
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
DHCPOFFER from 141.225.40.2
DHCPREQUEST on eth1 to 255.255.255.255 port 67
DHCPACK from 141.225.40.3
SIOCADDRT: Network is unreachable
bound to 10.2.41.21 -- renewal in 1405 seconds.

What I don't understand is why I get an IP address and "SIOCADDRT:
Network is unreachable" at the same time.

Subsequent calls to ifconfig show that I am receiving packets from the
network.

aolney@monkamu:~$ ifconfig eth1
eth1      Link encap:Ethernet  HWaddr 00:13:02:9B:DB:14
          inet addr:10.2.41.21  Bcast:10.2.41.255  Mask:255.255.255.0
          inet6 addr: fe80::213:2ff:fe9b:db14/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:29550 errors:0 dropped:1597 overruns:0 frame:0
          TX packets:20 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:923343 (901.7 KiB)  TX bytes:3084 (3.0 KiB)
          Interrupt:74 Base address:0xa000 Memory:edf00000-edf00fff

Dmesg shows that the right kinds of things (drivers) are being loaded at
startup:

[17179592.924000] ipw3945: Intel(R) PRO/Wireless 3945 Network Connection
driver for Linux, 1.0.5m
[17179592.924000] ipw3945: Copyright(c) 2003-2006 Intel Corporation
[17179593.136000] ipw3945: Detected Intel PRO/Wireless 3945ABG Network
Connection
[17179594.520000] ipw3945: Detected geography ABG (11 802.11bg channels,
13 802.11a channels)

But there might be a problem with the PCI. lspci gives (among other
things) this:

0000:03:00.0 Network controller: Intel Corporation: Unknown device 4227
(rev 02)

I'm wondering if the problem is that the 1.0.5m driver can't quite figure out pci express.

Other general config info:

Linux version 2.6.15-26-686 (buildd@terranova) (gcc version 4.0.3
(Ubuntu 4.0.3-1ubuntu5)) #1 SMP PREEMPT Thu Aug 3 03:13:28 UTC 2006

and I'm using Ubuntu Dapper 6.06


Any suggestions?

---

### Post by Andrew Olney on 2006-09-01
OK, I figured it out. Thanks to Thierry Nicola for first suggesting it might be a router problem.

I'm at a University where IP addressed are assigned via dhcp based on
MAC address.

The first time a user connects, they must register their machine with
their University password and username.

I brought in another laptop running XP to see what kind of information
it had about gateways, etc.

Before I register it, it is connecting to 10.2.41.63.

After I register it, it's connecting (without effort) to the normal
University address range (141.225.0.0-141.225.255.255).

I can use the XP laptop's IP address as a static address on my linux
laptop and then connect to the internet without difficulty (using the
linux laptop).

But that clearly wasn't good enough :)

I de-registered the XP machine, then successfully pinged its gateway
10.2.252.5 (which is the website for network registration). I knew before about this gateway b/c NetworkManager was listing it on my linux box.

I noticed that I couldn't ping the same site on my linux box using the
IP address assigned by dhcp (10.2.41.21).

So that brought me back to the routing table.

I think what makes this a little tricky is that the registration site
and the IP address assigned are not locally connected (i.e. the last two
octets of the IP addresses are different, 252.5 vs 41.21).

So I added the last two lines to the routing table. The first line was
already there (supplied I guess by the temp network dhcp)

aolney@monkamu:~$ route
Kernel IP routing table
Destination Gateway     Genmask         Flags Metric Ref    Use Iface
10.2.41.0    *          255.255.255.0   U     0      0        0 eth1
10.2.252.0   10.2.252.5 255.255.255.0   UG    0      0        0 eth1
10.2.252.0   *          255.255.255.0   U     0      0        0 eth1

And then I could ping into the other network. In fact, then I could go
to the website and register.

When I ifdown eth1 and ifup eth1, I get a new "real" university assigned
IP address in the 141.225.0.0 range, and my routing table is no longer
retarded.

I suppose the dhcp somehow refreshes the IP routing table with correct
values, and that the temporary values given before registration were
somehow an error on the network admin's part.

---

