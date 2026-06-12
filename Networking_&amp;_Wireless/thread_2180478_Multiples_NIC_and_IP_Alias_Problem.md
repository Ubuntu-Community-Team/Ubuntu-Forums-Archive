---
title: "Multiples NIC and IP Alias Problem"
date: 2013-10-13
forum: Networking &amp; Wireless
---

### Post by wtmann2 on 2013-10-13
Hi all,

I setting up a firewall using 12.04 LTS on a machine with 4 network cards (internal, dmz, external 1 and external 2). The two external cards have multiple IP addresses and I've set up NATing for forwarding to internal servers. However, when everything starts up I can see my IP aliases but I can't ping them (neither internally or externally) except for the last configured alias. My situation is as follows:

/etc/network/interfaces

# internal
auto eth0
iface eth0 inet static
    address 10.5.1.29
    netmask 255.255.255.0
    network 10.5.1.0
    broadcast 10.5.1.255

# dmz
auto eth1
iface eth1 inet static
        address 10.6.6.1
        netmask 255.255.255.0
        network 10.6.6.0
        broadcast 10.6.6.255

# internet 1
auto eth2
iface eth2 inet static
        address 217.56.44.130
        netmask 255.255.255.240
        network 217.56.44.128
        broadcast 217.56.44.143
        gateway 217.56.44.129
        # dns-* options are implemented by the resolvconf package, if installed
        dns-nameservers 217.56.44.130 127.0.0.1
        dns-search my.domain.com
        up route add -net 217.56.44.128 netmask 255.255.255.240 dev eth2
        down route del -net 217.56.44.128 netmask 255.255.255.240 dev eth2



auto eth0:0
iface eth0:0 inet static
        address 217.56.44.131
        netmask 255.255.255.240
        network 217.56.44.128
        broadcast 217.56.44.143


[... other 7 addresses ...]


auto eth0:8
iface eth0:8 inet static
        address 217.56.44.140
        netmask 255.255.255.240
        network 217.56.44.128
        broadcast 217.56.44.143


# internet 2
auto eth3
iface eth3 inet static
        address 5.96.32.2
        netmask 255.255.255.240
        network 5.96.32.0
        broadcast 5.96.32.15
        gateway 5.96.32.1



auto eth3:0
iface eth3:0 inet static
        address 5.96.32.3
        netmask 255.255.255.240
        network 5.96.32.0
        broadcast 5.96.32.15





I get no errors when the network starts. My output from ifconfig shows that all addresses are UP and RUNNING (including the aliases). However when I try to ping the aliases, only the 217.56.44.140 responds on eth2 and nothing responds on eth3. The other interfaces work normally. Is there something I'm missing?

Thanks.

---

### Post by The Cog on 2013-10-13
Have you configured the NAT yet, and if so, how is that configured?

I think the NAT would have to be DNAT, in the PREROUTING chain. 

You need to have ip forwarding enabled. There's a commented-out line for this in /etc/sysctl.conf and the command to enable it on the fly is "sysctl net.ipv4.ip_forward=1".

I would use tcpdump to watch and see what's happening on the interfaces - how far the packets are getting. Also you might find this commands like this useful to see what the kernel things should be done with a particular packet:
```
ip route get 217.56.44.131 from 10.5.1.1 iif eth0
```

---

### Post by wtmann2 on 2013-10-13
Thanks for the reply.

I already have DNAT configured in the correct chain. And IP forwarding is also enabled. However I can't ping those addresses even from the server itself. I think they should respond locally but that's not happening.

I'll have a go at tcpdump and the ip command: thanks for the suggestions.

---

