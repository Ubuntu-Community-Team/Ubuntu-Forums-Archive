---
title: "Masquerading Internet on a lower order NIC"
date: 2015-07-14
forum: Networking &amp; Wireless
---

### Post by Konstantin_Prinz on 2015-07-14
I have struggled with aptly naming the topic. I tried googling it in many ways but never really found a solution for this issue.

I have set up my ubuntu (14.04) VM as a router with three NICs:
eth1: Business Cable Service with fixed IP
eth4: Residential Cable Service with dynamic IP
eth2: Internal Network (10.0.2.0/24) - DHCP and DNS forwarder on this NIC
and a virtual device
tun0: OpenVPN Tunnel (10.8.0.0/24)

eth1 has incoming traffic (e.g. vpn) for the fixed IP and outgoing traffic from the host should use eth1 as well.
all inet traffic from eth4 (10.0.2.0/24) and VPN (10.8.0.0/24) should however be masqueraded over eth4

Now without some trickery, it is impossible to masquerade on something else than the first ordered network adapter.
As soon as I set the (ufw) rule to masquerade on eth4 instead on eth1 the routing fails. I understand (unfortunately not at depth) it has something to do with default routes and I need a route table or something to make this work.
This issue drove me from OS X (where the kernel does not support this) to ubuntu in the hope I can solve it here.

I hope somebody can shed light on the proper way to configure this.

---

### Post by SeijiSensei on 2015-07-15
First you need to set up the routing table properly.  Run the command "route -n" and post the results here in [noparse]```

```[/noparse] tags.

---

### Post by Konstantin_Prinz on 2015-07-15
With masquerading over eth1 it looks like

[COLOR=#000000][FONT=-apple-system-font]```
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         46.140.90.225   0.0.0.0         UG    0      0        0 eth1
10.0.2.0        0.0.0.0         255.255.255.0   U     1      0        0 eth2
10.8.0.0        10.8.0.2        255.255.255.0   UG    0      0        0 tun0
10.8.0.2        0.0.0.0         255.255.255.255 UH    0      0        0 tun0
46.126.200.0    0.0.0.0         255.255.252.0   U     1      0        0 eth4
46.140.90.224   0.0.0.0         255.255.255.248 U     1      0        0 eth1
```


[/FONT][/COLOR]

---

### Post by SeijiSensei on 2015-07-15
OK, the routing table looks fine.  The next step is complicated and will take some experimentation on your part.  You need to set up "source" routing so that packets coming from one network take a different route than the default.  I'll just pass along this link.  [http://blog.scottlowe.org/2013/05/29/a-quick-introduction-to-linux-policy-routing/](http://blog.scottlowe.org/2013/05/29/a-quick-introduction-to-linux-policy-routing/)

I've done this once myself when a client was transitioning between ISPs, but it was so long ago that I don't think I can offer much help.

You'll also need to use SNAT rather than MASQUERADE in this setup. For instance,
```
iptables -t nat -A POSTROUTING -o eth4 -j SNAT --to-source 46.126.200.x
```
with the address 46.126.200.x being the address assigned to eth4.

---

### Post by Konstantin_Prinz on 2015-07-16
> **SeijiSensei said:**
> 
You'll also need to use SNAT rather than MASQUERADE in this setup. For instance,
```
iptables -t nat -A POSTROUTING -o eth4 -j SNAT --to-source 46.126.200.x
```
with the address 46.126.200.x being the address assigned to eth4.

Issue at hand is eth4 has a dynamic IP. From looking at the manpage I couldn't find out if iptables can have an expression like pf where the ip adress is evaluated every time. In pf the notation would be [eth4].

I found [this]("http://askubuntu.com/questions/517561/configuring-two-internet-connections/517617#517617") about source based routing (thanks for the expression and the blog post), which I will try to combine with the blog post.
I'll report back on progress...

---

### Post by SeijiSensei on 2015-07-16
> **Konstantin_Prinz said:**
> Issue at hand is eth4 has a dynamic IP.

I run a script to set up my iptables rules. If you take that approach, you can try this:
```

EXT4=$(ifconfig eth4 | grep 'inet addr' | awk '{print $2}' | head -n 1 | awk -F: '{print $2}')
iptables -t nat -A POSTROUTING -o eth4 -j SNAT --to-source $EXT4

```

---

