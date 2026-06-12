---
title: "Bridging 10 Gb/s Internet with brctl (bridge-utilities)"
date: 2016-02-19
forum: Networking &amp; Wireless
---

### Post by Shane_Boissevain on 2016-02-19
I'm attempting to use an Ubuntu Server 14.04 as a network bridge between two 10 Gb/s networks. While the bridge seems to pass traffic to / from the connected machines, it does not play nicely with TCPReplay traffic. The traffic leaves p4p2, enters p1p1,  and i've NO idea why. I've confirmed that everything works when running over the on-board ethernet ports (1 Gb/s network). Here is my setup and what i've done so far.

**[SIZE=3]Network Setup [/SIZE]**
<--> Represents a DAC cable
-- Represents a 'virtual cable' via brctl 

```

Sending Server      Ubuntu Bridge-Server         Receiving-Server
        (p4p2) <--> (p1p1) -- br0 -- (p1p2) <--> (p1p1)

```

What is happening: Traffic leaves p4p2, enters p1p1, is visible on br0, about a second's worth of traffic makes it to p1p2 and hits receiver's p1p1. Then all traffic stops being forwarded from br0 to p1p2 (and consequently receiver's p1p1) until the bridge is destroyed and rebuilt. After destroying the bridge and rebuilding it, a blip of network traffic makes it through and goes quite again until it is rebuilt.....

**[SIZE=4]First Attempt:[/SIZE]**

[SIZE=3]**Ubuntu Bridge-Server:**[/SIZE]
```
# uname -a
    Linux r220-Plus 3.19.0-25-generic #26~14.04.1-Ubuntu SMP Fri Jul 24 21:16:20 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

```
[SIZE=2][B][SIZE=3]
Ubuntu Card Driver Version:
[/SIZE][/B][/SIZE]```
# modinfo ixgbe | grep version
    version:        4.0.1-k
    srcversion:     44CBFE422F8BAD726E61653
    vermagic:       3.19.0-25-generic SMP mod_unload modversions

```
[SIZE=2][B]
Setup the Bridge:[/B][/SIZE]
```

ifconfig p1p1 down
ifconfig p1p2 down
ifconfig p1p1 0.0.0.0
ifconfig p1p2 0.0.0.0
ifconfig p1p1 up
ifconfig p1p2 up
brctl addbr br0
brctl addif br0 p1p1
brctl addif br0 p1p2
# brctl show
    bridge name     bridge id           STP enabled     interfaces
    br0             8000.000cbd06c6c8   no              p1p1
                                                        p1p2
ifconfig br0 up

```
[SIZE=3][B]
Ifconfig:
[/B][/SIZE]```
br0       Link encap:Ethernet  HWaddr 00:0c:bd:06:c6:c8
          inet6 addr: fe80::20c:bdff:fe06:c6c8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 B)  TX bytes:418 (418.0 B)


p1p1      Link encap:Ethernet  HWaddr 00:0c:bd:06:c6:c8
          inet6 addr: fe80::20c:bdff:fe06:c6c8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:1024 (1.0 KB)


p1p2      Link encap:Ethernet  HWaddr 00:0c:bd:06:c6:c9
          inet6 addr: fe80::20c:bdff:fe06:c6c9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:598 (598.0 B)

```

[SIZE=3][B]Sending Server:
[/B][/SIZE]I downloaded a 5 GB pcap file of random network traffic to send over the wire. I'm doing so with tcpreplay, via the command:
```
tcpreplay -tK -i p4p2 ~/testing/5gb.pcap
```



**[SIZE=4]Second Attempt:[/SIZE]**
I noticed that the modinfo for my ixgbe driver was out of date, so i went to Intel's website and snatched up the new one. Upgrading from 4.0.1-k to 4.1.5 was straightforward (RSS=8 b/c 4 cores, hyper-threaded):

```
cd ~/ixgbe-4.1.5/src
make clean
make CFLAGS_EXTRA="-DIXGBE_NO_LRO" RSS=8
rmmod ixgbe
make install
modprobe ixgbe FdirPballoc=3
ifconfig p1p1 up
ifconfig p1p2 up

# modinfo ixgbe | grep version
    version:        4.1.5
    srcversion:     9781CEF8A3110F93FF9DBA8
    vermagic:       3.19.0-25-generic SMP mod_unload modversions

~/ixgbe-4.1.5/scripts/set_irq_affinity p1p1
~/ixgbe-4.1.5//scripts/set_irq_affinity p1p2

```

Unfortunately this had no impact on the behavior of the bridge. I'm at a loss, ANY assistance is appreciated.

---

### Post by Shane_Boissevain on 2016-02-29
SOLVED:

It was ARP. It's always freaking ARP. :-/

Since br0 is acting as a switch, there were arp requests flying everywhere asking who had the appropriate IP addresses. After rewriting the MAC's in the pcap file to be sourced from the Sending Server's NIC and the destination as the Receiving Server's NIC, everything works as expected. 

```
# tcprewrite  --fixcsum --enet-smac=00:0c:bd:06:c6:c8    \
                        --enet-dmac=00:0c:bd:06:c6:c9    \ 
                        --infile=~/5gb.pcap   \
                        --outfile=~/rewrite_5gb.pcap
```

---

