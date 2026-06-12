---
title: "Connection problem"
date: 2006-10-10
forum: Networking &amp; Wireless
---

### Post by dutchmega on 2006-10-10
Hey,

A new user of Ubuntu here. I've been playing around with Ubuntu in Vmware and I liked what I saw so far, so I decided to do a dual-boot with Ubuntu.

Anyway, about my problem: I don't get a connection to the internet. My computername is correct and I don't have any routers or switches. The 3 ethernet devices (modem + 2 ethernet) are all configured and set to DHCP. I can't even ping to my gateway. I also removed IPv6, according to the other topics but that doesn't change anything. All pings fail...

The 2 ethernet controllers are:
02:08.0 Ethernet controller: 3Com Corporation 3c900B-TPO Etherlink XL [Cyclone] (rev 04)
02:0d.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet (rev 10)

I don't have the output of ifconfig but all the ethernet devices are in there and eth2 is receiving packets.

It doesn't really matter which one is used but currently I'm using the Realtek.

Problem is both on Ubuntu 6.06 64-bit and Ubuntu 6.10 32-bit

---

### Post by mips on 2006-10-10
Is the realtek a 8139 or 8169. Do a search here for 8139 and you will find many posts.

What hardware are you using, modem/router model etc ???
How is the above hardware configured ???

[http://doc.gwos.org/index.php/DisableIPV6](http://doc.gwos.org/index.php/DisableIPV6)
[http://www.ubuntuforums.org/showthread.php?t=78337](http://www.ubuntuforums.org/showthread.php?t=78337) 

1. Please post output of **ifconfig eth0**  (Depends on your interface number)
2. Please post output of **lspci | grep Eth**
3. Please post output of **route -n**
4. Please post output of **cat /etc/resolv.conf**
5. Please post output of **cat /etc/network/interfaces**
6. Please post output of **cat /etc/dhcp3/dhclient.conf**
7. Please copy **entire** output of windows **ipconfig /all** command here
8. Who is your ISP and provide a web link.
[I]
If you are dual-booting install the **ext2ifs** driver in windows and access your ext2/3 partions in linux from windows if you want to transfer data across in order to paste here. Alternatively use a usb memory stick or stiffy disk.[/I]

---

### Post by dutchmega on 2006-10-11
It's a Realtek 8169. I don't have a router.
Also, I have cable with an Arris modem, with @Home in Europe.

Note: I'm currently using the 3com, which is Eth1 but the Realtek is better I suppose ;)

1. ifconfig eth1
```
eth1      Link encap:Ethernet  HWaddr 00:50:04:EE:4B:CD  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2474 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:150365 (146.8 KiB)  TX bytes:4104 (4.0 KiB)
          Interrupt:225 Base address:0x4000
```

2. lspci | grep Eth
```
00:05.0 Bridge: nVidia Corporation CK8S Ethernet Controller (rev a2)
02:08.0 Ethernet controller: 3Com Corporation 3c900B-TPO Etherlink XL [Cyclone] (rev 04)
02:0d.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet (rev 10)
```

3. route -n
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface

```

4. /etc/resolv.conf doesn't exists

5. /etc/network/interfaces
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
```

6. /etc/dhcp3/dhclient.conf
```
# Configuration file for /sbin/dhclient, which is included in Debian's
#	dhcp3-client package.
#
# This is a sample configuration file for dhclient. See dhclient.conf's
#	man page for more information about the syntax of this file
#	and a more comprehensive list of the parameters understood by
#	dhclient.
#
# Normally, if the DHCP server provides reasonable information and does
#	not leave anything out (like the domain name, for example), then
#	few changes must be made to this file, if any.
#

#send host-name "andare.fugue.com";
#send dhcp-client-identifier 1:0:a0:24:ab:fb:9c;
#send dhcp-lease-time 3600;
#supersede domain-name "fugue.com home.vix.com";
#prepend domain-name-servers 127.0.0.1;
request subnet-mask, broadcast-address, time-offset, routers,
	domain-name, domain-name-servers, host-name,
	netbios-name-servers, netbios-scope, interface-mtu;
#require subnet-mask, domain-name-servers;
#timeout 60;
#retry 60;
#reboot 10;
#select-timeout 5;
#initial-interval 2;
#script "/etc/dhcp3/dhclient-script";
#media "-link0 -link1 -link2", "link0 link1";
#reject 192.33.137.209;

#alias {
#  interface "eth0";
#  fixed-address 192.5.5.213;
#  option subnet-mask 255.255.255.255;
#}

#lease {
#  interface "eth0";
#  fixed-address 192.33.137.200;
#  medium "link0 link1";
#  option host-name "andare.swiftmedia.com";
#  option subnet-mask 255.255.255.0;
#  option broadcast-address 192.33.137.255;
#  option routers 192.33.137.250;
#  option domain-name-servers 127.0.0.1;
#  renew 2 2000/1/12 00:00:01;
#  rebind 2 2000/1/12 00:00:01;
#  expire 2 2000/1/12 00:00:01;
#}
```

7. ethtool eth1
```
Settings for eth1:
	Supported ports: [ TP MII ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	Supports auto-negotiation: Yes
	Advertised link modes:  10baseT/Half 10baseT/Full 
	Advertised auto-negotiation: Yes
	Speed: 10Mb/s
	Duplex: Full
	Port: MII
	PHYAD: 24
	Transceiver: internal
	Auto-negotiation: on
	Current message level: 0x00000001 (1)
	Link detected: yes
```

8. dmesg | grep eth
```
[17179576.472000] forcedeth.c: Reverse Engineered nForce ethernet driver. Version 0.54.
[17179577.408000] eth0: forcedeth.c: subsystem: 01462:0250 bound to 0000:00:05.0
[17179586.588000] eth0: no link during initialization.
[17179586.752000] eth1: Identified chip type is 'RTL8169s/8110s'.
[17179586.752000] eth1: RTL8169 at 0xf8926000, 00:11:09:67:d1:53, IRQ 217
[17179586.796000] r8169: eth2: link down
[17179587.364000] eth1:  setting full-duplex.

```

9. Windows ipconfig /all
```
Windows IP-configuratie

        Host-naam  . . . . . . . . . . . .: CC1074988-A
        Primair DNS-achtervoegsel. . . . .:
        Knooppunttype: . . . . . . . . . .: onbekend
        IP-routering ingeschakeld. . . . .: nee
        WINS-proxy ingeschakeld . . . . . : nee
        DNS-achtervoegselzoeklijst. . . . : ENSCH1.OV.HOME.NL

Ethernet-adapter 3COM netwerkkaart:

        Verbindingsspec. DNS-achtervoegsel: ENSCH1.OV.HOME.NL
        Beschrijving . . . . . . . . . . .:
          3Com 3C900B-TPO Ethernet Adapter (Generic)
        Fysiek adres. . . . . . . . . . . : 00-50-04-EE-4B-CD
        DHCP ingeshakeld. . . . . . . . . : ja
        Autom. configuratie ingeschakeld. : ja
        IP-adres. . . . . . . . . . . . . : 217.123.173.97
        Subnetmasker. . . . . . . . . . . : 255.255.254.0
        IP-adres. . . . . . . . . . . . . : fe80::250:4ff:feee:4bcd%4
        Standaardgateway. . . . . . . . . : 217.123.172.1
        DHCP-server . . . . . . . . . . . : 213.51.129.90
        DNS-servers . . . . . . . . . . . : 213.51.129.37
                                            213.51.144.37
                                            fec0:0:0:ffff::1%2
                                            fec0:0:0:ffff::2%2
                                            fec0:0:0:ffff::3%2
        Lease verkregen . . . . . . . . . : woensdag 11 oktober 2006 8:01
        Lease verlopen . . . . . . . . .  : maandag 16 oktober 2006 16:31

Ethernet-adapter Realtek Gigabit:

        Status van medium . . . . . . . . : medium ontkoppeld
        Beschrijving . . . . . . . . . . .:
          Realtek RTL8169/8110 Family Gigabit Ethernet NIC
        Fysiek adres. . . . . . . . . . . : 00-11-09-67-D1-53

Tunnel-adapter Teredo Tunneling Pseudo-Interface:

        Verbindingsspec. DNS-achtervoegsel:
        Beschrijving . . . . . . . . . . .:
          Teredo Tunneling Pseudo-Interface
        Fysiek adres. . . . . . . . . . . : FF-FF-FF-FF-FF-FF-FF-FF
        DHCP ingeschakeld:. . . . . . . . : nee
        IP-adres. . . . . . . . . . . . . : fe80::5445:5245:444f%6
        Standaardgateway. . . . . . . . . :
        NetBIOS over TCPIP. . . . . . . . : uitgeschakeld

Tunnel-adapter 6to4 Tunneling Pseudo-Interface:

        Verbindingsspec. DNS-achtervoegsel: ENSCH1.OV.HOME.NL
        Beschrijving . . . . . . . . . . .:
          6to4 Tunneling Pseudo-Interface
        Fysiek adres. . . . . . . . . . . : D9-7B-AD-61
        DHCP ingeschakeld:. . . . . . . . : nee
        IP-adres. . . . . . . . . . . . . : 2002:d97b:ad61::d97b:ad61
        Standaardgateway. . . . . . . . . : 2002:c058:6301::c058:6301
        DNS-servers . . . . . . . . . . . : fec0:0:0:ffff::1%2
                                            fec0:0:0:ffff::2%2
                                            fec0:0:0:ffff::3%2
        NetBIOS over TCPIP. . . . . . . . : uitgeschakeld

Tunnel-adapter Automatic Tunneling Pseudo-Interface:

        Verbindingsspec. DNS-achtervoegsel: ENSCH1.OV.HOME.NL
        Beschrijving . . . . . . . . . . .:
          Automatic Tunneling Pseudo-Interface
        Fysiek adres. . . . . . . . . . . : D9-7B-AD-61
        DHCP ingeschakeld:. . . . . . . . : nee
        IP-adres. . . . . . . . . . . . . : fe80::5efe:217.123.173.97%2
        Standaardgateway. . . . . . . . . :
        DNS-servers . . . . . . . . . . . : fec0:0:0:ffff::1%2
                                            fec0:0:0:ffff::2%2
                                            fec0:0:0:ffff::3%2
        NetBIOS over TCPIP. . . . . . . . : uitgeschakeld
```

---

### Post by dutchmega on 2006-10-12
Removing the 3COM networkcard from my computer or reinstalling Ubuntu or resetting the modem while Ubuntu is running.. don't work...

---

### Post by dutchmega on 2006-10-14
Anyone? :)

It's kinda weird considering I don't have DSL and other people with 8100/8169 networkcard don't have any problems...

---

### Post by dutchmega on 2006-10-15
Maybe this is interesting...

ifup eth1
```
There is already a pid file /var/run/dhclient.eth1.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth1/00:11:09:67:d1:53
Sending on   LPF/eth1/00:11:09:67:d1:53
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9
```

Those 255's don't look good...

Update: [Turning the pc off entirely](http://www.ubuntuforums.org/showpost.php?p=1563747&postcount=12) for 5min (with PSU switched off) and then reinstall Ubuntu.. nope..

---

### Post by mips on 2006-10-15
Tried using static IP parameters ?

---

### Post by dutchmega on 2006-10-15
I did... Also doesn't work. Still can't ping shit.

Also disabled any other network-devices in BIOS, like firewire. Now I have only a modem and the Realtek.

---

### Post by dutchmega on 2006-10-16
Problem fixed. * mumpels something like 'should use lowercase hostnames'

---

### Post by Crash80 on 2006-10-25
@dutchmega:
and do you know get an gigabit link to your switch? since you're using a gbit lan card and got and 100 mbit connection this seems to be to slow?!

---

