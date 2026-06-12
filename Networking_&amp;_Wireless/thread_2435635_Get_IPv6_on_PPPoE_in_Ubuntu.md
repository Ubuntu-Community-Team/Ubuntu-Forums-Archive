---
title: "Get IPv6 on PPPoE in Ubuntu"
date: 2020-01-23
forum: Networking &amp; Wireless
---

### Post by Anquietas on 2020-01-23
Hello,

I have a strange situation here. If anyone can help, please do so.

We're talking about a Linux Box running as Router using Ubuntu 18.04.3 LTS, with 2 interfaces: "lan" - which connects to my internal LAN and "wan" - which connects to my ISP.

However, my ISP requires PPPoE connection, so, basically, the "wan" interface is used only a starter for the ppp0 interface.

**[COLOR="#FF0000"]My problem is that I cannot get IPv6 global address on this server.[/COLOR]**

I am able to successfully connect to my ISP.
I already followed the tutorial from here: [http://gruffi.be/mediawiki/index.php/Ipv6_with_PPPoE_on_Ubuntu](http://gruffi.be/mediawiki/index.php/Ipv6_with_PPPoE_on_Ubuntu) , but it doesn't work for me.

So, here is what I did:

1. /etc/ppp/options:
```
+ipv6 ipv6cp-use-ipaddr
```

2. /etc/sysctl.conf:
```
net.ipv6.conf.all.forwarding=1
net.ipv6.conf.ppp0.accept_ra=2
```

3. /etc/wide-dhcpv6/dhcp6c.conf:
```
interface ppp0 {
    # Request Prefix Delegation on ppp0, and give the received prefix id 0
    send ia-pd 2;
    send ia-na 1;
};

# Use subnets from the prefix with id 0
id-assoc pd 2 {
    prefix-interface lan {
        # Assign subnet 1 to eth0
        sla-len 8; # <----- BELANGRIJK: 8 omdat ons klein net 64 en ons groot 56 is en dat het verschil is
        sla-id 2;
    };
};

id-assoc na 1 { };

```

4. /etc/radvd.conf:
```
interface lan
{
    AdvSendAdvert on;
    prefix ::/64
    {
        AdvOnLink on;
        AdvAutonomous on;
        AdvRouterAddr on;
    };
RDNSS 2001:4860:4860::8888  2001:4860:4860::8844
        {
                # AdvRDNSSLifetime 3600;
        };
};
```

My ISP told me that it doesn't use Router Advertisement, however it uses DHCPv6 Prefix Delegation and offers /64 subnets.

The problem is that I tried more configs from the net, non of them worked for me.

When I "ifconfig ppp0", it says:

```

inet 1.2.3.4 ...
inet6 fe80::xxxx:yyyy

```

No sign of a global IPv6 address.

If I turn on debugging on wide DHCP client and I examine /var/log/syslog, I see that it tries to send Solicit messages to ff02::1:2%ppp0 and the timers reset.
I get no reply.

However, router advertisements are working, both on "ppp0" and on my internal lan, because I have a Default Route: "default via fe80::1" when I "ip -6 r".
However, no global IPv6 address.

[COLOR="#FF0000"]I suspect it something to do with DHCP.
The address is not obtained correcly.[/COLOR]

I can ping:
```

ping6 fe80::1%ppp0
64 bytes from...

```

But when trying to "ping6 google.com", it says: "Beyond scope of source address"

[COLOR="#0000FF"]I need to do 2 things, in the long run:

1. Try to get a global IPv6 address on "ppp0" so my websites can be accesible from IPv6 addresses (DNS already taken care of)

2. I need to forward whatever /64 prefix my ISP gives me, let's say: "2001:abcd:dead:beef::/64" to my internal computers, but using a fixed part for the internal computers.[/COLOR]

For example:

```

Computer 1: 2001:abcd:dead:beef::1/64
Computer 2: 2001:abcd:dead:beef::2/64
Computer 3: 2001:abcd:dead:beef::3/64

```

I do NOT want EUI-64 addresses, NOR do I want Private Addresses.
I want my computers assigned an ORDERly IPv6 address with the prefix given, regardless of the dynamic prefix.

For example, after reboot, I might get "2001:1234:beef:dead::/64".
I want the same Host-part allocation using "*::1", "*::2", and so on...

Thank you !

---

### Post by wildmanne39 on 2020-01-23
Thread closed. Please do not post duplicates, it dilutes community effort.

Please use your other thread here:

[https://ubuntuforums.org/showthread.php?t=2435637](https://ubuntuforums.org/showthread.php?t=2435637)

---

