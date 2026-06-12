---
title: "No DHCP for Linksys WAP54G &amp; Gutsy Gibbon Server"
date: 2007-11-06
forum: Networking &amp; Wireless
---

### Post by DrJohn999 on 2007-11-06
We have 2 laptops, both of which have no problem with DCHP at other sites with other access points. If the laptop wireless card is configured with a fixed-IP address, no problems with the Linux server at this location. But, when I try to use DHCP with either laptop at this location with the Linux server, I see no DHCP traffic for the eth2 interface that has the WAP54G attached. There's plenty of valid DHCP traffic on the internal wired interface (eth0).

I'm running Gutsy Gibbon with Shorewall and dhcp3. The WAP54G is running WEP/TKIP, but there's no problem with connecting to it -- it's the DHCP part that's messed up for Linux -- the WAP54G passes DHCP traffic just fine if I run it off a WinXP box instead.

Main Questions: 1) is the problem with the Linksys box or the Linux configuration? and 2) what's wrong?

The WAP54G is running f/w v.2.08; mac filtering; WEP/TKIP; It's static IP is 192.168.3.245.

Here's some Linux configuration info (for the wireless portion; real names have been changed):
[FONT="Courier New"]$ifconfig
:
:
[INDENT]eth2      Link encap:Ethernet  HWaddr 00:10:5A:2A:21:44
          inet addr:192.168.3.1  Bcast:192.168.3.255  Mask:255.255.255.0
          inet6 addr: fe80::210:5aff:fe2a:2144/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10305 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10410 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1659319 (1.5 MB)  TX bytes:10058981 (9.5 MB)
          Interrupt:22 Base address:0x6000
[/INDENT]


$ cat /etc/network/interfaces
:
:
[INDENT]#The wireless interface
auto eth2
iface eth2 inet static
        address 192.168.3.1
        netmask 255.255.255.0
        network 192.168.3.0
        broadcast 192.168.3.255
[/INDENT]


$cat /etc/dhcp3/dhcpd.conf
[INDENT]ddns-update-style none;
option domain-name "mydomain.net";
option domain-name-servers mysys.mydomain.net;

default-lease-time 600;
max-lease-time 7200;
authoritative;
log-facility local7;

# A slightly different configuration for an internal subnet.
subnet 192.168.2.0 netmask 255.255.255.0 {
  range 192.168.2.200 192.168.2.250;
  option domain-name-servers mysys.mydomain.net;
  option domain-name "mydomain.net";
  option routers 192.168.2.254;
  option broadcast-address 192.168.2.255;
  default-lease-time 600;
  max-lease-time 7200;
}
subnet 192.168.3.0 netmask 255.255.255.0 {
  range 192.168.3.2 192.168.3.63;
  option domain-name-servers mysys.mydomain.net;
  option domain-name "mydomain.net";
  option routers 192.168.3.1;
  option broadcast-address 192.168.3.255;
  default-lease-time 600;
  max-lease-time 7200;
}

#Print server @ fixed IP addr
host NPI4255B7 {
  hardware ethernet 00:0E:7F:42:55:B7;
  fixed-address 192.168.2.253;
}[/INDENT]

$cat /etc/shorewall/zones
[INDENT]#ZONE   TYPE    OPTIONS                 IN                      OUT
#                                       OPTIONS                 OPTIONS
fw      firewall
net     ipv4
loc     ipv4
[/INDENT]

$ cat /etc/shorewall/interfaces
[INDENT]#ZONE   INTERFACE       BROADCAST       OPTIONS
net     eth1            detect          tcpflags,routefilter,nosmurfs,logmartians
loc     eth0            detect          dhcp,tcpflags,detectnets,nosmurfs
loc     eth2            detect          dhcp,tcpflags,detectnets,nosmurfs
[/INDENT]

$cat /etc/shorewall/masq
[INDENT]#INTERFACE              SUBNET          ADDRESS         PROTO   PORT(S) IPSEC
eth1                    eth0            detect
eth1                    eth2            detect
[/INDENT]
[/FONT]


Thanks for your help!

DrJohn

---

### Post by DrJohn999 on 2007-11-06
Update: 

It's not the wireless access point itself, it's DHCP not showing up on the interface. 

If I exchange the network cables for eth0 (first local ethernet card) with eth2 (other local ethernet card, eth1 is the external connection to the internet), then I get DCHP on the wireless and not on the wired LAN leg.

So, the question now is: Why does DHCP work only on eth0 and not on eth2??

Thanks,

DrJohn

---

