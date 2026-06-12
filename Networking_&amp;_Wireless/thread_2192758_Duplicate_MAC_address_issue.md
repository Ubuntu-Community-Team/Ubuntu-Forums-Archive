---
title: "Duplicate MAC address issue"
date: 2013-12-09
forum: Networking &amp; Wireless
---

### Post by mg9189 on 2013-12-09
I am not a networking expert, but I've been tasked to address an issue with our servers.

Our servers have 2 to 4 physical network ports, and for this I am only using the first 2 ports.

If I type dhclient, both port get IP addresses assigned to them as expected.  They both show distinct MAC addresses when typing ifconfig.

However, when you review the ipaddresses at the switch, the IP addresses assigned are both using the same MAC address.

I am using Ubuntu 10.04 with the latest patches upgraded.

I would mention the hardware, but it does not seem to matter as this has happened to several machines we have.

This issue prevents access to the server when both IP addresses are enabled when viewed outside of the local network.

ifconfig dump(minus header comments):
```
eth0      Link encap:Ethernet  HWaddr [COLOR=#ff0000]**00:25:90:d3:0b:d8**[/COLOR]  
          inet addr:192.168.30.77  Bcast:192.168.30.255  Mask:255.255.255.0
          inet6 addr: fe80::225:90ff:fed3:bd8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:1074 errors:0 dropped:0 overruns:0 frame:0
          TX packets:34 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:114510 (114.5 KB)  TX bytes:2780 (2.7 KB)


eth1      Link encap:Ethernet  HWaddr [COLOR=#ff0000]**00:25:90:d3:0b:d9**[/COLOR]  
          inet addr:192.168.30.81  Bcast:192.168.30.255  Mask:255.255.255.0
          inet6 addr: fe80::225:90ff:fed3:bd9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:1044 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:110404 (110.4 KB)  TX bytes:740 (740.0 B)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12306 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12306 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3004397 (3.0 MB)  TX bytes:3004397 (3.0 MB)

```

IP Address vs. MAC addresses at the switch:
....
192.168.30.77   [COLOR=#ff0000]**002590d30bd8  **[/COLOR]<-- same MAC
192.168.30.68   000c2955b4e1
192.168.30.95   000c29c7a929
192.168.30.81   [COLOR=#ff0000]**002590d30bd8  **[/COLOR]<-- as this one ?? why?
....


persistent rules file (minus comments in header):
```
# PCI device 0x8086:0x1533 (igb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:25:90:d3:0b:da", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth2"


# PCI device 0x8086:0x1533 (igb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:25:90:d3:0b:d9", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"


# PCI device 0x8086:0x1533 (igb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:25:90:d3:0b:db", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth3"


# PCI device 0x8086:0x1533 (igb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:25:90:d3:0b:d8", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"




```

lspci 
```
00:00.0 Host bridge: Intel Corporation Device 0c08 (rev 06)
00:01.0 PCI bridge: Intel Corporation Device 0c01 (rev 06)
00:14.0 USB Controller: Intel Corporation Device 8c31 (rev 04)
00:16.0 Communication controller: Intel Corporation Device 8c3a (rev 04)
00:16.1 Communication controller: Intel Corporation Device 8c3b (rev 04)
00:1a.0 USB Controller: Intel Corporation Device 8c2d (rev 04)
00:1c.0 PCI bridge: Intel Corporation Device 8c10 (rev d4)
00:1c.2 PCI bridge: Intel Corporation Device 8c14 (rev d4)
00:1c.3 PCI bridge: Intel Corporation Device 8c16 (rev d4)
00:1c.6 PCI bridge: Intel Corporation Device 8c1c (rev d4)
00:1c.7 PCI bridge: Intel Corporation Device 8c1e (rev d4)
00:1d.0 USB Controller: Intel Corporation Device 8c26 (rev 04)
00:1f.0 ISA bridge: Intel Corporation Device 8c54 (rev 04)
00:1f.3 SMBus: Intel Corporation Device 8c22 (rev 04)
00:1f.6 Signal processing controller: Intel Corporation Device 8c24 (rev 04)
01:00.0 RAID bus controller: Adaptec Device 028b (rev 01)
02:00.0 PCI bridge: ASPEED Technology, Inc. Device 1150 (rev 03)
03:00.0 VGA compatible controller: ASPEED Technology, Inc. ASPEED Graphics Family (rev 30)
04:00.0 Ethernet controller: Intel Corporation Device 1533 (rev 03)
05:00.0 Ethernet controller: Intel Corporation Device 1533 (rev 03)
06:00.0 Ethernet controller: Intel Corporation Device 1533 (rev 03)
07:00.0 Ethernet controller: Intel Corporation Device 1533 (rev 03)



```

---

### Post by jonobr on 2013-12-09
Hello

I was wondering if [this]("http://ubuntuforums.org/showthread.php?t=1423661") is the same as your seeing

---

### Post by bab1 on 2013-12-09
> **mg9189 said:**
> I am not a networking expert, but I've been tasked to address an issue with our servers.

Our servers have 2 to 4 physical network ports, and for this I am only using the first 2 ports.

If I type dhclient, both port get IP addresses assigned to them as expected.  They both show distinct MAC addresses when typing ifconfig.

However, when you review the ipaddresses at the switch, the IP addresses assigned are both using the same MAC address.

I am using Ubuntu 10.04 with the latest patches upgraded.

I would mention the hardware, but it does not seem to matter as this has happened to several machines we have.

This issue prevents access to the server when both IP addresses are enabled when viewed outside of the local network.

ifconfig dump(minus header comments):
```
eth0      Link encap:Ethernet  HWaddr [COLOR=#ff0000]**00:25:90:d3:0b:d8**[/COLOR]  
          inet addr:[COLOR="#0000FF"]**192.168.30**[/COLOR].77  Bcast:192.168.30.255  Mask:255.255.255.0
         
eth1      Link encap:Ethernet  HWaddr [COLOR=#ff0000]**00:25:90:d3:0b:d9**[/COLOR]  
          inet addr:[COLOR="#0000FF"]**192.168.30**[/COLOR].81  Bcast:192.168.30.255  Mask:255.255.255.0


```

IP Address vs. MAC addresses at the switch:

```
192.168.30.77   [COLOR=#ff0000]**002590d30bd8  **[/COLOR]<-- same MAC
192.168.30.68   000c2955b4e1
192.168.30.95   000c29c7a929
192.168.30.81   [COLOR=#ff0000]**002590d30bd8  **[/COLOR]<-- as this one ?? why?
```


Let's start with the networking problem first.  The basic premise is:  One IP address per host.  This means that each "server" should have only one IP address.  The fact that you have 4 physical ports (each with a distinct MAC address) does not alter that fact.  So why have 4 NICs?  For two reasons.  1. So you can bond them together for failover or more through-put and 2. So you can use the host as a router with an IP address in each network.

Since you have allowed the multiple addresses in the SAME network (see blue above) the OS disables one of them.

The duplicate MAC addresses problem is most likely a udev rules problem as @ jonobr has pointed out.  But the point is moot as the networking rules are in effect.  Even if the MAC addresses were seen as different the second NIC would not be allowed with your configuration.

To summarize; One physical connection per network unless you want to bond the interfaces.  If you bond the interfaces you will still only have 1 IP address and one MAC address per host,

---

### Post by codenine75a on 2013-12-09
It looks like your server is a "blade" not a Sun blade and it has two NICs.  I think maybe there are two interfaces tied to the same NIC.

---

