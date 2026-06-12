---
title: "Dual NICS (Inside, DMZ) one website on Apache, how do I keep default gw inside"
date: 2014-10-02
forum: Networking &amp; Wireless
---

### Post by david144 on 2014-10-02
I'm trying to setup an ownCloud website on a virtual machine on my ESXi server such that the website can be accessed from computers inside my firewall on eth0 192.168.4.4, and access outside my firewall goes to eth1 10.1.100.3:

[IMG]http://ft.trillian.im/e1bfa9d470eb89d8d546b9e42d0c23d585c4727f/6t2ftTXayaqNUefBRRNEWHnUyqzHy.jpg[/IMG]

The problem I'm having is my firewall can't forward to the DMZ ip because the default gateway is the inside NIC.

I've tried adding a second gateway for the DMZ and metric's to the interfaces and even though my route tables confirm the change traffic still isn't reaching the server.
```

(DOESN'T WORK)
~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.4.1     0.0.0.0         UG    1      0        0 eth0
0.0.0.0         10.1.100.1      0.0.0.0         UG    10     0        0 eth1
10.1.100.0      0.0.0.0         255.255.255.0   U     10     0        0 eth1
192.168.4.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

```

If I change my interfaces to not include a gateway on the inside network, and dump the metrics then traffic reaches the server (nothing is loading but that's a separate apache config problem because at least I know my packets are making it to the interface I want from the outside by tailing the access.log)
```

(WORKS, but not desired)
c10udadm1n6@cloud:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         10.1.100.1      0.0.0.0         UG    0      0        0 eth1
10.1.100.0      0.0.0.0         255.255.255.0   U     0      0        0 eth1
192.168.4.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0

```

The reason I don't just go this route is because I want to have the system use my inside network for all traffic other than this website (NTP, package updates, it has an X desktop with an app for backup to another 192.168.x.x network that I have routed internally)

I've been banging my head against a wall for two days trying to figure out what I'm doing wrong, but I have an almost identical setup on a windows server with nics in both subnets, gateways setup for each nic, metrics applied to make outbound traffic from the server favor the inside network, and a DNAT rule on my firewall to forward a different port for a different website to it and it works fine. I know the ubuntu server has network connectivity on the same broadcast vlans because from the windows server to the ubuntu apache website works on both IP's. It's something about traffic from outside my firewall coming in and the ubuntu host wanting to redirect the response out the inside nic is all I can assume but I see nothing in the syslog and nothing in the apache logs when I have the DNAT forwarding to the DMZ adapter. Simple change of the DNAT rule and I can see ufw blocking packets on the inside NIC in the syslog. (I'm forwarding 65080 from the outside for this particular website) My firewall rules and the DNAT rule are all working correctly but the destination (this ubuntu host) won't respond when the gateways are set for both NICs with the inside nic having a lower metric value.

Anyone have any ideas. Let me know if I need to put up a more detailed diagram, I figure less is usually more since I get pretty wordy.

---

