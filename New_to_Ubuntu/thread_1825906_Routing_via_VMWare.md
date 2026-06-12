---
title: "Routing via VMWare"
date: 2011-08-15
forum: New to Ubuntu
---

### Post by Ziocahn on 2011-08-15
Hi all,

I am very new to Ubuntu / Unix and I am trying to configure the VM's to forward between each other.

Some background information: 

Theres 3 VLAN's and 4 PC's. 
Each PC can ping the interface of the different vlan on the next PC. However pings any further then the outbound interface of the next PC will result in the local gateway returning error 500 - Unreachable.

Below I'll list the connections.
                              Vlan 2
    PC1:Eth1:192.168.2.1---------------- 192.168.2.2:Eth1: PC2
Eth0:192.168.1.1
     |
     |     Vlan 1
     |
Eth0:192.168.1.3
     PC3:Eth1:192.168.3.3 --------------- 192.168.3.4:Eth1: PC4
                                Vlan 3

Above is the topology I set up.

I used Sysctl.ipv4.ip_forward=1 on every computer.

Routing:

I used route add -net 192.168.x.x/24 broadcast X.X.X.255 on the two left PC's for the networks to the right of them.
I gave every PC a default gateway using: route add -net 0.0.0.0/24 gateway 192.168.x.x (Outbound gateway to 2 networks).


Now Traceroute never responds with more then one interface (Even when the one being routed to is 2-3 interfaces away) and I can never ping past the directly connected PC.

Any suggestions for what I can do to fix this or tips? If you need anymore info I will get it here asap!

Adam.

---

### Post by Ziocahn on 2011-08-16
:( Nobody can advise me if I missed any commands?

Here's the routing table of PC3 - Maybe it might shed some light on if I'm doing  configurations wrong,


[IMG]http://imageshack.us/photo/my-images/198/estse.png/[/IMG]
[http://imageshack.us/photo/my-images/198/estse.png/]("http://imageshack.us/photo/my-images/198/estse.png/")

---

### Post by alphacrucis2 on 2011-08-16
> **Ziocahn said:**
> Hi all,

I am very new to Ubuntu / Unix and I am trying to configure the VM's to forward between each other.

Some background information: 

Theres 3 VLAN's and 4 PC's. 
Each PC can ping the interface of the different vlan on the next PC. However pings any further then the outbound interface of the next PC will result in the local gateway returning error 500 - Unreachable.

Below I'll list the connections.
                              Vlan 2
    PC1:Eth1:192.168.2.1---------------- 192.168.2.2:Eth1: PC2
Eth0:192.168.1.1
     |
     |     Vlan 1
     |
Eth0:192.168.1.3
     PC3:Eth1:192.168.3.3 --------------- 192.168.3.4:Eth1: PC4
                                Vlan 3

Above is the topology I set up.

I used Sysctl.ipv4.ip_forward=1 on every computer.

Routing:

I used route add -net 192.168.x.x/24 broadcast X.X.X.255 on the two left PC's for the networks to the right of them.
I gave every PC a default gateway using: route add -net 0.0.0.0/24 gateway 192.168.x.x (Outbound gateway to 2 networks).


Now Traceroute never responds with more then one interface (Even when the one being routed to is 2-3 interfaces away) and I can never ping past the directly connected PC.

Any suggestions for what I can do to fix this or tips? If you need anymore info I will get it here asap!

Adam.


Set dgway on PC2 to point at 192.168.2.1
Set dgway on PC4 to point at 192.168.3.3

Set static route on PC1  192.168.3.0/24 -> 192.168.1.3
Set static route on PC3  192.168.2.0/24 -> 192.168.1.1

ie PC2 goes to PC1 for all destinations. PC4 goes to PC3 for all destinations. PC1 goes to PC3 to get to 192.168.3.0/24. PC3 goes to PC1 to get to 192.168.2.0/24

---

### Post by alphacrucis2 on 2011-08-16
Duplicate post sorry

---

### Post by Ziocahn on 2011-08-16
Hi Alpha,

I always configured them with Default Gateways as well. The only route out of the computers on the right are default gateways to the remainder of the networks.

I did notice if I set there virtual adaptors to Host-Only im VMWare it would allow routing to any network no longer in the VMNet custom defined networks (But still fails for any still in Custom: VMNet1 for example(So pings to 1.1 / 1.2 Fal before they even leave the PC)) - So this indicates my routing set up on Unix should be correct right?

---

### Post by Ziocahn on 2011-08-18
When I turn off connection to the VMnet interfaces (Switching them into host only) I can now ping to the network from that PC. Example I change P2 Vmnet connection 3 to host only, I can ping to network 3. Any idea why this would happen?

---

