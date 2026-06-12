---
title: "global ip address packets don't pass from tap interface to the virtual machine"
date: 2014-11-06
forum: Networking &amp; Wireless
---

### Post by igoryonya2 on 2014-11-06
hi, i have a config:
p6p1(physical nic, connected to isp with no addr promisc) -> pppbr0 (bridge with no addr promisc) -> tap0 (with no addr promisc connected to a vm)

iptables configured:
> iptables -A FORWARD -i p6p1 -j ACCEPT
iptables -A FORWARD -o p6p1 -j ACCEPT

and same rules for pppbr0 and tap0

vm configured with a static ip, provided by an isp:
172.16.21.12/16 gw 172.16.0.0

vm with a route:
-net 0.0.0.0 gw 172.168.0.1

when I ping from a vm to the 172.16 subnet all pings traverse all the way to the vm (I receive replies)
when I ping any global ip internet, don't get any replies back.
when I monitor p6p1, pppbr0 and tap0 for the global internet ip address, being pinged with tcpdump, I see that I get reply packets from those addresses.
when I tcpdump on eth0 in vm, and grep for that same address, it shows nothing.

when I stop tcpdump, it shows the line:
[so many] packets dropped by interface

I've monitored with the tcpdump, and saw, that they get all the way to the tap0 interface, the vm is connected to, but drop somewhere between tap0 of the host and eth0 of the guest.

tcpdump on the guest shows nothing about the global addresses being pinged, but when I stop tcpdump, it displays that so many packets were dropped by interface.

anyone can suggest, what blocks packets

---

