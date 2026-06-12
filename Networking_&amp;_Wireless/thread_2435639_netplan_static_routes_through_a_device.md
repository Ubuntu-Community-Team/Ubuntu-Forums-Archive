---
title: "netplan static routes through a device"
date: 2020-01-23
forum: Networking &amp; Wireless
---

### Post by irathore on 2020-01-23
I can use netplan to create static routes through a gateway:

network:
    version: 2
    vlans:
        ens8.4093:
           id: 4093
           link: ens8
           dhcp4: yes
           routes:
             - to: 224.0.0.0/4
               via: 10.0.0.1
               on-link: true

In effect it wil do same as below:
 
[COLOR=#000000][FONT=Calibri]/sbin/route -nv add -net 224.0.0.0/4 gw 10.0.0.1
and will add route:

224.0.0.0       10.0.0.1        240.0.0.0       UG    0      0        0 ens8.4093

How do I create this effect
[/FONT][/COLOR]/sbin/route -nv add -net 224.0.0.0/4 dev ens8.4093

This will add route like this:
224.0.0.0       0.0.0.0         240.0.0.0       U     0      0        0 ens8.4093

Both /sbin/route and "ip route" are capable of doing this I tried to use this plan, but it fails to add route and --debug does not show why it ignores this (neither syslog)
network:
    version: 2
    vlans:
        ens8.4093:
           id: 4093
           link: ens8
           dhcp4: yes
           routes:
             - to: 224.0.0.0/4
               via: 0.0.0.0
               on-link: true

---

