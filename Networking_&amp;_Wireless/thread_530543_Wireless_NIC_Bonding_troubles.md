---
title: "Wireless NIC Bonding troubles"
date: 2007-08-20
forum: Networking &amp; Wireless
---

### Post by sricketts on 2007-08-20
I am trying to set up host-to-host wireless link between two ubuntu machines. Each has two wireless NICs with Atheros chipsets (ath0 and ath1). Let's call my two machines host A and host B. I would like to put each card in ad hoc mode and configure so that there is a link between A.ath0 and B.ath0 on channel 1 and between A.ath1 and B.ath1 on channel 11. 

Then on each machine I want to use the linux bonding driver in round-robin mode to bond the ath0 and ath1 devices into one virtual interface in an attempt to increase streaming throughput between the two machines.

So far I have successfully set up the ad hoc links. They can run at the same time in parallel with good throughput (around 30 Mb/s). However, I cannot bond the interfaces. I am trying the following:

```

modprobe bonding miimon=100 mode=0
ifconfig bond0 192.168.1.XXX
ifenslave bond0 ath0 ath1
```

where XXX is 114 for host A and 113 for host B.

Then I configure the ad hoc links using madwifi tools:

```
/etc/dbus-1/event.d/25NetworkManager stop
wlanconfig ath0 destroy
wlanconfig ath0 create wlandev wifi0 wlanmode adhoc
iwconfig ath0 essid 'adhoc0'
iwconfig ath0 channel 1
iwconfig ath0 key 'password'
ifconfig ath0 up
ifconfig ath0 192.168.0.YYY
ifconfig ath0 netmask 255.255.255.0
ifconfig ath0 broadcast 192.168.0.255

wlanconfig ath1 destroy
wlanconfig ath1 create wlandev wifi1 wlanmode adhoc
iwconfig ath1 essid 'adhoc1'
iwconfig ath1 channel 11
iwconfig ath1 key 'password'
ifconfig ath1 up
ifconfig ath1 192.168.2.YYY
ifconfig ath1 netmask 255.255.255.0
ifconfig ath1 broadcast 192.168.2.255

```

Where YYY is 100 for host A and 101 for host B. After this I can ping over each of the ad hoc links (i.e. ping -I ath1 192.168.2.101 from host A). But a ping over the virtual link does not work (i.e. ping -I bond0 192.168.1.113 from host A).

The bonding instructions I quoted above work for a similar setup with wired ethernet links instead of wireless. I have also tried using arp instead of mii when loading the bonding driver -- same problem.

Any ideas?

Thanks,
S.

---

### Post by netztier on 2007-08-21
> **sricketts said:**
> Then I configure the ad hoc links using madwifi tools:

```
/etc/dbus-1/event.d/25NetworkManager stop
wlanconfig ath0 destroy
wlanconfig ath0 create wlandev wifi0 wlanmode adhoc
iwconfig ath0 essid 'adhoc0'
iwconfig ath0 channel 1
iwconfig ath0 key 'password'
ifconfig ath0 up
[COLOR="Red"]ifconfig ath0 192.168.0.YYY
ifconfig ath0 netmask 255.255.255.0
ifconfig ath0 broadcast 192.168.0.255[/COLOR]

wlanconfig ath1 destroy
wlanconfig ath1 create wlandev wifi1 wlanmode adhoc
iwconfig ath1 essid 'adhoc1'
iwconfig ath1 channel 11
iwconfig ath1 key 'password'
ifconfig ath1 up
[COLOR="Red"]ifconfig ath1 192.168.2.YYY
ifconfig ath1 netmask 255.255.255.0
ifconfig ath1 broadcast 192.168.2.255[/COLOR]

```

The bonding instructions I quoted above work for a similar setup with wired ethernet links instead of wireless. I have also tried using arp instead of mii when loading the bonding driver -- same problem.


I don't think it actually matters much, but in such a setup, the individual links/interfaces should not have IP addresses. It's the virtual bond0 interface that gets the IP configuration with address, netmask and broadcast statements. Although, upon second reading, I saw that you nicely kept all subnets separate, each one per physical link and a third for the virtual one.

The other thing was: I remember reading about bonding that the member interfaces (or their drivers/kernel modules, at that) needed to support the ethtool interface - at least for some bonding modes. That's something 802.11 interfaces/drivers probably can't.

If bonding will ultimately fail, you might think along the following lines for another approach:

[LIST]
[*]Setup each link individually with a small subnet (netmask 255.255.255.252 will do), basically just like you did.
[*]With some advanced routing techniques, it should be possible to distribute packets to the two links at the network layer (layer 3, IP) instead of the data link layer (layer 2, Ethernet), just like if you have two routers connected directly to each other by two equal-cost links. 
[*]It possibly requires that you configure these two machines as actual Linux based routers. This will of course require a bit of knowledge about the Linux Kernel's routing capabilities - that I don't have myself (I could do it within a few minutes with two Cisco Routers - but with Linux, it'd take me a while or two).
[/LIST]

[I]Edit:
Oh - and the most important question: What does **dmesg** or **/var/log/syslog** say when the bond is formed? I think it reports if the member interfaces of the link bundle have been (un)successfully "enslaved". If something goes wrong, the output should have some hints...[/I]

best regards

Marc

---

### Post by mips on 2007-08-21
> **netztier said:**
> I don't think it actually matters much, but in such a setup, the individual links/interfaces should not have IP addresses. It's the virtual bond0 interface that gets the IP configuration with address, netmask and broadcast statements. 

Agreed.

---

### Post by sricketts on 2007-08-22
> **netztier said:**
> I don't think it actually matters much, but in such a setup, the individual links/interfaces should not have IP addresses.

I basically have two subroutines here: (1) the bonding setup, and (2) the ad hoc links setup. In the procedure described in my post, yes, the interfaces have IP addresses because I setup the ad hoc links after setting up the bonding. Actually, I have also tried the other way around -- setting up the links (and subnets) first, then setting up the bonding. In this case, the interfaces lose their IP configuration when the bonding is fired up. Moreover, I cannot ping the individual links (e.g. ping -I ath1 192.168.2.101 from host A) as I could in the case where they do have IPs.

> **netztier said:**
> The other thing was: I remember reading about bonding that the member interfaces (or their drivers/kernel modules, at that) needed to support the ethtool interface - at least for some bonding modes. That's something 802.11 interfaces/drivers probably can't.

This would certainly be a problem, but apparently wireless NIC bonding is possible according to
[LIST]
[*][http://www.linuxhelp.net/forums/index.php?showtopic=8478&pid=28390&st=0&#entry28390](http://www.linuxhelp.net/forums/index.php?showtopic=8478&pid=28390&st=0&#entry28390)
[*][http://ubuntuforums.org/showthread.php?t=99668](http://ubuntuforums.org/showthread.php?t=99668) (specifically trubblemaker's posts)
[/LIST]

> **netztier said:**
> 
[LIST]
[*]Setup each link individually with a small subnet (netmask 255.255.255.252 will do), basically just like you did.
[*]With some advanced routing techniques, it should be possible to distribute packets to the two links at the network layer (layer 3, IP) instead of the data link layer (layer 2, Ethernet), just like if you have two routers connected directly to each other by two equal-cost links. 
[*]It possibly requires that you configure these two machines as actual Linux based routers. This will of course require a bit of knowledge about the Linux Kernel's routing capabilities - that I don't have myself (I could do it within a few minutes with two Cisco Routers - but with Linux, it'd take me a while or two).
[/LIST]


This is something I will certainly look into, although I have zero experience with any kind of advanced routing. I will google some howtos unless someone has a suggestion for a place to start.

> **netztier said:**
> [I]Edit:
Oh - and the most important question: What does **dmesg** or **/var/log/syslog** say when the bond is formed? I think it reports if the member interfaces of the link bundle have been (un)successfully "enslaved". If something goes wrong, the output should have some hints...[/I]

Ah yes, I definitely should have checked this before I posted. Here is the output. It may support the theory that the interfaces need to support ethtool, although as a bonding novice I am not entirely sure how to interpret this.

```

[17331887.456000] Ethernet Channel Bonding Driver: v3.0.3 (March 23, 2006)
[17331887.456000] bonding: ARP monitoring set to 2000 ms with 1 target(s): 192.168.1.113
[17331887.468000] ADDRCONF(NETDEV_UP): bond0: link is not ready
[17331887.552000] bonding: bond0: Warning: failed to get speed and duplex from ath0, assumed to be 100Mb/sec and Full.
[17331887.552000] bonding: bond0: enslaving ath0 as an active interface with an up link.
[17331887.600000] bonding: bond0: Warning: failed to get speed and duplex from ath1, assumed to be 100Mb/sec and Full.
[17331887.600000] bonding: bond0: enslaving ath1 as an active interface with an up link.
[17331888.460000] ADDRCONF(NETDEV_CHANGE): bond0: link becomes ready
[17331889.472000] bonding: bond0: interface ath0 is now down.
[17331889.472000] bonding: bond0: interface ath1 is now down.
[17331889.472000] bonding: bond0: now running without any active interface !
```

---

### Post by netztier on 2007-08-22
> **sricketts said:**
> In this case, the interfaces lose their IP configuration when the bonding is fired up. Moreover, I cannot ping the individual links (e.g. ping -I ath1 192.168.2.101 from host A) as I could in the case where they do have IPs.


Well, that's the way it's supposed to work - you can't ping individual interfaces on a link bundle. For the sake of comparison: If you aggregate multiple links between switches, the bundle becomes a logical single link. In terms of routing, spanning-tree, CAM tables (the switch's internal port-to-mac-address table), the link bundle is "one" port. Hence you won't be able to ping any member interfaces of a link bundle.


> **sricketts said:**
> 
```

...
[17331888.460000] ADDRCONF(NETDEV_CHANGE): bond0: link becomes ready
[COLOR="Red"][17331889.472000] bonding: bond0: interface ath0 is now down.
[17331889.472000] bonding: bond0: interface ath1 is now down.
[/COLOR][17331889.472000] bonding: bond0: now running without any active interface 
```

That's where it obviously goes wrong. Have you tried to rename the interfaces to be ethX instead of athX, as suggested by one of the threads you posted a link to? Fiddling around with **/etc/iftab** might help here.

best regards

Marc

---

### Post by sricketts on 2007-08-22
Thanks for the suggestions.

> **netztier said:**
> 
That's where it obviously goes wrong. Have you tried to rename the interfaces to be ethX instead of athX, as suggested by one of the threads you posted a link to? Fiddling around with **/etc/iftab** might help here.


I tried renaming the interfaces by adding

```

eth1 mac 01:23:45:67:89:10
eth2 mac 10:98:76:54:32:10

```

to /etc/iftab (with correct mac addresses obtained from ifconfig). This renaming step worked only on one of the machines. Regardless, on the machine that renaming was sucessful I tried to bond the eth1 and eth2 interfaces using the same commands as before. However, dmesg gives the same messages.

I have also tried using wlanconfig to create the VAP as ethX instead of athX. In this case the links do not work.

So it seems like renaming might not help here, unless there is something I am doing wrong.

Thanks,
S.

---

### Post by trubblemaker on 2007-08-22
K I've gotten this working but I used 2 different aps and although I did get added reliability I did not get any boost in speed.  I'll post my script that got it working in a little bit, 
(I'm not on the computer with the scirpt)

basically:

I set up the bonding, 
associated the wireless cards to the aps, 

I was using a network where both aps used the same essid but don't believe this to be an issue.

I can't remeber if I posted a howto but will post my script that works.

---

### Post by trubblemaker on 2007-08-24
sorry I haven't read into your problem too deep, my life's really busy but here is the script that I used to successfully get nic bonding.
```

#/bin/bash
sudo ifconfig wlan0 down
sudo ifconfig bond0 down
sudo ifconfig eth1 down
sudo ifconfig eth2 down
sudo ip link set dev wlan0 name eth1
sudo ifconfig eth2 up
sudo ifconfig eth1 up
sleep 2
sudo iwconfig eth1 essid ubc
sudo iwconfig eth2 essid ubc
sudo ifconfig bond0 192.168.1.100 up # static address
sudo ifenslave bond0 eth1 eth2
sudo dhclient bond0
```

on occassion I had to manipulate my two wireless cards to associate them to an ap.  I always associated to two different apps as I was looking for speed testing.  I did some work on using just one app but I can't rember my results.

---

### Post by sricketts on 2007-08-24
Thanks to trubblemaker and netztier for the suggestions.

I have tried two more approaches. First of all, I wanted to continue to test the hypothesis that the bonding tool does not like names like ath0. So I took from trubblemaker's script the line that changes the name of wlan0 and inserted it into my script for setting up the ad hoc links.

```

/etc/dbus-1/event.d/25NetworkManager stop
wlanconfig ath0 destroy
wlanconfig ath0 create wlandev wifi0 wlanmode adhoc
ip link set dev ath0 name eth1
iwconfig eth1 essid 'adhoc0'
iwconfig eth1 channel 1
iwconfig eth1 key 'password'
ifconfig eth1 up
ifconfig eth1 192.168.0.YYY
ifconfig eth1 netmask 255.255.255.0
ifconfig eth1 broadcast 192.168.0.255

wlanconfig ath1 destroy
wlanconfig ath1 create wlandev wifi1 wlanmode adhoc
ip link set dev ath0 name eth2
iwconfig eth2 essid 'adhoc1'
iwconfig eth2 channel 11
iwconfig eth2 key 'password'
ifconfig eth2 up
ifconfig eth2 192.168.2.YYY
ifconfig eth2 netmask 255.255.255.0
ifconfig eth2 broadcast 192.168.2.255

```

After running this script I have my two links connected successfully. However, when I apply my bonding script, everything dies. I cannot ping via the bond0, eth1, or eth2 interfaces. (same dmesg errors as before)

Another approach as suggested by netztier was to use advanced linux routing. A howto describes using **tc** to achieve round-robin load balancing just like the bonding driver. [http://lartc.org/howto/lartc.loadshare.html](http://lartc.org/howto/lartc.loadshare.html)

After running the ad hoc script, I followed this howto closely but not exactly. I ran the following:
```

tc qdisc add dev eth1 root teql0
tc qdisc add dev eth2 root teql0
ip link set dev teql0 up

```
After running this I could no longer ping over my ad hoc links or through teql0. So I followed the next step to setup subnets.

On host A:
```

ip addr add dev eth1 10.0.0.0/31
ip addr add dev eth2 10.0.0.2/31
ip addr add dev teql0 10.0.0.4/31

```
On host B:
```

ip addr add dev eth1 10.0.0.1/31
ip addr add dev eth2 10.0.0.3/31
ip addr add dev teql0 10.0.0.5/31

```
However, this did not change the IPs according to ifconfig. So I then ran the same commands but with **ifconfig** in place of **ip addr add dev**. This changed the IPs, but did not reestablish the links.

So still no success, although somehow I still feel like this should be possible.

Thanks,
S.

---

### Post by sricketts on 2007-12-13
Update: I finally got the bond to "work" in the sense that I can ping between the bond0 interfaces. I had to move the bond0 interfaces to a different subnet from the ath* interfaces:

```
modprobe bonding miimon=100 mode=0
ifconfig bond0 192.168.2.XXX
ifenslave bond0 ath0 ath1
```

However, pinging between the bond0 interfaces is extremely slow (about .29 ms) and packet loss is like 80+%. For example, I am running ping right now, and the icmp_seq numbers go like 4, 11, 15, 19, 23, 27, 31, 35, 39, and I can type the numbers into this post faster than they are showing up in the terminal.

I can't run iperf to get throughput measurements -- it just hangs after establishing the connection.

How can I figure out where the packets are going? Do I need to put some printfs in the bonding driver code and recompile? Is there a tool that would help me here?

Thanks,
S.

---

