---
title: "Problem accessing other subnet after connection hickup"
date: 2014-07-21
forum: Networking &amp; Wireless
---

### Post by bravid on 2014-07-21
Here's the background:

I have 5 separate locations, all connected via MPLS. Each location has it's own Cisco Router (default gateway), Cisco ASA, and an Ubuntu Server (latest LTS release).

Recently we've been having some issues with the T1 lines and as a result, the Ubuntu Servers have been acting up. 

What I'm seeing is the Ubuntu servers in each location occasionally stop being able to access the other locations subnets. The subnets are online and other networks devices don't exhibit any issues (Windows Servers, Printers, Access Points, Desktops, etc., etc.)

Another oddity is that even though the server can't ping the other subnet, the subnet that it's trying to ping is able to ping it just fine.

The only thing I've been able to do to correct the issue has been to restart networking on the impacted Ubuntu Servers. This isn't practical, nor how things should work!

Any thoughts about what's going on? I definitely think it's Ubuntu related.

---

### Post by sedawk on 2014-07-21
You can compare the outputs of commands like "traceroute", "ifconfig -a", "netstat -r", and "arp -a" before and after restaring networking.
Any strange differences, e.g. routing table changes, traceroute using different network paths, or arp listing same target with different MAC?

---

### Post by bravid on 2014-07-21
If I'm looking at routing tables, they are the same for two different servers on my local subnet, but only one is able to access a remote subnet:

Problem server:

```
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
default         vpn             0.0.0.0         UG        0 0          0 eth0
192.168.1.0     *               255.255.255.0   U         0 0          0 eth0

```

Working server:

```
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.168.1.0     *               255.255.255.0   U         0 0          0 eth0
default         vpn             0.0.0.0         UG        0 0          0 eth0

```

I don't think the order entry matters.

Problem server:

```
eth0      Link encap:Ethernet  HWaddr 78:2b:cb:05:02:35
          inet addr:192.168.1.223  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::7a2b:cbff:fe05:235/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:13105015 errors:0 dropped:589331 overruns:0 frame:0
          TX packets:4588648 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1991394895 (1.9 GB)  TX bytes:1639280335 (1.6 GB)

```

Working server:

```
eth0      Link encap:Ethernet  HWaddr 00:0B:CD:1B:8A:E8
          inet addr:192.168.1.212  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20b:cdff:fe1b:8ae8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1288312211 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1468810003 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:732245910 (698.3 MiB)  TX bytes:4263610907 (3.9 GiB)
          Interrupt:193 Memory:f5fe0000-f5ff0000

```

Here's a before and after traceroute...

```

# traceroute 192.168.4.204
traceroute to 192.168.4.204 (192.168.4.204), 30 hops max, 40 byte packets
 1  vpn (192.168.1.252)  1.623 ms  1.714 ms  1.846 ms
 2  10.252.7.2 (10.252.7.2)  7.199 ms  7.236 ms  7.435 ms
 3  10.252.7.9 (10.252.7.9)  16.793 ms  17.681 ms  18.484 ms
 4  * * *
 5  * * *
 6  * * *
 7  * * *
 8  * * *
 9  * * *
10  * * *
11  * * *
12  * * *
13  *
# traceroute 192.168.4.204
traceroute to 192.168.4.204 (192.168.4.204), 30 hops max, 40 byte packets
 1  vpn (192.168.1.252)  1.624 ms  1.610 ms  1.769 ms
 2  10.252.7.2 (10.252.7.2)  7.598 ms  7.713 ms  7.821 ms
 3  10.252.7.9 (10.252.7.9)  16.768 ms  17.416 ms  19.373 ms
 4  192.168.4.204 (192.168.4.204)  18.156 ms  18.647 ms  19.206 ms

```

---

