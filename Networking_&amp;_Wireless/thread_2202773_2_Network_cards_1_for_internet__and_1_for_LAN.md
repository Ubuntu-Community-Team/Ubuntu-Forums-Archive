---
title: "2 Network cards: 1 for internet  and 1 for LAN"
date: 2014-01-31
forum: Networking &amp; Wireless
---

### Post by mjwok on 2014-01-31
Hi,

Apologies if this post is a double up - I can't see to find a that helps.

I have 2 network cards in my workstation. I want to configure one card to be for internet access (eth0) and user the other card (eth1) to connect to my local area network. I've tried using "route" to add route connections to specific hosts on the LAN via eth1 - but every time I enable eth1 internet access dies.

route output without eht1:
```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.254   0.0.0.0         UG    0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

```

route output with both eth0 and eht1:
```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.254   0.0.0.0         UG    0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth1
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

```

Should I be doing this with "route" or is there a better tool that I should be using?

Regards,

Michael

---

### Post by TheFu on 2014-01-31
The 2 interfaces need to be on a different network. That will solve most of the routing issues.  The WAN network needs to have the default gateway and the LAN should probably NOT have a default gateway ... unless there is a router "inside" the LAN.  Is your LAN a small network or business?

If both the LAN and WAN remain on the same subnet ... it will be difficult to do what you want.  You'll need to tweak the subnets and metric numbers too.

BTW, a little more understanding of networking will go a long way.  grc.com/sn episodes 25-35 will explain clearly.

---

### Post by SeijiSensei on 2014-01-31
First, you probably haven't yet enabled IP packet forwarding by uncommenting the "net.ipv4.ip_forward=1" directive in /etc/sysctl.conf.  It's disabled by default as a security protection.  Then, If you want the machines behind the router to be able to access the Internet, you'll need to add a [masquerading]("https://help.ubuntu.com/community/Internet/ConnectionSharing#Ubuntu_Internet_Gateway_Method_.28iptables.29") rule to the iptables ruleset.  (I presume you intend to write a set of iptables rules for at least the externally-facing interface, yes?)

The Internet-facing side of the machine cannot have an arbitrary address.  It must have an address in the same space as the upstream router to which it forwards traffic by default.  Either that is an address you get from your ISP, or an address from another router between your box and the Internet.  As the TheFu says, the machines behind this box should have addresses in an entirely separate space like 192.168.1.0/24.

---

### Post by mjwok on 2014-01-31
Thanks for the responses!

I moved the internal network to a different subnet and it appears to be working a treat. NAS and dev environment are no longer forward facing!
I'll have to review my networking text book :)

Thank you.

---

