---
title: "2 nic cards sharing the same PHYADR ?"
date: 2006-08-17
forum: Networking &amp; Wireless
---

### Post by Dan Luevano on 2006-08-17
I'm still having problems enabling two nic cards on my box, when one is enabled the other doesn't respond to requests from outside the local network. I just noticed that using the ethtool both nic cards have the same PHYADR (physical address), is this ok?  One of the nic cards was installed before the OS was loaded, the other was installed after the OS was loaded.

Question: Can two nic cards share the same phyadr if they have different IRQs?  If not, how do I change the phyadr of one of the cards? How do I know what address to use?

Here is a dump of the ethtool for eth0 and eth1:

????@????:~# ethtool eth0
Settings for eth0:
        Supported ports: [ TP MII ]
        Supported link modes:   10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
        Advertised auto-negotiation: Yes
        Speed: 100Mb/s
        Duplex: Half
        Port: MII
        [COLOR="Red"]**PHYAD: 32**[/COLOR]
        Transceiver: internal
        Auto-negotiation: on
        Supports Wake-on: pumbg
        Wake-on: d
        Current message level: 0x00000007 (7)
        Link detected: yes
????@????:~# ethtool eth1
Settings for eth1:
        Supported ports: [ TP MII ]
        Supported link modes:   10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
        Advertised auto-negotiation: Yes
        Speed: 100Mb/s
        Duplex: Full
        Port: MII
        [COLOR="Red"]**PHYAD: 32**[/COLOR]
        Transceiver: internal
        Auto-negotiation: on
        Supports Wake-on: pumbg
        Wake-on: d
        Current message level: 0x00000007 (7)
        Link detected: yes


Any help or suggests will be appreciated greatly.  Thanks!

Dan Luevano

---

### Post by Original Brownster on 2006-08-17
Hi,
I dont think the phyaddr is an issue (mine both show 32).
Please post the output of 'ifconfig -a' and 'netstat -rn' with them both enabled and configured.
Also please explain the cabling / network setup.

Thanks.

---

### Post by cptnapalm on 2006-08-17
what does ifconfig output?

---

### Post by Dan Luevano on 2006-08-17
Hi, thanks for your help!

Here are the outputs you requested (plus):


username@hostname:~#
username@hostname:~# ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:10:B5:9C:21:63
          inet addr:72.54.107.147  Bcast:72.54.107.151  Mask:255.255.255.248
          inet6 addr: fe80::210:b5ff:fe9c:2163/64 Scope:Link
          UP BROADCAST RUNNING PROMISC MULTICAST  MTU:1500  Metric:1
          RX packets:2498009 errors:0 dropped:0 overruns:0 frame:0
          TX packets:194044 errors:0 dropped:0 overruns:0 carrier:0
          collisions:1878 txqueuelen:1000
          RX bytes:1802998434 (1.6 GiB)  TX bytes:116552448 (111.1 MiB)
          Interrupt:5 Base address:0x2000

eth1      Link encap:Ethernet  HWaddr 00:4F:4A:17:57:6A
          inet addr:10.0.10.135  Bcast:10.0.10.255  Mask:255.255.255.0
          inet6 addr: fe80::24f:4aff:fe17:576a/64 Scope:Link
          UP BROADCAST RUNNING PROMISC MULTICAST  MTU:1500  Metric:1
          RX packets:10448 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1453 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:11159944 (10.6 MiB)  TX bytes:201295 (196.5 KiB)
          Interrupt:10 Base address:0x6000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:68 errors:0 dropped:0 overruns:0 frame:0
          TX packets:68 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:5024 (4.9 KiB)  TX bytes:5024 (4.9 KiB)

sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

username@hostname:~#
username@hostname:~#
username@hostname:~# netstat -rn
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
72.54.107.144   0.0.0.0         255.255.255.248 U         0 0          0 eth0
10.0.10.0       0.0.0.0         255.255.255.0   U         0 0          0 eth1
0.0.0.0         10.0.10.1       0.0.0.0         UG        0 0          0 eth1
0.0.0.0         72.54.107.145   0.0.0.0         UG        0 0          0 eth0
username@hostname:~#
username@hostname:~#
username@hostname:~#
username@hostname:~#
username@hostname:~#
username@hostname:~# cat /etc/resolv.conf
search twinvisioninc.com
nameserver 10.0.10.1
nameserver 66.180.96.12
username@hostname:~#
username@hostname:~#
username@hostname:~#
username@hostname:~#
username@hostname:~# cat /etc/network/interfaces
### etherconf DEBCONF AREA. DO NOT EDIT THIS AREA OR INSERT TEXT BEFORE IT.
auto lo eth0 eth1

iface lo inet loopback

iface eth0 inet static
        address 72.54.107.147
        netmask 255.255.255.248
#        broadcast
        gateway 72.54.107.145

iface eth1 inet dhcp
        hostname tviftp


### END OF DEBCONF AREA.  PLACE YOUR EDITS BELOW; THEY WILL BE PRESERVED.

username@hostname:~#


configuration/hw setup:

linux box with Ubuntu 6.0; 2 nic cards, one (eth0) with static IP connected to a hub that is connected to a cisco router provided by CBEYOND, the other (eth1) with a DHCP IP connected to a switch that is being served by another UNIX box that is running DHCP Server.

If eth0 is UP, and eth1 is UP -- I cannot ping the static IP to eth0.

If eth0 is UP, and eth1 is DOWN  -- I CAN ping the static IP to eth0.

Weird...

Dan

---

### Post by Dan Luevano on 2006-08-17
The saga continues....

I ran a [COLOR="Red"]route [/COLOR]command (see below) and noticed that I had two entries for "default", one for each nic card. When I removed the entry for the eth1 card, I was then able to ping eth0 (the static IP) from outside my local network.

**How does this get created and is it something I can force or prevent on a reboot?**

username@hostname:~# route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
72.54.107.144   *               255.255.255.248 U     0      0        0 eth0
10.0.10.0       *               255.255.255.0   U     0      0        0 eth1
default         ddg.twinvisioni 0.0.0.0         UG    0      0        0 eth1
default         72.54.107.145   0.0.0.0         UG    0      0        0 eth0
username@hostname:~# route del default eth1



Any thoughts?

Thanks,

Dan

---

### Post by Original Brownster on 2006-08-19
Hi,
I suspect that the extra default route is the problem, I think only one is correct and needed and should point to the router/switch whatever that can reach the WAN and in your case the cisco router 72.54.107.145 appears to know the correct path as your ping from outside worked. 

I think that as you found, removing the default route associated with eth1, your ping request reaches the pc succesfully and then is routed (via the remaining default route) to your cisco router - I suspect this has the route back to your WAN (assuming your outside your LAN) and therefore works. When the other default route existed, it was higher in the order in the kernel routing table and therefore the packet was routed there by default, never reaching the next entry in the table and why would it - The entry was a default route.

The route entry you removed I guess is not the correct address to a gateway to return the packet to the external WAN. Set by the dhcp server this can be altered I believe through it's config file '/etc/dhcp3/dhclient.conf'
Check the docs on configuring your client to use dhcp. I understand you can determine which pieces of network information are received from the dhcp server.

HTH

> **Dan Luevano said:**
> The saga continues....

I ran a [COLOR="Red"]route [/COLOR]command (see below) and noticed that I had two entries for "default", one for each nic card. When I removed the entry for the eth1 card, I was then able to ping eth0 (the static IP) from outside my local network.

**How does this get created and is it something I can force or prevent on a reboot?**

username@hostname:~# route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
72.54.107.144   *               255.255.255.248 U     0      0        0 eth0
10.0.10.0       *               255.255.255.0   U     0      0        0 eth1
default         ddg.twinvisioni 0.0.0.0         UG    0      0        0 eth1
default         72.54.107.145   0.0.0.0         UG    0      0        0 eth0
username@hostname:~# route del default eth1



Any thoughts?

Thanks,

Dan

---

