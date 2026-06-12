---
title: "Large number of IP-addressed VLAN subinterfaces on Ubuntu"
date: 2020-03-12
forum: Networking &amp; Wireless
---

### Post by mmmzon on 2020-03-12
Dear community, 

I am trying to add a large number (1024) VLAN-tagged subinterfaces under a single NIC, add /31 IPv4 scope to each VLAN tagged subinterface, and then run (hopefully) PTPD one each and every subinterface for scale testing purposes. For each subinterface, I am using the following syntax to create the interface, assign the IP address (/31 subnet), and bring the interface up. 

```
sudo vconfig add enp0s25 1000
sudo ip addr add 24.95.248.29/31 dev enp0s25.1000
sudo ip link set up enp0s25.1000
sudo vconfig add enp0s25 1001
sudo ip addr add 24.95.248.31/31 dev enp0s25.1001
sudo ip link set up enp0s25.1001
```

I created two subinterfaces for test purposes, resulting in the following route table: 

```
route -nKernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         24.95.248.25    0.0.0.0         UG    10000  0        0 enp0s25
24.95.248.24    0.0.0.0         255.255.255.252 U     0      0        0 enp0s25
24.95.248.28    0.0.0.0         255.255.255.254 U     0      0        0 enp0s25.1000
24.95.248.30    0.0.0.0         255.255.255.254 U     0      0        0 enp0s25.1001
```

It does look solid as far as I am concerned. I enabled routing between interfaces (or so I believe I did) by enablign ip forwarding on IPv4 table

```
echo 1 > /proc/sys/net/ipv4/ip_forward
```

but that still does not allow me to get any response from .31 or .29 tagged subinterfaces on the device, when trying to ping them from outside the device. 

```
 ping 24.95.248.29    PING 24.95.248.29 (24.95.248.29) 56(84) bytes of data.
^C
--- 24.95.248.29 ping statistics ---
5 packets transmitted, 0 received, 100% packet loss, time 4031ms
```


Is there anything else that needs to be does to allow individual tagged subinterafces to route through the default gateway? I checked packet trace (via tshark) and I can see ICMP requests hitting .31 or .29, but there is no ICMP response generated at all. 

Thanks !

M

---

### Post by The Cog on 2020-03-12
First check your firewall to make sure it's not blocking pings. Temporarily disable it would nbe good. 

Strictly speaking, 24.95.248.29/31 is a subnet broadcast address. That might be the problem - broadcast icmp is often disabled. Configuring the interface as point-to-point rather than point-to-multipoint might do the trick though this is a guess. I can't find much but a search for **linux "/31" subnet** did turn this up - see the last post: [https://www.linuxquestions.org/questions/linux-networking-3/31-subnets-support-in-linux-2-6-34-a-924774/](https://www.linuxquestions.org/questions/linux-networking-3/31-subnets-support-in-linux-2-6-34-a-924774/)

I've done that kind of thing with /30 often enough, using the middle two addresses of the 4. I'm not familiar with using smaller subnet

---

### Post by mmmzon on 2020-03-12
> **The Cog said:**
> First check your firewall to make sure it's not blocking pings. Temporarily disable it would be good.

I believe i disabled it explicitly for the time being, since I am in isolated environment for the time begin with no Internet access. I think it is safe to conclude that the firewall is not a concern?

```
ufw statusStatus: inactive 

iptables -L -n
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         


Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         


Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination 
```

I do understand the /31 limitation. The thread did conclude (it seems) that /31 should work but after changing to /30 on tagged subinterface, I am getting through with no issues now.

```
ping 192.168.253.200 -S 24.95.248.26PING 192.168.253.200 (192.168.253.200) 56(84) bytes of data.
64 bytes from 192.168.253.200: icmp_seq=1 ttl=58 time=1.08 ms
64 bytes from 192.168.253.200: icmp_seq=2 ttl=58 time=1.08 ms
64 bytes from 192.168.253.200: icmp_seq=3 ttl=58 time=1.07 ms
^C
--- 192.168.253.200 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2002ms
rtt min/avg/max/mdev = 1.070/1.081/1.087/0.007 ms

ping 192.168.253.200 -S 24.95.248.30
PING 192.168.253.200 (192.168.253.200) 56(84) bytes of data.
64 bytes from 192.168.253.200: icmp_seq=1 ttl=58 time=1.04 ms
64 bytes from 192.168.253.200: icmp_seq=2 ttl=58 time=1.15 ms
64 bytes from 192.168.253.200: icmp_seq=3 ttl=58 time=1.12 ms
^C
--- 192.168.253.200 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2002ms
```

However, I am still unable to ping / reach anything sourcing from interface, i.e.:

```
ping 192.168.253.200 -I enp0s25.1000PING 192.168.253.200 (192.168.253.200) from 24.95.248.30 enp0s25.1000: 56(84) bytes of data.
^C
--- 192.168.253.200 ping statistics ---
9 packets transmitted, 0 received, 100% packet loss, time 8191ms
```

not quite sure why this happens.

---

### Post by mmmzon on 2020-03-12
Looking into the packet captures, it seems that there is some difference  between sourcing from interface (-I dev) and address (-S address). When  -I is used, kernel ARPs for target address directly, not following  routing table, in my case, I see the following:

```
32    1.619721224    d4:c9:ef:e6:03:b8    Broadcast    ARP    46    Who has 192.168.253.200?  Tell 24.95.248.30
```

When using -S option, routing table seems to be used, and default gateway is used in this case. I am not sure why this behavior is different in this case. The only way around it seems to be sourcing everything from target address, but then it kind of defeats the purpose of having multiple tagged subinterfaces on the same physical interface, since everything gets routed across the same gateway anyway. I can add a single host route but that does not scale for my task at hand - I would need a host route for each subinterface, and the kernel obviously will refuse to accept multiple entries for the same host without splitting routing tables.

---

### Post by The Cog on 2020-03-13
If your tagged interface is 24.95.248.30/30, then it exists on a LAN with only 4 addresses. They are the only 4 (2 usable) that you can directly ping. 

Presumably, if your address is 24.95.248.30 then the other computer on that VLAN is 24.95.248.29. This is the only address you could use as a next-hop if you want to talk via it to other addresses like 192*. So you would probably have to go:
```
sudo ip route add 192.168.253.0/24 via 24.95.248.29
ping 192.168.253.200
```
and it should use that interface automatically.

---

### Post by mmmzon on 2020-03-14
Thank you, just FYI i ended up using docker containers, putting a small Ubuntu 18.04 LTS image with PTPD installed, and then ended up creating ~1k of these on the machine with no issues. With macvlan bridge in place, all works like gold.

---

