---
title: "Router on different subnet?"
date: 2015-05-02
forum: Networking &amp; Wireless
---

### Post by Jakob Hede Madsen on 2015-05-02
Hello. I have been battling all day with the setup of a new provider.

The router from the provider 'Telenor.dk" is a "TG788vn-v2", and I am using a feature to "assign the public IP to internal IP" AKA 'bridge mode'.

When I do this with dhcp I get a public IP with a net mask 255.0.0.0 and an IP which is 85.x.x.x, and the router has IP 94.x.x.x.

The UbuntuBox I want to use as a router/firewall just says "network unreachable".
(It works when not in public IP, i.e. behind NAT).

My Netgear WNDR3700 running openwork also chokes on this network, whereas it worked with public IP on my previous provider.
Oddly my Mac seems to be able to use this network, when I assign the public IP directly to it, so it seems to be able to somehow 'compensate'.

AM i correct in assuming that the reason why this public IP setup throws off both my Ubuntubox and Openwrt router is because Linux refuses to use an IP on a different subnet as default route?

Is this problem solvable by doing something on the UbuntuBox, such as 'static route' or the like?

Or is the problem possibly something else?

I can provide more info, but firstly I wanted to focus on the subnet-discrepancy as I perceive it.

Kind regards, Jakob.

---

### Post by sandyd on 2015-05-03
> **Jakob Hede Madsen said:**
> Hello. I have been battling all day with the setup of a new provider.

The router from the provider 'Telenor.dk" is a "TG788vn-v2", and I am using a feature to "assign the public IP to internal IP" AKA 'bridge mode'.

When I do this with dhcp I get a public IP with a net mask 255.0.0.0 and an IP which is 85.x.x.x, and the router has IP 94.x.x.x.

The UbuntuBox I want to use as a router/firewall just says "network unreachable".
(It works when not in public IP, i.e. behind NAT).

My Netgear WNDR3700 running openwork also chokes on this network, whereas it worked with public IP on my previous provider.
Oddly my Mac seems to be able to use this network, when I assign the public IP directly to it, so it seems to be able to somehow 'compensate'.

AM i correct in assuming that the reason why this public IP setup throws off both my Ubuntubox and Openwrt router is because Linux refuses to use an IP on a different subnet as default route?

Is this problem solvable by doing something on the UbuntuBox, such as 'static route' or the like?

Or is the problem possibly something else?

I can provide more info, but firstly I wanted to focus on the subnet-discrepancy as I perceive it.

Kind regards, Jakob.

Linux doesn't like it when you give it an IP that is on a different subnet.

That goes for BSD OSes such as pfSense as well.

Windows seems to accept it, and as you mentioned, so does mac.

The main issue here is that while it is easy to get it working with static configuration (i.e. see below)
```

route add -host <iphere> dev eth0
route add default gw <iphere>
```I'm not sure if there is any way to get it to work using DHCP.
You may have to fiddle around with /etc/dhcp/dhclient-enter-hooks.d to get it working unless you have [access to the actual DHCP server]("http://serverfault.com/questions/536612/configure-dhcpd-with-assigned-ip-address-and-gateway-on-different-subnets-for-kv").

---

### Post by Jakob Hede Madsen on 2015-05-03
Thank you - that worked!

I added:

```

post-up route add 94.x.x.x/32 dev eth0
post-up route add default gw 94.x.x.x
```

to /etc/network/interfaces, so it looks like this:

```

auto    eth0
iface eth0 inet dhcp
post-up route add 94.x.x.x/32 dev eth0
post-up route add default gw 94.x.x.x
```

with 94.x.x.x being the ip of the gateway.

I noticed from the [linked article]("http://serverfault.com/questions/536612/configure-dhcpd-with-assigned-ip-address-and-gateway-on-different-subnets-for-kv"), that I should write '/32' behind the gateway-ip … would never have worked that out myself, but it makes sort of sense … ;-)


That is good for now, but hardcoding ips under dhcp is bad style, so I wonder if there is some way to soft code the gateway-ip from the provided dhcp answer - something like:
```

auto    eth0
iface eth0 inet dhcp
post-up route add $provided-gateway-ip/32 dev eth0
post-up route add default gw $provided-gateway-ip
```


with "$provided-gateway-ip" being my 'suggestion'.

---

