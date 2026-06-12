---
title: "Multiple NIC, no ping to host"
date: 2017-11-16
forum: Networking &amp; Wireless
---

### Post by iw5ejm on 2017-11-16
Ubuntu server 16.04, fresh install on x64.
Here the topology:

internet router (192.168.1.254) ---- enp0s7 (192.168.1.69)
host (192.168.0.70) ----- enp1s8 (192.168.0.69)

Internet works ok but I can't ping 192.168.0.70, only arp ping.

/etc/network/interfaces (note the comments):
```
# The primary network interfaceauto enp0s7
iface enp0s7 inet static
address 192.168.1.69
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
gateway 192.168.1.254
dns-nameservers 8.8.8.8 8.8.4.4


#The GRAF net network interface
auto enp1s8
iface enp1s8 inet static
address 192.168.0.69
netmask 255.255.255.0
network 192.168.0.0
broadcast 192.168.0.255
#gateway 192.168.0.70
#metric 400
#up route add -net 192.168.0.0/24 dev enp1s8
```

results from route -n:
```
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.254   0.0.0.0         UG    0      0        0 enp0s7
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 enp1s8
[FONT=&amp]192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 enp0s7[/FONT]
```

results from arp-scan on enp1s8 interface:
```
Interface: enp1s8, datalink type: EN10MB (Ethernet)
Starting arp-scan 1.8.1 with 256 hosts (http://www.nta-monitor.com/tools/arp-scan/)
192.168.0.70    00:0c:42:fa:05:e2    Routerboard.com


1 packets received by filter, 0 packets dropped by kernel
[COLOR=#28FE14][FONT=&amp]Ending arp-scan 1.8.1: 256 hosts scanned in 1.453 seconds (176.19 hosts/sec). 1 responded[/FONT][/COLOR]
```

I think doesn't matter but ipforward is YES.

Why I can't reach on level 3 host 192.168.0.70? What I'm doing wrong?
I think for what I know and what I read on the web this is the right configuration...doesn't work also uncommenting "up route add -net 192.168.0.0/24 dev enp1s8"

---

### Post by TheFu on 2017-11-17
These lines:```

network 192.168.1.0
broadcast 192.168.1.255
```

aren't needed. If incorrect, they cause issues.  The address and netmask and gateway are sufficient.

You are missing the
```
auto enp0s7

```line.

The use of Routerboard.com is unfortunate.  Best not to mix LAN DNS names with public DNS names.  Limits confusion,   it does.
No need to enable ip-forwarding, unless you want this machine to be a router for other systems on either subnet.

---

### Post by iw5ejm on 2017-11-19
Thanks for the reply.

The auto enp0s7 was an error in copy and paste the code here. I tried to remove broadcast and network line but no change, still the same situation!


Any other info I can give you?


In the future it will be a router (ipforward=yes) but  for the moment I would be happy if I could just ping between the two networks....:(

---

### Post by TheFu on 2017-11-19
[https://arstechnica.com/gadgets/2016/04/the-ars-guide-to-building-a-linux-router-from-scratch/](https://arstechnica.com/gadgets/2016/04/the-ars-guide-to-building-a-linux-router-from-scratch/) might be helpful.

---

### Post by iw5ejm on 2017-11-20
Ok, thanks...but I would like to know if with the upper configuration I should ping hosts in the two lan, right? I can't see anything wrong...

---

