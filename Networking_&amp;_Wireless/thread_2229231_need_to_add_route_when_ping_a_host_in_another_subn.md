---
title: "need to add route when ping a host in another subnet?"
date: 2014-06-11
forum: Networking &amp; Wireless
---

### Post by herbert6 on 2014-06-11
[COLOR=#000000][FONT=Arial]My host IP is 192.168.2.178/24
[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]and Previously my route table looks like:
[/FONT][/COLOR]
    [B]Kernel IP routing table
    Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
    192.168.2.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
    0.0.0.0         192.168.2.5     0.0.0.0         UG    0      0        0 eth0[/B]

[COLOR=#000000][FONT=Arial]I want to ping 192.168.10.21/24.which is located in another subnet. Ping failed first.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]But after I add this route:[/FONT][/COLOR]
    **route add -net 192.168.10.0 netmask 255.255.255.0 dev eth0**
[COLOR=#000000][FONT=Arial]now my route table looks like this:
[/FONT][/COLOR]
    [B]Kernel IP routing table
    Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
    192.168.2.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
    192.168.10.0    0.0.0.0         255.255.255.0   U     0      0        0 eth0
    0.0.0.0         192.168.2.5     0.0.0.0         UG    0      0        0 eth0[/B]
[COLOR=#000000][FONT=Arial]and I can ping.

[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]The question is :[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]In the previous case, ping 192.168.10.21 would apply the last rule and use the default gateway(192.168.2.5).[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]In the later case, ping 192.168.10.21 would apply the second rule and still use the default gateway(192.168.2.5).[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Why came out different result? What makes the difference?
[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Thanks a lot in advance![/FONT][/COLOR]

---

