---
title: "Network Failover Howto"
date: 2008-05-07
forum: Networking &amp; Wireless
---

### Post by tcpip4lyfe on 2008-05-07
So you have 2 network adapters in your server and you want to configure one of them to fail over if your connection on the other goes down.  It's pretty easy:

```
sudo pico /etc/modules
```
##add this at the bottom
bonding mode=active-backup miimon=100

Save and exit

```
sudo apt-get install ifenslave-2.6
```

Edit your /etc/network/interfaces
```
sudo pico /etc/network/interfaces
```

###Adapter bonding for Eth0 and Eth1
auto bond0
iface bond0 inet static
address 10.0.0.104
netmask 255.255.0.0
gateway 10.0.0.1
post-up ifenslave bond0 eth0 eth1
pre-down ifenslave -d bond0 eth0 eth1


And that's it!

Reboot and test.  


The nitty gritty:


There are several different modes of bonding that can be configured:
Taken from: [http://howtoforge.com/network_bonding_ubuntu_6.10](http://howtoforge.com/network_bonding_ubuntu_6.10)

mode=0

    This mode uses the Round-robin policy: Transmit packets in sequential order from the first available slave through the last. This mode provides load balancing and fault tolerance.  (this is the mode we just setup)

mode=1

    This mode uses an Active-backup policy: Only one slave in the bond is active. A different slave becomes active if, and only if, the active slave fails. The bond's MAC address is externally visible on only one port (network adapter) to avoid confusing the switch. This mode provides fault tolerance. The primary option affects the behavior of this mode.

mode=2

    Transmit based on [(source MAC address XOR'd with destination MAC address) modulo slave count]. This selects the same slave for each destination MAC address. This mode provides load balancing and fault tolerance.

mode=3

    Broadcast policy: transmits everything on all slave interfaces. This mode provides fault tolerance.

mode=4

    IEEE 802.3ad Dynamic link aggregation. Creates aggregation groups that share the same speed and duplex settings. Utilizes all slaves in the active aggregator according to the 802.3ad specification.

          *Pre-requisites:

        1. Ethtool support in the base drivers for retrieving the speed and duplex of each slave.

        2. A switch that supports IEEE 802.3ad Dynamic link aggregation. Most switches will require    some type of configuration to enable 802.3ad mode

mode=5

    Adaptive transmit load balancing: channel bonding that does not require any special switch support. The outgoing traffic is distributed according to the current load (computed relative to the speed) on each slave. Incoming traffic is received by the current slave. If the receiving slave fails, another slave takes over the MAC address of the failed receiving slave.

        *Prerequisite: Ethtool support in the base drivers for retrieving the speed of each slave.

mode=6

    Adaptive load balancing: includes balance-transmit load balancing plus receive load balancing for IPV4 traffic, and does not require any special switch support. The receive load balancing is achieved by ARP negotiation. The bonding driver intercepts the ARP Replies sent by the local system on their way out and overwrites the source hardware address with the unique hardware address of one of the slaves in the bond such that different peers use different hardware addresses for the server.

---

### Post by yanman on 2008-05-18
Thanks tcpip4lyfe!!

I got this working and it fails over nice and quickly. My problem at the moment is that my 2 adapters can both fail temporarily. They can be restored if I do ifdown and ifup but it doesnt happen automatically. ifenslave helps me with this as I can keep going easily with just 1 adapter lost however I need to login manually and restart the problem interface, otherwise when the remaining good one dies it will have no working inteface to fail back to (unless ifenslave and mode1 do actually disable the redundant adapter?). Is there any way I can script this as part of the fail-over mechanism?

[edit] I suppose I could simply add a script that pings the gateway, and if there is no response it restarts eth0 and eth1? Is that easy to do? (I'm a script novice)

---

### Post by HyRax on 2008-05-18
What a top-notch, simple and very useful post! I've got a spare port on my motherboard that will now find a use (if only just to play with it and to try out loading). Thanks a lot! :D

---

### Post by telecomando on 2008-06-27
You forgot the e in gateway... 
but great job!

---

### Post by tcpip4lyfe on 2008-08-05
> **telecomando said:**
> You forgot the e in gateway... 
but great job!

Whoops.

---

### Post by tyronenguyen on 2008-08-16
Thanks for the guide!

One question though... how do eth0 and eth1 get configured?  Is it in the /etc/network/interfaces file as well?

---

### Post by jvc26 on 2008-08-18
eth0 and eth1 are configured - they are bound into the bonded interface bond0.

The line below does the enslaving of the two interfaces to the bond, with the settings of the bond0 interface.

```

post-up ifenslave bond0 eth0 eth1

```

Il

---

### Post by 4tro on 2008-11-10
Thanks for this howto, it worked perfectly on our redundant servers

---

### Post by amitbiswas on 2010-01-25
Hi Guys,
I want to implement the fail over gateway for local network.
My /etc/network/interface file as below
##########################
# The loopback network interface
auto lo
iface lo inet loopback
        address 127.0.0.1
        netmast 255.0.0.0

# The primary network interface
auto eth0
iface eth0 inet static
        address 192.168.1.1
        netmask 255.255.254.0
        network 192.168.0.0
        broadcast 192.168.1.255

# The WAN interface 1
auto eth1
iface eth1 inet static
        address xxx.xxx.xxx.xxx
        netmask xxx.xxx.xxx.xxx
        network xxx.xxx.xxx.xxx
        broadcast xxx.xxx.xxx.xxx
        gateway xxx.xxx.xxx.xxx
        dns-nameservers xxx.xxx.xxx.xxx

# The WAN interface 2
auto eth2
iface eth2 inet static
        address xxx.xxx.xxx.xxx
        netmask xxx.xxx.xxx.xxx
        network xxx.xxx.xxx.xxx
        broadcast xxx.xxx.xxx.xxx
        gateway xxx.xxx.xxx.xxx
        dns-nameservers xxx.xxx.xxx.xxx

I like local LAN to use gateway from WAN interface 2 upon WAN interface 1 fails.

Any help on this will be much appreciated.
Thanks you,
Amit

---

### Post by miker95 on 2013-02-16
Thank you so much! I had been working on this for a few hours with other online tutorials, and each one I did my server wouldn't have internet (couldn't even ping the default gateway). But this one worked!

Thanks!

---

### Post by QIII on 2013-02-16
Thank you for sharing.

If a thread has had no activity for about a year or more, it is best to start a new thread of your own.  You will be more likely to get a response.  Please feel free to add a link to this thread in the new one you start.
[I][B]
Thread closed.[/B][/I]

---

