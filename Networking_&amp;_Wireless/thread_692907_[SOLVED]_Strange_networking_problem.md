---
title: "[SOLVED] Strange networking problem"
date: 2008-02-10
forum: Networking &amp; Wireless
---

### Post by viermaalj on 2008-02-10
Hi all

I have a laptop with ubuntu (7.10). It has an eth0 and ath0 interface.
The ath0 works perfectly, but recently I'm having problems with my wired connection. 

ath0 's address is  assigned by my router ( 192.168.2.x ) and eth0 has a static address ( 192.168.1.118 ).

```
# cat /etc/network/interfaces 
auto lo
iface lo inet loopback
address 127.0.0.1

auto ath0
iface ath0 inet dhcp

auto eth0
iface eth0 inet static
address 192.168.1.118
netmask 255.255.255.0
```

Now when i connect my laptop with my desktop ( windows xp ), using a cable, the ping command gives me a "host unreachable" and on windows a "timeout" response. 

```
# route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.2.0     0.0.0.0         255.255.255.0   U     0      0        0 ath0
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 ath0
0.0.0.0         192.168.2.1     0.0.0.0         UG    100    0        0 ath0

# ip route
192.168.2.0/24 dev ath0  proto kernel  scope link  src 192.168.2.200 
192.168.1.0/24 dev eth0  proto kernel  scope link  src 192.168.1.118 
169.254.0.0/16 dev ath0  scope link  metric 1000 
default via 192.168.2.1 dev ath0  metric 100 
```

```
# ip link
1: lo: <LOOPBACK,UP,10000> mtu 16436 qdisc noqueue 
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
2: eth0: <BROADCAST,MULTICAST,UP,10000> mtu 1500 qdisc pfifo_fast qlen 1000
    link/ether 00:a0:d1:36:77:12 brd ff:ff:ff:ff:ff:ff
3: wifi0: <BROADCAST,MULTICAST,UP,10000> mtu 1500 qdisc pfifo_fast qlen 199
    link/ieee802.11 00:16:e3:04:8a:c1 brd ff:ff:ff:ff:ff:ff
4: ath0: <BROADCAST,MULTICAST,UP,10000> mtu 1500 qdisc noqueue 
    link/ether 00:16:e3:04:8a:c1 brd ff:ff:ff:ff:ff:ff
```

```
# iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination   
```

Anybody got any idea's about what might be wrong.

---

### Post by Paris Heng on 2008-02-10
1. First check the LAN cable type, PC-to-PC suppose to cross-over type.

2. If Ok, try this,

> iptables –F
iptables –t nat –F
iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE
iptables-save > /etc/iptables.conf
#if you using ipv4
echo 1 > /proc/sys/net/ipv4/ip_forward
/etc/init.d/networking restart


3. Add appropriate route into the routing table.

---

### Post by mrsteveman1 on 2008-02-10
Check your arp tables since its easy to do

```
sudo arp
```

if you see anything weird clear it by doing  

```
sudo arp -d <ip>
```

then check and make sure this is a crossover cable you are using, if its a crossover the left wire pairs will be different colors on the ends like [this]("http://www.patraswireless.net/tutorial/basic%20tutorial/tut-equipemt/cable_utp_clip_image003.gif")

If you dont have a crossover (or even if you are using one now), connect this link through a switch so you can at least make sure layer 2 works correctly. I have a server that randomly refuses to connect to anything, and the only reason i know about it is the switch port flashes.

Post back whatever you find.

---

### Post by viermaalj on 2008-02-10
Hi

I should have mentioned this in the first post ( it was the first thing I checked :) ) but the cable is the right type. When I boot my laptop in XP (So its XP to XP) it all works and about a month ago it also worked with ubuntu, with the same hardware/cable.

**Paris Heng**

```
# iptables -t nat -L
Chain PREROUTING (policy ACCEPT)
target     prot opt source               destination         

Chain POSTROUTING (policy ACCEPT)
target     prot opt source               destination         
MASQUERADE  0    --  anywhere             anywhere            
MASQUERADE  0    --  anywhere             anywhere            

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination 
```

What would I need to add to my route table?

**mrsteveman1**

after a ping to my router (192.168.2.1) and a ping to my desktopPC (192.168.1.114)
```
# arp
Address                  HWtype  HWaddress           Flags Mask            Iface
desktopj4                        (incomplete)                              eth0
.                        ether   00:14:C1:14:B6:37   C                     ath0
```

---

### Post by mrsteveman1 on 2008-02-10
The routing table should be fine, at this point its a layer2 problem, particularly since arp has no valid mac address for your desktop at the moment.

try deleting that desktopj4 entry with arp -d desktopj4

I believe its saying desktopj4 and not an IP because you have it mapped in the hosts file, but it should work to remove that entry.

---

### Post by viermaalj on 2008-02-11
> **mrsteveman1 said:**
> The routing table should be fine, at this point its a layer2 problem, particularly since arp has no valid mac address for your desktop at the moment.

try deleting that desktopj4 entry with arp -d desktopj4

I believe its saying desktopj4 and not an IP because you have it mapped in the hosts file, but it should work to remove that entry.

When both my interfaces are up this is my arp table

```
# arp
Address                  HWtype  HWaddress           Flags Mask            Iface
.                        ether   00:14:C1:14:B6:37   C                     ath0
```

when i ping my desktop

```
# arp
Address                  HWtype  HWaddress           Flags Mask            Iface
desktopj4                        (incomplete)                              eth0
.                        ether   00:14:C1:14:B6:37   C                     ath0
[I]
With mapping removed in host file[/I]

# arp
Address                  HWtype  HWaddress           Flags Mask            Iface
.                        ether   00:14:C1:14:B6:37   C                     ath0
192.168.1.114                    (incomplete)                              eth0

```

when i remove the "incomplete" one, it just gets added again the next time.

What would I need to check / do to get him to add the correct HardwareAddress?

I have tried to add it manually (  arp -s 192.168.1.114 00:11:D8:94:91:52 -i eth0 ) but then my ping just gives me x packets dropped without any explanation as to why.

---

### Post by mrsteveman1 on 2008-02-11
Boot an ubuntu livecd and see if it works there.

You might also try running the following things (from the non-working system) and posting what they say:

```
sudo ethtool eth0
```

```
sudo ethtool -S eth0
```

also may help to set the parameters of the link manually

```
sudo ethtool -s eth0 speed 100 duplex full autoneg off
```

---

### Post by viermaalj on 2008-02-12
With a live cd (also ubuntu 7.10) it works.

After executing 
```
sudo ethtool -s eth0 speed 100 duplex full autoneg off
```

My output looks like this
```
$ sudo ethtool eth0
Settings for eth0:
        Supported ports: [ TP MII ]
        Supported link modes:   10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
        Advertised auto-negotiation: No
        Speed: 100Mb/s
        Duplex: Full
        Port: MII
        PHYAD: 32
        Transceiver: internal
        Auto-negotiation: off
        Supports Wake-on: pumbg
        Wake-on: d
        Current message level: 0x00000007 (7)
        Link detected: yes
```

But still nothing. Could it be that ubuntu tries to ping my desktop over my wireless interface (ath0) instead of my eth0 interface.

---

### Post by mrsteveman1 on 2008-02-12
Hmmm.

Since your routing table looks fine what SHOULD happen in this case is the following:

> you ping an IP in the 192.168.1.0/24 subnet

your computer checks the routing table and sees that this network is directly connected to eth0, hence no routing is required (no next hop/gateway)

your computer runs an ARP query to get the MAC address of the computer with the IP you are pinging (this is where your ping appears to fail for some reason, )

your computer then encapsulates the ping request into a layer 2 frame and sends it to the destination MAC address over eth0


Is it possible that there are conflicting IP assignments? Are there 2 machines sharing the 192.168.1.114 IP? Unless the arp program is just reporting the MAC address wrong, your computer isnt being given a mac address for the IP 192.168.1.114 for some reason.

Something you can try to do is use [Linkloop]("http://freshmeat.net/projects/linkloop/") to test ethernet connectivity directly to see if you can even get to the remote machine. There may be an ubuntu package for it.

---

### Post by viermaalj on 2008-02-15
Hi

I had some problems using linkloop. I got some sort of stack warning.

I changed my ip address (ubuntu = 192.168.10.5 and desktop = 192.168.10.6), but still nothing. 

When I ping my desktop after executing tcpdump + filter, I get the following result.

```
sudo tcpdump -ennqti eth0 \( arp or icmp \)
tcpdump: verbose output suppressed, use -v or -vv for full protocol decode
listening on eth0, link-type EN10MB (Ethernet), capture size 96 bytes
00:a0:d1:36:77:12 > ff:ff:ff:ff:ff:ff, ARP, length 42: arp who-has 192.168.10.7 tell 192.168.10.5
00:a0:d1:36:77:12 > ff:ff:ff:ff:ff:ff, ARP, length 42: arp who-has 192.168.10.7 tell 192.168.10.5
00:a0:d1:36:77:12 > ff:ff:ff:ff:ff:ff, ARP, length 42: arp who-has 192.168.10.7 tell 192.168.10.5
00:a0:d1:36:77:12 > ff:ff:ff:ff:ff:ff, ARP, length 42: arp who-has 192.168.10.7 tell 192.168.10.5
00:a0:d1:36:77:12 > ff:ff:ff:ff:ff:ff, ARP, length 42: arp who-has 192.168.10.7 tell 192.168.10.5
00:a0:d1:36:77:12 > ff:ff:ff:ff:ff:ff, ARP, length 42: arp who-has 192.168.10.7 tell 192.168.10.5

6 packets captured
6 packets received by filter
0 packets dropped by kernel
```

Using arping

```
sudo arping -I eth0 -c 3 192.168.10.6
ARPING 192.168.10.6

--- 192.168.10.6 statistics ---
3 packets transmitted, 0 packets received, 100% unanswered
```

---

### Post by mrsteveman1 on 2008-02-15
It looks like the interface isn't even receiving ethernet frames at all.

What chipset is this?

---

### Post by viermaalj on 2008-02-15
It's a Realtek chipset

My laptop is a Toshiba A100

---

### Post by viermaalj on 2008-02-15
```
ping 192.168.10.6
PING 192.168.10.6 (192.168.10.6) 56(84) bytes of data.
64 bytes from 192.168.10.6: icmp_seq=1 ttl=128 time=6.53 ms
64 bytes from 192.168.10.6: icmp_seq=2 ttl=128 time=1.36 ms
64 bytes from 192.168.10.6: icmp_seq=3 ttl=128 time=1.36 ms
64 bytes from 192.168.10.6: icmp_seq=4 ttl=128 time=1.41 ms

--- 192.168.10.7 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 2999ms
rtt min/avg/max/mdev = 1.363/2.669/6.535/2.232 ms
```

look at that :)

I removed the "noapic" option from my boot command which seemed to do the trick.

Thank you for all the help mrsteveman1

---

