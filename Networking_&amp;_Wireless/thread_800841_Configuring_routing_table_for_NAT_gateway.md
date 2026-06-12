---
title: "Configuring routing table for NAT gateway"
date: 2008-05-20
forum: Networking &amp; Wireless
---

### Post by bluedalmatian on 2008-05-20
Im getting a bit confused with the correct routing table entries for a Linux machine acting as a NAT gateway.

Its sitting between a private network on eth1 using IPs in the range 192.168.254.x and the public network on eth0 using x.x.x.40-47 where .40 is the network address and .46 is the ADSL router. ie. the gateway out onto the internet. The subnet mask for the public network is 255.255.255.248.

The gateway machine has 192.168.254.254 on the private net and x.x.x.42 on the public network.

The private network uses DHCP to hand out addresses. The same gateway machine is the DHCP server and that seems to be working OK.

The iptables script I also beleive is correct:

#setup rules for forward chain 
#allow packets which are part of established connexions to go through
/sbin/iptables -I FORWARD  1 -m state --state RELATED,ESTABLISHED -j ACCEPT

#allow new connx requests from internal network (MZ). This allows machines on MZ to establish connections to the Internet but not the
#other way round
/sbin/iptables -A FORWARD -m state --state NEW -i eth0 -j ACCEPT

#provide NAT between MZ & DMZ
modprobe iptables_nat
/sbin/iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE
echo "1" > /proc/sys/net/ipv4/ip_forward


I can SSH into the gateway machine off both the public & private networks, and its providing DHCP service on the private net OK, but it doesnt appear to be routing traffic between the two.

Ive had various entries in the routing table and got myself totally confused. Do they need to be in a particular order because the script keeps giving errors like 'Network unreachable'

Im familiar with how to add entries but Im not sure what they should be anymore.  

Any help appreciated.

Thanks

---

### Post by helgman on 2008-05-20
It's been a while since i worked with iptables but if I'm not mistaken

/sbin/iptables -A FORWARD -m state --state NEW -i eth0 -j ACCEPT

says that new connections coming in on eth0 (public?) should be accepted and

/sbin/iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE

packages passing out eth0 should be masqueraded. I might be way of here but shouldn't new connections be accepted from the private interface (or is that what is happening? As I said, haven't been working with iptables for some time)? Or are you trying to keep the private network from initiating contact?

As for the routing that depends a bit on how the whole setup looks but if you only have the two connected network you only need three routes,

 - one that tells the computer what interface to use when it connects to the public network (should be set up automatically) and

 - one that tells it where to send out packages for the private network (should also be set up automatically) and then

 - the third one is the default route, pointing at you ADSL router.

Since you are going to masquerade your ADSL router don't need routes to the private network. And don't forget to give your private clients the correct default gateway ... ;-)

Does it help?

Regards,
Helgman

---

### Post by bluedalmatian on 2008-05-20
none of the routes are setup automatically. the gateway doesnt use DHCP. The ADSL router isnt providing DHCP, the gateway is, to the internal network only. 

Perhaps a diagram would make things clearer:

[http://homepage.mac.com/woodturners/network.png](http://homepage.mac.com/woodturners/network.png)

The DHCP is providing the gateway address to the clients. Both the internal & external networks are working fine independently. You just cant access the external network from the internal one.

---

### Post by bluedalmatian on 2008-05-20
Helgman

I wondered if it should be eth1 as well, but the example I was following gave the impression it should be eth0. Yes theirs were the same way round as mine, but it may have been a typo.

Andrew

---

### Post by helgman on 2008-05-20
Ok, well ... never mind the routs ... the is always (I think) a rout set up in the routing table to the networks attached to the NIC, these where the two first routs i mentioned.

I just did a setup today (helping out in another thread) and
```
echo 1 > /proc/sys/net/ipv4/ip_forward
iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE
```
was all it took to set up the forwarding. 

Have you tried your setup with only the masquerade and the forwarding set (no filtering)? Just to eliminate that it's some forwarding rule that is blocking the traffic ... you could also try using tshark on both interfaces to monitor the connections, might help when trying to figure out what is happening.

Regards,
Helgman

---

### Post by SpaceTeddy on 2008-05-20
i think helgman is right
you are allowing new connections (SYN Pakets) with this command

```
/sbin/iptables -A FORWARD -m state --state NEW -i eth0 -j ACCEPT
```

But this will only allow incomming connections. The command should hold eth1 at the incoming and eth0 as the outgoing (-o eth0) device.

That should fix the problem.

hope it helps :)

---

### Post by bluedalmatian on 2008-05-21
Right thanks Ive made those changes. Unfortunately it looks like the NAT kernel module is missing as well I've just discovered.:lolflag:

Sendmail (dont even know why it was installed) is hanging the boot process now for some reason. I suspect its the AMD K6 CPU as Ive had compatability problems before. I think I'll ditch the hardware and start again on another machine.

At least now Ive got some clue as to how to configure it.  

Thanks v much.

---

