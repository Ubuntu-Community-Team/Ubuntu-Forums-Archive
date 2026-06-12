---
title: "Disappearing &quot;routeing&quot; table"
date: 2007-01-30
forum: Networking &amp; Wireless
---

### Post by JediDuck on 2007-01-30
Me again, still having some trouble connecting.

As I mentioned in [this post]("http://www.ubuntuforums.org/showthread.php?t=348317"), I managed to get the wifi working once I'd removed the duplicate default gateway.  I then made the mistake of moving my router (which included turning it off) and rebooting my computer.  Result, no connection again.

This is my **new** problem.  I commented out all mention of the wired ethernet card from /etc/networking/interfaces so only the lo and eth1 (the wireless) come up.  However, the routing table is missing and the eth1 has no IP address (big suprise).

So I use the route command to give me the following routing table;

```
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     *               255.255.255.0   U     0      0        0 eth1
default         192.168.0.1     0.0.0.0         UG    0      0        0 eth1
```

But then, if I do

```
sudo /etc/init.d/networking restart
```

or

```
sudo dhclient eth1
```

My eth1 gives me the "NO DHCPOFFERS RECEIVED" message and all the information from the routing table has disappeared.

If I bring the eth0 card back up and plug it in, I can get connected to the router (and the web) through that with no trouble.

When requesting an IP address for eth1 I also get an interesting message from dmesg;

```
SoftMAC: Received deauthentication packet from aa:bb:cc:dd:ee:ff, but that network is unknown
```

Which is strange, because the MAC address is quotes is the correct address for my router.

I'm running 64-bit Edgy on an AMD64. I'm using the BCM43xx drivers and wpa_supplicant. My router is a Netgear DG834v3.  Again, I don't think this is a wifi issue, it feels more like a generic networking problem.  If anyone has any idea on how I can remove all my current network settings (so I can start from scratch) and give me instructions on how to build the wifi side back up I would be really grateful.

Many thanks in advance!

---

### Post by JediDuck on 2007-01-30
After some research, I'm starting to think that manually configured routing tables are *supposed* to disappear on reboot and network restart.  Which kind of explains why my routing tables are disappearing.

So does that mean that this routing information should be set up somewhere else or returned to the computer from the router?

I'm so close that I can smell my wireless connection, I just need that extra little bit...

---

