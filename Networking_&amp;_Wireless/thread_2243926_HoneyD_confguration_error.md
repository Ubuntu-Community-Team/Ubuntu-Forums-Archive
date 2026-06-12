---
title: "HoneyD confguration error"
date: 2014-09-12
forum: Networking &amp; Wireless
---

### Post by livez2 on 2014-09-12
I installed ubuntu 14.04 and i have installed  HoneyD in my computer.Here i have shown my Configuration file
 [HTML]
create default
set default default tcp action filtered
set default default udp action filtered
set default default icmp action filtered

create windows
set windows default tcp action filtered
set windows default udp action filtered
set windows default icmp action closed
set windows personality "Microsoft Windows XP Professional SP3"
add windows tcp port 135 open
add windows tcp port 139 open
add windows tcp port 445 open

set windows ethernet "00:0c:38:8d:8c:17"
bind 192.168.10.6 windows


[/HTML]


Here is my eth0 output of ifconfig 

[HTML]
eth0      Link encap:Ethernet  HWaddr 38:60:EF:BE:65:75  
          inet addr:192.168.10.5  Bcast:192.168.10.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)



[/HTML]

My problem is when i run honeyd using ```

sudo honeyd -d -f /home/weever/Honeyd-master/sample-config/honeyd4.conf 

```

The only output that i can see is 
[HTML]honeyd[4219]: listening promiscuously on eth0: (arp or ip proto 47 or (udp and src port 67 and dst port 68) or (ip )) and not ether src 38:60:EF:BE:65:75
honeyd[4219]: Demoting process privileges to uid 65534, gid 6553[/HTML]

It doesn't show any Ip that the new created XP machine got... 
[HTML]
honeyd[4219]: Demoting process privileges to uid 65534, gid 65534

[/HTML]
After that it doesn't display anything not even the ip address that the newly created machine got.

Can someone tell me what i need to do to correct it.When i did it using HoneyDrive the machine got resolved to an ip and it worked correctly.

---

