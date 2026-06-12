---
title: "Host to host NIC bonding works only in one direction"
date: 2007-07-18
forum: Networking &amp; Wireless
---

### Post by sricketts on 2007-07-18
I am trying to set up a host-to-host link between two ubuntu machines. I would like to use NIC bonding so that the link is made of two (or more) wired ethernet channels. My NICs support 100 Mb/s. In one direction (host a to host b), I can get about 190 Mb/s measured with iperf. In the other, however, I am only getting about 95 Mb/s.

My setup is as follows. Host A has a Broadcom BCM4401-B0 and a US Robotics USR997902. Host B has an Intel Pro 100 VE and a Realtek RTL-8139. Each machine also has a third NIC installed that I am not using. The Broadcom is wired directly to the Realtek, and the USR to the Intel. To configure the bonding, I first run mii-tool to make sure my links are ok. Then on each host I run

```
modprobe bonding miimon=100
ifconfig bond0 <addr>
ifenslave bond0 ethX ethY
```

where <addr> is the address of the other host and ethX and ethY are the appropriate devices. These instructions come from an example in Documentation/networking/bonding.txt.

To measure the performance, I use iperf. I have tried both TCP and UDP. In both cases, the throughput is at 190 Mb/s when host a is the client and host b is the server, but when the opposite is true, the throughput is 95 Mb/s.

A quick check of ifconfig shows that the USR on host a has only received 93 packets after running several performance tests, while the Broadcom has received about 300,000. However, their TX levels are both at about 350,000. So it seems the Intel->USR channel works only in one direction under the bonding.

Any ideas? What other kind of output would help debug this problem?

Thanks,
S.

---

### Post by VorDesigns on 2007-07-18
Based on what I know of NIC Bonding or Teaming, the process combines the potential throughput of two or more NICs making them appear as a single NIC.  From what I can tell by your post, you aren't letting the NICs do that because you cabling the NICs independently into other independent devices. IE., NICa0 crossovered to NICb0 and NICa1 crossovered to NICb1.
This would seem to defeat the configuration as to how the functionality is supposed to work IMO.
You also seem to be missing by the sin of omission, one of the other required pieces of a properly functioning bonded ethernet channel.  That is, a switch capable of handling the link aggregation as per the IEEE 802.3 standard.  To be honest, I have not spent a lot of time looking at this feature but, you need to have all the elements necessary in place before you can even begin to test throughput.

---

### Post by sricketts on 2007-07-18
Thanks for your thoughts, Vor.

At first I too thought a switch was necessary, until I saw this (there is an example for host to host for double speed):

[http://www.kernel.org/pub/linux/kernel/people/marcelo/linux-2.4/Documentation/networking/bonding.txt](http://www.kernel.org/pub/linux/kernel/people/marcelo/linux-2.4/Documentation/networking/bonding.txt)

Moreover, I am getting about double the performance in one direction, which leads me to believe that I am doing at least something right. In any case, I would like to be able to do this without a switch. 

My understanding was that by enslaving two devices to bond0, the devices all share the same IP address. So my naive interpretation is that the following happens when data is sent through A.bond0 - the bonding driver stripes the data across the slave interfaces. The slave interfaces then try to send to the destination. For both interfaces, their crossover neighbors match the IP of the destination, so they just go ahead and send there. Then the slaves at the other end send the data along to B.bond0, with the help of the bonding driver which orders the striped data.

---

### Post by VorDesigns on 2007-07-18
This may not be pertinent for the current Kernel and I have only toyed with this in the MS arena but, you may find some throughput increases via adjustments that you can find here:
[Enabling High Performance Data Transfers]("http://www.psc.edu/networking/projects/tcptune/")

---

### Post by sricketts on 2007-07-18
Thanks for the pointer. Unfortunately my application is using RTP over UDP. I should be clear about my goals. I would like eventually to replace the wired NICs with wireless NICs for the purposes of demonstrating a proof of concept. Fine tuning the protocols for higher performance is not as important to me as measuring the scalability of the bonding driver as it applies to wireless NICs.

As a first step, I want to build a wired setup. Like I said, my current setup works fine in one direction, but not at all in the other. I think this reveals a hole in my approach -- perhaps as you suggested the host-to-host scheme is just not possible. However, I think it is possible, and that there is a better explanation for my problem.

S.

---

### Post by VorDesigns on 2007-07-20
I still think you need a switch.  
Wireless wouldl require an access point even if you configure the wireless NICs to act as an AP on one or the other system.
You might take a look at [http://www.howtoforge.com/network_card_bonding_centos]("http://www.howtoforge.com/network_card_bonding_centos") and or [http://www.howtoforge.com/network_bonding_ubuntu_6.10]("http://www.howtoforge.com/network_bonding_ubuntu_6.10") for additional configuration suggestions looking specifically at the mode settings.

---

### Post by netztier on 2007-07-20
> **sricketts said:**
> I
Any ideas? What other kind of output would help debug this problem?


Remember: a bond of n 100Mbps links is NOT a n00Mbps connection, but a n x 100Mbps connection. Like a freeway with the same speed limit, but more lanes. For a bond to work, you don't actually need a switch - its just mandatory that both ends agree on how the bond is formed (manual, LACP, cisco-proprietary PAgP).

Then it is of great importance how a bond chooses the link to sent a particular frame through.

In general, this is done by XORing the last n bits of the source- and destination MAC addresses, with some modulo of the number of links (ore something alike). The result is a binary number representing the link number to use. For two links, one bit is used, for four links it's 2, for eight links it's three bits

So with this mode, and a direct computer-to-computer connection, this operation will always calculate the same link number, and you should get only the throughput of one link.
(I'm still thinking why you reached 195Mbit/s).

You could configure the bonding to do round-robin at *both* ends, so the frames get distributed statistically 50/50 on the two links. The downside of this might be that you could get out-of-order packet delivery and TCP throughput might drop a bit.

So again: which bonding mode has been configured? Do the settings match at both ends?

best regards

Marc

---

### Post by sricketts on 2007-07-20
> **netztier said:**
> You could configure the bonding to do round-robin at *both* ends, so the frames get distributed statistically 50/50 on the two links.

So again: which bonding mode has been configured? Do the settings match at both ends?


My intention was to use the round-robin mode. I did not explicitly set that parameter when I loaded the bonding module because I thought it was default. I went back and changed my script to include mode=0 for round-robin -- still the same problem though. To be clear, I ran the following on both machines:

```
modprobe bonding miimon=100 mode=0
ifconfig bond0 <addr>
ifenslave bond0 ethX ethY
```

where <addr> is the IP address of the other host and ethX and ethY are the appropriate device names.

> **netztier said:**
> For a bond to work, you don't actually need a switch - its just mandatory that both ends agree on how the bond is formed (manual, LACP, cisco-proprietary PAgP).

I'm not quite sure what this means. Since I use the same script to configure on both ends, I assume they "agree" in some sense. Or is there something else I should do?

Thanks,
S.

---

### Post by sricketts on 2007-07-20
I thought maybe there might be a duplex mismatch problem on the channel that is causing trouble. I used *mii-tool -F 100baseTx-FD ethX* to force 100 Mb, full duplex on both ends. Unfortunately, I am still getting half performance in one direction as in the other.

---

### Post by netztier on 2007-07-21
> **sricketts said:**
> I thought maybe there might be a duplex mismatch problem on the channel that is causing trouble. I used *mii-tool -F 100baseTx-FD ethX* to force 100 Mb, full duplex on both ends. Unfortunately, I am still getting half performance in one direction as in the other.

That's good thinking - especially the bit about fixing duplex at *both* ends. 

You could check beforehand: **mii-tool** and **ethtool** are good for that; they even show which modes the link peer had advertised during the autoneg process. If autoneg successfully resulted in a FullDuplex configuration, there's no need to configure things manually.

I still wonder what could be wrong, though. Did you check if any or both of the cards support TCP checksum offloading in either or both Rx and Tx directions and if it is enabled on all cards in the bond? That could help to boost throughput, but it still wouldn't explain the difference.

Let me think and try to be systematic. Let's not use iPerf's terms of "server" and "client", because they're inverted to the way we would normally use them. Let's rather talk about a *sender* (that's where iperf runs as **iperf -c <ip-address>**) and a *receiver* (running **iperf -s**).

So we're having System A and System B.

```
**Sender   Receiver	troughput	traffic on Link1	traffic on Link2**
A          B              190Mbit		yes			yes
B          A	           95Mbit	         no			yes

```

[COLOR="Red"]Hm.. leads me to believe that on system B, the bonding driver does not distribute traffic amongst the member links in the bond.[/COLOR] Other possible explanation: system A has more trouble to handle the possible out-of-order packet delivery that might occur - but I don't think that this is the problem, because it wouldn't half the throughput so precisely.

Are all these NICs the same, same kernel versions, same modules? Do outputs in dmesg or syslog confirm the successful bonding of the links on system A and system B?

Some thoughts about using a Wireless bond: the idea seems clever, but I don't really see the benefit (yet) - associating them with a different WLAN access points would require some really advanced stuff on the WLAN bridges and the Switches behind them.

Associating them the same AP and  channel would most probably  achieve nothing but a quite busy channel, collisions, backoffs and bad throughput. WLAN is still a "shared medium" (per non-overlapping channel) with all the drawbacks that come with the 
package. If you thing that the net throughput of a single WLAN channel (25-27MBit/s) won't be good enough, think of using **802.11n** instead of 802.11a/b/g. Here, the "bonding" logic is  already implemented "in hardware", it's that MIMO thing these NICs and APs do (Multiple Input, Multiple Output). 

If it's not about associating the WLAN NICs with AccessPoints but about a point-to-point connection between two hosts, it might work - as long as you make sure that each "Link" uses a channel that does not overlap with the other and you make sure that there is not too much latency difference between them. I imagine that out-of-order packet delivery on UDP could be somewhat more difficult ot to handle than on TCP. OTOH, I don't know too much about RTP and it's capabilities in that context, so I better don't play clever here.

best regards

Marc

---

### Post by sricketts on 2007-07-23
Thanks for the suggestions, netztier.

> **netztier said:**
> Are all these NICs the same, same kernel versions, same modules? Do outputs in dmesg or syslog confirm the successful bonding of the links on system A and system B?

The NICs are all different. System A has a Broadcom BCM4401-B0 and a US Robotics USR997902. System B has an Intel Pro 100 VE and a Realtek RTL-8139. System A is running 2.6.20-16-generic, while System B is running 2.6.17-11-generic.

The dmesg output seems to confirm the success of the bonding. Here is the dmesg output on System A

```
[  121.668777] Ethernet Channel Bonding Driver: v3.1.1 (September 26, 2006)
[  121.668786] bonding: MII link monitoring set to 100 ms
[  121.677646] ADDRCONF(NETDEV_UP): bond0: link is not ready
[  121.709307] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  121.723359] bonding: bond0: enslaving eth0 as an active interface with a down link.
[  121.756945] r8169: eth1: link up
[  121.772893] bonding: bond0: enslaving eth1 as an active interface with an up link.
[  122.177902] ADDRCONF(NETDEV_CHANGE): bond0: link becomes ready
[  123.703387] b44: eth0: Link is up at 100 Mbps, half duplex.
[  123.703392] b44: eth0: Flow control is off for TX and off for RX.
[  123.704439] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  123.725274] bonding: bond0: link status definitely up for interface eth0.
[  127.216863] bond0: no IPv6 routers present
[  127.226843] eth1: no IPv6 routers present
[  128.999588] eth0: no IPv6 routers present
```

and on System B...

```
[17412373.568000] Ethernet Channel Bonding Driver: v3.0.3 (March 23, 2006)
[17412373.568000] bonding: MII link monitoring set to 100 ms
[17412373.584000] ADDRCONF(NETDEV_UP): bond0: link is not ready
[17412373.640000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[17412373.640000] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
[17412373.656000] bonding: bond0: enslaving eth0 as an active interface with an up link.
[17412373.660000] eth1: link up, 10Mbps, half-duplex, lpa 0x0000
[17412373.684000] bonding: bond0: enslaving eth1 as an active interface with an up link.
[17412374.576000] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[17412374.580000] ADDRCONF(NETDEV_CHANGE): bond0: link becomes ready
[17412384.356000] eth1: no IPv6 routers present
[17412385.152000] bond0: no IPv6 routers present
[17412393.984000] eth0: no IPv6 routers present
```

In this instance A.eth0 is linked to B.eth1. The dmesg output suggests that this link is at half duplex, while mii-tool says full duplex on both ends. I'm not sure why this is the case.

> **netztier said:**
> If it's not about associating the WLAN NICs with AccessPoints but about a point-to-point connection between two hosts, it might work - as long as you make sure that each "Link" uses a channel that does not overlap with the other and you make sure that there is not too much latency difference between them.

Yes, this is the plan. I don't know if it will work -- I think it is an interesting enough experiment to try though.

---

### Post by sricketts on 2007-07-23
Also, here is the iperf output for the bad direction (System B to System A)

```
sricketts@blink2:~$ iperf -c 192.168.1.113 -u -b 300M
------------------------------------------------------------
Client connecting to 192.168.1.113, UDP port 5001
Sending 1470 byte datagrams
UDP buffer size:   105 KByte (default)
------------------------------------------------------------
[  3] local 192.168.1.114 port 32815 connected with 192.168.1.113 port 5001
[  3]  0.0-10.0 sec    228 MBytes    191 Mbits/sec
[  3] Sent 162752 datagrams
[  3] Server Report:
[  3]  0.0-10.0 sec    114 MBytes  95.7 Mbits/sec  0.259 ms 81375/162750 (50%)
[  3]  0.0-10.0 sec  1 datagrams received out-of-order
```

Notice the report of 191 Mbits/sec initially and then 95.7 in the server report. I don't know the meaning of the first number as opposed to the second, and the user docs for iperf did not help.

---

### Post by netztier on 2007-07-24
> **sricketts said:**
> 
The dmesg output seems to confirm the success of the bonding. Here is the dmesg output on System A

```
[  121.668777] Ethernet Channel Bonding Driver: v3.1.1 (September 26, 2006)
[  121.668786] bonding: MII link monitoring set to 100 ms
[  121.677646] ADDRCONF(NETDEV_UP): bond0: link is not ready
[  121.709307] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  121.723359] bonding: bond0: enslaving eth0 as an active interface with a down link.
[  121.756945] r8169: eth1: link up
[  121.772893] bonding: bond0: enslaving eth1 as an active interface with an up link.
[  122.177902] ADDRCONF(NETDEV_CHANGE): bond0: link becomes ready
[COLOR="Red"][  123.703387] b44: eth0: Link is up at 100 Mbps, half duplex.[/COLOR]
[  123.703392] b44: eth0: Flow control is off for TX and off for RX.
[  123.704439] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  123.725274] bonding: bond0: link status definitely up for interface eth0.
[  127.216863] bond0: no IPv6 routers present
[  127.226843] eth1: no IPv6 routers present
[  128.999588] eth0: no IPv6 routers present
```

and on System B...

```
[17412373.568000] Ethernet Channel Bonding Driver: v3.0.3 (March 23, 2006)
[17412373.568000] bonding: MII link monitoring set to 100 ms
[17412373.584000] ADDRCONF(NETDEV_UP): bond0: link is not ready
[17412373.640000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[17412373.640000] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
[17412373.656000] bonding: bond0: enslaving eth0 as an active interface with an up link.
[COLOR="Red"][17412373.660000] eth1: link up, 10Mbps, half-duplex, lpa 0x0000[/COLOR]
[17412373.684000] bonding: bond0: enslaving eth1 as an active interface with an up link.
[17412374.576000] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[17412374.580000] ADDRCONF(NETDEV_CHANGE): bond0: link becomes ready
[17412384.356000] eth1: no IPv6 routers present
[17412385.152000] bond0: no IPv6 routers present
[17412393.984000] eth0: no IPv6 routers present
```

In this instance A.eth0 is linked to B.eth1. The dmesg output suggests that this link is at half duplex, while mii-tool says full duplex on both ends. I'm not sure why this is the case.


There's a problem around the duplex mode of the links. If I recall correctly, Cisco states that for forming what they call FEC (FastEtherChannel, which is their way of a manually configured link bundle), all ports must be of the same speed an duplex setting. This might be true for their switches, I'm not sure if it also pertains to "general" link aggregation.

It might be that a link with duplex mismatch is considered "degraded" and is not actively being used in the bond - in one direction, that is, because the collisions/errors are bound to appear only on one end of the link.

So before creating a bond, I suggest you first debug the individual links and see that you can bring each of them up in FullDuplex mode. Try it with autonegotiation first; the autoneg feature can be considered mature enough to trust it. Only go back to manual duplex configuration if really necessary. Test each link in both directions to see if you get the full FasEthernet speed of ~95Mbit/s. 

Then proceed with aggregating the link afterwards.

best regards

Marc

---

### Post by sricketts on 2007-07-30
> **netztier said:**
> So before creating a bond, I suggest you first debug the individual links and see that you can bring each of them up in FullDuplex mode. Try it with autonegotiation first; the autoneg feature can be considered mature enough to trust it. Only go back to manual duplex configuration if really necessary. Test each link in both directions to see if you get the full FasEthernet speed of ~95Mbit/s. 


With 2 NICs on both ends (Host A has a Broadcom BCM4401-B0 and a US Robotics USR997902, Host B has an Intel Pro 100 VE and a Realtek RTL-8139) I have 4 possible links. I went through each of the four links and below I describe the results. The problem NIC seems to be the Broadcom BCM4401-B0.

First, the broadcom -- Realtek link. I tried restarting autonegotiation, and got the following...
```
sricketts@dimE521:~$ sudo mii-tool -r eth0
restarting autonegotiation...
sricketts@dimE521:~$ sudo mii-tool
eth0: no autonegotiation, 100baseTx-HD, link ok
```
...even though the other side of the link is reporting...
```
eth0: negotiated, 100baseTx-FD flow control, link ok
```
Still, in this case I get 95 Mb/s over the single link in both directions. When I try to force full duplex on the broadcom NIC, I get...
```
sricketts@dimE521:~$ sudo mii-tool -F 100baseTx-FD
sricketts@dimE521:~$ sudo mii-tool
eth0: 100 Mbit, full duplex, no link
```
...even though ethtool says that 100baseT/Full is supported by eth0.

Then I changed the link so it went from the broadcom to the other NIC on the other machine (Intel Pro 100 VE). Under this scenario, mii-tool shows autonegotiation working fine, with 100baseTx-FD on both ends. However, iperf gives some strange behavior. With the broadcom as the client, I can't get a connection (ping works).

```
sricketts@dimE521:~$ iperf -c 192.168.1.114 -u -b 400M
write2 failed: Connection refused
------------------------------------------------------------
Client connecting to 192.168.1.114, UDP port 5001
Sending 1470 byte datagrams
read failed: Connection refused
[  3] WARNING: did not receive ack of last datagram after 1 tries.
UDP buffer size:   126 KByte (default)
------------------------------------------------------------
[  3] local 192.168.1.113 port 32772 connected with 192.168.1.114 port 5001
[  3]  0.0- 0.0 sec  17.2 KBytes    276 Mbits/sec
[  3] Sent 12 datagrams
```

With the intel as the client, I can get what seems to be arbitrary throughput by just increasing the *-b* iperf parameter.

```
sricketts@dimE521:~$ iperf -c 192.168.1.113 -u -b 400M
------------------------------------------------------------
Client connecting to 192.168.1.113, UDP port 5001
Sending 1470 byte datagrams
UDP buffer size:   126 KByte (default)
------------------------------------------------------------
[  3] local 192.168.1.113 port 32772 connected with 192.168.1.113 port 5001
[  3]  0.0-10.0 sec    483 MBytes    405 Mbits/sec
[  3] Sent 344622 datagrams
[  3] Server Report:
[  3]  0.0-10.0 sec    482 MBytes    405 Mbits/sec  0.000 ms  522/344621 (0.15%)
[  3]  0.0-10.0 sec  1 datagrams received out-of-order
```

Then I checked the US Robotics -- Realtek link. The autonegotiation did not work at first (even with restart from mii-tool) but after a system reboot everything was working at 100baseTx-FD. The throughput measured by iperf was 95 Mb/s in both directions.

The US Robotics -- Intel link had similar success, with full 95 Mb/s throughput in both directions.

So in summary, building a link from the USR to either of the other NICs is not a problem, while doing so from the broadcom creates quite a mess that I cannot explain.

---

