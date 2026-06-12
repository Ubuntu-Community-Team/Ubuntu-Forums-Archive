---
title: "Policy Routing with VLANs"
date: 2017-02-01
forum: Networking &amp; Wireless
---

### Post by bizzy07 on 2017-02-01
[COLOR=#242729][FONT=Arial]I'm in need of some assistance troubleshooting a policy routing issue.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]I have a linux host with multiple VLANs. I'm trying to create a unique routing table for each VLAN and I can ping bidirectionally between the host and the router on VLAN20, however, on the upstream router I'm seeing ARP requests for remote IPs instead of ARP requests for the gateway or traffic being sent to the gateway from the Linux host.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]
The goal is to have a default route out each VLAN from traffic sourced from IP(s) assigned to that interface.

Linux Host VLAN20: 192.168.20.50[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]Router interface VLAN20: 192.168.20.1[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial][B]
Created the table "vlan20[/B]"[/FONT][/COLOR]
$ cat /etc/iproute2/rt_tables
# # reserved values
# 255 local
254 main
253 default
220 vlan20
0 unspec #
#local
1 inr.ruhep

[COLOR=#242729][FONT=Arial]**Created rule to send all traffic sourced from VLAN20 interface using table vlan20**[/FONT][/COLOR]

$ ip rule show
0: from all lookup local
32765: from all iif eth0.20 lookup vlan20
32766: from all lookup main
32767: from all lookup default

[COLOR=#242729][FONT=Arial]**routing all traffic to the router vlan20 interfac**e[/FONT][/COLOR]

$ ip route list table vlan20
default via 192.168.20.1 dev eth0.20

[COLOR=#242729][FONT=Arial]**testing from linux host**[/FONT][/COLOR]
ping 8.8.8.8 -I eth0.20
[COLOR=#242729][FONT=Arial]PING 8.8.8.8 (8.8.8.8) from 192.168.20.50 eth0.20: 56(84) bytes of data. From 192.168.20.50 icmp_seq=1 Destination Host Unreachable[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial][B]
From Router VLAN20 interface[/B][/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]9.568940 arp who-has 8.8.8.8 tell 192.168.20.50
10.565495 arp who-has 8.8.8.8 tell 192.168.20.50[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]What am I missing here? Thanks for your assistance![/FONT][/COLOR]

---

### Post by geeksmith on 2017-02-01
Does the vlan20 table need a route for the local subnet? Without that I presume it would act strange, kinda like what you're seeing with the ARP traffic for remote hosts.

---

### Post by bizzy07 on 2017-02-01
I added the local network to the route table but seeing the same results.

ip route list table vlan20
default via 192.168.20.1 dev eth0.20 
192.168.20.0/24 dev eth0.20  scope link

---

### Post by geeksmith on 2017-02-01
Does "ip route get 8.8.8.8 dev eth0.20" show you the right route?

I find it odd that the route table wouldn't already have a route for the interface, since it has an address in the subnet. I confess that I haven't done this kind of setup in a long time, and I'm not sure that I ever did it with iproute2. Sorry I'm not much more help. If I get time I'll try to do something similar in my home lab.

---

### Post by bizzy07 on 2017-02-01
If I'm reading the output right, it appears that it's not sending the traffic to the gateway, just out the interface. This seems to match what I'm seeing with the ARP request for 8.8.8.8 going out dev eth0.20.

The first output is using the "main" routing table. As expected, the route is going to the gateway for my wireless network.

 $ ip route get 8.8.8.8
8.8.8.8 via 192.168.1.99 dev wlan0  src 192.168.1.116 
    cache 

:~ $ ip route get 8.8.8.8 dev eth0.20
8.8.8.8 dev eth0.20  src 192.168.20.50 
    cache 




I appreciate your assistance. I added a basic network diagram to the main post.

---

### Post by geeksmith on 2017-02-01
Yes, you're interpreting the output correctly (or at least the same way I'm interpreting it :) ).

I've reviewed a few tutorials on this and I can tell you're on the right path. There's just something missing, and it's tough to see without a bigger picture. It would be helpful if you posted the same information given by the author of this post: [http://superuser.com/questions/638044/source-based-policy-routing-nat-dnat-snat-aka-multi-wans-on-centos-5](http://superuser.com/questions/638044/source-based-policy-routing-nat-dnat-snat-aka-multi-wans-on-centos-5)

---

### Post by The Cog on 2017-02-01
```
$ ip rule show
0: from all lookup local
32765: from all**[COLOR="#FF0000"] iif eth0.20 [/COLOR]**lookup vlan20
32766: from all lookup main
32767: from all lookup default

```
I don't think eth0.20 is your incoming interface, so I don't think it's applying rule 32765.
You may have to use iptables to mangle your packets by adding a fwmark, and then use fwmark instead of iif to select the appropriate routing table. Perhaps:
```
iptables -t mangle -A OUTPUT -j MARK --set-mark 20
ip rule add pref 32765 fwmark 20 table vlan20
```

P.S.
You can see all the vlan tagging on the packets with this tcpdump command:
sudo tcpdump -npe -o eth0
And on re-reading man ping, maybe I'm wrong about iif not being eth0.20. The above tcpdump will tell you if the packet is tagged with vlan20.

---

