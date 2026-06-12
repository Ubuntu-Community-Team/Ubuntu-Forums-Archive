---
title: "Ubuntu 14.04 LTS Server Routing Problem"
date: 2014-10-14
forum: Networking &amp; Wireless
---

### Post by edubidu on 2014-10-14
Hi,

I should be able to ping 10.57.1.110 but it does not work. I googled around now for some days. Can someone help me?
The target should not be the problem, cause an Ubuntu 11.10 (GNU/Linux 3.0.0-32-server x86_64) installation on the same server worked.
BTW I did a complete new installation, not an upgrade.

cat /etc/network/interfaces

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# External network 
auto p4p3
allow-hotplug p4p3
iface p4p3 inet static
    address 192.168.1.5
    netmask 255.255.255.0
    gateway 192.168.1.1


# private VLAN storage network
auto p4p4
allow-hotplug p4p4
iface p4p4 inet static
    address 10.57.1.108
    netmask 255.255.255.0
    ### Ubuntu Linux add persistent route command ###
        post-up route add -net 10.57.1.0 netmask 255.255.255.0 gw 192.168.1.5
```

route

```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         gw-vlan57.bla   0.0.0.0         UG    0      0        0 p4p3
10.57.1.0       ubuntu.bla      255.255.255.0   UG    0      0        0 p4p3
10.57.1.0       *               255.255.255.0   U     0      0        0 p4p4
192.168.1.0     *               255.255.255.0   U     0      0        0 p4p3
```

cat /etc/sysctl.conf
```

...
net.ipv4.ip_forward=1
...
```

iptables -L

```
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
```

ifconfig

```
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:27 errors:0 dropped:0 overruns:0 frame:0
          TX packets:27 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2724 (2.7 KB)  TX bytes:2724 (2.7 KB)

p4p3      Link encap:Ethernet  HWaddr 00:26:55:df:81:5b  
          inet addr:192.168.1.5  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::226:55ff:fedf:815b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1368 errors:0 dropped:0 overruns:0 frame:0
          TX packets:757 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:148678 (148.6 KB)  TX bytes:76832 (76.8 KB)
          Interrupt:37 Memory:fbce0000-fbd00000 

p4p4      Link encap:Ethernet  HWaddr 00:26:55:df:81:5a  
          inet addr:10.57.1.108  Bcast:10.57.1.255  Mask:255.255.255.0
          inet6 addr: fe80::226:55ff:fedf:815a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:521 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:55502 (55.5 KB)  TX bytes:680 (680.0 B)
          Interrupt:30 Memory:fbbe0000-fbc00000 
```

Thank you!
edubidu

---

### Post by Iowan on 2014-10-14
Try removing one of the gateways (gw 192.168.1.5).

---

### Post by davit2 on 2014-10-14
Hi,
delete this one

post-up route add -net 10.57.1.0 netmask 255.255.255.0 gw 192.168.1.5

---

### Post by edubidu on 2014-10-15
Thank you Iowan and davit2 for your responses!
Removing just the gw 192.168.1.5
does not help
and uncommenting the line post-up route add -net 10.57.1.0 netmask 255.255.255.0 gw 192.168.1.5
does not help:
```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         gw-vlan57.bla   0.0.0.0         UG    0      0        0 p4p3
10.57.1.0       *               255.255.255.0   U     0      0        0 p4p4
192.168.1.0     *               255.255.255.0   U     0      0        0 p4p3
```

---

### Post by edubidu on 2014-10-15
This config worked on the old ubuntu installation and works actually for the first NAS head:
```

   # Configure the primary bonding interface that will be used for NIC4/NIC5 pairing.
 auto bond0
     iface bond0 inet static  
     address 192.168.1.5
     netmask 255.255.255.0
     network 192.168.1.0
     gateway 192.168.1.1  
     dns-nameservers 192.168.1.100
     # This option must always be 'none'; use "bond-master" on each interface.
     bond-slaves none
     # Common modes are active-backup and 802.3ad [1]
     bond-mode 802.3ad  
     bond-ad_select bandwidth
     bond-lacp_rate slow  
     # MII link monitoring frequency in ms [2]
     bond-miimon 100
     bond-use_carrier 1
     # Wait this long in ms before disabling an interface after MII failure [2]
     bond-downdelay 200
     # Wait this long in ms before enabling an interface after MII recovery [2]
     bond-updelay 50
     # This part is important to have the interface come up  
     post-up ifenslave bond0 eth4 eth5
     pre-down ifenslave bond0 eth4 eth5

 # Bind the NIC4 physical interface to the primary bonding interface.
 auto eth4
 allow-bond0 eth4
 iface eth4 inet manual
    bond-master bond0
    bond-primary eth5 eth4
  
 # Bind the NIC5 physical interface to the primary bonding interface.
 auto eth5
 allow-bond0 eth5
 iface eth5 inet manual
    bond-master bond0
    bond-primary eth4 eth5
  
  /etc/vip-down.sh -z -B
  
 # Bind the NIC1/NIC2 physical interface to network 10.57.
 auto eth0
 iface eth0 inet static
 address 10.57.1.108
 netmask 255.255.255.0
 gateway 192.168.1.5

 auto eth1
 iface eth1 inet static
 address 10.57.1.118
 netmask 255.255.255.0
 gateway 192.168.1.5


```

---

### Post by edubidu on 2014-10-15
I begin to believe this is not a routing problem but some additional security inside of the new Ubuntu version.

---

### Post by The Cog on 2014-10-15
As far as I can see, p4p4 is working OK and has both transmit and receive packets being counted.

My next step would be to run tcpdump on the interface and see if I can see packets going out and replies coming back:
```
sudo tcpdump -np -i p4p4
```

You could also check the routing with this command but I don't expect any surprises there:
```
ip route get 10.57.1.110 
```

As you had another machine there earlier (with the same IP address?), is it possible that the other end (10.57.1.110) still has the wrong MAC address in its ARP table? You could try a promiscuous trace and look for replies to the wrong MAC address like this:
```
sudo tcpdump -n -e -i p4p4
```

---

### Post by edubidu on 2014-10-16
Thank you for your help!
To reume: I have 2 NAS Heads. Both identical hardware and identical installations before I migrated to Ubuntu 14.04, were installed with ubuntu 11.10.
They access via iscsi to 4 storages with IP's 
```
10.57.1.101     00:05:33  68b5.99ae.dfb6  Vlan557         
10.57.1.102     00:13:01  68b5.99ae.4f18  Vlan557         
10.57.1.103     00:14:15  68b5.99ae.df86  Vlan557         
10.57.1.104     00:15:19  68b5.99ae.bf2e  Vlan557
```
The [FONT=courier new]VIP[/FONT] of those 4 Storages is [FONT=courier new]10.57.1.110[/FONT]
The first NAS head (NAS07), still Ubuntu 11.10, has IP address [FONT=courier new]192.168.1.7 [/FONT]
The second (Nas08), now on Ubuntu 14.04 has IP address [FONT=courier new]192.168.1.5[/FONT]
The [FONT=courier new]/etc/network/interfaces[/FONT] I posted in post [COLOR=#ff8c00]#5[/COLOR] is the old one (backuped) of Nas08 that worked like a charm on Ubuntu 11.10.

The output of your suggested commands (a bit chinese to me):

[FONT=courier new]ip route get 10.57.1.110[/FONT]

```
10.57.1.110 dev p4p3  src 192.168.1.5 
    cache
```

[FONT=courier new]tcpdump -n -e -i p4p4[/FONT]

```
tcpdump: verbose output suppressed, use -v or -vv for full protocol decode
listening on p4p4, link-type EN10MB (Ethernet), capture size 65535 bytes
09:39:36.583214 00:00:5e:00:00:2a > 01:00:5e:00:00:12, ethertype IPv4 (0x0800), length 70: 192.168.1.7 > 224.0.0.18: VRRPv2, Advertisement, vrid 42, prio 0, authtype none, intvl 1s, length 36
09:39:37.583293 00:00:5e:00:00:2a > 01:00:5e:00:00:12, ethertype IPv4 (0x0800), length 70: 192.168.1.7 > 224.0.0.18: VRRPv2, Advertisement, vrid 42, prio 0, authtype none, intvl 1s, length 36
09:39:38.390473 00:00:0c:9f:f0:39 > 01:00:5e:00:00:66, ethertype IPv4 (0x0800), length 94: 192.168.1.3.1985 > 224.0.0.102.1985: HSRPv1
09:39:38.394716 54:7f:ee:3c:86:c1 > 01:00:5e:00:00:66, ethertype IPv4 (0x0800), length 94: 192.168.1.2.1985 > 224.0.0.102.1985: HSRPv1
09:39:38.583304 00:00:5e:00:00:2a > 01:00:5e:00:00:12, ethertype IPv4 (0x0800), length 70: 192.168.1.7 > 224.0.0.18: VRRPv2, Advertisement, vrid 42, prio 0, authtype none, intvl 1s, length 36
09:39:39.360537 54:7f:ee:3c:86:c1 > 01:00:5e:00:00:0d, ethertype IPv4 (0x0800), length 70: 192.168.1.2 > 224.0.0.13: PIMv2, Hello, length 36
09:39:39.583315 00:00:5e:00:00:2a > 01:00:5e:00:00:12, ethertype IPv4 (0x0800), length 70: 192.168.1.7 > 224.0.0.18: VRRPv2, Advertisement, vrid 42, prio 0, authtype none, intvl 1s, length 36
09:39:40.490108 3c:d9:2b:07:c6:ba > ff:ff:ff:ff:ff:ff, ethertype IPv4 (0x0800), length 156: 192.168.1.75.17500 > 255.255.255.255.17500: UDP, length 114
09:39:40.490800 3c:d9:2b:07:c6:ba > ff:ff:ff:ff:ff:ff, ethertype IPv4 (0x0800), length 156: 192.168.1.75.17500 > 192.168.1.255.17500: UDP, length 114
09:39:40.583328 00:00:5e:00:00:2a > 01:00:5e:00:00:12, ethertype IPv4 (0x0800), length 70: 192.168.1.7 > 224.0.0.18: VRRPv2, Advertisement, vrid 42, prio 0, authtype none, intvl 1s, length 36
09:39:41.400878 00:00:0c:9f:f0:39 > 01:00:5e:00:00:66, ethertype IPv4 (0x0800), length 94: 192.168.1.3.1985 > 224.0.0.102.1985: HSRPv1
09:39:41.403238 54:7f:ee:3c:86:c1 > 01:00:5e:00:00:66, ethertype IPv4 (0x0800), length 94: 192.168.1.2.1985 > 224.0.0.102.1985: HSRPv1
09:39:41.583227 00:00:5e:00:00:2a > 01:00:5e:00:00:12, ethertype IPv4 (0x0800), length 70: 192.168.1.7 > 224.0.0.18: VRRPv2, Advertisement, vrid 42, prio 0, authtype none, intvl 1s, length 36
09:39:42.582674 00:21:28:3d:99:9a > ff:ff:ff:ff:ff:ff, ethertype ARP (0x0806), length 60: Request who-has 192.168.1.52 (ff:ff:ff:ff:ff:ff) tell 192.168.1.26, length 46
```


[FONT=courier new]tcpdump -np -i p4p4[/FONT]
```
tcpdump: verbose output suppressed, use -v or -vv for full protocol decode
listening on p4p4, link-type EN10MB (Ethernet), capture size 65535 bytes
09:41:53.417869 ARP, Request who-has 192.168.1.12 (ff:ff:ff:ff:ff:ff) tell 192.168.1.3, length 46
09:41:55.430216 ARP, Request who-has 192.168.1.12 (ff:ff:ff:ff:ff:ff) tell 192.168.1.3, length 46
09:41:59.440345 ARP, Request who-has 192.168.1.12 (ff:ff:ff:ff:ff:ff) tell 192.168.1.3, length 46
09:42:07.458920 ARP, Request who-has 192.168.1.12 (ff:ff:ff:ff:ff:ff) tell 192.168.1.3, length 46
09:42:07.687936 ARP, Reply 192.168.1.25 is-at 00:21:28:3d:99:9b, length 46
09:42:09.910229 ARP, Request who-has 192.168.1.1 tell 192.168.1.180, length 46
09:42:10.726400 IP 192.168.1.75.17500 > 255.255.255.255.17500: UDP, length 114
09:42:10.727364 IP 192.168.1.75.17500 > 192.168.1.255.17500: UDP, length 114
```

---

### Post by edubidu on 2014-10-16
interesting thing: on the second Nas Head (Nas7) the Network card corresponding to **[COLOR=#800080]p4p1 is eth0[/COLOR]** and tcp's on the network 10.57.1.
[COLOR=#800080]On the other Nas head (**Nas07**), still working with **Ubuntu 11.10**:[/COLOR] 
[COLOR=#800080]tcpdump -n -e -i **eth0**[/COLOR]
[COLOR=#800080]```
tcpdump: verbose output suppressed, use -v or -vv for full protocol decode
listening on eth0, link-type EN10MB (Ethernet), capture size 65535 bytes
10:38:49.334581 54:7f:ee:3c:86:c1 > 01:00:5e:00:00:66, ethertype IPv4 (0x0800), length 94: 10.57.1.2.1985 > 224.0.0.102.1985: HSRPv1
10:38:49.338612 00:00:0c:9f:f2:2d > 01:00:5e:00:00:66, ethertype IPv4 (0x0800), length 94: 10.57.1.3.1985 > 224.0.0.102.1985: HSRPv1
10:38:52.337400 00:00:0c:9f:f2:2d > 01:00:5e:00:00:66, ethertype IPv4 (0x0800), length 94: 10.57.1.3.1985 > 224.0.0.102.1985: HSRPv1
10:38:52.340263 54:7f:ee:3c:86:c1 > 01:00:5e:00:00:66, ethertype IPv4 (0x0800), length 94: 10.57.1.2.1985 > 224.0.0.102.1985: HSRPv1
10:38:53.412277 70:81:05:00:26:54 > 01:80:c2:00:00:0e, ethertype LLDP (0x88cc), length 329: LLDP, name per010c76, length 315
10:38:55.334642 54:7f:ee:3c:86:c1 > 01:00:5e:00:00:66, ethertype IPv4 (0x0800), length 94: 10.57.1.2.1985 > 224.0.0.102.1985: HSRPv1
10:38:55.339074 00:00:0c:9f:f2:2d > 01:00:5e:00:00:66, ethertype IPv4 (0x0800), length 94: 10.57.1.3.1985 > 224.0.0.102.1985: HSRPv1
```[/COLOR]

In fact, **[COLOR=#ff0000]p4p4 corresponds to "old" eth5 on Nas8[/COLOR]**

If my analyse is right, p4p1 should connect to 10.57.1.110. But there I have another problem:
ifconfig
```
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:15 errors:0 dropped:0 overruns:0 frame:0
          TX packets:15 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1458 (1.4 KB)  TX bytes:1458 (1.4 KB)

p4p1      Link encap:Ethernet  HWaddr 00:26:55:df:81:59  
          inet addr:10.57.1.108  Bcast:10.57.1.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:38 Memory:fbae0000-fbb00000 
```


ifup p4p1
```
ifup: interface p4p1 already configured
```
ethtool p4p1
```
Settings for p4p1:
    Supported ports: [ TP ]
    Supported link modes:   10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
                            1000baseT/Full 
    Supported pause frame use: No
    Supports auto-negotiation: Yes
    Advertised link modes:  10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
                            1000baseT/Full 
    Advertised pause frame use: No
    Advertised auto-negotiation: Yes
    Speed: Unknown!
    Duplex: Unknown! (255)
    Port: Twisted Pair
    PHYAD: 1
    Transceiver: internal
    Auto-negotiation: on
    MDI-X: Unknown (auto)
    Supports Wake-on: pumbg
    Wake-on: d
    Current message level: 0x00000007 (7)
                   drv probe link
    [COLOR=#ff0000]**Link detected: no**[/COLOR]
```
ifdown p4p1
ifup p4p1
```
SIOCADDRT: File exists
Failed to bring up p4p1.
```

dmesg | grep -i p4p1
```
[   15.261882] systemd-udevd[186]: [COLOR=#ff0000]**renamed network interface eth0 to p4p1**[/COLOR]
[   17.616393] IPv6: ADDRCONF(NETDEV_UP): p4p1: link is not ready
[   18.222024] IPv6: ADDRCONF(NETDEV_UP): p4p1: link is not ready
[ 1489.522828] IPv6: ADDRCONF(NETDEV_UP): p4p1: link is not ready
```

---

### Post by edubidu on 2014-10-16
I changed now my [FONT=courier new]/etc/network/interfaces[/FONT]:
(Note: In the future, the p4p4 will be a bond0 together with p4p3)

```
# The loopback network interface
auto lo
iface lo inet loopback

# LAN network 
auto p4p4
allow-hotplug p4p4
iface p4p4 inet static
        address 192.168.1.5
        netmask 255.255.255.0
        gateway 192.168.1.1

# private VLAN storage network
auto p4p1
allow-hotplug p4p1
iface p4p1 inet static
        address 10.57.1.108
        netmask 255.255.255.0
        ### Ubuntu Linux add persistent route command ###
        post-up route add -net 10.57.1.0 netmask 255.255.255.0 gw 192.168.1.5

auto p4p2
allow-hotplug p4p2
iface p4p2 inet static
        address 10.57.1.118
        netmask 255.255.255.0
        ### Ubuntu Linux add persistent route command ###
        post-up route add -net 10.57.1.0 netmask 255.255.255.0 gw 192.168.1.5
```


Now, the output is: for both, p4p1 and p4p2:
```
**[COLOR=#ff0000]Link detected: no[/COLOR]**
```

dmesg | grep -i p4p1
```
[   13.358138] systemd-udevd[185]: **[COLOR=#ff0000]renamed network interface eth0 to p4p1[/COLOR]**
[   17.070492] IPv6: ADDRCONF(NETDEV_UP): p4p1: link is not ready
[   17.630845] IPv6: ADDRCONF(NETDEV_UP): p4p1: link is not ready
```
dmesg | grep -i p4p2
```
[   13.341993] systemd-udevd[187]: **[COLOR=#ff0000]renamed network interface eth1 to p4p2[/COLOR]**
[   17.070499] IPv6: ADDRCONF(NETDEV_UP): p4p2: link is not ready
```

Could there be a problem because Ubuntu 14.04 renames the network cards?

---

### Post by The Cog on 2014-10-16
I don't understand that second interfaces file you posted. It seems to be for the same machine (same IP address) but a completely different set of interfaces. What's all that about?

It looks like the entry that davit2 asked you to remove is back again. I don't expect things to work while that entry is there bacause packets for 10.57.1.110 will be going the wrong way (as the ip route get 10.57.1.110 shows).

I don't see any packets from your PC (either 192.168.1.5 or 10.57.1.108) in the trace you posted. Possibly because they were going the wrong way (p4p3) and you were tracing on p4p4, possibly because you didn't try to ping 10.57.1.110 while tracing. Can you remove the route as davit2 asked, then run the traces again and try the ping while running the traces?

---

### Post by edubidu on 2014-10-16
Hah, it's working now!
Thank you a lot for your tipps!!

In fact, I discovered that there were two additional network cards named em1 and em2.
So instead of p4p1 and p4p2 I used em1 and em2 and yes, now I removed the entry that davit2 asked and it works!!
So thanks of your post #7



I discovered that Nas07 responded with network 10.57.x.x
tcpdump -n -e -i eth0
```
12:37:39.625557 00:00:0c:9f:f2:2d > 01:00:5e:00:00:66, ethertype IPv4 (0x0800), length 94: [COLOR=#ff0000]10.57.1.3[/COLOR]
```

but Nas08 responded with  network 192.168.x.x
tcpdump -np -i p4p4
```
09:41:53.417869 ARP, Request who-has 192.168.1.12 (ff:ff:ff:ff:ff:ff) tell [COLOR=#ff0000]192.168.1.3[/COLOR], length 46
```

And yes, now removing again the gw it works.

```
Here's the new /etc/network/interfaces:
# The loopback network interface
auto lo
iface lo inet loopback

# LAN network 
auto p4p4
allow-hotplug p4p4
iface p4p4 inet static
        address 192.168.1.5
        netmask 255.255.255.0
        gateway 192.168.1.1

# private VLAN storage network
auto em1
allow-hotplug em1
iface em1 inet static
        address 10.57.1.108
        netmask 255.255.255.0
       
auto em2
allow-hotplug em2
iface em2 inet static
        address 10.57.1.118
        netmask 255.255.255.0
```

What a thing!

---

### Post by The Cog on 2014-10-16
Excellent. Thanks for the feedback.

---

