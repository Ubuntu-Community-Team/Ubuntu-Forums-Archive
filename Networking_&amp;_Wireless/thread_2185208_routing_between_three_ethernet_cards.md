---
title: "routing between three ethernet cards"
date: 2013-11-01
forum: Networking &amp; Wireless
---

### Post by firenetzone on 2013-11-01
I have three network cards installed in my Ubuntu10.04 system. please tell me how to enable routing between all the three and establish a communication between them??:o

---

### Post by tgalati4 on 2013-11-01
You want to bridge the connections.  [https://help.ubuntu.com/community/NetworkConnectionBridge](https://help.ubuntu.com/community/NetworkConnectionBridge) and [https://help.ubuntu.com/community/Network%20Bridge%20with%20a%20Tap!](https://help.ubuntu.com/community/Network%20Bridge%20with%20a%20Tap!).

---

### Post by SeijiSensei on 2013-11-01
Well, unless he needs to route among different subnets.  I would never suggest bridging as the default solution with multiple interfaces.

OP, what *specifically* are you trying to do?  How you treat these interfaces depends on what applications and services you intend to do.

---

### Post by tgalati4 on 2013-11-01
Yes, that is true.  If it was only two cards, then I would propose *bonding*--the ability to increase bandwidth by using 2 cards and combining the throughput of both.  But with 3 cards, then there must be something else going on--so I assumed different networks.

On bonding:  [https://help.ubuntu.com/community/UbuntuBonding](https://help.ubuntu.com/community/UbuntuBonding)

I was banking on a 50/50 proposition.  The OP would say, yes, that is what I want, or no that is not what I want.  Of course the third option:  I have no idea what I want is always in play.

Maybe what the OP wants is two cards bonded together to increase bandwidth, and the third card bridged to support and isolate another network.

---

### Post by The Cog on 2013-11-01
Assuming that you have the IP addressing for the three interfaces sorted out, just edit /etc/sysctl.conf and remove the # from the front of this line: "#net.ipv4.ip_forward=1" and reboot.

You will of course need to make sure that all the devices on the three networks know that your server is the next-hop to be used to get to the other two networks. If you need help on doing that, you will need to be more specific about what you are setting up.

---

### Post by firenetzone on 2013-11-03
Thanks to all for your replies... I would like to further elaborate my  problem. I have networks A, B and C. I want communication between B  & C through A. I mean the services like mail and web of each network  should be available to all the three and i want to monitor the  services form network A using nagios3. please help.:P

---

### Post by SeijiSensei on 2013-11-03
If you attach each network to a separate adapter, and activate packet forwarding by uncommenting "net.ipv4.ip_forward=1" in /etc/sysctl.conf, all three networks will be able to exchange traffic if the common router is designated as their default gateways.  So if 10.10.10.0/24 is connected to eth0 with address 10.10.10.1, all the machines on 10.10.10.0/24 should have 10.10.10.1 as their default gateway.

If you need to route the private networks out to the Internet you'll have to add "masquerading" with an iptables rule.  Suppose 10.10.10.1 connects upstream to an Internet-facing router.  Then you can tell the machine to handle all the Internet traffic from the three networks with a rule like this:

```
/sbin/iptables -t nat -A POSTROUTING -o eth0 -j SNAT --to-source 10.10.10.1
```

---

