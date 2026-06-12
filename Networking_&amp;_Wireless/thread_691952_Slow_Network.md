---
title: "Slow Network"
date: 2008-02-09
forum: Networking &amp; Wireless
---

### Post by jr mcfly on 2008-02-09
I've recently installed Ubuntu 7.10 & so far it's working well, except for network/LAN speed.  eth0 is a wired network connection, and claims to be connected at 100Mb/s, but LAN transfer speeds are maxing out at around 10Mb/s.  I'm connecting to a server running Fedora Linux via an NFS share.  The LAN has several other boxes on it, and all other LAN activity happens at 100Mb/s.  (I've found lots of forum posts about slow network speeds, but haven't found anything that helps - most of those relate to Samba shares.)

Here are some stats:

root@moe:~# lshw -C network
  *-network               
       description: Ethernet interface
       product: VT6102 [Rhine-II]
       vendor: VIA Technologies, Inc.
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth0
       version: 7c
       serial: 00:1a:92:6f:49:f0
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.4.3 duplex=full ip=192.168.7.26 latency=32 link=yes maxlatency=8 mingnt=3 module=via_rhine multicast=yes port=MII speed=100MB/s

Copying a 250 MB file over the NFS share takes 3 1/2 minutes.  The System Monitor shows transfer speeds of about 1.2 MB/s.

I do not believe it's a hardware or network problem.  The PC also has Fedora 8 installed, and when I boot that and connect to the same NFS share and try the same file transfer I get normal LAN transfer speeds of around 100Mb/s (my 250MB file transfers in about 22 seconds).

The fact that it's exactly 10 times slower seems to be telling me that somewhere the connection is being treated as a 10Mbps link rather than 100Mbps.  Where could it be?  There's no firewall running, no other network activity at the time I'm doing this test.  I've tried disabling IPV6, but that doesn't speed things up any.  

Any ideas or suggestions gratefully accepted!

---

### Post by jr mcfly on 2008-02-11
thanks for all the replies.  Well, I threw money at the problem & fixed it. I went out and bought a Dlink DFE-530TX+ fast ethernet card for 10 bucks and installed that. Upon booting, I ran lsmod and found, to my horror, that this card uses exactly the same driver as the NIC built into the motherboard (via_rhine). Crap, thinks I. Then I run lspci and find that the board in fact uses a slightly different chipset (the VT6105). With cautious optimism, I fire up a 250MB file transfer from my NFS share, and it transfers in 22 seconds (11.7 MB/s). Hooray.

The VT6102 is not a new chipset, and according to the Free Software Foundation's list of supported network cards at [https://www.fsf.org/resources/hw/net/wired-ethernet](https://www.fsf.org/resources/hw/net/wired-ethernet), that chipset is "known to work with free GNU/Linux systems". I would argue that this device does not really "work" under Ubuntu, since although it connects OK it operates 10 times slower than its advertised capacity, (it works fine with Fedora, by the way.) But what the hell. I'm up & running now & it only cost me 10 bucks.

---

### Post by Amorphous_Snake on 2008-04-06
Did the VT6105 card work under Ubuntu or under Fedora?

Perhaps you can help me with my problem:
[http://ubuntuforums.org/showpost.php?p=4631559&postcount=1](http://ubuntuforums.org/showpost.php?p=4631559&postcount=1)

---

