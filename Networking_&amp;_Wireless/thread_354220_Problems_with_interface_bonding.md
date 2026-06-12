---
title: "Problems with interface bonding"
date: 2007-02-05
forum: Networking &amp; Wireless
---

### Post by dionysian_mind on 2007-02-05
I am currently trying to set-up interface bonding (round-robin) on ubuntu server 6.10, amd64, kernel 2.6.17. I am currently experiencing two problems:
1.) when bonding is set up, /proc/net/bonding/bond0 sees both links as up and fine, both NICs have the appropriate same MAC, but it will only transmit and receive on the primary interface (eth0) and only transmit (but not receive) on the secondary interface (eth1) resulting in 50% packet loss.

2.) When I attempt to ifconfig bond0 down, or /etc/init.d/networking restart, or unload the bonding module the computer hard-locks (stops pinging and everything). It does not produce any errors that I can find in logs pertaining to this hard-lock.

This problem is really beginning to frustrate me. Any help would be greatly appreciated.

note: I have tried the following processes, both with the same results:
[http://www.howtoforge.com/nic_bonding](http://www.howtoforge.com/nic_bonding)
[http://www.debianadmin.com/linux-ethernet-bonding-configuration.html#more-77](http://www.debianadmin.com/linux-ethernet-bonding-configuration.html#more-77) (using mode=0, not mode=1)

---

### Post by dionysian_mind on 2007-02-06
nobody? 

sorry, this problem is really driving me nuts.

---

### Post by mips on 2007-02-06
Have you manually specified your duplex & speed ? Are the LAN cards the same or different ?

Post your config files here.

---

### Post by dionysian_mind on 2007-02-15
I have 1 nvidia gigabit card and two netgear gigabit cards. Results do not change if I use only the two netgear cards.

my /etc/modprobe.d/aliases file has the following section:
```
alias bond0 bonding
alias eth0 e100
alias eth1 e100
alias eth2 e100
options bonding mode=0 miimon=100
```


my /etc/modprobe.d/arch/i386 has the following lines:
```
alias bond0 bonding
options bonding mode=0 miimon=100 downdelay=200 updelay=200
```

my /etc/network/interfaces looks like this:
```
auto bond0
iface bond0 inet static
address 10.0.1.253
netmask 255.255.255.0
hwaddress ether de:ad:be:ef:ca:fe
network 10.0.1.0
broadcast 10.0.1.255
gateway 10.0.1.1
post-up /sbin/ifenslave bond0 eth0 eth1 eth2
down /sbin/ifenslave -d bond0 eth0 eth1 eth2
```

This all produces the following ifconfig output:
```

bond0     Link encap:Ethernet  HWaddr DE:AD:BE:EF:CA:FE
          inet addr:10.0.1.253  Bcast:10.0.1.255  Mask:255.255.255.0
          inet6 addr: fe80::dcad:beff:feef:cafe/64 Scope:Link
          UP BROADCAST RUNNING MASTER MULTICAST  MTU:1500  Metric:1
          RX packets:78 errors:0 dropped:0 overruns:0 frame:0
          TX packets:54 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:8502 (8.3 KiB)  TX bytes:5238 (5.1 KiB)

eth0      Link encap:Ethernet  HWaddr DE:AD:BE:EF:CA:FE
          inet6 addr: fe80::dcad:beff:feef:cafe/64 Scope:Link
          UP BROADCAST RUNNING SLAVE MULTICAST  MTU:1500  Metric:1
          RX packets:42 errors:0 dropped:0 overruns:0 frame:0
          TX packets:24 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:4534 (4.4 KiB)  TX bytes:2044 (1.9 KiB)
          Interrupt:50

eth1      Link encap:Ethernet  HWaddr DE:AD:BE:EF:CA:FE
          inet6 addr: fe80::dcad:beff:feef:cafe/64 Scope:Link
          UP BROADCAST RUNNING SLAVE MULTICAST  MTU:1500  Metric:1
          RX packets:17 errors:0 dropped:0 overruns:0 frame:0
          TX packets:15 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1931 (1.8 KiB)  TX bytes:1587 (1.5 KiB)
          Interrupt:58 Base address:0x4000

eth2      Link encap:Ethernet  HWaddr DE:AD:BE:EF:CA:FE
          inet6 addr: fe80::dcad:beff:feef:cafe/64 Scope:Link
          UP BROADCAST RUNNING SLAVE MULTICAST  MTU:1500  Metric:1
          RX packets:19 errors:0 dropped:0 overruns:0 frame:0
          TX packets:15 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:2037 (1.9 KiB)  TX bytes:1607 (1.5 KiB)
          Interrupt:66 Base address:0x6000

```

the /proc/net/bonding/bond0 looks like this: 
```

Ethernet Channel Bonding Driver: v3.0.3 (March 23, 2006)

Bonding Mode: load balancing (round-robin)
MII Status: up
MII Polling Interval (ms): 100
Up Delay (ms): 200
Down Delay (ms): 200

Slave Interface: eth0
MII Status: up
Link Failure Count: 0
Permanent HW addr: 00:50:8d:81:d2:83

Slave Interface: eth1
MII Status: up
Link Failure Count: 0
Permanent HW addr: 00:14:6c:cb:d5:c7

Slave Interface: eth2
MII Status: up
Link Failure Count: 0
Permanent HW addr: 00:14:6c:82:0d:b3

```

and I get ping times that look like this:
```
PING 10.0.1.1 (10.0.1.1) 56(84) bytes of data.
64 bytes from 10.0.1.1: icmp_seq=1 ttl=64 time=0.317 ms
64 bytes from 10.0.1.1: icmp_seq=3 ttl=64 time=0.304 ms
64 bytes from 10.0.1.1: icmp_seq=5 ttl=64 time=0.303 ms
64 bytes from 10.0.1.1: icmp_seq=7 ttl=64 time=0.308 ms
64 bytes from 10.0.1.1: icmp_seq=8 ttl=64 time=0.292 ms
64 bytes from 10.0.1.1: icmp_seq=10 ttl=64 time=0.304 ms
64 bytes from 10.0.1.1: icmp_seq=12 ttl=64 time=0.339 ms
64 bytes from 10.0.1.1: icmp_seq=14 ttl=64 time=0.311 ms
64 bytes from 10.0.1.1: icmp_seq=18 ttl=64 time=0.313 ms
64 bytes from 10.0.1.1: icmp_seq=20 ttl=64 time=0.293 ms

--- 10.0.1.1 ping statistics ---
20 packets transmitted, 10 received, 50% packet loss, time 19006ms
rtt min/avg/max/mdev = 0.292/0.308/0.339/0.020 ms
```

Any ideas?

---

### Post by dionysian_mind on 2007-02-15
*bump*

---

### Post by mips on 2007-02-16
Why are you using the same MAC address on all interfaces ? That is a no-no. They are supposed to be unique hence every ethernet adapter in the world having a unique mac address.

---

### Post by dionysian_mind on 2007-02-16
Bonding automatically sets all interfaces to the same MAC/IP/etc. The [HowtoForge instructions]("http://www.howtoforge.com/nic_bonding") state this should happen:
"You do NOT set up entries for 'eth0' or 'eth1' outside of whats listed above under the 'bond0' entry. Bond0 will now be the interface that the kernel works with. running an 'ifconfig' will show all three interface (bond0,eth0,eth1), all with the same MAC and IP addresses."

Is this information incorrect?

---

### Post by mips on 2007-02-16
> **dionysian_mind said:**
> 

Is this information incorrect?

No. My bad I thought you manually configured them. This is correct.

Try and follow the example in post#3 here [http://www.ubuntuforums.org/showpost.php?p=549356](http://www.ubuntuforums.org/showpost.php?p=549356)

Just change it for your addresses and remove anything you have in addition to this.

What is wrong with your ping times ? Ping is not a very good measurement of speed/throughput.

---

### Post by dionysian_mind on 2007-02-16
the 50% packet loss is the part I'm concerned about.

---

### Post by dionysian_mind on 2007-02-16
Looks like I've found my problem:
```
# ethtool eth0 && ethtool eth1 && ethtool eth2
Settings for eth0:
        Supported ports: [ MII ]
        Supported link modes:   10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
                                1000baseT/Full 
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
                                1000baseT/Full 
        Advertised auto-negotiation: Yes
        Speed: 1000Mb/s
        Duplex: Full
        Port: MII
        PHYAD: 1
        Transceiver: external
        Auto-negotiation: on
        Supports Wake-on: g
        Wake-on: d
        Link detected: yes
Settings for eth1:
        **Supported ports: [ TP ]**
        Supported link modes:   10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
                                1000baseT/Full 
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
                                1000baseT/Full 
        Advertised auto-negotiation: Yes
        Speed: 1000Mb/s
        Duplex: Full
        **Port: Twisted Pair**
        PHYAD: 0
        Transceiver: internal
        Auto-negotiation: on
        Supports Wake-on: pumbg
        Wake-on: g
        Current message level: 0x00000033 (51)
        Link detected: yes
Settings for eth2:
        **Supported ports: [ TP ]**
        Supported link modes:   10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
                                1000baseT/Full 
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
                                1000baseT/Full 
        Advertised auto-negotiation: Yes
        Speed: 1000Mb/s
        Duplex: Full
        **Port: Twisted Pair**
        PHYAD: 0
        Transceiver: internal
        Auto-negotiation: on
        Supports Wake-on: pumbg
        Wake-on: g
        Current message level: 0x00000033 (51)
        Link detected: yes
```

Netgear gigabit cards, presumably any gigabit card using a RealTek chip set, don't support mii. Ordered some cards with marvell chip-set to see if it solves the problem...

---

