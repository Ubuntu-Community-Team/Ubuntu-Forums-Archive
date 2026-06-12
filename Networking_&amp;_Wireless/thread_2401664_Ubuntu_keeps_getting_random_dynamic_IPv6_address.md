---
title: "Ubuntu keeps getting random dynamic IPv6 address"
date: 2018-09-20
forum: Networking &amp; Wireless
---

### Post by courtney2 on 2018-09-20
EDIT: I'm rewriting this from scratch as I found out the culprit to my original topic, but not the solution.

My server has a static IPv6 address assigned to it. We will say it's aaaa:bbbb:cccc::10
It also has a link local address of fe80:1111:2222:3333

Out of left field, I will get this random dynamic global IPv6 address which is a mish-mash of my IPv6 network and a portion of my link-local address, like:
aaaa:bbbb:2222:3333

This completely shuts down all my IPv6 networking once this address shows up, it does not go away. And is impossible to Keep removed. I don't have DHCP enabled, 
I have these in my sysctl.conf:

net.ipv6.conf.all.autoconf=0
net.ipv6.conf.default.autoconf=0

I will even manually delete the address with the ip tool, and moments later the address will show back up. This is a SolusVM generated Ubuntu 14.04 install

---

### Post by courtney2 on 2018-09-22
```

network:
    version: 2
    renderer: networkd
    ethernets:
        eth0:
            addresses:
            - 1.2.3.4/24
            - 1234:abcd:4::10/64
            gateway4: 1.2.3.1
            gateway6: 1234:abcd:4::1
            nameservers:
                addresses:
                - 2001:4860:4860::8844
                - 2001:4860:4860::8888
                - 8.8.8.8
                - 8.8.4.4
                search: []

```

Basically, I added the renderer line and that seemed to work. BUT. ping6 will work great for maybe a minute or two, and then it will go back to just sending 
```

Destination unreachable: Address unreachable

```

I just noticed that there's this completely unknown, no idea where it's coming from IPv6 address and it's trying to use that. It is in none of my configs that I can see

---

### Post by courtney2 on 2018-09-24
It has nothing to do with the configuration it seems. This random "dynamic" address just shows up out of nowhere and crashes the party. So I'll have:

2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qlen 1000
    inet6 ipv6:that:i:want/64 scope global 
       valid_lft forever preferred_lft forever
    inet6 link:local/64 scope link 
       valid_lft forever preferred_lft forever

Then out of nowhere get an IPv6 address from the same network that has "scope global dynamic" at the end. And once that address shows up, all IPv6 traffic fails

---

### Post by ve3dcl on 2019-02-08
Hi,

I'm experiencing the same problem (hence why I registered onto the ubuntu forum).  Were you able to resolve your problem?

Thank you,

---

### Post by billy.j.subs on 2019-03-11
Now I'm no ubuntu expert but I did have the same issue.

I have the following values in the /etc/sysctl.conf but IPV6 still rasied its ugly head.

net.ipv6.conf.all.disable_ipv6 = 1
net.ipv6.conf.default.disable_ipv6 = 1
net.ipv6.conf.lo.disable_ipv6 = 1

I can only assume that after an 'apt upgrade' that the setting was enabled in my network interface to enable ipv6 - in the gui. I disabled this via the gui and normal service was resumed.

---

