---
title: "Configuration setup for ICS on wireless NIC?"
date: 2007-02-14
forum: Networking &amp; Wireless
---

### Post by mitsos on 2007-02-14
I'm running 6.06 on my desktop pc and I've been trying to setup a wireless connection to a laptop using the Ralink RT2500 802.11 card (interface ra0) installed and working properly on my desktop. 
I know it is working because the laptop picks up the signal but it cannot connect/obtain IP or share the internet connection. Moreover (i hated finding this out but i can't hide it), the desktop is a dual boot with xp as a second boot option and with xp everything works. After following the firewall section guide of [http://www.isc.org/index.pl?/sw/dhcp/]("http://www.isc.org/index.pl?/sw/dhcp/") to set up the firewall on the dsl modem to allow dhcp queries the two pcs got connected.

The other component in the network is my dsl modem. It is connected to my desktop via an ethernet card (interface eth0).
The modem's IP is  10.0.0.2
The desktop's IP is 10.0.0.11

I have instqalled dhcpd3 but never managed to start it successfully for my wireless interface.

Q1) Do I need dhcpd3 in the first place?

This is my ifconfig output:
```
$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:14:85:B4:E8:AC
          inet addr:10.0.0.11  Bcast:255.255.255.255  Mask:255.0.0.0
          inet6 addr: fe80::214:85ff:feb4:e8ac/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4677 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4879 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:3245328 (3.0 MiB)  TX bytes:1018934 (995.0 KiB)
          Interrupt:185 Base address:0x6000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:11 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:572 (572.0 b)  TX bytes:572 (572.0 b)

ra0       Link encap:Ethernet  HWaddr 00:50:18:3C:89:90
          inet addr:192.168.0.1  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::250:18ff:fe3c:8990/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:165510 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:7613460 (7.2 MiB)
          Interrupt:185 Base address:0x4000

sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
```
and this is my iwconfig output:
```
$ iwconfig
lo        no wireless extensions.

ra0       RT2500 Wireless  ESSID:"fytili"
          Mode:Managed  Frequency=2.412 GHz  Bit Rate:11 Mb/s   Tx-Power:0 dBm
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level=-120 dBm  Noise level:-192 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

sit0      no wireless extensions.
```

Another file that bothers me is **/etc/dhcp3/dhcpd.conf**:
```
$ cat /etc/dhcp3/dhcpd.conf
# Sample /etc/dhcpd.conf
default-lease-time 2100;
max-lease-time 8400;
option subnet-mask 255.255.255.0;
option broadcast-address 192.168.0.255;
#option routers 192.168.0.1;
#option domain-name-servers 192.168.0.1;

#subnet 192.168.0.0 netmask 255.255.255.0 {
#range 192.168.0.2 192.168.0.254;
#}

subnet 192.168.0.0 netmask 255.255.255.0 {}
```

As you can imagine i have tried many things, i've no idea what it takes to make dhcp server to run correctly. The output when i try to start dhcpd3 is:
```
$ sudo dhcpd3 ra0
Internet Systems Consortium DHCP Server V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/
Wrote 0 leases to leases file.
Listening on LPF/ra0/00:50:18:3c:89:90/192.168.0/24
Sending on   LPF/ra0/00:50:18:3c:89:90/192.168.0/24
Sending on   Socket/fallback/fallback-net
```

Q2) Should I worry that a manual ra0 configuration through iwconfig has no effect on the network properties? The only thing i can do is change some setting with the System->Administration->Networking tool. But the gui does not offer many options so i cannot experiment a lot.

Q3) How should I find out what's wrong?

Q4) Is it possible to have Internet Connection Sharing between these two machines?

Q5) Do i necessarily need samba on the laptop?

cheers!

---

