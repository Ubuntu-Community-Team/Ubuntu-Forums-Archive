---
title: "Relatively new to Ubuntu, NIC question"
date: 2008-08-18
forum: Networking &amp; Wireless
---

### Post by evollusion on 2008-08-18
I've installed ubuntu 8.04 on an old computer to play with it and I'm liking everything so far but I cannot get the system to communicate over the network.  Ping's get a destination host unreachable to the gateway, but I can ping loopback and the interface IP address.

I've browsed through the forums looking for possible problems that might be causing it.  I've disabled IPv6 support, made sure that IPTables didn't have any configuration on them and checked the logfile with this line.

*grep "eth1" /etc/var/log/messages | more and receive the following line*

> Aug 18 16:02:16 xxxx-Ubuntu kernel: [ 1881.712794] e100: eth1: e100_watchdog: link up, 100Mbps, full-duplex

From what I know of logs this indicates that there is a connection that is up between the router and the NIC, however, I can't seem to get the internet.  When I open the properties window have tried changing from roaming, to dchp, to static ip addressing and am unsuccessful on each one.  I've tried using the GUI network properties window as well as setting the /etc/network/interfaces file to manually apply settings to the interface.  However, the system does pick up DNS information and does list the name of the router in "Search Domains" under the DNS tab of Network properties.  I've tried everything that I can think of but I'm now officially stumped... ](*,)

Please help!!!  

Thanks in andvance!

---

### Post by alastair on 2008-08-18
> Please help!!!  

Thanks in andvance!

Open a terminal and give us the output of :

```
ifconfig -a
```

```
route -n
```

Then, what IP address are you "pinging"?
Do you know your "router" IP address e.g

```
ping 192.168.0.1
```

(the above may be the wrong network for you)

Alastair

---

### Post by evollusion on 2008-08-18
```
ifconfig -a
```

```
eth0      Link encap:Ethernet  HWaddr 00:05:5d:34:55:84  
          inet addr:192.168.1.116  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:20 Base address:0xd800 

eth1      Link encap:Ethernet  HWaddr 00:07:e9:f7:77:c1  
          inet addr:192.168.1.115  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:358 dropped:0 overruns:0 frame:358
          TX packets:373 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:26851 (26.2 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:141 errors:0 dropped:0 overruns:0 frame:0
          TX packets:141 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:12448 (12.1 KB)  TX bytes:12448 (12.1 KB)
```

```
route -n
```

```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth1
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth1
0.0.0.0         192.168.1.1     0.0.0.0         UG    100    0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    100    0        0 eth1
```

> Then, what IP address are you "pinging"?
Do you know your "router" IP address e.g

```
ping 192.168.0.1
```

```
From 192.168.1.115 icmp_seq=1 Destination Host Unreachable
From 192.168.1.115 icmp_seq=2 Destination Host Unreachable
From 192.168.1.115 icmp_seq=3 Destination Host Unreachable
From 192.168.1.115 icmp_seq=4 Destination Host Unreachable
```


My home network is on the 192.168.1.0 network.  The network shouldn't be the problem.  All of my other TCP/IP enabled devices are working correctly.

---

### Post by Iowan on 2008-08-18
Two NIC's in the same subnet?  Try disabling one (or removing it).

---

### Post by evollusion on 2008-08-18
disabled eth0 and still no pings being returned.

---

### Post by Iowan on 2008-08-18
That machine has 2 NIC's? 
 Can you verify which (physical) card got disabled (MAC address printed on it)? 
(just won't work to plug into the disabled card ;)  )
I presume you restarted networking (via reboot after disabling NIC)? 
Current results of **ifconfig -a**?

(The routing table may need to be "cleaned up" if it still references disabled interface.)

---

### Post by evollusion on 2008-08-18
> **Iowan said:**
> That machine has 2 NIC's? 
 Can you verify which (physical) card got disabled (MAC address printed on it)? 
(just won't work to plug into the disabled card ;)  )
I presume you restarted networking (via reboot after disabling NIC)? 
Current results of **ifconfig -a**?

(The routing table may need to be "cleaned up" if it still references disabled interface.)

if config still references the interface, although it has no IP address.  The disabled one is an onboard card that can be kind of flaky, the eth1 interface is a nic that I've added on a PCI slot.

---

### Post by bab1 on 2008-08-18
Can you ping 127.0.0.1 ?  Do I see that you are trying to ping yourself and getting host unreachable?

---

### Post by evollusion on 2008-08-18
Yes, I'm able to ping my interface, as well as the loopback.  The interface is showing as up.  It's just when I try to get to the gateway that thinks go squirrelly

---

### Post by pparks1 on 2008-08-18
Evolussion.

It looks like your computer is in the 192.168.1.x network, but you screenshot shows you are pinging 192.168.0.1 as the gateway.  Is your gateway 192.168.1.1????

---

### Post by bab1 on 2008-08-18
> 
Code:

From 192.168.1.115 icmp_seq=1 Destination Host Unreachable
From 192.168.1.115 icmp_seq=2 Destination Host Unreachable
From 192.168.1.115 icmp_seq=3 Destination Host Unreachable
From 192.168.1.115 icmp_seq=4 Destination Host Unreachable



So you are saying that the above was from you trying to ping 192.168.1.1?

Are there any other hosts (computers) on this network.  Can you ping them?  When ever I see a host unreachable return, I go and check to see if the host is indeed running.  The unreachable statement means it knows of the host but can't find it on the network.

---

### Post by pparks1 on 2008-08-18
Destination Host Unreachable usually indicates a significant network config problem rather than a downed host.  Its pretty much a plea that it simply is unable to find the network that the host is located on.   I suspect the gateway is improperly configured on the host.


Can you give us a screenshot of your interfaces file for the NIC that is active?  I believe you said it was ETH1 as ETH0 is a bit flakey.

---

### Post by bab1 on 2008-08-18
pparks1  -- Not true.  If I ping one of my local hosts that are down, I get host unreachable.  The key work is "host".  If you ping something that does not exist it will not return anything.  I bet his router and/or the Ubuntu host needs a reboot.  The erroneous GW IP was an example by someone else.

---

### Post by pparks1 on 2008-08-18
Sorry, I was thinking destination network unavailable.   My bad.   Destination host unreachable could indeed be a host which is down.

---

### Post by Iowan on 2008-08-19
You've verified cables (and types - crossover vs straight) and router, hub and/or switch ports?

---

